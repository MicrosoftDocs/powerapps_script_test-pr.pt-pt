---
title: Funktionen „AddColumns“, „DropColumns“, „RenameColumns“ und „ShowColumns“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „AddColumns“, „DropColumns“, „RenameColumns“ und „ShowColumns“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/24/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 056c5e1142b3a34776e72f788f5b2cef9e3b2a27
ms.sourcegitcommit: 3dc330d635aaf5bc689efa6bd39826d6e396c832
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48875897"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-powerapps"></a>Die Funktionen „AddColumns“, „DropColumns“, „RenameColumns“ und „ShowColumns“ in PowerApps
Formen eine [Tabelle](../working-with-tables.md) durch Hinzufügen, Verwerfen, Umbenennen und Auswählen der [Spalten](../working-with-tables.md#columns)

## <a name="overview"></a>Übersicht
Diese Funktionen formen eine Tabelle, indem sie deren Spalten anpassen:

* Verringern Sie mehreren Spalten in einer Tabelle auf eine einige Spalte, um sie mit Funktionen wie **[Lower](function-lower-upper-proper.md)** oder **[Abs](function-numericals.md)** zu verwenden, die sich nur auf einzelne Spalten beziehen.  
* Fügen Sie einer Tabelle eine berechnete Spalte hinzu (z.B. die Spalte **Gesamtpreis**, die das Ergebnis der Multiplikation von **Quantität** und **Stückpreis** anzeigt).
* Geben Sie einer Spalte für die Benutzer oder die Verwendung in Formeln einen aussagekräftigeren Namen.

Tabellen stellen in PowerApps einen Wert dar, genau wie Zeichenfolgen oder Zahlen.  Sie können eine Tabelle als Argument in einer Formel angeben, und Formeln können eine Tabelle als Ergebnis zurückgeben. Die in diesem Thema beschriebenen Funktionen ändern eine Tabelle nicht. Stattdessen nehmen sie eine Tabelle als Argument und geben eine neue Tabelle mit einer angewendeten Transformation zurück.  Weitere Details erfahren Sie unter [Arbeiten mit Tabellen](../working-with-tables.md).  

Die Spalten einer [Datenquelle](../working-with-data-sources.md) können durch diese Funktionen nicht geändert werden. Daten müssen an ihrer Quelle geändert werden. Sie können einer [Sammlung](../working-with-data-sources.md#collections) mit der **[Collect](function-clear-collect-clearcollect.md)** -Funktion Spalten hinzufügen.  Weitere Informationen finden Sie unter [Arbeiten mit Datenquellen](../working-with-data-sources.md).  

## <a name="description"></a>Beschreibung
Die Funktion **AddColumns** fügt einer Tabelle eine Spalte hinzu, und eine Formel definiert die Werte in dieser Spalte. Vorhandene Spalten bleiben unverändert.

Die Formel wird für jeden Datensatz der Tabelle ausgewertet.
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Die Funktion **DropColumns** schließt Spalten aus einer Tabelle aus.  Alle anderen Spalten bleiben unverändert. **DropColumns** schließt Spalten aus, und **ShowColumns** schließt Spalten ein.

Verwenden Sie die Funktion **RenameColumns**, um eine oder mehrere Spalten einer Tabelle mithilfe von mindestens einem Argumentpaar, das den Namen einer in der Tabelle enthaltenen Spalte (der alte Name, den Sie ersetzen möchten) und den Namen einer in der Tabelle nicht enthaltenen Spalte (der neue Name, den Sie verwenden möchten) angibt. Der alte Name muss bereits in der Tabelle vorhanden sein, und der neue Name darf noch nicht vorhanden sein. Jeder Spaltenname darf nur einmal in der Argumentliste angezeigt werden, entweder als alter Spaltenname oder als neuer Spaltenname. Um eine Spalte in eine vorhandene Spalte umzubenennen, verwerfen Sie zuerst die vorhandene Spalte mit einem Klick auf **DropColumns**, oder benennen Sie die vorhandene Spalte separat um, indem Sie eine Funktion **RenameColumns** innerhalb einer anderen schachteln.

Die Funktion **ShowColumns** schließt Spalten einer Tabelle ein und verwirft alle anderen Spalten. Sie können **ShowColumns** verwenden, um eine einspaltige Tabelle aus einer Tabelle mit mehreren Spalten zu erstellen.  **ShowColumns** schließt Spalten ein, und **DropColumns** schließt Spalten aus.  

Das Ergebnis all dieser Funktionen ist eine neue Tabelle mit angewendeter Transformation.  Die ursprüngliche Tabelle wird nicht geändert.

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Syntax
**AddColumns**( *Tabelle*, *Spaltenname1*, *Formel1* [, *Spaltenname2*, *Formel2*, ... ] )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *ColumnName(s)*: erforderlich. Name(n) der hinzuzufügenden Spalte(n).  Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)
* *Formel(n)* (erforderlich):  Die für jeden Datensatz der Tabelle auszuwertende(n) Formel(n). Das Ergebnis wird als der Wert der entsprechenden neuen Spalte hinzugefügt. Sie können in dieser Formel auf andere Spalten der Tabelle verweisen.

**DropColumns**( *Tabelle*, *Spaltenname1* [, *Spaltenname2*, ... ] )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *ColumnName(s)*: erforderlich. Name(n) der zu verwerfenden Spalte(n). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)

