---
title: Übersicht über Connectors für Canvas-Apps | Microsoft-Dokumentation
description: Übersicht über alle verfügbaren Connectors, die Sie verwenden können, um Canvas-Apps zu erstellen
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/28/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f7a053aff947ffd543381956cf725a7e656d8a65
ms.sourcegitcommit: ebe0a9c41b693a2134e9198ffc7e7a8eabee4330
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/28/2018
ms.locfileid: "51276370"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>Übersicht über die Canvas-App-Connectors für PowerApps
Daten bilden das Herzstück der meisten Apps, u.a. bei denen, die Sie in PowerApps erstellen. Daten werden in einer *Datenquelle* gespeichert, und Sie übergeben diese Daten an Ihre App, indem Sie eine *Verbindung* erstellen. Die Verbindung verwendet einen bestimmten *Connector* für die Kommunikation mit der Datenquelle. PowerApps verfügt über Connectors für viele gängige Dienste und lokale Datenquellen, u.a. SharePoint, SQL Server, Office 365, Salesforce und Twitter. Die ersten Schritte zum Hinzufügen von Daten zu einer Canvas-App werden unter [Hinzufügen einer Datenverbindung in PowerApps](add-data-connection.md) beschrieben.

Ein Connector kann **Tabellen** mit Daten oder **Aktionen** bereitstellen. Einige Connectors stellen nur Tabellen bereit, einige nur Aktionen, einige beides. Bei Ihrem Connector kann es sich außerdem um einen standardmäßigen oder einen benutzerdefinierten Connector handeln.

## <a name="tables"></a>Tabellen

Wenn Ihr Connector Tabellen bereitstellt, fügen Sie Ihre Datenquelle hinzu und wählen dann die Tabelle in der Datenquelle aus, die Sie verwalten möchten. PowerApps ruft die Tabellendaten in Ihre App ab und aktualisiert die Daten in Ihrer Datenquelle für Sie. Sie können z.B. eine Datenquelle hinzufügen, die eine Tabelle namens **Lessons** enthält, und dann in der Formularleiste die **Items**-Eigenschaft eines Steuerelements, etwa einen Katalog oder ein Formular, auf diesen Wert festlegen:

 ![Items-Eigenschaft für Quelle mit einfachen Daten](./media/connections-list/ItemPropertyPlain.png)

Sie können die Daten angeben, die von Ihrer App abgerufen werden, indem Sie die **Items**-Eigenschaft des Steuerelements anpassen, das Ihre Daten anzeigt. Als Fortführung des vorherigen Beispiels können Sie die Daten in der Tabelle **Lessons** sortieren oder filtern, indem Sie diesen Namen als Argument für die Funktionen **Search** und **SortByColumn** verwenden. In dieser Abbildung wird durch die Formel, auf die die **Items**-Eigenschaft festgelegt ist, angegeben, dass die Daten basierend auf dem Text in **TextSearchBox1** sortiert und gefiltert werden sollen. 

 ![Items-Eigenschaft für Quelle mit erweiterten Daten](./media/connections-list/ItemPropertyExpanded.png)

Weitere Informationen zum Anpassen Ihrer Formel mit Tabellen finden Sie in den folgenden Themen:

  [Grundlegendes zu Datenquellen in PowerApps](working-with-data-sources.md)<br> 
  [Generieren einer App aus Excel-Daten](get-started-create-from-data.md)<br> 
  [App von Grund auf neu erstellen](get-started-create-from-blank.md)<br>
  [Understand tables and records in PowerApps (Grundlegendes zu Tabellen und Datensätzen in PowerApps)](working-with-tables.md)

  > [!NOTE]
  > Zum Herstellen einer Verbindung mit Daten in einer Excel-Arbeitsmappe muss die Arbeitsmappe in einem Cloudspeicherdienst wie OneDrive gehostet werden. Weitere Informationen finden Sie im Artikel zum [Verbinden mit Cloudspeicher aus PowerApps](connections/cloud-storage-blob-connections.md).

## <a name="actions"></a>Aktionen

Wenn Ihr Connector Aktionen bereitstellt, müssen Sie trotzdem weiterhin wie oben die Datenquelle auswählen. Sie wählen allerdings als nächsten Schritt keine Tabelle aus, sondern stellen manuell eine Verbindung zwischen einem Steuerelement und einer Aktion her, indem Sie die **Items**-Eigenschaft des Steuerelements bearbeiten, das Ihre Daten anzeigen soll. Die Formel, auf die Sie die **Items**-Eigenschaft festlegen, gibt die Aktion an, die Daten abruft. Die App ruft beispielsweise keine Daten ab, wenn Sie eine Verbindung mit Yammer herstellen und dann die **Items**-Eigenschaft auf den Namen der Datenquelle festlegen. Um ein Steuerelement mit Daten aufzufüllen, geben Sie eine Aktion an, wie z.B. **GetMessagesInGroup(5033622).messages**.

![Items-Eigenschaft für Datenquelle für Aktionen](./media/connections-list/ItemPropertyAction.png)

Wenn Sie benutzerdefinierte Datenupdates für Aktionsconnectors verarbeiten müssen, erstellen Sie eine Formel, die die **Patch**-Funktion enthält. Geben Sie in der Formel die Aktion und die Felder an, die Sie an die Aktion binden.  

Weitere Informationen zum Anpassen Ihrer Formel für benutzerdefinierte Updates finden Sie in den folgenden Themen:

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

## <a name="popular-connectors"></a>Gängige Connectors

Diese Tabelle enthält Links zu weiteren Informationen zu den am häufigsten verwendeten Connectors. Eine vollständige Liste der Connectors finden Sie unter [Alle Connectors](#all-standard-connectors).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive for Business](./media/connections-list/onedrive.png) |[**OneDrive for Business**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Office 365-Benutzer](./media/connections-list/office365.png) |[**Office 365-Benutzer**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="standard-and-custom-connectors"></a>Standardmäßige und benutzerdefinierte Connectors
PowerApps bietet *standardmäßige* Connectors für viele häufig genutzte Datenquellen an, wie z.B. die oben genannten. Wenn PowerApps einen Standardconnector für den von Ihnen gewünschten Datenquellentyp bietet, sollten Sie diesen Connector verwenden. Wenn Sie eine Verbindung mit anderen Arten von Datenquellen herstellen möchten, z.B. mit einem von Ihnen erstellten Dienst, finden Sie weitere Informationen unter [Registrieren und Verwenden von benutzerdefinierten Connectors](../canvas-apps/register-custom-api.md).

## <a name="all-standard-connectors"></a>Alle Standardconnectors
Eine vollständige Liste aller Standardconnectors finden Sie in der [Microsoft-Referenz zu Connectors](https://docs.microsoft.com/connectors/). Für Premium-Connectors ist PowerApps-Plan 1 oder 2 erforderlich. Weitere Informationen finden Sie auf der [Seite mit den PowerApps-Plänen](https://powerapps.microsoft.com/pricing/).

In den [PowerApps-Foren](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) können Sie Fragen zu einem bestimmten Connector stellen, und unter [PowerApps Ideas](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas) können Sie Vorschläge für neue Connectors oder anderen Verbesserungen einreichen.
