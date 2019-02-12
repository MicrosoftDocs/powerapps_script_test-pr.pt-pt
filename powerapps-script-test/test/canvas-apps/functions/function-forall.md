---
title: Funktion „ForAll“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „ForAll“ in PowerApps
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
ms.openlocfilehash: 688b1e87e5bc1d2ee3429711b9995f3b4ef61e1c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42857106"
---
# <a name="forall-function-in-powerapps"></a>Funktion „ForAll“ in PowerApps
Berechnet Werte und führt Aktionen für alle [Datensätze](../working-with-tables.md#records) einer [Tabelle](../working-with-tables.md) durch.

## <a name="description"></a>Beschreibung
Die **ForAll**-Funktion wertet eine Formel für alle Datensätze einer Tabelle aus.  Die Formel kann einen Wert berechnen und/oder Aktionen wie das Ändern von Daten oder das Arbeiten mit einer Verbindung ausführen.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

### <a name="return-value"></a>Rückgabewert
Das Ergebnis jeder Formelauswertung wird in einer Tabelle in der gleichen Reihenfolge wie in der Eingabetabelle zurückgegeben.

Wenn das Ergebnis der Formel ein einzelner Wert ist, ist die resultierende Tabelle eine einspaltige Tabelle.  Wenn das Ergebnis der Formel ein Datensatz ist, enthält die resultierende Tabelle Datensätze mit den gleichen Spalten wie der Ergebnisdatensatz.  

Wenn das Ergebnis der Formel ein *leerer* Wert ist, gibt es für diesen Eingabedatensatz in der Ergebnistabelle keinen Datensatz.  In diesem Fall gibt es weniger Datensätze in der Ergebnistabelle als in der Quelltabelle.

### <a name="taking-action"></a>Ausführen von Aktionen
Die Formel kann Funktionen enthalten, die Aktionen ausführen, wie z.B. die Datensätze einer Datenquelle mit den Funktionen **[Patch](function-patch.md)** und **[Collect](function-clear-collect-clearcollect.md)** ändern.  Die Formel kann auch Methoden auf Verbindungen aufrufen.  Pro Datensatz können mithilfe des [**;**-Operators](operators.md) mehrere Aktionen ausgeführt werden. Die Tabelle, die das Subjekt der **ForAll**-Funktion ist, kann nicht geändert werden.

Beim Schreiben der Formel sollten Sie bedenken, dass Datensätze in beliebiger Reihenfolge und nach Möglichkeit parallel verarbeitet werden können.  Der erste Datensatz der Tabelle kann nach dem letzten Datensatz verarbeitet werden.  Achten Sie darauf, Reihenfolgeabhängigkeiten zu vermeiden.  Aus diesem Grund können Sie die Funktionen **[UpdateContext](function-updatecontext.md)**, **[Clear](function-clear-collect-clearcollect.md)** und **[ClearCollect](function-clear-collect-clearcollect.md)** nicht innerhalb einer **ForAll**-Funktion verwenden, da sie leicht Variablen enthalten könnten, die für diese Auswirkung anfällig sind.  Sie können **[Collect](function-clear-collect-clearcollect.md)** verwenden, aber die Reihenfolge, in der die Datensätze hinzugefügt werden, ist nicht definiert.

Mehrere Funktionen zum Ändern von Datenquellen, darunter **Collect**, **Remove** und **Update**, geben die geänderte Datenquelle als Rückgabewert zurück.  Diese Rückgabewerte können groß sein und umfangreiche Ressourcen in Anspruch nehmen, wenn sie für jeden Datensatz der **ForAll**-Tabelle zurückgegeben werden.  Möglicherweise entsprechen diese Rückgabewerte auch nicht Ihren Erwartungen, da **ForAll** parallel ausgeführt werden kann, und die Nebeneffekte dieser Funktionen von deren Ergebnis trennen kann.  Wenn der Rückgabewert von **ForAll** nicht verwendet wird, was bei Funktionen für die Änderung von Daten häufig der Fall ist, wird der Rückgabewert zum Glück nicht erstellt, und es gibt keine Bedenken hinsichtlich Ressourcen oder Reihenfolge.  Aber wenn Sie das Ergebnis einer **ForAll**-Funktion und einer der Funktionen verwenden, die eine Datenquelle zurückgeben, sollten Sie sich genau überlegen, wie Sie das Ergebnis strukturieren, und es zuerst mit kleinen Datensätzen ausprobieren.  

### <a name="alternatives"></a>Alternativen
Viele Funktionen in PowerApps können gleichzeitig mehrere Werte mit einer einspaltigen Tabelle verarbeiten.  Zum Beispiel kann die **Len**-Funktion eine Tabelle mit Textwerten verarbeiten und eine Tabelle mit Längen auf die gleiche Weise zurückgeben wie **ForAll**.  Dadurch ist **ForAll** in vielen Fällen nicht mehr erforderlich, und Effizienz und Lesbarkeit können erhöht werden.

Ein weiterer Aspekt ist, dass **ForAll** im Gegensatz zu anderen Funktionen wie z.B. **Filter** nicht delegiert werden kann.  

### <a name="delegation"></a>Delegierung
[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>Syntax
**ForAll**( *Tabelle*, *Formel* )

* *Tabelle* (erforderlich): Zugrunde liegende Tabelle.
* *Formel* (erforderlich):  Die Formel zur Auswertung für alle Datensätze der *Tabelle*.

## <a name="examples"></a>Beispiele
### <a name="calculations"></a>Berechnungen
In den folgenden Beispielen wird die **Squares**-[Datenquelle](../working-with-data-sources.md) verwendet:

![](media/function-forall/squares.png)

Legen Sie die **OnSelect**-Eigenschaft eines **Button**-Steuerelements auf diese Formel fest, öffnen Sie den Vorschaumodus, und klicken oder tippen Sie anschließend auf die Schaltfläche, um diese Datenquelle als Sammlung zu erstellen:

* **ClearCollect( Squares, [ "1", "4", "9" ] )**

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **ForAll(&nbsp;Squares, Sqrt(&nbsp;Value&nbsp;)&nbsp;)**<br><br>**Sqrt(&nbsp;Squares&nbsp;)** |Berechnet für alle Datensätze der Eingabetabelle die Quadratwurzel der **Value**-Spalte.  Die **Sqrt**-Funktion kann auch mit einer einspaltigen Tabelle verwendet werden, sodass dieses Beispiel ohne **ForAll** ausgeführt werden kann. |<style> img { max-width: none } </style> ![](media/function-forall/sqrt.png) |
| **ForAll(&nbsp;Squares, Power(&nbsp;Value,&nbsp;3&nbsp;)&nbsp;)** |Berechnet für alle Datensätze der Eingabetabelle die dritte Potenz der **Value**-Spalte.  Die **Power**-Funktion unterstützt einspaltige Tabellen nicht. Deshalb muss in diesem Fall **ForAll** verwendet werden. |<style> img { max-width: none } </style> ![](media/function-forall/power3.png) |

### <a name="using-a-connection"></a>Verwenden einer Verbindung
In den folgenden Beispielen wird die **Expressions**-[Datenquelle](../working-with-data-sources.md) verwendet:

![](media/function-forall/translate.png)

Legen Sie die **OnSelect**-Eigenschaft eines **Button**-Steuerelements auf diese Formel fest, öffnen Sie den Vorschaumodus, und klicken oder tippen Sie anschließend auf die Schaltfläche, um diese Datenquelle als Sammlung zu erstellen:

* **ClearCollect( Expressions, [ "Hello", "Good morning", "Thank you", "Goodbye" ] )**

Dieses Beispiel verwendet auch eine [Microsoft Translator](../connections/connection-microsoft-translator.md)-Verbindung.  Wie Sie diese Verbindung zu Ihrer App hinzufügen, erfahren Sie im Thema [Manage your connections (Verwalten von Verbindungen)](../add-manage-connections.md).

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "es" ) )** |Übersetzt für alle Datensätze in der Expressions-Tabelle den Inhalt der **Value**-Spalte ins Spanische (abgekürzt "es"). |<style> img { max-width: none } </style> ![](media/function-forall/translate-es.png) |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "fr" ) )** |Übersetzt für alle Datensätze in der Expressions-Tabelle den Inhalt der **Value**-Spalte ins Französische (abgekürzt "fr"). |<style> img { max-width: none } </style> ![](media/function-forall/translate-fr.png) |

