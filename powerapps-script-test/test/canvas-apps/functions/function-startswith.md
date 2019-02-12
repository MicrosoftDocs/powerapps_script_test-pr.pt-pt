---
title: Funktionen „EndsWith“ und „StartsWith“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich von Syntax und Beispielen, für die Funktionen „EndsWith“ und „StartsWith“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e202ce052bf12f5f67715deb2e86b385c2e515a7
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42835558"
---
# <a name="endswith-and-startswith-functions-in-powerapps"></a>Funktionen „EndsWith“ und „StartsWith“ in PowerApps
Testet, ob eine Textzeichenfolge mit einer anderen Textzeichenfolge beginnt oder endet.

## <a name="description"></a>Beschreibung
Die **EndsWith**-Funktion testet, ob eine Textzeichenfolge mit einer anderen endet.

Die **StartsWith**-Funktion testet, ob eine Zeichenfolge mit einer anderen beginnt.    

Bei beiden Funktionen wird in den Tests die Groß-/Kleinschreibung nicht beachtet.  Der Rückgabewert beider Funktionen ist der boolescher Wert **TRUE** oder **FALSE**.  

Verwenden Sie **EndsWith** und **StartsWith** mit der **[Filter](function-filter-lookup.md)**-Funktion, um die Daten in der App zu durchsuchen. Sie können auch mit dem **[in](operators.md#in-and-exactin-operators)**-Operator oder der **[Search](function-filter-lookup.md)**-Funktion an einer beliebigen Stelle innerhalb von Textzeichenfolgen und nicht nur am Anfang oder Ende suchen.  Die Wahl der Funktionen hängt von den Anforderungen der Anwendung ab, und davon welche Funktion für Ihre bestimmte Datenquelle [delegiert](../delegation-overview.md) werden kann.  Wenn eine dieser Funktionen nicht delegiert werden kann, wird beim Erstellen eine Delegierungswarnung angezeigt, um Sie bezüglich dieser Einschränkung zu warnen.

## <a name="syntax"></a>Syntax
**EndsWith**( *Text*, *EndText* )

* *Text*: Erforderlich.  Der zu prüfende Text
* *EndText*: Erforderlich.  Der am Ende von *Text* zu suchende Text.  Wenn *EndText* eine leere Zeichenfolge ist, gibt **EndsWith** *TRUE* zurück.

**StartsWith**( *Text*, *StartText* )

* *Text*: Erforderlich.  Der zu prüfende Text
* *StartText*: erforderlich.  Der am Anfang von *Text* zu suchende Text  Wenn *StartText* eine leere Zeichenfolge ist, gibt **StartsWith** *TRUE* zurück.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **EndsWith( "Hello World", "world" )** |Überprüft, ob **"Hello World"** mit **"world"** endet.  Bei diesem Test wird die Groß-/Kleinschreibung nicht beachtet. |**TRUE** |
| **EndsWith( "Good bye", "good" )** |Überprüft, ob **"Good bye"** mit **"good"** endet.  Das *EndText*-Argument (**"good"**) ist im Text enthalten, jedoch nicht am Ende. |**FALSE** |
| **EndsWith( "Always say hello", "hello" )** |Prüft, ob **"Always say hello"** mit **"hello"** endet. |**TRUE** |
| **EndsWith( "Bye bye", "" )** |Prüft, ob **"Bye bye"** mit einer leeren Textzeichenfolge endet (**Len** gibt 0 zurück).  Bei seiner vereinfachten Verwendung in **Filter**-Ausdrücken ist **EndsWith** so definiert, dass in diesem Fall **TRUE** zurückgegeben wird. |**TRUE** |

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **StartsWith( "Hello World", "hello" )** |Prüft, ob **„Hello World“** mit **„Hello“** beginnt.  Bei diesem Test wird die Groß-/Kleinschreibung nicht beachtet. |**TRUE** |
| **StartsWith( "Good bye", "hello" )** |Prüft, ob **„Good Bye“** mit **„Hello“** beginnt |**FALSE** |
| **StartsWith( "Always say hello", "hello" )** |Prüft, ob **„Always Say Hello“** mit **„Hello“** beginnt.  Obwohl **„Hello“** im Text vorkommt, kommt es nicht am Anfang vor. |**FALSE** |
| **StartsWith( "Bye bye", "" )** |Prüft, ob **"Bye bye"** mit einer leeren Textzeichenfolge beginnt (**Len** gibt 0 zurück).  Bei seiner vereinfachten Verwendung in **Filter**-Ausdrücken ist **StartsWith** so definiert, dass in diesem Fall **TRUE** zurückgegeben wird. |**TRUE** |

### <a name="search-user-experience"></a>Benutzererfahrung beim Durchsuchen
In vielen Apps können Sie ein oder mehrere Zeichen in ein Suchfeld eingeben, um eine gefilterte Liste mit Datensätzen aus einem großen Datenbestand zu erzeugen. Während der Eingabe zeigt die Liste nur die Datensätze, die den Suchkriterien entsprechen.

Die Beispiele im Rest dieses Themas zeigen die Ergebnisse der Suche in einer Liste **Customers** (Kunden), die diese Daten enthalten:

![](media/function-startswith/customers.png)

Erstellen Sie ein **[Button](../controls/control-button.md)**-Steuerelement, und legen Sie dessen **OnSelect**-Eigenschaft auf folgende Formel fest, um diese Datenquelle als Sammlung zu erstellen:

**ClearCollect( Customers, Table( { Name: "Fred Garcia", Company: "Northwind Traders" }, { Name: "Cole Miller", Company: "Contoso" }, { Name: "Glenda Johnson", Company: "Contoso" }, { Name: "Mike Collins", Company: "Adventure Works" }, { Name: "Colleen Jones", Company: "Adventure Works" } ) )**

Sie können wie in diesem Beispiel eine Datensatzliste in einem [**Katalogsteuerelement**](../controls/control-gallery.md) am unteren Rand des Bildschirms anzeigen. Fügen Sie im oberen Bereich des Bildschirms ein [**Texteingabe**](../controls/control-text-input.md)-Steuerelement mit dem Namen **SearchInput** ein, sodass Benutzer angeben können, welche Datensätze für sie relevant sind.

![](media/function-startswith/customers-ux-unfiltered.png)

Wenn der Benutzer Zeichen in **SearchInput** eingibt, werden die Ergebnisse im Katalog automatisch gefiltert. In diesem Fall ist der Katalog so konfiguriert, dass er Datensätze anzeigt, für die der Name des Kunden (nicht der Namen des Unternehmens) mit der Zeichensequenz in **SearchInput** beginnt. Wenn der Benutzer **co** in das Suchfeld eingibt, zeigt der Katalog folgende Ergebnisse:

![](media/function-startswith/customers-ux-startswith-co.png)

Legen Sie die Eigenschaft **Items** des Katalogsteuerelements auf eine der folgenden Formeln fest, um anhand der Spalte **Name** zu filtern:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in der die Suchzeichenfolge am Anfang der Spalte **Name** vorkommt. Bei diesem Test wird die Groß-/Kleinschreibung nicht beachtet. Wenn der Benutzer **co** in das Suchfeld eingibt, zeigt der Katalog **Colleen Jones** und **Cole Miller** an. **Mike Collins** wird nicht im Katalog angezeigt, weil die Spalte **Name** dieses Datensatzes nicht mit der Suchzeichenfolge beginnt. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in der die Suchzeichenfolge am Anfang der Spalte **Name** vorkommt. Bei diesem Test wird die Groß-/Kleinschreibung nicht beachtet. Wenn der Benutzer **co** in das Suchfeld eingibt, zeigt der Katalog **Colleen Jones**, **Cole Miller** und **Mike Collins** an, da die Suchzeichenfolge an einer beliebigen Stelle in der Spalte **Name** dieser Datensätze vorkommt. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name" )** |Die **Search**-Funktion wird so ähnlich wie der **in**-Operator verwendet und sucht nach einer Übereinstimmung in der Spalte **Name** in jedem Datensatz. Beachten Sie, dass Sie den Spaltennamen in doppelte Anführungszeichen setzen müssen. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-contains.png) |

Sie können Ihre Suche auch so ausweiten, dass sie die Spalte **Company** sowie die Spalte **Name** enthält:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) &#124;&#124; StartsWith( Company, SearchInput.Text ) )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in denen entweder die Spalte **Name** oder die Spalte **Company** mit der Suchzeichenfolge beginnt (z.B. **co**).  Der [**&#124;&#124;**-Operator](operators.md) ist *TRUE*, wenn eine **StartsWith**-Funktion *TRUE* ist. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name &#124;&#124; SearchInput.Text in Company )** |Filtert die **Customers**-Datenquelle nach Datensätzen, in denen entweder die Spalte **Name** oder die Spalte **Company** die Suchzeichenfolge (z.B. **co**) an beliebiger Stelle enthält. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name", "Company" )** |Die **Search**-Funktion wird so ähnlich wie der **in**-Operator verwendet und durchsucht die **Customers**-Datenquelle nach Datensätzen, in denen entweder die **Name**-Spalte oder die **Company**-Spalte die Suchzeichenfolge (z.B. **co**) an beliebiger Stelle enthält. Die **Search**-Funktion ist einfacher zu lesen und zu schreiben als die **Filter**-Funktion, wenn Sie mehrere Spalten und mehrere **in**-Operatoren angeben möchten. Beachten Sie, dass Sie die Spaltennamen in doppelte Anführungszeichen setzen müssen. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-contains.png) |

