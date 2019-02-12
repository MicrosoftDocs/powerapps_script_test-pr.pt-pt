---
title: Funktionen „GroupBy“ und „Ungroup“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktionen „GroupBy“ und „Ungroup“ in PowerApps
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
ms.openlocfilehash: 0ac3f0549e89153d9362d6a8a040833608d4e287
ms.sourcegitcommit: 2300de0a0486187762f830068c872116d5b04c32
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806200"
---
# <a name="groupby-and-ungroup-functions-in-powerapps"></a>GroupBy- und Ungroup-Funktionen in PowerApps
Gruppiert und hebt die Gruppierung von [Datensätzen](../working-with-tables.md#records) in einer [Tabelle](../working-with-tables.md) auf.

## <a name="description"></a>Beschreibung
Die **GroupBy**-Funktion gibt eine Tabelle mit Datensätzen zurück, die auf der Basis der Werte in einer oder mehreren [Spalten](../working-with-tables.md#columns) gruppiert sind. Datensätze in der gleichen Gruppe werden in einem einzelnen Datensatz platziert. Dabei wird eine Spalte hinzugefügt, die eine geschachtelte Tabelle der übrigen Spalten enthält.   

Die **Ungroup**-Funktion kehrt den **GroupBy**-Prozess um. Diese Funktion gibt eine Tabelle zurück, die die zuvor gruppierten Datensätze in einzelne Datensätze aufteilt.

Sie können Datensätze mithilfe der Funktion **GroupBy** gruppieren. Ändern Sie die Tabelle, die zurückgegeben wird, und heben Sie anschließend die Gruppierung der Datensätze in der geänderten Tabelle über die Funktion **Ungroup** wieder auf. Beispielsweise können Sie eine Gruppe von Datensätzen entfernen, indem Sie diesem Ansatz folgen:

* Verwenden Sie die **GroupBy**-Funktion.
* Verwenden Sie die  **[Filter](function-filter-lookup.md)**-Funktion, um die gesamte Gruppe von Datensätzen zu entfernen.
* Verwenden Sie die **Ungroup**-Funktion.  

Sie können Ergebnisse auch aufgrund einer Gruppierung aggregieren:

* Verwenden Sie die **GroupBy**-Funktion.
* Verwenden Sie die **[AddColumns](function-table-shaping.md)**-Funktion mit **[Sum](function-aggregates.md)**, **[Average](function-aggregates.md)** und andere Aggregatfunktionen, um eine neue Spalte hinzufügen, die ein Aggregat der Gruppentabellen darstellt.
* Verwenden Sie die **[DropColumns](function-table-shaping.md)**-Funktion, um die Gruppentabelle zu löschen.

**Ungroup** versucht, die ursprüngliche Reihenfolge der Datensätze zu erhalten, die von **GroupBy** eingelesen wurden.  Dies ist nicht immer möglich (z.B. wenn die ursprüngliche Tabelle *leere* Datensätze enthält).

Tabellen stellen in PowerApps einen Wert dar, genau wie Zeichenfolgen oder Zahlen. Sie können eine Tabelle als Argument für eine Funktion angeben, und eine Funktion kann eine Tabelle zurückgeben. **GroupBy** und **Ungroup** führen nicht zur Änderung einer Tabelle; stattdessen verwenden sie die Tabelle als Argument und geben eine andere Tabelle zurück. Weitere Details erfahren Sie unter [Arbeiten mit Tabellen](../working-with-tables.md).

## <a name="syntax"></a>Syntax
**GroupBy**( *Tabelle*, *SpaltenName1* [, *SpaltenName2*, ... ], *GruppenSpaltenName* )

* *Tabelle* (erforderlich): Zu gruppierende Tabelle.
* *ColumnName(s)*: erforderlich.  Die Spaltennamen der *Tabelle* für die Gruppierung der Datensätze.  Diese Spalten werden in der Ergebnistabelle zu Spalten.
* *GruppenSpaltenName*: erforderlich.  Der Spaltenname für die Speicherung von Datensatzdaten, die nicht in *SpaltenName(n)* enthalten sind.
  
    > [!NOTE]
  > Bei Excel- oder SharePoint-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, geben Sie jedes Leerzeichen als **"\_x0020\_"** an. **"Name der Spalte"** wird z.B. als **"Name_x0020_der_x0020_Spalte"** angegeben.

**Ungroup**( *Tabelle*, *GruppenSpaltenName* )

* *Tabelle* (erforderlich): Tabelle, deren Gruppierung aufgehoben werden soll.
* *GruppenSpaltenName*: erforderlich. Die Spalte mit dem Datensatzdaten-Setup mit der **GroupBy**-Funktion.
  
    > [!NOTE]
  > Bei Excel- oder SharePoint-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, geben Sie jedes Leerzeichen als **"\_x0020\_"** an. **"Name der Spalte"** wird z.B. als **"Name_x0020_der_x0020_Spalte"** angegeben.

## <a name="examples"></a>Beispiele
### <a name="create-a-collection"></a>Sammlung erstellen
1. Fügen Sie eine Schaltfläche hinzu, und legen Sie Ihre **[Text](../controls/properties-core.md)**-Eigenschaft so fest, dass die Schaltfläche **Original** anzeigt.
2. Legen Sie die Eigenschaft **[OnSelect](../controls/properties-core.md)** der Schaltfläche **Original**auf diese Formel fest:
   
    **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
3. Halten Sie die ALT-TASTE gedrückt, und klicken Sie auf die Schaltfläche **Ursprünglich**.
   
    Sie haben jetzt eine [Sammlung](../working-with-data-sources.md#collections) mit dem Namen **CityPopulations** erstellt, die die folgenden Daten enthält:
   
    ![](media/function-groupby/cities.png)
4. Um diese Sammlung anzuzeigen, wählen Sie im Menü **Datei** die Option **Sammlungen** und anschließend die Sammlung **CityPopulations** aus.  Die ersten fünf Datensätze in der Sammlung werden angezeigt:
   
    ![](media/function-groupby/citypopulations-collection.png)

### <a name="group-records"></a>Gruppieren von Datensätzen
1. Fügen Sie eine andere Schaltfläche hinzu, und legen Sie deren  **[Text](../controls/properties-core.md)**-Eigenschaft auf**Group** fest.
2. Legen Sie die Eigenschaft **[OnSelect](../controls/properties-core.md)** der Schaltfläche auf diese Formel fest:
   
    **ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )**
3. Halten Sie die ALT-TASTE gedrückt, und klicken Sie auf die Schaltfläche **Gruppe**.
   
    Sie haben jetzt eine Sammlung mit dem Namen **CitiesByCountry** erstellt, in der die Datensätze der vorherigen Sammlung mithilfe der Spalte **Country** gruppiert werden.
   
    ![](media/function-groupby/cities-grouped.png)
4. Um die ersten fünf Datensätze in dieser Sammlung anzuzeigen, wählen Sie im Menü **Datei** die Option **Sammlungen** aus.
   
    ![](media/function-groupby/citiesbycountry-collection.png)
5. Zum Anzeigen der Einwohnerzahlen der Städte in einem Land wählen Sie das Tabellensymbol in der Spalte **Cities** für dieses Land aus (z.B. Germany):
   
    ![](media/function-groupby/population-germany.png)

### <a name="filter-and-ungroup-records"></a>Filtern und Aufheben der Gruppierung von Datensätzen
1. Fügen Sie eine andere Schaltfläche hinzu, und legen Sie deren **[Text](../controls/properties-core.md)**-Eigenschaft so fest, dass die Schaltfläche **„Filter“** anzeigt.
2. Legen Sie die Eigenschaft **[OnSelect](../controls/properties-core.md)** der Schaltfläche auf diese Formel fest:
   
    **ClearCollect( CitiesByCountryFiltered, Filter( CitiesByCountry, "e" in Country ) )**
3. Halten Sie die ALT-TASTE gedrückt, und klicken Sie auf die Schaltfläche, die Sie hinzugefügt haben.
   
    Sie haben jetzt eine dritte Sammlung mit dem Namen **CitiesByCountryFiltered** erstellt, die nur Länder mit einem „e“ im Namen enthält, d h. nicht „Spain“ oder „Italy“.
   
    ![](media/function-groupby/cities-grouped-hase.png)
4. Fügen Sie eine weitere Schaltfläche hinzu, und legen Sie deren **[Text](../controls/properties-core.md)**-Eigenschaft so fest, dass die Schaltfläche **„Ungroup “** anzeigt.
5. Legen Sie die Eigenschaft **[OnSelect](../controls/properties-core.md)** der Schaltfläche auf diese Formel fest:
   
    **ClearCollect( CityPopulationsUngrouped, Ungroup( CitiesByCountryFiltered, "Cities" ) )**
   
    Dies führt zu folgendem Ergebnis:
   
    ![](media/function-groupby/cities-hase.png)

### <a name="aggregate-results"></a>Aggregieren von Ergebnissen
Mit einer gruppierten Tabelle lassen sich außerdem Ergebnisse aggregieren.  In diesem Beispiel addieren wir die Einwohnerzahlen der größten Städte jedes Landes zusammen.

1. Fügen Sie eine andere Schaltfläche hinzu, und legen Sie deren **[Text](../controls/properties-core.md)**-Eigenschaft so fest, dass die Schaltfläche **„Sum“** anzeigt.
2. Legen Sie die Eigenschaft **[OnSelect](../controls/properties-core.md)** der Schaltfläche **„Sum“** auf diese Formel fest:
   
    **ClearCollect( CityPopulationsSum, AddColumns( CitiesByCountry, "Sum of City Populations", Sum( Cities, Population ) ) )**
   
    Dies führt zu folgendem Ergebnis:
   
    ![](media/function-groupby/cities-sum.png)
   
    **[AddColumns](function-table-shaping.md)**  beginnt mit der grundlegenden Sammlung **CitiesByCountry** und fügt eine neue Spalte **Sum of City Populations** hinzu.  Die Werte dieser Spalte werden zeilenweise auf der Basis der Formel **Sum ( Cities, Population)** berechnet.  **AddColumns** stellt den Wert der Spalte **Cities** (eine Tabelle) für jede Zeile, und  **[Sum](function-aggregates.md)** addiert die Zahlen unter **Population** für jede Zeile dieser untergeordneten Tabelle.

    Wir haben jetzt die gewünschte Summe berechnet und können **[DropColumns](function-table-shaping.md)** verwenden, um die untergeordneten Tabellen zu entfernen.
  
3. Fügen Sie eine andere Schaltfläche hinzu, und legen Sie deren **[Text](../controls/properties-core.md)**-Eigenschaft so fest, dass die Schaltfläche **"SumOnly"** anzeigt.
4. Legen Sie die Eigenschaft **[OnSelect](../controls/properties-core.md)** der Schaltfläche **"Sum"** auf diese Formel fest:

    **ClearCollect( CityPopulationsSumOnly, DropColumns( CityPopulationsSum, "Cities" ) )**
   
    Dies führt zu folgendem Ergebnis:
   
    ![](media/function-groupby/cities-sum-drop-cities.png)
   
    Beachten Sie, dass wir die Gruppierung dieser Tabelle nicht aufheben mussten.

