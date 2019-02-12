---
title: Funktionen „Update“ und „UpdateIf“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Update“ und „UpdateIf“ in PowerApps
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
ms.openlocfilehash: d74f05c87cd5b9a3e7aed7891c6d2aaa54adfd1a
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834306"
---
# <a name="update-and-updateif-functions-in-powerapps"></a>Funktionen „Update“ und „UpdateIf“ in PowerApps
Aktualisieren [Datensätze](../working-with-tables.md#records) in einer [Datenquelle](../working-with-data-sources.md)

## <a name="description"></a>Beschreibung
### <a name="update-function"></a>„Update“-Funktion
Verwenden Sie die **Update**-Funktion, um einen gesamten Datensatz in einer Datenquelle zu ersetzen. Im Gegensatz dazu ändern die Funktionen **UpdateIf** und **[Patch](function-patch.md)** einen oder mehrere Werte in einem Datensatz, ohne dabei die anderen Werte zu ändern.

Bei einer [Sammlung](../working-with-data-sources.md#collections) muss der gesamte Datensatz übereinstimmen. Sammlungen lassen doppelte Datensätze zu, sodass mehrere Datensätze übereinstimmen könnten. Sie können das **All**-Argument verwenden, um alle Kopien eines Datensatzes zu aktualisieren; andernfalls wird nur eine Kopie des Datensatzes aktualisiert.

Wenn die Datenquelle den Wert einer Spalte automatisch generiert, muss der Wert dieser [Spalte](../working-with-tables.md#columns) erneut bestätigt werden.

### <a name="updateif-function"></a>„UpdateIf“-Funktion
Verwenden Sie die **UpdateIf**-Funktion, um einen oder mehrere Werte in einem oder mehreren Datensätzen zu ändern, die mit mindestens einer Bedingungen übereinstimmen. Bei der Bedingung kann es sich um jede Formel handeln, die zu **TRUE** oder **FALSE** führt und über den Namen auf Spalten der Datenquelle verweisen kann. Die Funktion wertet die Bedingung für jeden Datensatz aus und bearbeitet jeden Datensatz, für den das Ergebnis **TRUE** ist.  

Um eine Änderung anzugeben, verwenden Sie einen Änderungsdatensatz, der neue Eigenschaftenwerte enthält. Wenn Sie diesen Änderungsdatensatz in geschweifte Klammern eingebunden bereitstellen, können Eigenschaftenformeln auf Eigenschaften des Datensatzes verweisen, der bearbeitet wird. Sie können dieses Verhalten verwenden, um Datensätze anhand einer Formel zu ändern.

Ähnlich wie die **UpdateIf**-Funktion können Sie auch die **[Patch](function-patch.md)**-Funktion verwenden, um bestimmte Spalten eines Datensatzes zu ändern, ohne dass sich dies auf andere Spalten auswirkt.

Sowohl **Update** als auch **UpdateIf** geben die geänderte Datenquelle als [Tabelle](../working-with-tables.md) zurück. Sie müssen beide Funktionen in einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

### <a name="delegation"></a>Delegierung
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Syntax
**Update**( *Datenquelle*, *AlterDatensatz*, *NeuerDatensatz* [, **All** ] )

* *Datenquelle*: Erforderlich. Die Datenquelle, die den Datensatz enthält, den Sie ersetzen möchten.
* *AlterDatensatz*: Erforderlich. Der zu ersetzende Datensatz.
* *NeuerDatensatz*: Erforderlich. Der Ersatzdatensatz. Dabei handelt es sich nicht um einen Änderungsdatensatz. Der gesamte Datensatz wird ersetzt, und fehlende Eigenschaften werden als *blank* angezeigt.
* **All**: Optional. In einer Sammlung wird möglicherweise der gleiche Datensatz mehr als einmal angezeigt. Geben Sie das **All**-Argument an, um alle Kopien des Datensatzes zu entfernen.

**UpdateIf**( *Datenquelle*, *Bedingung1*, *Änderungsdatensatz1* [, *Bedingung2*, *Änderungsdatensatz2*, ... ] )

* *Datenquelle*: Erforderlich. Die Datenquelle, die den Datensatz bzw. die Datensätze enthält, die Sie ändern möchten.
* *Bedingung(en)*: Erforderlich. Eine Formel, die für den Datensatz bzw. die Datensätze, die Sie ändern möchten, **TRUE** ergibt.  Sie können Spaltennamen von *Datenquelle* in der Formel verwenden.  
* *Änderungsdatensatz bzw. -sätze*: Erforderlich.  Für jede entsprechende Bedingung ein Änderungsdatensatz mit neuen Eigenschaftenwerten, die auf Datensätze von *Datenquelle* angewandt werden, die die Bedingung erfüllen. Wenn Sie den Datensatz in geschweifte Klammern eingebunden bereitstellen, können Eigenschaftenwerte des vorhandenen Datensatzes in den Eigenschaftenformeln verwendet werden.

## <a name="examples"></a>Beispiele
In diesen Beispielen ersetzen oder ändern Sie Datensätze in einer Datenquelle mit dem Namen **IceCream**, die mit den Daten in dieser Tabelle beginnt:

![](media/function-update-updateif/icecream.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Update(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;), {&nbsp;ID:&nbsp;1,&nbsp;Flavor:&nbsp;"Mint&nbsp;Chocolate",&nbsp;Quantity:150&nbsp;} )** |Ersetzt einen Datensatz aus der Datenquelle |<style> img { max-width: none } </style> ![](media/function-update-updateif/icecream-mint.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **UpdateIf(&nbsp;IceCream, Quantity > 175, {&nbsp;Quantity:&nbsp;Quantity&nbsp;+&nbsp;10&nbsp;} )** |Ändert Datensätze, bei der **Quantity** größer als **150** ist.  Das Feld **Quantity** wird um 10 erhöht, und es werden keine anderen Felder geändert. |![](media/function-update-updateif/icecream-mint-plus10.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **Update(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream, Flavor="Strawberry"&nbsp;)&nbsp;),<br>{&nbsp;ID:&nbsp;3, Flavor:&nbsp;"Strawberry Swirl"} )** |Ersetzt einen Datensatz aus der Datenquelle Die Eigenschaft **Quantity** wurde im Ersatzdatensatz nicht bereitgestellt. Diese Eigenschaft bleibt im Ergebnis also *blank*. |![](media/function-update-updateif/icecream-mint-swirl.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **UpdateIf(&nbsp;IceCream, true, {&nbsp;Quantity:&nbsp;0&nbsp;} )** |Legt den Wert für die Eigenschaft **Quantity** für alle Datensätze in der Datenquelle auf 0 fest. |![ ](./media/function-update-updateif/icecream-mint-zero.png)<br> <br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |

### <a name="step-by-step"></a>Schritt für Schritt
1. Importieren oder erstellen Sie eine Sammlung mit dem Namen **Inventory** (Lagerbestand), und zeigen Sie diese in einem Katalog an, wie unter [Show images and text in a gallery, including gallery selection, sort, and filter (Anzeigen von Bildern und Text in einem Katalog, einschließlich Auswählen, Sortieren und Filtern des Katalogs)](../show-images-text-gallery-sort-filter.md) beschrieben.
2. Nennen Sie den Katalog **ProductGallery**.
3. Fügen Sie einen Schieberegler mit dem Namen **UnitsSold** hinzu, und legen Sie dessen **Max**-Eigenschaft auf diesen Ausdruck fest:<br>**ProductGallery.Selected.UnitsInStock**
4. Fügen Sie eine Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Formel fest:<br>**UpdateIf(Inventory, ProductName = ProductGallery.Selected.ProductName, {UnitsInStock:UnitsInStock-UnitsSold.Value})**
5. Drücken Sie F5, wählen Sie ein Produkt aus dem Katalog aus, geben Sie mit dem Schieberegler einen Wert an, und wählen Sie dann die Schaltfläche aus.
   
    Die Anzahl der Einheiten des von Ihnen angegebenen Produkts im Lager sinkt um die Anzahl, die Sie angegeben haben.