**RenameColumns**( *Tabelle*, *AlterSpaltenname1*, *NeuerSpaltenname1* [, *AlterSpaltenname2*, *NeuerSpaltenname2*, ... ] )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *AlterSpaltenname*: erforderlich. Name einer umzubenennenden Spalte aus der ursprünglichen Tabelle. Dieses Element wird als erstes in dem Argumentpaar angezeigt (oder als erstes in jedem Argumentpaar, wenn die Formel mehr als ein Paar enthält). Der Name muss eine Zeichenfolge sein (z.B. **"Name"** in doppelten Anführungszeichen).
* *NeuerSpaltenname*: erforderlich. Der neue Name. Dieses Element wird als letztes in dem Argumentpaar angezeigt (oder als letztes in jedem Argumentpaar, wenn die Formel mehr als ein Paar enthält). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Customer Name"** (Kundenname) in doppelten Anführungszeichen).

**ShowColumns**( *Tabelle*, *Spaltenname1* [, *Spaltenname2*, ... ] )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *ColumnName(s)*: erforderlich. Name(n) der einzuschließenden Spalte(n). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)

## <a name="examples"></a>Beispiele
In den Beispielen in diesem Abschnitt wird die Datenquelle **IceCreamSales** (Eiscremeverkäufe) verwendet, die die Daten in dieser Tabelle enthält:

![](media/function-table-shaping/icecream.png)

Keines dieser Beispiele verändert die Datenquelle **IceCreamSales**. Jede Funktion transformiert den Wert der Datenquelle in eine Tabelle und gibt den Wert als Ergebnis zurück.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )** |Fügt dem Ergebnis die Spalte **Revenue** (Umsatz) hinzu.  **UnitPrice * QuantitySold** (Stückpreis * verkaufte Menge) wird für jeden Datensatz ausgewertet, und das Ergebnis wird in die neue Spalte eingefügt. |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns( IceCreamSales, "UnitPrice" )** |Schließt die Spalte **UnitPrice** aus dem Ergebnis aus. Mit dieser Funktion können Spalten ausgeschlossen und mit **ShowColumns** eingeschlossen werden. |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, "Flavor" )** |Schließt nur die Spalte **Flavor** (Geschmack) im Resultset ein. Mithilfe dieser Funktion können Sie Spalten einschließen und mithilfe der Funktion **DropColumns** ausschließen. |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |Benennt die Spalte **UnitPrice** im Resultset um. |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |Benennt die Spalten **UnitPrice** und **QuantitySold** im Ergebnis um. |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |Führt der Reihe nach die folgenden Transformationen aus, beginnend im Kern der Formel: <ol><li>Fügt eine **Revenue**-Spalte basierend auf der Berechnung von **UnitPrice * Quantity** (Stückpreis * Menge) pro Datensatz hinzu.<li>Benennt **UnitPrice** in **Price** (Preis) um.<li>Schließt die Spalte **Quantity** aus.</ol>  Beachten Sie, dass diese Reihenfolge wichtig ist. Angenommen, **UnitPrice** kann nach der Umbenennung nicht berechnet werden. |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>Schritt für Schritt
1. Importieren oder erstellen Sie eine Sammlung namens **Inventory** (Inventar), wie im ersten Unterverfahren unter [Anzeigen von Bildern und Text in einem Katalog](../show-images-text-gallery-sort-filter.md) beschrieben.
2. Fügen Sie eine Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Formel fest:
   
    **ClearCollect(Inventory2, RenameColumns(Inventory, "ProductName", "JacketID"))**
3. Drücken Sie F5, klicken Sie auf die Schaltfläche, die Sie gerade erstellt haben, und drücken Sie die ESC-TASTE, um zum Designarbeitsbereich zurückzukehren.
4. Wählen Sie im Menü **Datei** **Sammlungen** aus.
5. Vergewissern Sie sich, dass Sie eine Sammlung namens **Inventory2** erstellt haben. Die neue Sammlung enthält fast dieselben Informationen wie **Inventory**, nur die Spalte **ProductName** in **Inventory** heißt **JacketID** in **Inventory2**.

