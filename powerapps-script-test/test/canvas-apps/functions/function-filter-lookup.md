---
title: Funktionen „Filter“, „Search“ und „LookUp“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Filter- und LookUp-Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/05/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c37aa315981c51a446254473686c44501e72a96f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42831474"
---
# <a name="filter-search-and-lookup-functions-in-powerapps"></a>Filter-, Search- und LookUp-Funktionen in PowerApps
Sucht nach einem oder mehreren [Datensätzen](../working-with-tables.md#records) in einer [Tabelle](../working-with-tables.md).

## <a name="description"></a>Beschreibung
Die **Filter**-Funktion sucht Datensätze in einer Tabelle, die eine Formel erfüllen.  Mit **Filter** finden Sie Datensätze, die mindestens ein Kriterium erfüllen; Datensätze, die kein Kriterium erfüllen, werden verworfen.

Die **LookUp**-Funktion sucht den ersten Datensatz in einer Tabelle, der eine Formel erfüllt.  Verwenden Sie **LookUp**, um einen einzelnen Datensatz zu suchen, der mindestens ein Kriterium erfüllt.

Bei beiden wird die Formel für jeden Datensatz der Tabelle ausgewertet.  Datensätze, die *TRUE* ausgeben, sind im Ergebnis enthalten.  Neben den normalen [Operatoren](operators.md) der Formel können Sie die **[in](operators.md#in-and-exactin-operators)**- und **[exactin](operators.md#in-and-exactin-operators)**-Operatoren für Übereinstimmungen mit Teilzeichenfolgen verwenden.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Die **Search**-Funktion sucht Datensätze in einer Tabelle, die eine Zeichenfolge in eine ihrer Spalten enthalten. Die Zeichenfolge kann an einer beliebigen Stelle innerhalb der Spalte auftreten. Beispielsweise würde die Suche nach „rob“ oder „bert“ eine Übereinstimmung in einer Spalte finden, die „Robert“ enthält. Bei Search wird die Groß-/Kleinschreibung beachtet. Im Gegensatz zu **Filter** und **LookUp**, verwendet die **Search**-Funktion anstelle einer Formel eine einzelne Zeichenfolge für die Übereinstimmung.

**Filter** und **Search** geben eine Tabelle zurück, die dieselben Spalten wie die ursprüngliche Tabelle und die Datensätze enthält, die den Kriterien entsprechen. **LookUp** gibt nach dem Anwenden einer Formel, um den Datensatz auf einen einzelnen Wert zu reduzieren, nur den ersten gefundenen Datensatz zurück. Wenn keine Datensätze gefunden wurden, geben **Filter** und **Search** eine [leere](function-isblank-isempty.md) Tabelle und **LookUp** *leer* zurück.  

Wie Zeichenfolgen und Zahlen sind auch [Tabellen](../working-with-tables.md) in PowerApps Werte. Sie können an Funktionen übergeben und von diesen zurückgegeben werden.  **Filter**, **Search** und **LookUp** ändern eine Tabelle nicht. Stattdessen nehmen sie eine Tabelle als Argument entgegen und geben eine Tabelle, einen Datensatz oder einen einzelnen Wert daraus zurück. Weitere Details erfahren Sie unter [Arbeiten mit Tabellen](../working-with-tables.md).

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>Syntax
**Filter**( *Tabelle*, *Formel1* [, *Formel2*, ... ] )

* *Tabelle* (erforderlich): die zu suchende Tabelle.
* *Formel(n)* (erforderlich): Formel, anhand derer die einzelnen Datensätze in der Tabelle ausgewertet werden. Diese Funktion gibt alle Datensätze zurück, die zu **WAHR** ausgewertet werden. Sie können auf Spalten innerhalb der Tabelle verweisen. Wenn Sie mehr als eine Formel angeben, werden die Ergebnisse aller Formeln mit einer **[And](function-logicals.md)**-Funktion kombiniert.

**Search**( *Tabelle*, *Suchzeichenfolge*, *Spalte1* [, *Spalte2*, ... ] )

* *Tabelle* (erforderlich): die zu suchende Tabelle.
* *Suchzeichenfolge* (erforderlich): Zeichenfolge, nach der gesucht werden soll. Bei *leer* oder einer leeren Zeichenfolge werden alle Datensätze zurückgegeben.
* *Spalte(n)* (erforderlich): Spaltennamen in der *Tabelle*, die gesucht werden sollen. Die zu suchenden Spalten müssen Text enthalten. Spaltennamen müssen Zeichenfolgen und in doppelte Anführungszeichen eingeschlossen sein. Allerdings müssen die Spaltennamen statisch sein und können nicht mit einer Formel berechnet werden. Wenn *Suchzeichenfolge* als Teilergebnis innerhalb der Daten einer Spalte gefunden wird, wird der vollständige Datensatz zurückgegeben werden.

> [!NOTE]
> Bei Excel- oder SharePoint-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, geben Sie jedes Leerzeichen als **"\_x0020\_"** an. **"Name der Spalte"** wird z.B. als **"Name_x0020_der_x0020_Spalte"** angegeben.

**LookUp**( *Tabelle*, *Formel* [, *Reduzierformel* ] )

* *Tabelle* (erforderlich): die zu suchende Tabelle. Auf der Benutzeroberfläche wird die Syntax oberhalb des Funktionsfelds als *Quelle* angezeigt.
* *Formel* (erforderlich):
  Formel, anhand derer die einzelnen Datensätze in der Tabelle ausgewertet werden. Die Funktion gibt den ersten Datensatz zurück, der als **WAHR** ausgewertet wird. Sie können auf Spalten innerhalb der Tabelle verweisen. Auf der Benutzeroberfläche wird die Syntax oberhalb des Funktionsfelds als *Bedingungen* angezeigt.
* *Reduzierformel* (optional): Diese Formel wird über den gefundenen Datensatz ausgewertet, anschließend wird der Datensatz auf einen einzigen Wert reduziert. Sie können auf Spalten innerhalb der Tabelle verweisen. Wenn Sie diesen Parameter nicht verwenden, gibt die Funktion den gesamten Datensatz aus der Tabelle zurück. Auf der Benutzeroberfläche wird die Syntax oberhalb des Funktionsfelds als *Ergebnis* angezeigt.

## <a name="examples"></a>Beispiele
Die folgenden Beispiele verwenden die **IceCream**-[Datenquelle](../working-with-data-sources.md):

![](media/function-filter-lookup/icecream.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Filter( IceCream, OnOrder > 0 )** |Gibt Datensätze zurück, bei denen **OnOrder** größer als 0 ist. |<style> img { max-width: none; } </style> ![](media/function-filter-lookup/icecream-onorder.png) |
| **Filter( IceCream, Quantity + OnOrder > 225 )** |Gibt Datensätze zurück, bei denen die Summe der Spalten **Quantity** und **OnOrder** größer als 225 ist. |![](media/function-filter-lookup/icecream-overstock.png) |
| **Filter( IceCream, "chocolate" in Lower( Flavor ) )** |Gibt Datensätze zurück, bei denen das Wort „chocolate“ im **Flavor**-Namen auftaucht. Die Groß-/Kleinschreibung wird hierbei nicht berücksichtigt. |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Filter( IceCream, Quantity < 10  && OnOrder < 20 )** |Gibt Datensätze zurück, bei denen **Quantity** kleiner als 10 und **OnOrder** kleiner als 20 ist.  Keine Datensätze entsprechen diesen Kriterien, sodass eine leere Tabelle zurückgegeben wird. |![](media/function-filter-lookup/icecream-empty.png) |
| **Search( IceCream, "choc", "Flavor" )** |Gibt Datensätze zurück, bei denen die Zeichenfolge „choc“ im **Flavor**-Namen auftaucht. Die Groß-/Kleinschreibung wird hierbei nicht berücksichtigt. |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Search( IceCream, "", "Flavor" )** |Da der Suchbegriff leer ist, werden alle Datensätze zurückgegeben. |![](media/function-filter-lookup/icecream.png) |
| **LookUp( IceCream, Flavor = "Chocolate", Quantity )** |Sucht einen Datensatz, bei dem **Flavor** „chocolate“ entspricht. Hierzu gibt es einen passenden Datensatz.  Für den ersten gefundenen Datensatz wird die **Quantity** dieses Datensatzes zurückgegeben. |100 |
| **LookUp( IceCream, Quantity > 150, Quantity + OnOrder )** |Sucht einen Datensatz mit **Quantity** größer als 100, von denen es mehrere gibt.  Für den ersten gefundenen Datensatz, welcher „Vanilla“-**Flavor** ist, wird die Summe der Spalten **Quantity** und **OnOrder** zurückgegeben. |250 |
| **LookUp( IceCream, Flavor = "Pistachio", OnOrder )** |Sucht einen Datensatz, bei dem **Flavor** „Pistachio“ entspricht. Hierzu gibt es keinen passenden Datensatz.  Deswegen gibt **LookUp** *blank* zurück. |*blank* |
| **LookUp( IceCream, Flavor = "Vanilla" )** |Sucht einen Datensatz, bei dem **Flavor** „Vanilla“ entspricht. Hierzu gibt es einen passenden Datensatz.  Da keine Reduzierformel angegeben wurde, wird der gesamte Datensatz zurückgegeben. |{ Flavor: "Vanilla", Quantity: 200, OnOrder: 75 } |

### <a name="search-user-experience"></a>Benutzererfahrung beim Durchsuchen
In vielen Apps können Sie ein oder mehrere Zeichen in ein Suchfeld eingeben, um eine gefilterte Liste mit Datensätzen aus einem großen Datenbestand zu erzeugen. Bei der Eingabe zeigt die Liste nur die Datensätze, die den Suchkriterien entsprechen.

Die nachfolgenden Beispiele zeigen Ergebnisse der Suche in einer Liste namens **Customers** an, die die folgenden Daten enthält:

![](media/function-filter-lookup/customers.png)

Erstellen Sie ein **[Button](../controls/control-button.md)**-Steuerelement, und legen Sie dessen **OnSelect**-Eigenschaft auf folgende Formel fest, um diese Datenquelle als Sammlung zu erstellen:

**ClearCollect( Customers, Table( { Name: "Fred Garcia", Company: "Northwind Traders" }, { Name: "Cole Miller", Company: "Contoso" }, { Name: "Glenda Johnson", Company: "Contoso" }, { Name: "Mike Collins", Company: "Adventure Works" }, { Name: "Colleen Jones", Company: "Adventure Works" } ) )**

Sie können wie in diesem Beispiel eine Datensatzliste in einem [**Katalogsteuerelement**](../controls/control-gallery.md) am unteren Rand des Bildschirms anzeigen. Fügen Sie im oberen Bereich des Bildschirms ein [**Texteingabe**](../controls/control-text-input.md)-Steuerelement mit dem Namen **SearchInput** ein, sodass Benutzer angeben können, welche Datensätze für sie relevant sind.

![](media/function-filter-lookup/customers-ux-unfiltered.png)

Wenn der Benutzer Zeichen in **SearchInput** eingibt, werden die Ergebnisse im Katalog automatisch gefiltert. In diesem Fall ist der Katalog so konfiguriert, dass er Datensätze anzeigt, für die der Name des Kunden (nicht der Namen des Unternehmens) mit der Zeichensequenz in **SearchInput** beginnt. Wenn der Benutzer **co** in das Suchfeld eingibt, zeigt der Katalog die folgenden Ergebnisse:

![](media/function-filter-lookup/customers-ux-startswith-co.png)

Legen Sie die Eigenschaft **Items** des Katalogsteuerelements auf eine der folgenden Formeln fest, um anhand der Spalte **Name** zu filtern:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in der die Suchzeichenfolge am Anfang der Spalte **Name** vorkommt. Bei diesem Test wird die Groß-/Kleinschreibung nicht beachtet. Wenn der Benutzer **co** in das Suchfeld eingibt, zeigt der Katalog **Colleen Jones** und **Cole Miller** an. **Mike Collins** wird nicht im Katalog angezeigt, weil die Spalte **Name** dieses Datensatzes nicht mit der Suchzeichenfolge beginnt. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in der die Suchzeichenfolge am Anfang der Spalte **Name** vorkommt. Bei diesem Test wird die Groß-/Kleinschreibung nicht beachtet. Wenn der Benutzer **co** in das Suchfeld eingibt, zeigt der Katalog **Colleen Jones**, **Cole Miller** und **Mike Collins** an, da die Suchzeichenfolge an einer beliebigen Stelle in der Spalte **Name** dieser Datensätze vorkommt. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name" )** |Die **Search**-Funktion wird so ähnlich wie der **in**-Operator verwendet und sucht nach einer Übereinstimmung in der Spalte **Name** in jedem Datensatz. Beachten Sie, dass Sie den Spaltennamen in doppelte Anführungszeichen setzen müssen. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |

Sie können Ihre Suche auch so ausweiten, dass sie die Spalte **Company** sowie die Spalte **Name** enthält:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) &#124;&#124; StartsWith( Company, SearchInput.Text ) )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in denen entweder die Spalte **Name** oder die Spalte **Company** mit der Suchzeichenfolge beginnt (z.B. **co**).  Der [**&#124;&#124;**-Operator](operators.md) ist *TRUE*, wenn eine **StartsWith**-Funktion *TRUE* ist. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name &#124;&#124; SearchInput.Text in Company )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in denen entweder die Spalte **Name** oder die Spalte **Company** die Suchzeichenfolge (z.B. **co**) an beliebiger Stelle enthält. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name", "Company" )** |Die **Search**-Funktion wird so ähnlich wie der **in**-Operator verwendet und durchsucht die **Customers**-Datenquelle nach Datensätzen, in denen entweder die **Name**-Spalte oder die **Company**-Spalte die Suchzeichenfolge (z.B. **co**) an beliebiger Stelle enthält. Die **Search**-Funktion ist einfacher zu lesen und zu schreiben als die **Filter**-Funktion, wenn Sie mehrere Spalten und mehrere **in**-Operatoren angeben möchten. Beachten Sie, dass Sie die Spaltennamen in doppelte Anführungszeichen setzen müssen. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |

