---
title: Optimieren der Leistung von Canvas-Apps | Microsoft-Dokumentation
description: Befolgen Sie die Best Practices in diesem Thema, um die Leistung von Canvas-Apps zu steigern, die Sie in PowerApps erstellen.
author: yingchin
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/31/2018
ms.author: yingchin
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9d86bcaf02050da1b3cd0364e28bc4ec05a6407d
ms.sourcegitcommit: 6e579014ebb1f801985b8b4b68b7b768a09559c7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53247584"
---
# <a name="optimize-canvas-app-performance-in-powerapps"></a>Optimieren der Leistung von Canvas-Apps in PowerApps
Microsoft arbeitet beständig daran, die Leistung aller Apps zu verbessern, die auf der PowerApps-Plattform ausgeführt werden. Sie können aber die Best Practices in diesem Thema befolgen, um die Leistung der von Ihnen erstellten Apps noch weiter zu steigern.

Wenn ein Benutzer eine App öffnet, durchläuft sie folgende Ausführungsphasen, bevor eine Benutzeroberfläche angezeigt wird: 
1. **Authentifizierung des Benutzers**: Der Benutzer wird, sofern er diese App zuvor noch nie geöffnet hatte, aufgefordert, sich mit den Anmeldeinformationen anzumelden, die für die Verbindungen der App erforderlich sind. Wenn dieser Benutzer die App erneut öffnet, wird er möglicherweise erneut zur Angabe dieser Informationen aufgefordert, je nach Sicherheitsrichtlinien der Organisation. 
2. **Abrufen der Metadaten**: Die Metadaten werden abgerufen, z.B. die Version der PowerApps-Plattform, auf der die App ausgeführt wird, und die Quellen, aus denen Daten abgerufen werden müssen. 
3. **Initialisieren der App**: Tasks, die in der **OnStart**-Eigenschaft angegeben sind, werden ausgeführt. 
4. **Rendern der Bildschirme**: Der erste Bildschirm, der das Auffüllen der App mit Daten steuert, wird gerendert. Wenn der Benutzer weitere Bildschirme öffnet, rendert die App diese mithilfe des gleichen Prozesses.  

## <a name="limit-data-connections"></a>Einschränken von Datenverbindungen 
**Stellen Sie in ein und derselben App nicht mehr als 30 Verbindungen mit Datenquellen her**. Apps fordern neue Benutzer auf, sich bei jedem Connector anzumelden, daher erhöht jeder Connector die Zeitspanne, die die App zum Starten benötigt. Während der Ausführung einer App erfordert jeder Connector CPU-Ressourcen, Arbeitsspeicher und Netzwerkbandbreite, wenn die App Daten aus einer Quelle anfordert. 

Sie können die Leistung Ihrer App schnell messen, indem Sie während der Ausführung der App die Entwicklertools in [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) oder [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) aktivieren. Ihre App benötigt wahrscheinlich mehr als 15 Sekunden für die Datenrückgabe, wenn sie häufig Daten aus mehr als 30 Datenquellen wie Common Data Service für Apps, Azure SQL, SharePoint und Excel on OneDrive anfordert.  

## <a name="limit-the-number-of-controls"></a>Beschränken der Anzahl von Steuerelementen 
**Fügen Sie einer App nicht mehr als 500 Steuerelemente hinzu**. PowerApps generiert ein HTML-DOM-Element für jedes Steuerelement, das gerendert werden muss. Je mehr Steuerelemente Sie hinzufügen, desto mehr Zeit benötigt PowerApps zum Generieren. 

Sie können in einigen Fällen das gleiche Ergebnis erzielen und für einen schnelleren App-Start sorgen, wenn Sie anstelle von einzelnen Steuerelementen einen Katalog verwenden. Darüber hinaus sollten Sie die Anzahl von Steuerelementtypen im gleichen Bildschirm reduzieren. Einige Steuerelemente (z.B. PDF-Viewer, Datentabellen und Kombinationsfelder) benötigen große Ausführungsskripts, und es dauert länger, sie zu rendern. 

## <a name="optimize-the-onstart-function"></a>Optimieren der OnStart-Funktion
Verwenden Sie die [**ClearCollect**](functions/function-clear-collect-clearcollect.md)-Funktion, um Daten lokal zwischenzuspeichern, wenn sie während der Benutzersitzung nicht geändert werden. Verwenden Sie außerdem die [**Concurrent**](functions/function-concurrent.md)-Funktion, um Datenquellen gleichzeitig zu laden.

Wie in [diesem Referenzthema](functions/function-concurrent.md) veranschaulicht, können Sie **Concurrent** verwenden, um die Zeitspanne zu halbieren, die eine App zum Laden von Daten benötigt.

Ohne die **Concurrent**-Funktion lädt diese Formel jede der vier Tabellen einzeln:

    ClearCollect( Product, '[SalesLT].[Product]' );
    ClearCollect( Customer, '[SalesLT].[Customer]' );
    ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );
    ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )

Sie können dieses Verhalten in den Entwicklertools Ihres Browsers überprüfen:

![ClearCollect, serielle Ausführung](./media/performance-tips/perfconcurrent1.png)
    
Sie können diese Formel in die **Concurrent**-Funktion einschließen, um die gesamten Ausführungsdauer des Vorgangs zu reduzieren:

    Concurrent( 
        ClearCollect( Product, '[SalesLT].[Product]' ),
        ClearCollect( Customer, '[SalesLT].[Customer]' ),
        ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),
        ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' ))
        
Mit dieser Änderung ruft die App die Tabellen parallel ab: 

![ClearCollect, parallele Ausführung](./media/performance-tips/perfconcurrent2.png)  

## <a name="cache-lookup-data"></a>Zwischenspeichern von Suchdaten
Verwenden Sie die **Set**-Funktion, um Daten aus Nachschlagetabellen lokal zwischenzuspeichern und so ein wiederholtes Abrufen von Daten aus der Quelle zu vermeiden. Diese Technik optimiert die Leistung, wenn sich die Daten während einer Sitzung voraussichtlich nicht ändern. Wie in diesem Beispiel werden die Daten einmal aus der Quelle abgerufen. Danach wird lokal auf die Daten verwiesen, bis der Benutzer die App schließt. 

    Set(CustomerOrder, Lookup(Order, id = “123-45-6789”));
    Set(CustomerName, CustomerOrder.Name);
    Set(CustomerAddress, CustomerOrder.Address);
    Set(CustomerEmail, CustomerOrder.Email);
    Set(CustomerPhone, CustomerOrder.Phone);

Kontaktinformationen ändern sich nicht häufig, und das Gleiche gilt für Standardwerte und Benutzerinformationen. Sie können diese Technik also im Allgemeinen auch mit den Funktionen **Defaults** und **User** verwenden. 

## <a name="avoid-controls-dependency-between-screens"></a>Vermeiden der Abhängigkeit von Steuerelementen zwischen Bildschirmen
Wenn der Wert eines Steuerelements vom Wert eines Steuerelements in einem anderen Bildschirm abhängig ist, verwalten Sie die Daten mithilfe einer Variablen, einer Sammlung oder einem Datenquellenverweis.

## <a name="use-global-variables"></a>Verwenden von globalen Variablen
Um den Zustand einer App zwischen Bildschirmen zu übergeben, erstellen oder ändern Sie den Wert einer globalen Variablen, indem Sie die [**Set**](functions/function-set.md)-Funktion anstelle der Funktionen **Navigate** und **UpdateContext** verwenden.

## <a name="use-delegation"></a>Verwenden der Delegierung
Verwenden Sie nach Möglichkeit Funktionen, die die Datenverarbeitung an die Datenquelle delegieren, anstatt Daten zur Verarbeitung auf das lokale Gerät abzurufen. Wenn eine App Daten lokal verarbeiten muss, benötigt dieser Vorgang wesentlich mehr Verarbeitungsleistung, Arbeitsspeicher und Netzwerkbandbreite – insbesondere bei großen Datasets.

Wie [diese Liste](delegation-list.md) zeigt, unterstützen verschiedene Datenquellen die Delegierung aus verschiedenen Funktionen:

![Verwenden der Delegierung](./media/performance-tips/perfdelegation1.png)

SharePoint-Listen unterstützen z.B. die Delegierung aus der [**Filter**](functions/function-filter-lookup.md)-Funktion, aber nicht aus der [**Search**](functions/function-filter-lookup.md)-Funktion. Daher sollten Sie **Filter** anstelle von **Search** verwenden, um Elemente in einem Katalog zu suchen, wenn die SharePoint-Liste mehr als 500 Elemente enthält. Weitere Tipps finden Sie unter [Working with large SharePoint lists in PowerApps](https://powerapps.microsoft.com/blog/powerapps-now-supports-working-with-more-than-256-items-in-sharepoint-lists/) (Arbeiten mit großen SharePoint-Listen in PowerApps, Blogbeitrag). 

## <a name="use-delayed-load"></a>Verwenden des verzögerten Ladens
Aktivieren Sie das [experimentelle Feature](working-with-experimental.md) für das verzögerte Laden, wenn Ihre App über mehr als 10 Bildschirme, keine Regeln und viele Steuerelemente verfügt, die sich auf mehreren Bildschirmen befinden und direkt an die Datenquelle gebunden sind. Wenn Sie diese Art App erstellen und dieses Feature nicht aktivieren, könnte die App-Leistung beeinträchtigt werden, weil die Steuerelemente in allen Bildschirmen aufgefüllt werden müssen – auch in Bildschirmen, die gar nicht geöffnet sind. Darüber hinaus müssen alle Bildschirme der App aktualisiert werden, sobald sich die Datenquelle ändert, weil beispielsweise der Benutzer einen Datensatz hinzufügt.

## <a name="working-with-large-data-sets"></a>Arbeiten mit großen Datasets
Verwenden Sie Datenquellen und Formeln, die delegiert werden können, um die Leistungsfähigkeit Ihrer Apps zu sichern, dafür zu sorgen, dass Benutzer auf alle benötigten Informationen zugreifen können, und die maximale Anzahl von 2000 Datenzeilen für nicht delegierbare Abfragen nicht zu überschreiten. Bei Datensatzspalten, in denen Benutzer Daten suchen, filtern oder sortieren können, sollten die Indizes gemäß den Beschreibungen unter [SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017) und [SharePoint](https://support.office.com/article/Add-an-index-to-a-SharePoint-column-f3f00554-b7dc-44d1-a2ed-d477eac463b0) entworfen werden.  

## <a name="republish-apps-regularly"></a>Regelmäßiges erneutes Veröffentlichen von Apps
Veröffentlichen Sie Ihre Apps neu, um Leistungssteigerungen zu erzielen und von weiteren Features der PowerApps-Plattform zu profitieren. Informationen dazu finden Sie im Blogbeitrag [Republish your apps](https://powerapps.microsoft.com/blog/republish-your-apps-to-get-performance-improvements-and-additional-features/).
