---
title: Funktionen „Sort“ und „SortByColumns“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Sort“ und „SortByColumns“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d3a83f5ae96b8d9146163ed7d5ff4c4529f8d562
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42830769"
---
# <a name="sort-and-sortbycolumns-functions-in-powerapps"></a>Funktionen „Sort“ und „SortByColumns“
Zum Sortieren von [Tabellen](../working-with-tables.md).

## <a name="description"></a>Beschreibung
Die Funktion **Sort** sortiert eine Tabelle basierend auf einer Formel.  

Die Formel wird für jeden [Datensatz](../working-with-tables.md#records) der Tabelle ausgewertet, und die Ergebnisse werden zum Sortieren der Tabelle verwendet.  Die Formel muss eine Zahl, eine Zeichenfolge oder einen Booleschen Wert zum Ergebnis haben; das Ergebnis darf keine Tabelle und kein Datensatz sein.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Um zuerst nach einer Spalte und dann nach einer anderen zu sortieren, betten Sie eine **Sort**-Formel in eine andere ein. Beispielsweise können Sie diese Formel verwenden, um eine Tabelle **Kontakte** zuerst nach der Spalte **Nachname** und dann nach der Spalte **Vorname** zu sortieren: **Sort( Sort( Kontakte, Nachname ), Vorname )**

Die Funktion **SortByColumns** kann ebenfalls verwendet werden, um eine Tabelle basierend auf einer oder mehreren Spalten zu sortieren.

Die Parameterliste für **SortByColumns** gibt die Namen der Spalten, nach denen sortiert werden soll, und die Sortierungsrichtung pro Spalte an.  Die Sortierung erfolgt in der Reihenfolge der Parameter (zuerst wird nach der ersten Spalte sortiert, dann nach der zweiten usw.).  Spaltennamen werden als Zeichenfolgen angegeben, für deren direkte Aufnahme in die Parameterliste sind doppelte Anführungszeichen erforderlich.  Beispiel: **SortByColumns( Kundentabelle, "Nachname" )**.

Sie können **SortByColumns** mit einer **[Dropdownliste](../controls/control-drop-down.md)** oder einem **[Listenfeld](../controls/control-list-box.md)** kombinieren, um Benutzern die Auswahl der Spalte zu ermöglichen, auf der die Sortierung basieren soll.

Über das aufsteigende oder absteigende Sortieren hinaus kann **SortByColumns** auf der Grundlage einer einspaltigen Wertetabelle sortieren.  Beispielsweise können Sie datensatzbasiert nach dem Namen eines Wochentags sortieren, indem Sie **[ "Montag", "Dienstag", "Mittwoch", "Donnerstag", "Freitag", "Samstag", "Sonntag" ]** als Sortierreihenfolge angeben.  Alle Datensätze, die **Montag** enthalten, werden zuerst aufgeführt, gefolgt von **Dienstag** usw.  Gefundene Datensätze, die in der Sortierungstabelle nicht vorkommen, werden an das Ende der Liste gesetzt.

Wie Zeichenfolgen und Zahlen sind auch [Tabellen](../working-with-tables.md) in PowerApps Werte.  Sie können an Funktionen übergeben und von diesen zurückgegeben werden.  **Sort** und **SortByColumn** ändern eine Tabelle nicht; sie nehmen vielmehr eine Tabelle als Argument an und geben eine neue Tabelle zurück, die sortiert wurde.  Weitere Details erfahren Sie unter [Arbeiten mit Tabellen](../working-with-tables.md).

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>Syntax
**Sort**( *Table*, *Formula* [, *SortOrder* ] )

* *Tabelle* (erforderlich): Die zu sortierende Tabelle.
* *Formel* (erforderlich): Die Formel wird für jeden Datensatz der Tabelle ausgewertet, und die Ergebnisse werden zur Sortierung der Tabelle verwendet.  Sie können auf Spalten innerhalb der Tabelle verweisen.
* *SortOrder*: optional. Geben Sie **SortOrder.Descending** an, um die Tabelle in absteigender Reihenfolge zu sortieren. **SortOrder.Ascending** ist der Standardwert.

**SortByColumns**( *Table*, *ColumnName1* [, *SortOrder1*, *ColumnName2*, *SortOrder2*, ... ] )

* *Table*: erforderlich. Die zu sortierende Tabelle.
* *ColumnName(s)*: erforderlich. Die Spaltennamen, nach denen sortiert werden soll, als Zeichenfolgen.
* *SortOrder(s)*: optional.  **SortOrder.Ascending** oder **SortOrder.Descending**.  **SortOrder.Ascending** ist der Standardwert.  Wenn mehrere *ColumnNames* angegeben sind, müssen alle außer dem letzten einen *SortOrder*-Parameter umfassen.
  
    > [!NOTE]
  > Bei Excel- oder SharePoint-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, geben Sie jedes Leerzeichen als **"\_x0020\_"** an. **"Name der Spalte"** wird z.B. als **"Name_x0020_der_x0020_Spalte"** angegeben.

**SortByColumns**( *Table*, *ColumnName*, *SortOrderTable* )

* *Tabelle* (erforderlich): Die zu sortierende Tabelle.
* *ColumnName*: erforderlich. Der Name der Spalte, nach der sortiert werden soll, als Zeichenfolge.
* *SortOrderTable*: erforderlich.  Einspaltige Tabelle mit Werten, nach denen sortiert werden soll.
  
    > [!NOTE]
  > Bei Excel- oder SharePoint-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, geben Sie jedes Leerzeichen als **"\_x0020\_"** an. **"Name der Spalte"** wird z.B. als **"Name_x0020_der_x0020_Spalte"** angegeben.

## <a name="examples"></a>Beispiele
Für das folgende Beispiel verwenden wir die **Speiseeis**-[Datenquelle](../working-with-data-sources.md), die die Daten in dieser Tabelle enthält:

![](media/function-sort/icecream.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Sort( Speiseeis, Geschmacksrichtung )**<br><br>**SortByColumns( Speiseeis, "Geschmacksrichtung" )** |Sortiert **Speiseeis** nach deren Spalte **Geschmacksrichtung**. Die Spalte **Geschmacksrichtung** enthält Zeichenfolgen, daher wird die Tabelle alphabetisch sortiert. Die Standard-Sortierreihenfolge ist aufsteigend. |<style> img { max-width: none; } </style> ![](media/function-sort/icecream-flavor.png) |
| **Sort( Speiseeis, Menge )**<br><br>**SortByColumns( Speiseeis, "Menge" )** |Sortiert **Speiseeis** nach deren Spalte **Menge**.  Die Spalte **Menge** enthält Zahlen, daher wird die Tabelle numerisch sortiert.  Die Standard-Sortierreihenfolge ist aufsteigend. |![](media/function-sort/icecream-quantity-asc.png) |
| **Sort( Speiseeis, Menge, SortOrder.Descending )**<br><br>**SortByColumns( Speiseeis, "Menge", SortOrder.Descending )** |Sortiert **Speiseeis** nach deren Spalte **Menge**.  Die Spalte **Menge** enthält Zahlen, daher erfolgt die Sortierung numerisch.  Die Sortierreihenfolge wurde als absteigend angegeben. |![](media/function-sort/icecream-quantity-desc.png) |
| **Sort( Speiseeis, Menge + Nachbestellt )** |Sortiert **Speiseeis** für jeden Datensatz einzeln nach der Summe ihrer Spalten **Menge** und **Nachbestellt**. Die Summe ist eine Zahl, daher wird die Tabelle numerisch sortiert.  Die Standard-Sortierreihenfolge ist aufsteigend.  Da wir anhand einer Formel und nicht nach bloßen Spaltenwerten sortieren, gibt es kein Äquivalent, das **SortByColumns** verwendet. |![](media/function-sort/icecream-total.png) |
| **Sort( Sort( Speiseeis, Nachbestellt ), Menge )**<br><br>**SortByColumns( Speiseeis, "Nachbestellt", Aufsteigend, "Menge", Aufsteigend )** |Sortiert **Speiseeis** zuerst nach deren Spalte **Nachbestellt** und dann nach der Spalte **Menge**.  Beachten Sie, dass „Pistazie“ in der ersten Sortierung basierend auf **Nachbestellung** über „Vanille“ aufstieg und sie dann gemeinsam basierend auf **Menge** an ihren passenden Platz rückten. |![](media/function-sort/icecream-onorder-quantity.png) |
| **SortByColumns( Speiseeis, "Geschmacksrichtung", [&nbsp;"Pistazie",&nbsp;"Erdbeer"&nbsp;] )** |Sortiert **Speiseeis** nach deren Spalte **Geschmacksrichtung**, basierend auf der einspaltigen Tabelle, die „Pistazie“ und „Erdbeer“ enthält.  Datensätze mit der **Geschmacksrichtung** „Pistazie“ werden in den Ergebnissen zuerst angezeigt, gefolgt von Datensätzen, die „Erdbeer“ enthalten.  Werte in der Spalte **Geschmacksrichtung**, die nicht zugeordnet werden, wie etwa „Vanille“, werden nach den zugeordneten Werten aufgeführt. |![](media/function-sort/icecream-onflavor-sorttable.png) |

### <a name="step-by-step"></a>Schritt für Schritt
Um diese Beispiele selbst auszuführen, erstellen Sie die Datenquelle **Speiseeis** als [Sammlung](../working-with-data-sources.md#collections):

1. Fügen Sie eine Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Formel fest:<br>**ClearCollect( Speiseeis, { Geschmacksrichtung: "Schokolade", Menge: 100, Nachbestellt: 150 }, { Geschmacksrichtung: "Vanille", Menge: 200, Nachbestellt: 20 }, { Geschmacksrichtung: "Erdbeer", Menge: 300, Nachbestellt: 0 }, { Geschmacksrichtung: "Schoko-Minz", Menge: 60, Nachbestellt: 100 }, { Geschmacksrichtung: "Pistazie", Menge: 200, Nachbestellt: 10 } )**
2. Führen Sie eine Vorschau der App aus, wählen Sie die Schaltfläche aus, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.
3. Wählen Sie im Menü **Datei** das Element **Sammlungen** aus, um die soeben erstellte Sammlung anzuzeigen, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.

#### <a name="sort"></a>Sort
1. Fügen Sie eine weitere Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Formel fest:<br>
   **ClearCollect( SortByFlavor, Sort( IceCream, Flavor ) )**
   
     Die vorstehende Formel erstellt eine zweite Sammlung mit dem Namen **SortByFlavor**, die die gleichen Daten wie **Speiseeis** enthält. Die neue Sammlung enthält jedoch die Daten alphabetisch aufsteigend nach der Spalte **Geschmacksrichtung** sortiert.
2. Drücken Sie F5, wählen Sie die neue Schaltfläche aus, und drücken Sie dann ESC.
3. Wählen Sie im Menü **Datei** das Element **Sammlungen** aus, um beide Sammlungen anzuzeigen, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.
4. Wiederholen Sie die letzten drei Schritte, ändern Sie jedoch den Namen der Sammlung, die Sie erstellen möchten, und ersetzen Sie die Formel **Sort** durch eine andere Formel aus der Tabelle mit Beispielen weiter oben in diesem Abschnitt, die **Sort** verwendet.

#### <a name="sortbycolumns"></a>SortByColumns
1. Fügen Sie eine weitere Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Formel fest:<br>
   **ClearCollect( SortByQuantity, SortByColumns( IceCream, "Quantity", Ascending, "Flavor", Descending ) )**
   
     Die vorstehende Formel erstellt eine dritte Sammlung mit dem Namen **SortByQuantity**, die die gleichen Daten wie **Speiseeis** enthält. Die neue Sammlung enthält die Daten jedoch numerisch aufsteigend nach der Spalte **Menge** und dann absteigend nach der Spalte **Geschmacksrichtung** sortiert.
2. Drücken Sie F5, wählen Sie die neue Schaltfläche aus, und drücken Sie dann ESC.
3. Wählen Sie im Menü **Datei** das Element **Sammlungen** aus, um alle drei Sammlungen anzuzeigen, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.
4. Wiederholen Sie die letzten drei Schritte, ändern Sie jedoch den Namen der Sammlung, die Sie erstellen möchten, und ersetzen Sie die Formel **SortByColumns** durch eine andere Formel aus der Tabelle mit Beispielen weiter oben in diesem Abschnitt, die **SortByColumns** verwendet.