### <a name="copying-a-table"></a>Kopieren einer Tabelle
In einigen Fällen müssen Sie Daten filtern, strukturieren, sortieren und bearbeiten.  PowerApps bietet dafür eine Reihe von Funktionen wie **Filter**, **AddColumns** und **Sort**.  PowerApps behandelt jede Tabelle als Wert, sodass sie Formeln passieren und auf einfache Weise genutzt werden kann.      

Zudem kann es vorkommen, dass Sie eine Kopie dieses Ergebnisses zur späteren Verwendung erstellen möchten.  Oder Sie möchten Informationen aus einer Datenquelle in eine andere verschieben.  PowerApps bietet die **Collect**-Funktion zum Kopieren von Daten.

Aber bevor Sie eine Kopie erstellen, sollten Sie sich genau überlegen, ob dies wirklich erforderlich ist.  Viele Situationen können durch Filtern und Strukturieren der zugrunde liegenden Datenquelle nach Bedarf mit einer Formel behoben werden. Zu den Nachteilen der Erstellung einer Kopie gehören:

* Bei zwei Kopien derselben Informationen kann eine von ihnen möglicherweise nicht mehr synchron abgerufen werden.  
* Das Erstellen einer Kopie kann viel Arbeitsspeicher, Netzwerkbandbreite und/oder Zeit beanspruchen.  
* Bei den meisten Datenquellen kann der Kopiervorgang nicht delegiert werden, und dadurch wird beschränkt, wie viele Daten verschoben werden können.      

