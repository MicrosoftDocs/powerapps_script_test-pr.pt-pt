---
title: Funktionen „Remove“ und „RemoveIf“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Remove“ und „RemoveIf“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a6887694f2cc64cd44dcdc74e7769ce874872f70
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863276"
---
# <a name="remove-and-removeif-functions-in-powerapps"></a>Die Funktionen „Remove“ und „RemoveIf“ in PowerApps
Entfernt [Datensätze](../working-with-tables.md#records) aus einer [Datenquelle](../working-with-data-sources.md).

## <a name="description"></a>Beschreibung
### <a name="remove-function"></a>Remove-Funktion
Verwenden Sie die **Remove**-Funktion, um einen bestimmten Datensatz oder bestimmte Datensätze aus einer Datenquelle zu entfernen.  

Für [Sammlungen](../working-with-data-sources.md#collections) muss der gesamte Datensatz übereinstimmen. Sie können das **All**-Argument verwenden, um alle Kopien eines Datensatzes zu entfernen; andernfalls wird nur eine Kopie des Datensatzes entfernt.

### <a name="removeif-function"></a>RemoveIf-Funktion
Verwenden Sie die **RemoveIf**-Funktion,um einen Datensatz oder Datensätze auf Grundlage einer Bedingung oder eine Reihe von Bedingungen zu entfernen. Jede Bedingung kann jede beliebige Formel sein, die **TRUE** oder **FALSE** ergibt, und die auf [Spalten](../working-with-tables.md#columns) der Datenquelle anhand des Namens verweisen kann. Jede Bedingung wird einzeln für jeden Datensatz ausgewertet, und der Eintrag wird entfernt, wenn alle Bedingungen als **TRUE** ausgewertet werden.

**Remove** und **RemoveIf** geben die geänderten Datenquelle als eine [Tabelle](../working-with-tables.md) zurück. Beide Funktionen können nur in [Verhaltensformeln](../working-with-formulas-in-depth.md) geändert werden.

Sie können auch die **[Clear](function-clear-collect-clearcollect.md)**  Funktion verwenden, um alle Datensätze in einer Datenquelle zu entfernen.

### <a name="delegation"></a>Delegierung
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Syntax
**Remove**( *DataSource*, *Record1* [, *Record2*, ... ] [, **All** ] )

* *Datenquelle*: Erforderlich. Die Datenquelle mit den Datensatz bzw. Datensätze, die Sie entfernen möchten.
* *Datensatz/Datensätze*: erforderlich. Der Datensatz oder die Datensätze, die entfernt werden sollen.
* **All**: Optional. In einer Sammlung wird möglicherweise der gleiche Datensatz mehr als einmal angezeigt.  Sie können das **All**-Argument hinzufügen, um alle Kopien des Datensatzes zu entfernen.

**Remove**( *DataSource*, *Table* [, **All** ] )

* *Datenquelle*: Erforderlich. Die Datenquelle, die die Datensätze enthält, die Sie entfernen möchten.
* *Tabelle*: erforderlich. Eine Tabelle von zu entfernenden Datensätzen
* **All**: Optional. In einer Sammlung wird möglicherweise der gleiche Datensatz mehr als einmal angezeigt.  Sie können das **All**-Argument hinzufügen, um alle Kopien des Datensatzes zu entfernen.

**RemoveIf**( *DataSource*, *Condition* [, ... ] )

* *Datenquelle*: Erforderlich. Die Datenquelle mit den Datensatz bzw. Datensätze, die Sie entfernen möchten.
* *Bedingung(en)* : Erforderlich. Eine Formel, die **TRUE** für die zu ersetzenden Datensätze ergibt.  Sie können auch die Spaltennamen aus *DataSource* in der Formel verwenden.  Wenn Sie mehrere *Bedingungen* angeben, müssen alle für Datensätze oder zu entfernende Datensätze zu **TRUE** ausgewertet werden.

## <a name="examples"></a>Beispiele
In diesen Beispielen entfernen Sie einen Datensatz oder Datensätze aus einer Datenquelle mit dem Namen **IceCream** (Eiscreme), die mit den Daten in dieser Tabelle beginnt:

![](media/function-remove-removeif/icecream.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) )** |Entfernt den Datensatz **Chocolate** (Schokolade) aus der Datenquelle |<style> img { max-width: none } </style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;) )** |Entfernt zwei Datensätze aus der Datenquelle. |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150 )** |Entfernt die Datensätze mit einer **Quantity** (Menge) größer als **150**. |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150, Left(&nbsp;Flavor,&nbsp;1&nbsp;) = "S" )** |Entfernt die Datensätze mit einer **Quantity** (Menge) größer als 150 und einem **Flavor** (Geschmack), der mit **S** beginnt |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **RemoveIf(&nbsp;IceCream, true )** |Entfernt alle Einträge aus der Datenquelle |![](media/function-remove-removeif/icecream-empty.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |

### <a name="step-by-step"></a>Schritt für Schritt
1. Importieren oder erstellen Sie eine Sammlung mit dem Namen **Inventory** (Lagerbestand), und zeigen Sie diese in einem Katalog an, wie unter [Show images and text in a gallery, including gallery selection, sort, and filter (Anzeigen von Bildern und Text in einem Katalog, einschließlich Auswählen, Sortieren und Filtern des Katalogs)](../show-images-text-gallery-sort-filter.md) beschrieben.
2. Legen Sie im Katalog die **[OnSelect](../controls/properties-core.md)**-Eigenschaft des Bilds auf diesen Ausdruck fest:<br>**Remove(Inventory, ThisItem)**
3. Drücken Sie F5, und wählen Sie ein Bild im Katalog.<br>Das Element wird aus dem Katalog und der Sammlung entfernt.

