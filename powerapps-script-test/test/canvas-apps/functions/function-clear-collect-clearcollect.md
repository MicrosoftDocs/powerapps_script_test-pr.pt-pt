---
title: Funktionen „Collect“, „Clear“ und „ClearCollect“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Collect-, Clear- und ClearCollect-Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8a7c52962c23df5f2efcf76c04aeba528e94217c
ms.sourcegitcommit: 464ee88a958dda11c5de5603c608deab6c9cdcab
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48578740"
---
# <a name="collect-clear-and-clearcollect-functions-in-powerapps"></a>Collect-, Clear- und ClearCollect-Funktionen in PowerApps
Erstellt und löscht [Sammlungen](../working-with-data-sources.md#collections) und fügt [Datensätze](../working-with-tables.md#records) zu einer beliebigen [Datenquelle](../working-with-data-sources.md) hinzu.

## <a name="description"></a>Beschreibung
### <a name="collect"></a>Collect
Die **Collect**-Funktion fügt Datensätze zu einer Datenquelle hinzu. Die hinzuzufügenden Elemente können sein:

* Ein einzelner Wert: Der Wert befindet sich im **[Wert](function-value.md)**-Feld eines neuen Datensatzes.  Alle anderen Eigenschaften bleiben [leer](function-isblank-isempty.md).
* Ein Datensatz: Jede benannte Eigenschaft wird in der entsprechenden Eigenschaft des neuen Datensatzes eingefügt.  Alle anderen Eigenschaften bleiben leer.
* Ein [Tabelle](../working-with-tables.md): Jeder Datensatz der Tabelle wird als ein separater Datensatz der Datenquelle hinzugefügt, wie oben beschrieben. Die Tabelle wird nicht als geschachtelte Tabelle zu einen Datensatz hinzugefügt. Umschließen Sie zu diesem Zweck zuerst die Tabelle in einem Datensatz.

Bei Verwendung mit einer Sammlung werden bei Bedarf zusätzliche [Spalten](../working-with-tables.md#columns) erstellt. Die Spalten für andere Datenquellen werden von der Datenquelle vordefiniert, und neue Spalten können nicht hinzugefügt werden.  

Wenn die Datenquelle nicht bereits vorhanden ist, wird eine Sammlung erstellt.

Sammlungen werden manchmal verwendet, um globale Variablen zu halten oder eine temporäre Kopie einer Datenquelle zu erstellen. PowerApps basiert auf Formeln, die automatisch neu berechnet werden, während der Benutzer mit einer App interagiert. Sammlungen haben diesen Vorteil nicht und ihre Verwendung kann das Erstellen und Verstehen Ihrer App erschweren. Lesen Sie vor dem Verwenden einer Sammlung auf diese Weise [Working with Variables (Mit Variablen arbeiten)](../working-with-variables.md).

Sie können auch die **[Patch](function-patch.md)**-Funktion für die Erstellung von Datensätzen in einer Datenquelle verwenden.

**Collect** gibt die geänderte Datenquelle als Tabelle zurück.  **Collect** kann nur in einer [behavior formula (Verhaltensformel)](../working-with-formulas-in-depth.md) verwendet werden.

### <a name="clear"></a>Clear
Die **Clear**-Funktion löscht alle Datensätze einer Sammlung.  Die Spalten der Sammlung bleiben erhalten.

Beachten Sie, dass **Clear** nur bei Sammlungen und nicht bei anderen Datenquellen angewendet wird.  Für diesen Zweck können Sie **[RemoveIf](function-remove-removeif.md)( *DataSource*, TRUE)** verwenden.  Seien Sie vorsichtig, da dies alle Datensätze aus dem Speicher der Datenquelle entfernt und Auswirkungen auf andere Benutzer haben kann.

Sie können die **[Remove](function-remove-removeif.md)**-Funktion verwenden, um Datensätze gezielt zu entfernen.

**Clear** hat keinen Rückgabewert.  Es kann nur in einer Verhaltensformel verwendet werden.

### <a name="clearcollect"></a>ClearCollect
Die **ClearCollect**-Funktion löscht alle Datensätze aus einer Sammlung und fügt anschließend ein anderes Set von Datensätzen zur selben Sammlung hinzu.  Mit einer einzelnen Funktion bietet **ClearCollect** die Kombination von **Clear** und anschließend **Collect**.

**ClearCollect** gibt die geänderte Sammlung als Tabelle zurück.  **ClearCollect** kann nur in einer Verhaltensformel verwendet werden.

## <a name="syntax"></a>Syntax
**Collect**( *Datenquelle*, *Element*, ... )

* *Datenquelle*: Erforderlich. Die Datenquelle, in die Sie Daten hinzufügen möchten.  Wenn nicht bereits vorhanden, wird eine neue Sammlung erstellt.
* *Element(e)*: Erforderlich.  Eine oder mehrere Datensätze oder Tabellen, die der Datenquelle hinzugefügt werden sollen.  

**Clear**( *Auflistung* )

* *Auflistung*: Erforderlich. Die Sammlung, die Sie löschen möchten.

**ClearCollect**( *Auflistung*, *Element*, ... )

* *Auflistung*: Erforderlich. Die Sammlung, die Sie löschen und zu der Sie dann Daten hinzufügen möchten.
* *Element(e)*: Erforderlich.  Eine oder mehrere Datensätze oder Tabellen, die der Datenquelle hinzugefügt werden sollen.  

## <a name="examples"></a>Beispiele
### <a name="clearing-and-adding-records-to-a-data-source"></a>Löschen und Hinzufügen von Datensätzen zu einer Datenquelle
In diesen Beispielen löschen und fügen Sie Daten zu einer Sammlung mit dem Namen **IceCream** hinzu.  Die Datenquelle beginnt mit dem folgenden Inhalt:

![](media/function-clear-collect-clearcollect/icecream.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **ClearCollect( IceCream, {&nbsp;Flavor:&nbsp;"Strawberry",&nbsp;Quantity:&nbsp;300&nbsp;} )** |Löscht alle Daten aus der Sammlung **IceCream**, und fügt anschließend einen Datensatz hinzu, der eine Menge von Erdbeereis enthält. |<style> img { max-width: none } </style> ![](media/function-clear-collect-clearcollect/icecream-clearcollect.png)<br><br>Die Datenquelle **IceCream** wurde auch geändert. |
| **Collect( IceCream, {&nbsp;Flavor:&nbsp;"Pistachio",&nbsp;Quantity:&nbsp;40&nbsp;}, {&nbsp;Flavor:&nbsp;"Orange",&nbsp;Quantity:&nbsp;200&nbsp;}  )** |Fügt zwei Datensätze zur Sammlung **IceCream** hinzu, die eine Menge von Pistazien- und Orangeneis enthält. |![](media/function-clear-collect-clearcollect/icecream-collect.png)<br><br>Die Datenquelle **IceCream** wurde auch geändert. |
| **Clear( IceCream )** |Entfernt alle Datensätze aus der Sammlung **IceCream**. |![](media/function-clear-collect-clearcollect/icecream-clear.png)<br><br>Die Datenquelle **IceCream** wurde auch geändert. |

### <a name="collect-a-static-list"></a>Sammeln einer statischen Liste

1. Fügen Sie eine Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Funktion fest:<br>**Collect(Products, &quot;Europa&quot;, &quot;Ganymede&quot;, &quot;Callisto&quot;)**
   
    Diese Funktion erstellt eine Sammlung mit dem Namen **Products**, die eine Zeile für jeden der drei Produktnamen enthält.
    
1. Halten Sie die ALT-TASTE gedrückt, und wählen Sie die Schaltfläche aus.

1. (Optional) Klicken Sie im **Dateimenü** auf **Sammlungen**, um die erstellte Sammlung als Vorschau anzuzeigen.

### <a name="put-a-sharepoint-list-into-a-collection"></a>Einfügen einer SharePoint-Liste in eine Sammlung

1. [Herstellen einer Verbindung mit einer SharePoint-Liste](../connect-to-sharepoint.md) 

1. Fügen Sie eine Schaltfläche hinzu, und legen Sie die folgende Funktion für die **[OnSelect](../controls/properties-core.md)**-Eigenschaft fest, ersetzen Sie hierbei *ListName* durch den Namen der SharePoint-Liste:<br>
**Collect**(**MySPCollection**, *ListName*)

    Diese Funktion erstellt eine Sammlung namens **MySPCollection**, die die gleichen Daten wie Ihre SharePoint-Liste enthält.
    
1. Halten Sie die ALT-TASTE gedrückt, und wählen Sie die Schaltfläche aus.

1. (Optional) Klicken Sie im **Dateimenü** auf **Sammlungen**, um die erstellte Sammlung als Vorschau anzuzeigen.

Weitere Informationen zum Anzeigen von Daten aus einer SharePoint-Liste (z.B. Datumsangaben, Optionen und Personen) in einem Katalog finden Sie unter [Anzeigen von Daten in einem Katalog](../connections/connection-sharepoint-online.md#show-data-in-a-gallery). Informationen zum Anzeigen von Daten in einem Formular (mit Dropdownlisten, Datumsauswahl und Personenauswahl) finden Sie im Artikel zu den [Steuerelementen „Formular anzeigen“ und „Formular bearbeiten“](../controls/control-form-detail.md).