In den folgenden Beispielen wird die **Products**-[Datenquelle](../working-with-data-sources.md) verwendet:

![](media/function-forall/prod.png)

Legen Sie die **OnSelect**-Eigenschaft eines **Button**-Steuerelements auf diese Formel fest, öffnen Sie den Vorschaumodus, und klicken oder tippen Sie anschließend auf die Schaltfläche, um diese Datenquelle als Sammlung zu erstellen:

* **ClearCollect( Products, Table( { Product: "Widget", 'Quantity Requested': 6, 'Quantity Available': 3 }, { Product: "Gadget", 'Quantity Requested': 10, 'Quantity Available': 20 }, { Product: "Gizmo", 'Quantity Requested': 4, 'Quantity Available': 11 }, { Product: "Apparatus", 'Quantity Requested': 7, 'Quantity Available': 6 } ) )**

Unser Ziel ist es, mit einer abgeleiteten Tabelle zu arbeiten, die nur die Artikel enthält, von denen mehr angefordert wurde als verfügbar ist, und für die wir eine Bestellung aufgeben müssen:

![](media/function-forall/prod-order.png)  

Wir können diese Aufgabe auf verschiedene Weisen ausführen, die alle mit verschiedenen Vor- und Nachteilen zum gleichen Ergebnis führen.

#### <a name="table-shaping-on-demand"></a>Tabellenstrukturierung nach Bedarf
Erstellen Sie keine Kopie!  Wir können die folgende Formel an einer beliebigen Stelle verwenden:

* **ShowColumns( AddColumns( Filter( Products, 'Quantity Requested' > 'Quantity Available' ), "Quantity To Order", 'Quantity Requested' - 'Quantity Available' ), "Product", "Quantity To Order" )**

