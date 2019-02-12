---
title: Funktionen, Signale und Enumerationen | Microsoft-Dokumentation
description: Referenzinformationen zu Funktionen, Signalen und Enumerationen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/05/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 752bb630c1ecd1e86f37a1a063bcc5ee192431f0
ms.sourcegitcommit: 3aeb9381fbeb66cf08355d9a3d0f00ce2737e256
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43163635"
---
# <a name="formula-reference-for-powerapps"></a>Referenz zu Formeln für PowerApps
Formeln kombinieren viele Elemente miteinander.  Im Folgenden sind aufgeführt:

* **Funktionen** verwenden Parameter, führen einen Vorgang aus und geben einen Wert zurück. So gibt beispielsweise **Sqrt(25)** den Wert **5** zurück. Funktionen sind Microsoft Excel-Funktionen nachgebildet.  Einige Funktionen haben nachteilige Auswirkungen, wie z.B. **SubmitForm**, die sich nur für [Verhaltensformeln](working-with-formulas-in-depth.md) wie **Button.OnSelect** eignet.
* **Signale** geben Informationen über die Umgebung zurück. Die Funktion  **[Location](functions/signals.md)** gibt beispielsweise die aktuellen GPS-Koordinaten des Geräts zurück. Signale verwenden keine Parameter und haben keine nachteiligen Auswirkungen.
* **Enumerationen** geben einen vordefinierten Konstantenwert zurück. **[Color](functions/function-colors.md)** ist eine Enumeration, die über vordefinierte Werte für **Color.Red**, **Color.Blue**usw. verfügt.  An dieser Stelle werden nur allgemeine Enumerationen beschrieben. Funktionsspezifische Enumerationen werden mit der jeweiligen Funktion erläutert.
* **Benannte Operatoren**, wie z.B. **[ThisItem](functions/operators.md#thisitem-operator)** und **[Parent](functions/operators.md#parent-operator)**, ermöglichen den Zugriff auf Informationen innerhalb eines Containers.

Andere Elemente enthalten:

* [Alle Operatoren](functions/operators.md)
* [Steuerelemente und deren Eigenschaften](reference-properties.md)

## <a name="a"></a>A
**[Abs](functions/function-numericals.md)** : absoluter Wert einer Zahl  

**[Acceleration](functions/signals.md)**: liest den Beschleunigungssensor in Ihrem Gerät.

**[Acos](functions/function-trig.md)** : gibt den Arkuskosinus einer Zahl im Bogenmaß zurück.

**[Acot](functions/function-trig.md)**: gibt den Arkuskotangens einer Zahl im Bogenmaß zurück.

**[AddColumns](functions/function-table-shaping.md)**: gibt eine Tabelle mit hinzugefügten [Spalten](working-with-tables.md#columns) zurück.

**[And](functions/function-logicals.md)**: boolesche Logikfunktion AND.  Gibt **TRUE** zurück, wenn für alle Argumente **TRUE** gilt.  Sie können auch den [**&&**-Operator](functions/operators.md) verwenden.

**[App](functions/signals.md)**: gibt Informationen zur derzeit ausgeführten App zurück, z.B. welcher Bildschirm gerade angezeigt wird.

**[Asin](functions/function-trig.md)**: gibt den Arkussinus einer Zahl im Bogenmaß zurück.

**[Atan](functions/function-trig.md)**: gibt den Arkustangens einer Zahl im Bogenmaß zurück.

**[Atan2](functions/function-trig.md)**: gibt den Arkustangens basierend auf einer (*x*,*y*)-Koordinate im Bogenmaß zurück.

**[Average](functions/function-aggregates.md)**: berechnet den Durchschnitt eines Tabellenausdrucks oder eines Satzes von Argumenten.

## <a name="b"></a>B
**[Back](functions/function-navigate.md)**: zeigt den vorherigen Bildschirm an.  

**[Blank](functions/function-isblank-isempty.md)**: Gibt einen *leeren* Wert zurück, der zum Einfügen eines NULL-Werts in eine Datenquelle verwendet werden kann.

## <a name="c"></a>C
**[Calendar](functions/function-clock-calendar.md)**: ruft Informationen zum Kalender für das aktuelle Gebietsschema ab.

**[Char](functions/function-char.md)**: übersetzt einen Zeichencode in eine Zeichenfolge.

**[Choices](functions/function-choices.md)**: Gibt eine Tabelle mit den möglichen Werten für eine Nachschlagespalte zurück

**[Clear](functions/function-clear-collect-clearcollect.md)**: löscht alle Daten aus einer [Sammlung](working-with-data-sources.md#collections).

**[ClearCollect](functions/function-clear-collect-clearcollect.md)**: löscht alle Daten aus einer Sammlung und fügt anschließend einen Satz von [Datensätzen](working-with-tables.md#records) hinzu.

**[Clock](functions/function-clock-calendar.md)**: ruft Informationen über die Uhr für das aktuelle Gebietsschema ab.

**[Coalesce](functions/function-isblank-isempty.md)**: ersetzt *leere* Werte, während nicht *leere* Wert nicht geändert werden.

**[Collect](functions/function-clear-collect-clearcollect.md)**: erstellt eine Sammlung oder fügt Daten zu einer Datenquelle hinzu.

**[Color](functions/function-colors.md)**: legt eine Eigenschaft auf einen integrierten Farbwert fest.

**[ColorFade](functions/function-colors.md)**: blendet einen Farbwert aus.

**[ColorValue](functions/function-colors.md)** : übersetzt den Namen einer CSS-Farbe oder einen Hexadezimalcode in einen Farbwert.  

**[Compass](functions/signals.md)**: gibt Ihre Compass-Überschrift zurück.

**[Concat](functions/function-concatenate.md)**: verkettet Zeichenfolgen in einer Datenquelle.  

**[Concatenate](functions/function-concatenate.md)**: verkettet Zeichenfolgen.

**[Concurrent](functions/function-concurrent.md)**: Wertet mehrere Formeln gleichzeitig miteinander aus 

**[Connection](functions/signals.md)**: gibt Informationen zu Ihrer Netzwerkverbindung zurück.

**[Count](functions/function-table-counts.md)**: zählt die Anzahl der Datensätze, die Zahlen enthalten.

**[Cos](functions/function-trig.md)**: gibt den Kosinus eines im Bogenmaß angegebenen Winkels zurück.

**[Cot](functions/function-trig.md)**: gibt den Kotangens eines im Bogenmaß angegebenen Winkels zurück.

**[CountA](functions/function-table-counts.md)**: zählt Tabellendatensätze, die nicht [leer](functions/function-isblank-isempty.md) sind.

**[CountIf](functions/function-table-counts.md)**: zählt Tabellendatensätze, die eine Bedingung erfüllen.  

**[CountRows](functions/function-table-counts.md)**: zählt Tabellendatensätze.   

## <a name="d"></a>D
**[DataSourceInfo](functions/function-datasourceinfo.md)** : enthält Informationen zu einer Datenquelle.

**[Date](functions/function-date-time.md)**: gibt einen Datums- oder Uhrzeitwert auf der Grundlage von Werten für **Year**, **Month** und **Tag**.  

**[DateAdd](functions/function-dateadd-datediff.md)** : fügt Tage, Monate, Quartale oder Jahre zu einem Datums- oder Uhrzeitwert hinzu.

**[DateDiff](functions/function-dateadd-datediff.md)**: subtrahiert zwei Datumswerte und zeigt das Ergebnis in Tagen, Monaten, Quartalen oder Jahren an.

**[DateTimeValue](functions/function-datevalue-timevalue.md)**: konvertiert eine Datums- und Uhrzeitzeichenfolge in einen Datums- oder Uhrzeitwert.

**[DateValue](functions/function-datevalue-timevalue.md)**: konvertiert eine ausschließlich datumsbezogene Zeichenfolge in einen Datums- oder Uhrzeitwert.

**[Day](functions/function-datetime-parts.md)**: ruft den Tagteil eines Datums- und Uhrzeitwerts ab.  

**[Defaults](functions/function-defaults.md)**: gibt die Standardwerte für eine Datenquelle zurück.

**[Degrees](functions/function-trig.md)**: wandelt das Bogenmaß in Grad um.

**[Disable](functions/function-enable-disable.md)**: deaktiviert ein Signal, z.B. **[Location](functions/signals.md)**  zum Lesen des GPS.

**[Distinct](functions/function-distinct.md)**: fasst die Datensätze einer Tabelle zusammen, wobei Duplikate entfernt werden.  

**[Download](functions/function-param.md)**: lädt eine Datei aus dem Web auf das lokale Gerät herunter.

**[DropColumns](functions/function-table-shaping.md)**: gibt eine Tabelle an, bei der eine oder mehrere Spalten entfernt wurden.

## <a name="e"></a>E
**[EditForm](functions/function-form.md)**: setzt ein Formularsteuerelement zum Bearbeiten eines Elements zurück.

**[Enable](functions/function-enable-disable.md)**: aktiviert ein Signal, z.B.  **[Location](functions/signals.md)**, zum Lesen des GPS.

**[EndsWith](functions/function-startswith.md)**: Überprüft, ob eine Textzeichenfolge mit einer anderen Textzeichenfolge endet.

**[Errors](functions/function-errors.md)**: enthält Fehlerinformationen zu vorherigen Änderungen an einer Datenquelle.

**[EncodeUrl](functions/function-encode-decode.md)**: codiert Sonderzeichen mit URL-Codierung.

**[Exit](functions/function-exit.md)**: beendet die derzeit ausgeführte App.

**[Exp](functions/function-numericals.md)**: gibt *e* zur Potenz erhoben zurück.

## <a name="f"></a>F
**[Filter](functions/function-filter-lookup.md)**: gibt eine gefilterte Tabelle basierend auf mindestens einem Kriterium zurück.

**[Find](functions/function-find.md)**: überprüft, ob eine Zeichenfolge innerhalb einer anderen angezeigt wird, und gibt den Speicherort zurück.

**[First](functions/function-first-last.md)**: gibt den ersten Datensatz einer Tabelle zurück.

**[FirstN](functions/function-first-last.md)**: gibt die erste Gruppe von Datensätzen (N-Datensätze) einer Tabelle zurück.

**[ForAll](functions/function-forall.md)**: berechnet Werte und führt Aktionen für alle Datensätze einer Tabelle durch.

## <a name="g"></a>G
**[GroupBy](functions/function-groupby.md)**: gibt eine Tabelle mit gruppierten Datensätzen zurück.

**[GUID](functions/function-guid.md)**: konvertiert eine GUID-Zeichenfolge in einen GUID-Wert oder erstellt einen neuen GUID-Wert.

## <a name="h"></a>H
**[HashTags](functions/function-hashtags.md)**: extrahiert die Hashtags (#strings) aus einer Zeichenfolge.

**[Hour](functions/function-datetime-parts.md)**: gibt den Stundenteil eines Datums- oder Uhrzeitwerts zurück.

## <a name="i"></a>I
**[If](functions/function-if.md)**: gibt einen bestimmten Wert zurück, wenn für eine Bedingung TRUE gilt, und ansonsten einen anderen Wert. 

**[IfError](functions/function-iferror.md)**: erkennt Fehler und stellt einen Alternativwert bereit oder führt eine Aktion aus. 

**[IsBlank](functions/function-isblank-isempty.md)**: sucht nach einem Wert [blank](functions/function-isblank-isempty.md).

**[IsEmpty](functions/function-isblank-isempty.md)**: sucht nach einer leeren Tabelle.

**[IsMatch](functions/function-ismatch.md)** : überprüft eine Zeichenfolge anhand eines Musters.  Reguläre Ausdrücke können verwendet werden.

**[IsNumeric](functions/function-isnumeric.md)**: sucht nach einem numerischen Wert.

**[IsToday](functions/function-now-today-istoday.md)**: überprüft, ob ein Datums- oder Uhrzeitwert am heutigen Tag gilt.

## <a name="l"></a>L
**[Language](functions/function-language.md)**: gibt den Sprach-Tag des aktuellen Benutzers zurück.

**[Last](functions/function-first-last.md)**: gibt den letzten Datensatz einer Tabelle zurück.

**[LastN](functions/function-first-last.md)**: gibt die letzte Gruppe von Datensätzen (N-Datensätze) einer Tabelle zurück.

**[Launch](functions/function-param.md)**: startet eine Webadresse oder eine App.

**[Left](functions/function-left-mid-right.md)**: gibt den äußersten linken Teil einer Zeichenfolge zurück.

**[Len](functions/function-len.md)**: gibt die Länge einer Zeichenfolge zurück.

**[Ln](functions/function-numericals.md)**: gibt den natürlichen Logarithmus zurück.

**[LoadData](functions/function-savedata-loaddata.md)**: lädt eine Sammlung dem privaten Speicher von PowerApps.

**[Location](functions/signals.md)**: gibt Ihren Standort mithilfe des Globalen Positionierungssystems (GPS) und anderer Informationen als Kartenkoordinaten zurück.

**[LookUp](functions/function-filter-lookup.md)**: sucht einen einzelnen Datensatz in einer Tabelle basierend auf mindestens einem Kriterium.

**[Lower](functions/function-lower-upper-proper.md)**: konvertiert Buchstaben in einer Textzeichenfolge in Kleinbuchstaben.

## <a name="m"></a>M
**[Max](functions/function-aggregates.md)**: der Höchstwert eines Tabellenausdrucks oder eines Satzes von Argumenten.

**[Mid](functions/function-left-mid-right.md)**: gibt den mittleren Teil einer Zeichenfolge zurück.

**[Min](functions/function-aggregates.md)**: Mindestwert eines Tabellenausdrucks oder eines Satzes von Argumenten.

**[Minute](functions/function-datetime-parts.md)**: ruft den Minutenteil eines Datums- oder Uhrzeitwerts ab.  

**[Mod](functions/function-mod.md)**: gibt den Rest zurück, der nach der Division einer zu teilenden Zahl durch einen Divisor übrig bleibt.

**[Month](functions/function-datetime-parts.md)**: ruft den Monatsteil eines Datums- oder Uhrzeitwerts ab.

## <a name="n"></a>N
**[Navigate](functions/function-navigate.md)**: ändert die Anzeige des Bildschirms.

**[NewForm](functions/function-form.md)**: setzt ein Formularsteuerelement für die Erstellung eines Elements zurück.

**[Not](functions/function-logicals.md)** : boolesche Logikfunktion NOT.  Gibt **TRUE** zurück, wenn für das Argument **FALSE** gilt, und **FALSE** wenn für das Argument **TRUE** gilt.  Sie können auch den [**!**-Operator](functions/operators.md) verwenden.

**[Notify](functions/function-showerror.md)**: Zeigt dem Benutzer eine Bannermeldung an.

**[Now](functions/function-now-today-istoday.md)**: gibt den aktuellen Datums- oder Uhrzeitwert zurück.

## <a name="o"></a>O
**[Or](functions/function-logicals.md)** : boolesche Logikfunktion ODER.  Gibt **TRUE** zurück, wenn für eines der Argumente **TRUE** gilt.  Sie können auch den [**||**-Operator](functions/operators.md) verwenden.

## <a name="p"></a>P
**[Param](functions/function-param.md)**: ermöglicht den Zugriff auf Parameter, die an die App übergeben werden, wenn der Benutzer sie geöffnet hat.

**[Parent](functions/operators.md#parent-operator)**: ermöglicht den Zugriff auf die Eigenschaften eines Container-Steuerelements.

**[Patch](functions/function-patch.md)**: ändert oder erstellt einen Datensatz in einer Datenquelle oder verbindet Datensätze außerhalb einer Datenquelle.

**[Pi](functions/function-trig.md)**:gibt die Zahl &pi; zurück.

**[PlainText](functions/function-encode-decode.md)**: entfernt HTML- und XML-Tags aus einer Zeichenfolge.

**[Power](functions/function-numericals.md)** : gibt eine zu einer Potenz erhobene Zahl zurück.  Sie können auch den [**^**-Operator](functions/operators.md) verwenden.

**[Proper](functions/function-lower-upper-proper.md)**: konvertiert den ersten Buchstaben jedes Worts in einer Zeichenfolge in Großbuchstaben und alle anderen in Kleinbuchstaben.

## <a name="r"></a>R
**[Radians](functions/function-trig.md)**: konvertiert Grad in Bogenmaß.

**[Rand](functions/function-rand.md)**: gibt eine pseudozufällige Zahl zurück.

**[Refresh](functions/function-refresh.md)**: aktualisiert die Datensätze einer Datenquelle.

**[Remove](functions/function-remove-removeif.md)**: entfernt einen oder mehrere bestimmte Datensätze aus einer Datenquelle.

**[RemoveIf](functions/function-remove-removeif.md)**: entfernt Datensätze aus einer Datenquelle auf der Grundlage einer Bedingung.

**[RenameColumns](functions/function-table-shaping.md)**: benennt Spalten einer Tabelle um.

**[Replace](functions/function-replace-substitute.md)**: ersetzt einen Teil einer Zeichenfolge mit einer anderen Zeichenfolge und beginnt dabei mit der Anfangsposition der Zeichenfolge.

**[Reset](functions/function-reset.md)**: Setzt ein Eingabesteuerelement auf seinen Standardwert zurück, wobei alle Benutzeränderungen verworfen werden.

**[ResetForm](functions/function-form.md)**: setzt ein Formularsteuerelement zum Bearbeiten eines vorhandenen Elements ein.

**[Revert](functions/function-revert.md)**: lädt erneut und löscht Fehler für die Datensätze einer Datenquelle.

**[RGBA](functions/function-colors.md)**: gibt einen Farbwert für einen Satz von roten, grünen, blauen und Alpha-Komponenten zurück.

**[Right](functions/function-left-mid-right.md)** : gibt den äußersten rechten Teil einer Zeichenfolge zurück.

**[Round](functions/function-round.md)**: rundet auf nächste Zahl auf.

**[RoundDown](functions/function-round.md)** : rundet auf die höchste vorherige Zahl ab.

**[RoundUp](functions/function-round.md)**: rundet auf die kleinste nächste Zahl auf.

## <a name="s"></a>S
**[SaveData](functions/function-savedata-loaddata.md)**: speichert eine Sammlung im privaten Speicher von PowerApps ab.

**[Search](functions/function-filter-lookup.md)** : sucht nach Datensätzen in einer Tabelle, die eine Zeichenfolge in einer ihrer Spalten enthält.  

**[Second](functions/function-datetime-parts.md)**: ruft den zweiten Teil eines Datums- oder Uhrzeitwerts ab.

**[Select](functions/function-select.md)**: Simuliert eine Auswahlaktion für ein Steuerelement, sodass die Formel **OnSelect** ausgewertet wird

**[Set](functions/function-set.md)**: legt den Wert einer globalen Variablen fest.

**[ShowColumns](functions/function-table-shaping.md)**: gibt eine Tabelle zurück, die nur ausgewählte Spalten enthält.

**[Shuffle](functions/function-shuffle.md)**: ordnet die Datensätze einer Tabelle nach dem Zufallsprinzip an.

**[Sin](functions/function-trig.md)**: gibt den Sinus eines im Bogenmaß angegebenen Winkels zurück.

**[Sort](functions/function-sort.md)**: gibt eine anhand einer Formel sortierte Tabelle zurück.

**[SortByColumns](functions/function-sort.md)** : gibt eine anhand einer oder mehrerer Spalten sortierte Tabelle zurück.

**[Split](functions/function-split.md)**: Teilt eine Textzeichenfolge in eine Tabelle von Teilzeichenfolgen auf.

**[Sqrt](functions/function-numericals.md)**: gibt die Quadratwurzel einer Zahl zurück.

**[StartsWith](functions/function-startswith.md)**: überprüft, ob eine Textzeichenfolge mit einer anderen Textzeichenfolge beginnt.

**[StdevP](functions/function-aggregates.md)**: gibt die Standardabweichung der Argumente zurück.  

**[Substitute](functions/function-replace-substitute.md)**: ersetzt einen Teil einer Zeichenfolge mit einer anderen Zeichenfolge, wobei nach übereinstimmenden Zeichenfolgen vorgegangen wird.

**[SubmitForm](functions/function-form.md)**: speichert das Element in einem Formularsteuerelement in der Datenquelle.

**[Sum](functions/function-aggregates.md)** : berechnet die Summe eines Tabellenausdrucks oder eines Satzes von Argumenten.  

**[Switch](functions/function-if.md)**: Führt einen Abgleich mit einer Menge von Werten durch und wertet dann eine entsprechende Formel aus.

## <a name="t"></a>T
**[Table](functions/function-table.md)**: erstellt eine temporäre Tabelle.  

**[Tan](functions/function-trig.md)**: gibt den Tangens eines im Bogenmaß angegebenen Winkels zurück.

**[Text](functions/function-text.md)**: formatiert eine Zahl als Zeichenfolge für die Anzeige.

**[ThisItem](functions/operators.md#thisitem-operator)**: gibt in einem Katalog oder einem Formular die Daten für das aktuelle Element aus dem Container zurück.

**[Time](functions/function-date-time.md)**: gibt einen Datums- oder Uhrzeitwert auf der Grundlage von Werten für **Hour**, **Minute** und **Second** zurück.  

**[TimeValue](functions/function-datevalue-timevalue.md)**: konvertiert eine ausschließlich zeitbezogene Zeichenfolge in einen Datums- oder Uhrzeitwert.

**[TimeZoneOffset](functions/function-dateadd-datediff.md)** : Gibt die Differenz zwischen UTC und Ortszeit des Benutzers in Minuten zurück.

**[Today](functions/function-now-today-istoday.md)**: gibt den aktuellen Datums- oder Uhrzeitwert zurück.

**[Trim](functions/function-trim.md)**: entfernt zusätzliche Leerzeichen am Ende oder in der Mitte einer Textzeichenfolge.

**[TrimEnds](functions/function-trim.md)**: entfernt zusätzliche Leerzeichen am Ende einer ausschließlich textbezogenen Zeichenfolge.

## <a name="u"></a>U
**[Ungroup](functions/function-groupby.md)**: entfernt eine Gruppierung.

**[Update](functions/function-update-updateif.md)**: ersetzt einen Datensatz in einer Datenquelle.

**[UpdateContext](functions/function-updatecontext.md)**: Legt den Wert einer oder mehrerer [Kontextvariablen](working-with-variables.md#create-a-context-variable) des aktuellen Bildschirms fest.

**[UpdateIf](functions/function-update-updateif.md)** : ändert eine Gruppe von Datensätzen in einer Datenquelle auf der Grundlage einer Bedingung.

**[Upper](functions/function-lower-upper-proper.md)**: konvertiert Buchstaben in einer Textzeichenfolge in Großbuchstaben.

**[User](functions/function-user.md)**: Gibt Informationen über den aktuellen Benutzer zurück.

## <a name="v"></a>V
**[Validate](functions/function-validate.md)**: überprüft, ob der Wert einer einzelnen Spalte oder eines vollständigen Datensatzes für eine Datenquelle gültig ist.

**[Value](functions/function-value.md)**: konvertiert eine Zeichenfolge in eine Zahl.

**[VarP](functions/function-aggregates.md)**: gibt die Varianz der Argumente zurück.  

**[ViewForm](functions/function-form.md)**: Setzt ein Formularsteuerelement zum Anzeigen eines vorhandenen Elements zurück.

## <a name="w"></a>W
**[Weekday](functions/function-datetime-parts.md)**: ruft den Wochentagteil eines Datums- oder Uhrzeitwerts ab.

## <a name="y"></a>Y
**[Year](functions/function-datetime-parts.md)**: ruft den Jahresteil eines Datums- oder Uhrzeitwerts ab.  

