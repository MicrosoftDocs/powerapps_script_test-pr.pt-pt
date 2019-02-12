---
title: Funktion „Text“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Text“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dab6004afe7350b2375ade21871efe9144b6325b
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849291"
---
# <a name="text-function-in-powerapps"></a>Funktion „Text“ in PowerApps
Formatiert eine Zahl oder einen Datums-/Uhrzeit-Wert für die Anzeige als Textzeichenfolge.

## <a name="description"></a>Beschreibung
Die Funktion **Text** formatiert eine Zahl oder einen Datums-/Uhrzeit-Wert auf der Grundlage eines dieser Argumenttypen:

* Eines vordefinierten Datums-/Uhrzeitformats, das Sie mithilfe der **DateTimeFormat**-Enumeration angeben.  Dies ist das bevorzugte Format für Datums- und Uhrzeitwerte, da es sich automatisch an die Sprache und das Gebietsschema des Benutzers anpasst.
* Eines benutzerdefinierten Formats, d.h. einer Textzeichenfolge, die Platzhalter beinhaltet, die ihrerseits die Formatierung der Zahl oder des Datums-/Uhrzeitwerts beschreiben. Platzhalter definieren, wie viele Stellen angezeigt, ob Gruppentrennzeichen verwendet und wie Monatsnamen angezeigt werden sollen. PowerApps unterstützt eine Teilmenge der von Microsoft Excel unterstützten Platzhalter.

Weitere Informationen finden Sie unter [Arbeiten mit Datums- und Uhrzeitangaben](../show-text-dates-times.md).

### <a name="predefined-datetime-formats"></a> Vordefinierte Datums-/Uhrzeitformate

| Vordefiniertes Format | Beschreibung |
| --- | --- |
| **DateTimeFormat.LongDate** |Vollständiges Jahr, Monat, Tag des Monats und Wochentag. Monatsnamen und Wochentage sind nicht abgekürzt. |
| **DateTimeFormat.LongDateTime** |Vollständiges Jahr, Monat, Tag des Monats und Wochentag plus Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe. Monatsnamen und Wochentage sind nicht abgekürzt. |
| **DateTimeFormat.LongDateTime24** |Vollständiges Jahr, Monat, Tag des Monats und Wochentag plus Stunde (24-Stunden-Format), Minuten und Sekunden. Monatsnamen und Wochentage sind nicht abgekürzt. |
| **DateTimeFormat.LongTime** |Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe. Identisch mit ShortTime. |
| **DateTimeFormat.LongTime24** |Stunde (24-Stunden-Format), Minuten, Sekunden. Identisch mit ShortTime24. |
| **DateTimeFormat.ShortDate** |Vierstellige Jahresangabe mit zweistellig angegebenem Monat und Tag im Monat. |
| **DateTimeFormat.ShortDateTime** |Vierstellige Jahresangabe mit zweistellig angegebenem Monat und Tag im Monat plus Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe. |
| **DateTimeFormat.ShortDateTime24** |Vierstellige Jahresangabe mit zweistellig angegebenem Monat und Tag im Monat plus Stunde (24-Stunden-Format), Minuten und Sekunden. |
| **DateTimeFormat.ShortTime** |Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe.  Identisch mit LongTime. |
| **DateTimeFormat.ShortTime24** |Stunde (24-Stunden-Format), Minuten und Sekunden.  Identisch mit LongTime24. |
| **DateTimeFormat.UTC** |Der Datums-/Uhrzeitwert wird basierend auf der Zeitzone des Benutzers in UTC konvertiert und gemäß dem ISO 8601-Standard formatiert. |

### <a name="number-placeholders"></a>Zahlplatzhalter