Es wird ein [Datensatzbereich](../working-with-tables.md#record-scope) von den Funktionen **Filter** und **AddColumns** erstellt, um den Vergleich bzw. die Subtraktion mit den Feldern **'Quantity Requested'** (Angeforderte Menge) und **'Quantity Available'** (Verfügbare Menge) jedes Datensatzes durchzuführen.

In diesem Beispiel kann die **Filter**-Funktion delegiert werden.  Dies ist wichtig, da sie alle Produkte finden kann, die die Kriterien erfüllen, auch wenn es nur wenige Datensätze aus einer Tabelle mit Millionen von Datensätzen sind.  Zu diesem Zeitpunkt können **ShowColumns** und **AddColumns** nicht delegiert werden, sodass die tatsächliche Anzahl von Produkten, die bestellt werden müssen, beschränkt ist.  Wenn Sie wissen, dass der Umfang dieses Ergebnisses immer relativ gering sein wird, ist dieser Ansatz in Ordnung.

Und da wir keine Kopie erstellt haben, muss keine zusätzliche Kopie der Informationen verwaltet werden und kann auch nicht veralten.  

#### <a name="forall-on-demand"></a>ForAll nach Bedarf
Ein anderer Ansatz ist die **ForAll**-Funktion, um die Funktionen zur Tabellenstrukturierung zu ersetzen:

* **ForAll( Products, If( 'Quantity Requested' > 'Quantity Available', { Product: Product, 'Quantity To Order': 'Quantity Requested' - 'Quantity Available' } ) )**

Diese Formel ist für einige Personen möglicherweise einfacher zu lesen und zu schreiben.

Kein Teil der **ForAll**-Funktion kann delegiert werden.  Es wird nur der erste Teil der **Products**-Tabelle ausgewertet, was möglicherweise ein Problem darstellt, wenn diese Tabelle sehr groß ist.  Da **Filter** im vorherigen Beispiel delegiert werden konnte, konnte die Funktion besser mit großen Datensätzen arbeiten.

#### <a name="collect-the-result"></a>Sammeln des Ergebnisses
In einigen Situationen ist möglicherweise eine Kopie der Daten erforderlich.  Es kann vorkommen, dass Sie Informationen aus einer Datenquelle in eine andere verschieben müssen.  In diesem Beispiel werden alle Bestellungen über eine **NewOrder**-Tabelle auf dem System eines Anbieters aufgegeben.  Für Hochgeschwindigkeits-Benutzerinteraktionen empfiehlt es sich, eine lokale Kopie einer Tabelle zwischenzuspeichern, sodass es nicht zu Serverwartezeit kommt.

Wir verwenden die gleiche Tabellenstrukturierung wie in den beiden vorherigen Beispielen, aber wir erfassen das Ergebnis in einer Sammlung:

* **ClearCollect( NewOrder, ShowColumns( AddColumns( Filter( Products, 'Quantity Requested' > 'Quantity Available' ), "Quantity To Order", 'Quantity Requested' - 'Quantity Available' ), "Product", "Quantity To Order" ) )**
* **ClearCollect( NewOrder, ForAll( Products, If( 'Quantity Requested' > 'Quantity Available', { Product: Product, 'Quantity To Order': 'Quantity Requested' - 'Quantity Available' } ) ) )**

**ClearCollect** und **Collect** können nicht delegiert werden.  Deshalb ist die Menge der Daten, die auf diese Weise verschoben werden können, beschränkt.

#### <a name="collect-within-forall"></a>Sammeln innerhalb von ForAll
Schließlich können wir **Collect** direkt in **ForAll** ausführen:

* **Clear( ProductsToOrder ); ForAll( Products, If( 'Quantity Requested' > 'Quantity Available', Collect( NewOrder, { Product: Product, 'Quantity To Order': 'Quantity Requested' - 'Quantity Available' } ) ) )**

In diesem Fall kann die **ForAll**-Funktion auch nicht delegiert werden.  Wenn die **Products**-Tabelle sehr groß ist, untersucht **ForAll** nur den ersten Satz von Datensätzen und lässt möglicherweise Produkte aus, die bestellt werden müssen.  Aber für Tabellen, die klein bleiben, ist dieser Ansatz in Ordnung.

Beachten Sie, dass wir das Ergebnis von **ForAll** nicht erfassen.  Die **Collect**-Funktionsaufrufe, die daraus erfolgen, geben die **NewOrder**-Datenquelle für alle Datensätze zurück, was auf eine große Datenmenge hinauslaufen könnte, wenn wir es erfassen würden.  

