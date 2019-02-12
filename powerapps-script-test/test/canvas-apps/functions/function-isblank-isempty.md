---
title: Funktionen „Blank“, „Coalesce“, „IsBlank“ und „IsEmpty“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich von Syntax und Beispielen, für die Funktionen „Blank“, „Coalesce“, „IsBlank“ und „IsEmpty“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.component: canvas
ms.date: 07/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e31d3689c7b61c408be90c31f1e212e4fdd9a91c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42848981"
---
# <a name="blank-coalesce-isblank-and-isempty-functions-in-powerapps"></a>Die Funktionen „Blank“, „Coalesce“, „IsBlank“ und „IsEmpty“ in PowerApps
Prüft, ob ein Wert leer ist oder eine [Tabelle](../working-with-tables.md) keine [Datensätze](../working-with-tables.md#records) enthält, und stellt ein Verfahren zum Erstellen von *leeren* Werten zur Verfügung.

## <a name="overview"></a>Übersicht
*Blank* ist ein Platzhalter für "no value" (kein Wert) oder "unknown value" (unbekannter Wert). Ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement ist *leer*, wenn der Benutzer keinerlei Zeichen darin eingegeben hat. Das Steuerelement ist nicht mehr *blank*, sobald der Benutzer ein Zeichen eingibt.  Einige Datenquellen können NULL-Werte speichern und zurückgeben, die in PowerApps als *leer* dargestellt werden.

> [!NOTE]
> Aktuell wird das Speichern von *leeren* Werten nur für lokale Sammlungen unterstützt. Es ist uns bewusst, dass viele Datenquellen *leere* Werte (NULL-Werte) unterstützen und arbeiten daran, diese Einschränkung aufzuheben.

Jede Eigenschaft und jeder berechnete Wert kann *blank* sein.  Ein boolescher Wert weist normalerweise einen von zwei Werten auf: **TRUE** oder **FALSE**.  Zusätzlich zu diesen beiden Werten kann ein boolescher Wer auch *blank* sein.  Dies ist vergleichbar mit Microsoft Excel, wo eine Zelle eines Arbeitsblatts zunächst leer ist, aber u.a. auch die Werte **TRUE** und **FALSE** enthalten darf. Der Inhalt der Zelle kann immer entfernt werden, sodass die Zelle dann wieder *blank* wäre.

*Empty* bezieht sich auf Tabellen, die keine Datensätze enthalten. Die Tabellenstruktur ist möglicherweise mit [Spaltennamen](../working-with-tables.md#columns) intakt, enthält jedoch keine Werte. Eine Tabelle kann zunächst leer sein, Datensätzen aufnehmen und dann nicht mehr leer sein, und dann erneut leer sein, wenn die Datensätze entfernt werden.

## <a name="description"></a>Beschreibung
Die Funktion **Blank** gibt einen *leeren* Wert zurück. Sie können sie verwenden, um einen NULL-Wert in einer Datenquelle zu speichern, die diese Werte unterstützt, wodurch effektiv jeder Wert aus dem Feld entfernt wird.

Die **IsBlank**-Funktion prüft auf einen *blank*-Wert. *Blank*-Werte entstehen in folgenden Szenarios:

* Der Rückgabewert der Funktion **Blank**.
* Eine Steuerelementeigenschaft verfügt nicht über eine festgelegte Formel.
* In ein Texteingabe-Steuerelement wurde kein Wert eingegeben, oder in einem Listenfeld wurde keine Auswahl getroffen. Sie können **IsBlank** dazu verwenden, zu melden, dass ein Feld erforderlich ist.
* Eine Zeichenfolge, die keine Zeichen enthält, verfügt über eine **[Len](function-len.md)** (Länge) von 0.
* In einer Funktion ist ein Fehler aufgetreten. Oft ist dann ein Argument der Funktion nicht gültig. Viele Funktionen geben *blank* zurück, wenn der Wert eines Arguments *blank* ist.
* Verbundene [Datenquellen](../working-with-data-sources.md), z.B. SQL Server, verwenden möglicherweise NULL-Werte. Diese Werte werden als *blank* in PowerApps angezeigt.
* Der *else*-Teil einer **[If](function-if.md)**-Funktion wurde nicht angegeben, und alle Bedingungen sind **FALSE**.
* Sie haben die **[Update](function-update-updateif.md)**-Funktion verwendet, aber keinen Wert für alle Spalten angegeben. Daher wurden keine Werte in die Spalten aufgenommen, die Sie nicht angegeben haben.

Die **Coalesce**-Funktion wertet ihre Argumente der Reihe nach aus und gibt den ersten Wert zurück, der nicht *leer* ist.  Ersetzen Sie mithilfe dieser Funktion einen *blank*-Wert durch einen anderen Wert, während die anderen nicht *leeren* Werte unverändert beibehalten werden.  Sind alle Argumente *leer*, gibt die Funktion *blank* zurück.  Alle Argumente von **Coalesce** müssen vom selben Typ sein; es können nicht Zahlen und Textzeichenfolgen gleichzeitig angegeben werden.  **Coalesce( Wert1, Wert2 )** ist die präzisere Entsprechung von **If( Not( IsBlank( Wert1 ) ), Wert1, Wert2 )**, und **Wert1** muss nicht zweimal ausgewertet werden.  

Die **IsEmpty**-Funktion prüft, ob eine Tabelle keine Datensätze enthält. Dies entspricht dem Einsatz der **[CountRows](function-table-counts.md)**-Funktion und dem Prüfen auf 0. Sie können nach Fehlern in Datenquellen suchen, indem Sie **IsEmpty** mit der **[Errors](function-errors.md)**-Funktion kombinieren.

Der Rückgabewert für die beiden Funktionen **IsBlank** und **IsEmpty** ist ein Boolescher Wert **WAHR** oder **FALSCH**.

## <a name="syntax"></a>Syntax
**Blank**()

**Coalesce**( *Wert1* [, *Wert2*, ... ] )

* *Wert(e)* – Erforderlich. Die zu testenden Werte.  Jeder Wert wird der Reihe nach ausgewertet, bis ein nicht *leerer* Wert gefunden wird.  Werte nach dem ersten nicht *leeren* Wert werden nicht ausgewertet.  

**IsBlank**( *Value* )

* *Wert*: Erforderlich. Der zu prüfende Wert

**IsEmpty**( *Table* )

* *Tabelle* (erforderlich): Tabelle, die auf Datensätze geprüft werden soll

## <a name="examples"></a>Beispiele
### <a name="blank"></a>Blank
> [!NOTE]
> Aktuell funktioniert das folgende Beispiel nur mit lokalen Sammlungen.  Es ist uns bewusst, dass viele Datenquellen *leere* Werte (NULL-Werte) unterstützen. Wir arbeiten daran, diese Einschränkung aufzuheben.

1. Erstellen Sie eine Anwendung von Grund auf, und fügen Sie ein **Schaltfläche**-Steuerelement hinzu.
2. Legen Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:

    **ClearCollect( Cities, { Name: "Seattle", Weather: "Rainy" } )**
3. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die hinzugefügte Schaltfläche, und schließen Sie dann die Vorschau.  
4. Klicken oder tippen Sie im Menü **Datei** auf **Sammlungen**.

     Die Sammlung **Cities** wird angezeigt und enthält einen Datensatz mit „Seattle“ und „Rainy“:

    ![Sammlung, die Seattle bei Regen zeigt](./media/function-isblank-isempty/seattle-rainy.png)
5. Klicken oder tippen Sie auf den Rückwärtspfeil, um zum Standardarbeitsbereich zurückzukehren.
6. Fügen Sie ein **Label**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **Text**-Eigenschaft auf diese Formel fest:

    **IsBlank( First( Cities ).Weather )**

    Die Bezeichnung zeigt **FALSCH** an, da das Feld **Weather** einen Wert („Rainy“) enthält.
7. Fügen Sie eine zweite Schaltfläche hinzu, und legen Sie ihre **OnSelect**-Eigenschaft auf diese Formel fest:

    **Patch( Cities, First( Cities ), { Weather: Blank() } )**
8. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die hinzugefügte Schaltfläche, und schließen Sie dann die Vorschau.  

    Das Feld **Weather** des ersten Datensatzes in **Cities** wird durch ein *leeres* Element ersetzt, wodurch der vorherige Wert „Rainy“ entfernt wird.

    ![Sammlung, die Seattle mit einem leeren Feld „Weather“ enthält](./media/function-isblank-isempty/seattle-blank.png)

    Die Bezeichnung zeigt **WAHR** an, da das Feld **Weather** keinen Wert mehr enthält.

### <a name="coalesce"></a>Coalesce

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Coalesce( Blank(), 1 )** |Prüft den Rückgabewert der Funktion **Blank**, die immer einen *leeren* Wert zurückgibt. Da das erste Argument *leer* ist, wird mit der Auswertung des nächsten Arguments fortgefahren, bis ein nicht *leerer* Wert gefunden wird. |**1** |
| **Coalesce( Blank(), Blank(), Blank(), Blank(), 2, 3 )** |**Coalesce** beginnt am Anfang der Argumentliste und wertet nacheinander jedes Argument aus, bis ein nicht *leerer* Wert gefunden wird.  In diesem Fall geben die ersten vier Argumente *blank* (leer) zurück, sodass die Auswertung mit dem fünften Argument fortgesetzt wird. Das fünfte Argument ist nicht *leer*, sodass die Auswertung hier beendet wird. Der Wert des fünften Arguments wird zurückgegeben, und das sechste Argument wird nicht ausgewertet. |**2** |

### <a name="isblank"></a>IsBlank
1. Erstellen Sie eine App von Grund auf, fügen Sie ein Texteingabe-Steuerelement hinzu, und benennen Sie es **FirstName**.
2. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](../controls/properties-core.md)** auf diese Funktion fest:

    **If( IsBlank( FirstName.Text ), "First Name is a required field." )**

    Standardmäßig ist die Eigenschaft **[Text](../controls/properties-core.md)** eines Texteingabe-Steuerelements auf **„Texteingabe“** festgelegt. Da die Eigenschaft einen Wert enthält, ist sie nicht leer, und die Bezeichnung zeigt keinerlei Nachricht an.
3. Entfernen Sie alle Zeichen aus dem Texteingabe-Steuerelement, einschließlich Leerzeichen.

    Da die Eigenschaft **[Text](../controls/properties-core.md)** keine Zeichen mehr enthält, ist sie *leer*, und **IsBlank( FirstName.Text )** ist daher **WAHR**. Die Meldung für ein erforderliches Feld wird angezeigt.

Informationen für die Validierung mithilfe anderer Tools finden Sie bei der Funktion **[Validate](function-validate.md)** und unter [Arbeiten mit Datenquellen](../working-with-data-sources.md).  

Weitere Beispiele:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **IsBlank( Blank() )** |Prüft den Rückgabewert der Funktion **Blank**, die immer einen *leeren* Wert zurückgibt. |**TRUE** |
| **IsBlank( "" )** |Eine Zeichenfolge, die keine Zeichen enthält |**TRUE** |
| **IsBlank ("Hello")** |Eine Zeichenfolge, die ein oder mehrere Zeichen enthält |**FALSE** |
| **IsBlank ( *AnyCollection* )** |Da die [Sammlung](../working-with-data-sources.md#collections) vorhanden ist, ist sie nicht leer, auch wenn sie keine Datensätze enthält. Verwenden Sie stattdessen zum Überprüfen auf eine leeren Sammlung **IsEmpty**. |**FALSE** |
| **IsBlank( Mid( "Hello", 17, 2 ) )** |Das Anfangszeichen für **[Mid](function-left-mid-right.md)** befindet sich hinter dem Ende der Zeichenfolge.  Das Ergebnis ist eine leere Zeichenfolge. |**TRUE** |
| **IsBlank( If( false, false ) )** |Eine **[If](function-if.md)**-Funktion ohne *ElseResult*.  Da die Bedingung immer **FALSE** ist, gibt diese **[If](function-if.md)**-Funktion immer *blank* zurück. |**TRUE** |

### <a name="isempty"></a>IsEmpty
1. Erstellen Sie eine Anwendung von Grund auf, und fügen Sie ein **Schaltfläche**-Steuerelement hinzu.
2. Legen Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:

    **Collect( IceCream, { Flavor: "Strawberry", Quantity: 300 }, { Flavor: "Chocolate", Quantity: 100 } )**
3. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die hinzugefügte Schaltfläche, und schließen Sie dann die Vorschau.  

    Eine Sammlung mit dem Namen **IceCream** wird erstellt und enthält diese Daten:

    ![](media/function-isblank-isempty/icecream-strawberry-chocolate.png)

    Diese Sammlung verfügt über zwei Datensätze und ist nicht leer. **IsEmpty( IceCream )** gibt **FALSE** zurück, und **CountRows( IceCream )** gibt **2** zurück.
4. Fügen Sie eine zweite Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Formel fest:

    **Clear( IceCream )**
5. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die zweite Schaltfläche, und schließen Sie dann die Vorschau.  

    Die Sammlung ist jetzt leer:

    ![](media/function-isblank-isempty/icecream-clear.png)

    Die **[Clear](function-clear-collect-clearcollect.md)**-Funktion entfernt alle Datensätze aus einer Sammlung, woraus sich eine leere Sammlung ergibt. **IsEmpty( IceCream )** gibt **TRUE** und **CountRows( IceCream )** gibt **0** zurück.

Sie können auch **IsEmpty** verwenden, um zu prüfen, ob eine berechnete Tabelle leer ist, wie diese Beispiele zeigen:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **IsEmpty( [&nbsp;1,&nbsp;2,&nbsp;3 ] )** |Die einspaltige Tabelle enthält drei Datensätze und ist daher nicht leer. |**FALSE** |
| **IsEmpty( [&nbsp;] )** |Die einspaltige Tabelle enthält keine Datensätze und ist leer. |**TRUE** |
| **IsEmpty( Filter( [&nbsp;1,&nbsp;2,&nbsp;3&nbsp;], Value > 5 ) )** |Die einspaltige Tabelle enthält keine Werte, die größer als 5 sind.  Das Ergebnis des Filters enthält keine Datensätze und ist leer. |**TRUE** |