| Platzhalter | Beschreibung |
| --- | --- |
| **0** (*null*) |Zeigt nicht signifikante Nullen an, wenn eine Zahl weniger Stellen aufweist, als Nullen im Format festgelegt sind. Verwenden Sie beispielsweise das Format **#,00**, wenn Sie **8,9** im Format **8,90** anzeigen möchten. |
| **#** |Folgt den gleichen Regeln wie **0** (null). **Text** gibt jedoch keine zusätzlichen Nullen zurück, wenn die Zahl weniger Stellen auf beiden Seiten des Dezimaltrennzeichens aufweist, als #-Symbole im Format vorhanden sind. Beispielsweise wird **8,9** angezeigt, wenn das benutzerdefinierte Format **#,##** und die zu formatierende Zahl **8,9** ist. |
| **.** (*Punkt*) |Zeigt das Dezimaltrennzeichen in einer Zahl an.  Hängt von der Sprache des benutzerdefinierten Formats ab, Details finden Sie unter [globale Anwendungen](#global-apps). |
| **.** (*Komma*) |Zeigt das Gruppierungstrennzeichen in einer Zahl an, häufig für Tausender verwendet. **Text** trennt Gruppen durch Punkte ab, wenn ein Format einen Punkt enthält, der von Zahlenzeichen (**#**) oder Nullen eingeschlossen ist.  Hängt von der Sprache des benutzerdefinierten Formats ab, Details finden Sie unter [globale Anwendungen](#global-apps). |

Wenn eine Zahl mehr Stellen rechts vom Dezimaltrennzeichen aufweist, als Platzhalter im Format vorhanden sind, wird die Zahl zu der im Format definierten Anzahl Dezimalstellen gerundet. Wenn links vom Dezimaltrennzeichen mehr Stellen als Platzhalter vorhanden sind, werden die zusätzlichen Stellen angezeigt. Wenn das Format nur Zahlenzeichen (#) links vom Dezimaltrennzeichen aufweist, beginnen Zahlen kleiner als 1 mit dem Dezimaltrennzeichen (z. B. **,47**).

### <a name="date-and-time-placeholders"></a>Platzhalter für Datum und Uhrzeit

|                                                                                                 Platzhalter                                                                                                  |                                                                                                     Beschreibung                                                                                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                    **m**                                                                                                     |                                                                               Zeigt den Monat als Zahl ohne führende Null an.                                                                                |
|                                                                                                    **mm**                                                                                                    |                                                                        Zeigt den Monat als Zahl mit führender Null an, wenn das angebracht ist.                                                                         |
|                                                                                                   **mmm**                                                                                                    |                                                                             Zeigt den Monat als Abkürzung an (**Jan** bis **Dez**).                                                                             |
|                                                                                                   **mmmm**                                                                                                   |                                                                          Zeigt den Monat als vollständigen Namen an (**Januar** bis **Dezember**).                                                                           |
|                                                                                                    **d**                                                                                                     |                                                                                Zeigt den Tag als Zahl ohne führende Null an.                                                                                 |
|                                                                                                    **dd**                                                                                                    |                                                                         Zeigt den Tag als Zahl mit führender Null an, wenn das angebracht ist.                                                                          |
|                                                                                                   **ddd**                                                                                                    |                                                                              Zeigt den Tag als Abkürzung an (**So** bis **Sa**).                                                                              |
|                                                                                                   **dddd**                                                                                                   |                                                                            Zeigt den Tag als vollständigen Namen an (**Sonntag** bis **Samstag**).                                                                            |
|                                                                                                    **yy**                                                                                                    |                                                                                      Zeigt das Jahr als zweistellige Zahl an.                                                                                       |
|                                                                                                   **yyyy**                                                                                                   |                                                                                      Zeigt das Jahr als vierstellige Zahl an.                                                                                      |
|                                                                                                    **h**                                                                                                     |                                                                                Zeigt die Stunde als Zahl ohne führende Null an.                                                                                |
|                                                                                                    **hh**                                                                                                    | Zeigt die Stunde als Zahl mit führender Null an, wenn das angebracht ist. Wenn das Format **AM** oder **PM** enthält, wird die Stunde basierend auf der 12-Stunden-Uhr angezeigt. Andernfalls wird die Stunde auf der 24-Stunden-Uhr basierend angezeigt. |
|                                                                                                    **m**                                                                                                     |                                                                         Zeigt die Minute als Zahl ohne führende Null an.  > [!NOTE]                                                                          |
|            Der Code **m** oder **mm** muss unmittelbar auf den Code **h** oder **hh** folgen oder dem Code **ss** unmittelbar voranstehen, andernfalls gibt **Text** den Monat anstelle von Minuten zurück.            |                                                                                                                                                                                                                     |
|                                                                                                    **mm**                                                                                                    |                                                                   Zeigt die Minute als Zahl mit führender Null an, wenn das angebracht ist. > [!NOTE]                                                                   |
| Der Code **m** oder **mm** muss unmittelbar auf den Code **h** oder **hh** folgen oder dem Code **ss** unmittelbar voranstehen. Andernfalls gibt **Text** den Monat anstelle von Minuten zurück. |                                                                                                                                                                                                                     |
|                                                                                                    **s**                                                                                                     |                                                                               Zeigt die Sekunde als Zahl ohne führende Null an.                                                                               |
|                                                                                                    **ss**                                                                                                    |                                                                        Zeigt die Sekunde als Zahl mit führender Null an, wenn das angebracht ist.                                                                        |
|                                                                                                    **f**                                                                                                     |                                                                                         Zeigt die Sekundenbruchteile an.                                                                                          |
|                                                                                    **AM/PM**, **am/pm**, **A/P**, **a/p**                                                                                    |               Zeigt die Stunde basierend auf dem 12-Stunden-Format an. **Text** gibt „AM“, „am“, „A“ oder „a“ für Uhrzeiten von Mitternacht bis Mittag und „PM“, „pm“, „P“ oder „p“ für Uhrzeiten von Mittag bis Mitternacht an                |

### <a name="literal-placeholders"></a>Literalplatzhalter
Sie können jedes dieser Zeichen in Ihre Formatzeichenfolge aufnehmen.  Sie werden im Ergebnis von **Text** wie eingegeben angezeigt. Zusätzliche Zeichen sind für kommende Platzhalter reserviert, daher sollten Sie diese nicht verwenden.

| Zeichen | Beschreibung |
| --- | --- |
| Beliebiges Währungssymbol |Dollarzeichen, Centzeichen, Eurozeichen usw. |
| **+** |Pluszeichen |
| **(** |Öffnende Klammer |
| **:** |Doppelpunkt |
| **^** |Zirkumflexakzent (Caretzeichen) |
| **'** |Apostroph |
| **{** |Öffnende geschweifte Klammer |
| **<** |Kleiner-als-Zeichen |
| **=** |Gleichheitszeichen |
| **-** |Minuszeichen |
| **/** |Schrägstrich |
| **)** |Schließende Klammer |
| **&** |Kaufmännisches Und-Zeichen |
| **~** |Tilde |
| **}** |Schließende geschweifte Klammer |
| **>** |Größer-als-Zeichen |
| &nbsp; |Leerzeichen |

## <a name="global-apps"></a>Globale Anwendungen
Die Funktion **Text** ist global kompatibel.  Sie „weiß“ für eine Vielzahl von Sprachen, wie Datumswerte, Uhrzeiten, Währungen und Zahlen ordnungsgemäß geschrieben werden.  Für ihren Job benötigt sie zwei Informationen :

* **Die Sprache des benutzerdefinierten Formats:** Wie soll ein benutzerdefiniertes Format aus Autorensicht interpretiert werden?  Die Trennzeichen (**.** und **,**) haben in verschiedenen Sprachen verschiedene Bedeutungen.  Dies wird mit einem besonderen Platzhalter bearbeitet, der ein Sprachkennzeichen enthält.  Um es noch zu vereinfachen, unterscheiden die [vordefinierten Datums-/Uhrzeitformate](#predefined-datetime-formats) nicht nach der Sprache.
* **Die Sprache des Ergebnisses:** Welche Sprache soll für Benutzer im Ergebnis der Funktion verwendet werden?  Namen von Monaten und Wochentagen müssen in der für den Benutzer der App passenden Sprache ausgegeben werden.  Dies wird mithilfe eines dritten, optionalen Arguments der Funktion **Text** verarbeitet. 

Für beide wird die Sprache in einem [Sprachkennzeichen](function-language.md#language-tags) angegeben.  Um eine Liste der unterstützten Sprachen anzuzeigen, geben Sie **Text( 1234, "", )** in die Bearbeitungsleiste oder die erweiterte Ansicht ein, und scrollen Sie durch die Liste der Gebietsschemas, die für das dritte Argument vorgeschlagen werden.

#### <a name="custom-format-language-placeholder"></a>Sprachplatzhalter für benutzerdefiniertes Format
Um die Sprache des benutzerdefinierten Formats anzugeben, verwenden Sie:

| Platzhalter | Beschreibung |
| --- | --- |
| **[$-*LanguageTag*]** |*Sprachkennzeichen* ist ein Sprachkennzeichen, wie es von der Funktion **Language** zurückgegeben wird.  Es kann die Form der einfachen Sprachangabe annehmen, wie etwa **[$-de]** für Deutsch, oder außerdem die Region enthalten, wie in **[$-de-AT]**, um das Gebietsschema auf Österreich einzugrenzen. |

Der Sprachplatzhalter kann an beliebiger Stelle im benutzerdefinierten Format auftreten, darf jedoch nur einmal angegeben werden.

Wenn Sie beim Erstellen einer Formel keinen Sprachplatzhalter angeben und das Format der Zeichenfolge vom globalen Standpunkt aus mehrdeutig ist, setzt das Verfassertool automatisch das Sprachkennzeichen für Ihre aktuelle Sprache ein.  

**[$-en-US]** wird zugrunde gelegt, wenn dieser Platzhalter beim Ausführen Ihrer App nicht vorhanden ist. 

> [!NOTE]
> In einer kommenden Version kann sich dieser Platzhalter möglicherweise ändern, um die Verwechselung mit einem ähnlichen, aber doch unterschiedlichen Platzhalter zu vermeiden, der von Excel unterstützt wird.

#### <a name="result-language-tag"></a>Sprachkennzeichen für das Ergebnis
Im Ergebnis von **Text** werden übersetzte Zeichenfolgen für Monat, Wochentag und AM/PM-Angaben sowie die passenden Gruppen- und Dezimaltrennzeichen angezeigt.

Standardmäßig verwendet **Text** die Sprache des Benutzers, der die Anwendung ausführt.  Die Funktion **Language** gibt das Sprachkennzeichen für den aktuellen Benutzer zurück.  Sie können diesen Standardwert überschreiben, indem Sie ein Sprachkennzeichen für das optionale dritte Argument von **Text** angeben.

## <a name="syntax"></a>Syntax
**Text**( *Number*, *DateTimeFormatEnum* [, *ResultLanguageTag* ] )

* *Number*: erforderlich. Die zu formatierende Zahl bzw. der zu formatierende Datums-/Uhrzeitwert.
* *DateTimeFormat*: erforderlich.  Ein Mitglied der **DateTimeFormat**-Enumeration.
* *ResultLanguageTag*: optional.  Das Sprachkennzeichen, das für den Ergebnistext verwendet werden soll.  Standardmäßig wird die Sprache des aktuellen Benutzers verwendet.

**Text**( *Number*, *CustomFormat* [, *ResultLanguageTag* ] )

* *Number*: erforderlich. Die zu formatierende Zahl bzw. der zu formatierende Datums-/Uhrzeitwert.
* *CustomFormat*: erforderlich. Mindestens ein in doppelte Anführungszeichen gesetzter Platzhalter.
* *ResultLanguageTag*: optional.  Das Sprachkennzeichen, das für den Ergebnistext verwendet werden soll.  Standardmäßig wird die Sprache des aktuellen Benutzers verwendet.

## <a name="examples"></a>Beispiele
Der Benutzer, der diese Formeln ausführt, befindet sich in den USA und hat Englisch als seine Sprache ausgewählt.  Die Funktion **Language** gibt „en-US“ zurück.

### <a name="number"></a>Number

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text (&nbsp;1234.59,&nbsp;"###, #"&nbsp;)** |Formatiert die Zahl mit einer Dezimalstelle. |"1234,6" |
| **Text (&nbsp;8,9&nbsp;"#,000"&nbsp;)** |Füllt die Nachkommastellen der Zahl mit nachfolgenden Nullen auf, falls erforderlich. |"8,900" |
| **Text (&nbsp;0,631,&nbsp;"0,#"&nbsp;)** |Füllt den ganzzahligen Teil der Zahl mit führenden Nullen auf, falls erforderlich. |"0,6" |
| **Text(&nbsp;12;&nbsp;"#,0#"&nbsp;)**<br>**Text(&nbsp;1234,568;&nbsp;"#,0#"&nbsp;)** |Füllt die Nachkommastellen der Zahl mit Nullen für eine Dezimalstelle auf und schließt eine zweite Dezimalstelle ein, wenn sie angegeben wird. |"12,0"<br>"1234,57" |
| **Text(&nbsp;12000;&nbsp;"$ #.###"&nbsp;)**<br>**Text(&nbsp;1200000;&nbsp;"$&nbsp;#.###"&nbsp;)** |Fügt nach jeweils drei Stellen ein Tausendertrennzeichen ein und schließt ein Währungssymbol mit ein. |"$&nbsp;12.000"<br>"$&nbsp;1.200.000" |

### <a name="datetime"></a>Datum/Uhrzeit
* Um **2:37:47 PM** am **Montag, 23. November 2015**
* Pacific-Zeitzone der USA (UTC-8)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text( Now(); DateTimeFormat.LongDate )** |Formatiert als lange Datumszeichenfolge in der Sprache und dem Gebietsschema des aktuellen Benutzers. |"Montag, 23 November 2015" |
| **Text( Now(); DateTimeFormat.LongDateTime )** |Formatiert als lange Datums- und Uhrzeitzeichenfolge in der Sprache und dem Gebietsschema des aktuellen Benutzers und legt eine 12-Stunden-Uhr zugrunde. |"Montag, 23. November 2015 2:37:47 PM" |
| **Text( Now(); DateTimeFormat.LongTime24 )** |Formatiert als lange Uhrzeitzeichenfolge und legt eine 24-Stunden-Uhr zugrunde. |"14:37:47" |
| **Text( Now(); DateTimeFormat.ShortDate )** |Formatiert als kurze Datumszeichenfolge in der Sprache und dem Gebietsschema des aktuellen Benutzers. |"23.11.2015" |
| **Text( Now(); "d-mmm-yy" )** |Formate mit Platzhalterzeichen: <ul><li>**d** für eine einstellige oder zweistellige Angabe des Tags im Monat<li>**-** als literales Zeichen, das in das Ergebnis kopiert wird<li>**mmm** für eine aus drei Buchstaben bestehende Abkürzung des Monats<li>**-** als weiteres literales Zeichen, das in das Ergebnis kopiert wird<li>**yy** für eine zweistellige Kurzform für das Jahr</ul> |"23. Nov. 15" |

### <a name="global-apps"></a>Globale Anwendungen

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text( 1234567,89; "[$-en-US]$ #.###" )** |Interpretiert **.** als Gruppierungszeichen, das nach jedem dritten Zeichen eingefügt wird, und **$** als Währungssymbol. Da keine Dezimalstellen angezeigt werden sollen, wird der Wert auf die nächsthöhere ganze Zahl aufgerundet. Die Angabe **[$-en-US]** ist in diesem Fall optional, da sie den Standardwert darstellt. |"$ 1.234.568" |
| **Text( 1234567.89, "[$-es-ES]&euro; #,###" )** |Interpretiert **,** als Dezimaltrennzeichen und **&euro;** als Währungssymbol.  Da die Angabe **[$-fr-FR]** nur bestimmt, wie die Formatierungszeichenfolge interpretiert werden soll, verwendet das Ergebnis die Zeichen aus dem standardmäßigen Sprachkennzeichen "en-US" – **.** (Punkt) – als Dezimaltrennzeichen und **$** als Währungssymbol. |"$ 1234567.89" |
| **Text( 1234567.89, "[$-es-ES]&euro; #,###", "es-ES" )** |Interpretiert **,** als Dezimaltrennzeichen.  Das Sprachkennzeichen für das Ergebnis wurde auf „fr-FR“ festgelegt, was bewirkt, dass **,** (Komma) als Dezimaltrennzeichen und **&euro;** als Währungssymbol verwendet wird. |"&euro; 1234567,89" |
| **Text( Date(2016,1,31), "dddd mmmm d" )** |Gibt den Wochentag, Monat und Tag des Monats in der Sprache des aktuellen Benutzers zurück. Da keiner der Platzhalter sprachabhängig ist, gibt es keine Notwendigkeit für ein Textformat-Sprachkennzeichen. |"Saturday January 31" |
| **Text( Date(2016,1,31), "dddd mmmm d", "es-ES" )** |Gibt den Wochentag, Monat und Tag des Monats in der Sprache „es-ES“ zurück. |"Domingo Enero 31" |

