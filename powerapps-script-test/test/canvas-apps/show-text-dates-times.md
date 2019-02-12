---
title: Anzeigen von Text, Datumswerten und Uhrzeiten in einer Canvas-App | Microsoft-Dokumentation
description: Anzeigen von Text sowie von Datumswerten und Uhrzeiten in einer Canvas-App in PowerApps
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/16/2016
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 54712803d0cc119aa385162088df468e339a7298
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42848524"
---
# <a name="show-text-dates-and-times-in-powerapps"></a>Anzeigen von Text, Datumswerten und Uhrzeiten in PowerApps
Fügen Sie in einer Canvas-App in PowerApps Datumsangaben und Uhrzeiten hinzu, und formatieren Sie sie, um die geeignete Detailebene anzuzeigen oder Ihr Gebietsschema widerzuspiegeln. Berechnen Sie die Zeitspanne zwischen zwei Datumswerten, oder berechnen Sie ein Datum, das eine bestimmte Zeitspanne vor oder nach einem von Ihnen angegebenen Datum liegt. Konvertieren Sie Datumswerte in getrennte Werte für Tage, Monate und Jahre, und konvertieren Sie Werte für Stunden, Minuten und Sekunden.

Fügen Sie beispielsweise Benutzerdaten zu Änderungen am Warenbestand oder zu Kundenbesprechungen, Daten aus einer externen Quelle oder Daten aus einer anderen, in PowerApps erstellten App hinzu. Wenn diese Daten bis auf die Millisekunde genaue Uhrzeitwerte umfassen, runden Sie diese zur Vereinfachung auf die nächste Minute. Berechnen Sie, wie viele Tagen bis zu einem wichtigen Meilenstein verbleiben. Wenn Sie alle fünf Tage eine Kundenbesprechung planen möchten, können Sie diese Datumswerte automatisch berechnen. Wenn der 10. Mai 1985 in getrennten Feldern für Tag, Monat und Jahr gespeichert ist, können Sie das Datum in einem einzelnen Wert konsolidieren. Umgekehrt können Sie Datumswerte in getrennte Werte aufteilen, wenn Ihre App diese separat verwaltet.

## <a name="prerequisites"></a>Voraussetzungen

* [Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.
* Erstellen Sie eine App, oder öffnen Sie eine vorhandene App in PowerApps.
* Erfahren Sie, wie Sie [ein Steuerelement](add-configure-controls.md) in PowerApps konfigurieren.

## <a name="show-text-in-a-label-control"></a>Anzeigen von Text in einem Bezeichnung-Steuerelement
Zeigen Sie Text in einem **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) an, indem Sie den Wert seiner Eigenschaft **[Text](controls/properties-core.md)** festlegen. Legen Sie diese Eigenschaft fest, indem Sie eine direkte Eingabe im Steuerelement durchführen oder einen Ausdruck in der Bearbeitungsleiste eingeben.

* Wenn Sie eine direkte Eingabe im Steuerelement durchführen, wird genau der Text angezeigt, den Sie eingeben.
* Wenn Sie in der Bearbeitungsleiste einen Ausdruck eingeben, zeigt das Steuerelement das Ergebnis des Ausdrucks an.

Hier sehen Sie einige Beispiele.

1. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) mit dem Namen **ShowText** hinzu, und legen Sie dessen Eigenschaft **[Text](controls/properties-core.md)** auf diese Formel fest:
   <br>**Now()**
   
    Wenn Ihr Computer auf das Gebietsschema „en-us“ eingestellt ist, werden Datum und Uhrzeit in diesem Format angezeigt:  <br>*MM/TT/JJJJ hh:mm AM/PM*
   
    Wenn Ihr Computer auf das Gebietsschema „fr-fr“ eingestellt ist, werden Datum und Uhrzeit in diesem Format angezeigt:  <br>*TT/MM/JJJJ hh:mm AM/PM*
2. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **ShowText** auf diese Formel fest:
   <br>**DateDiff(Today(), DateValue("01/01/2020"))**
   
    ![Anzahl von Tagen zwischen heute und dem 1. Januar 2020](./media/show-text-dates-times/date-diff-text.png)
   
    Das Steuerelement zeigt die Anzahl von Tagen zwischen dem heutigen Tag und dem 1. Januar 2020. Hierbei werden diese Funktionen verwendet:
   
   * **DateDiff** berechnet die Anzahl von Tagen, Quartalen oder Jahren zwischen zwei Datumswerten.
   * **Today** berechnet den aktuellen Tag als Wert.
   * **DateValue** konvertiert eine Literalzeichenfolge (der zwischen den doppelten Anführungszeichen angezeigte Wert) in einen Wert, für den Berechnungen durchgeführt werden können.
3. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement mit dem Namen **BirthDate** hinzu, und verschieben Sie es unter **ShowText**.

4. Geben Sie in **BirthDate** den Monat und den Tag Ihrer Geburt ein (z.B. **05/18**).

5. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **ShowText** auf diese Formel fest:
   <br>**DateDiff(Today(), DateValue(BirthDate.Text))**
   
    ![Anzahl von Tagen zwischen heute und Ihrem Geburtstag](./media/show-text-dates-times/birth-diff.png)
   
    **ShowText** zeigt die Anzahl von Tagen zwischen dem heutigen Tag und dem in **BirthDate** eingegebenen Datum an. Wenn Ihr diesjähriger Geburtstag bereits in der Vergangenheit liegt, zeigt **ShowText** einen negativen Wert an.

## <a name="format-dates-and-times-by-using-datetimevalue"></a>Formatieren von Datumsangaben und Uhrzeiten mithilfe von „DateTimeValue“
Konvertieren Sie Datums- und Uhrzeitwerte aus Textzeichenfolgen in Werte, die Sie in vielfältiger Weise formatieren und in Berechnungen verwenden können. Geben Sie das Format mithilfe integrierter und benutzerdefinierter Optionen an.

> [!NOTE]
> Die Funktionen **[DateTimeValue](functions/function-datevalue-timevalue.md)** und **[DateValue](functions/function-datevalue-timevalue.md)** können Datumsangaben in einem beliebigen dieser Formate in Werte konvertieren:  
> 
> * MM/TT/JJJJ  
> * TT/MM/JJJJ  
> * TT Mon JJJJ  
> * Monat TT, JJJJ  
> 
> 

1. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement mit dem Namen **ArrivalDateTime** hinzu, und geben Sie ein Datum und eine Uhrzeit in diesem Format ein:
   <br>**5/10/85 6:15 AM**
2. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) mit dem Namen **ShowDate** hinzu, und legen Sie dessen Eigenschaft **[Text](controls/properties-core.md)** auf diese Formel fest:
   <br>**DateTimeValue(ArrivalDateTime.Text)**
   
    ![Konvertieren einer Datums-/Uhrzeitangabe von einer Textzeichenfolge in einen Wert](./media/show-text-dates-times/date-value.png)
   
    **ShowDate** zeigt dieselben Informationen an wie die von Ihnen eingegebenen, aber die Eingabe wird von Text in einen Wert konvertiert und anders formatiert. Beispielsweise wird das Jahr nicht mit zwei, sondern mit vier Ziffern angezeigt.
3. Ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **ShowDate** in diese Formel:
   <br>**DateTimeValue(ArrivalDateTime.Text, "fr")**
   
    ![Anzeigen einer Datums-/Uhrzeitangabe im französischen Format](./media/show-text-dates-times/date-value-fr.png)
   
    **ShowDate** zeigt den Tag vor dem Monat, so wie ein französischer Benutzer es erwarten würde.
   
   > [!TIP]
   > Um eine Liste weiterer Gebietsschemas in Intellisense anzuzeigen, entfernen Sie das schließende Anführungszeichen und **fr** aus der Formel, aber behalten das öffnende Anführungszeichen bei:
   > 
   > ![Anzeigen einer Liste der Gebietsschemas](./media/show-text-dates-times/locale-list.png)
   > 
   > 
4. Um eines der verschiedenen integrierten Formate zu verwenden, ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **ShowDate** in diese Formel:
   <br>**Text(DateTimeValue(ArrivalDateTime.Text), DateTimeFormat.LongDateTime)**
   
    ![Anzeigen einer Datums-/Uhrzeitangabe im französischen Format](./media/show-text-dates-times/long-date-time.png)
   
    **ShowDate** zeigt den Tag der Woche, das Datum und die Uhrzeit.
   
   > [!TIP]
   > Der Parameter **DateTimeFormat** unterstützt verschiedene weitere integrierte Formate. Um diese Liste anzuzeigen, entfernen Sie **LongDateTime** aus der Formel.
   > 
   > 
5. Um ein benutzerdefiniertes Format zu verwenden, ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **ShowDate** in diese Formel:
   <br>**Text(DateTimeValue(ArrivalDateTime.Text), "mm/dd/yyyy hh:mm:ss.fff AM/PM")**
   
    ![Anzeigen einer Datums-/Uhrzeitangabe im französischen Format](./media/show-text-dates-times/format-milliseconds.png)
   
    **ShowDate** zeigt den Datums-/Uhrzeitwert in dem von Ihnen angegebenen Format, einschließlich von Millisekunden.
   
   > [!TIP]
   > Um die Uhrzeit auf das nächste Zehntel oder Hundertstel einer Sekunde zu runden, geben Sie in der Formel **hh:mm:ss.f** oder **hh:mm:ss.ff** an.
   > 
   > 

## <a name="format-a-date-by-using-datevalue"></a>Formatieren eines Datums mithilfe von „DateValue“

1. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement namens **ArrivalDate** hinzu, und geben Sie dann ein Datum ein (z.B. **5/10/85**).

2. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) mit dem Namen **FormatDate** hinzu, und legen Sie dessen Eigenschaft **[Text](controls/properties-core.md)** auf diese Formel fest:
   <br>**DateValue(ArrivalDate.Text)**
   
    **FormatDate** zeigt das eingegebene Datum an, das Jahr wird jedoch mit vier Ziffern angezeigt.
3. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **FormatDate** auf diese Formel fest:
   <br>**DateValue(ArrivalDate.Text, "fr")**
   
    **FormatDate** zeigt den Tag vor dem Monat, so wie ein französischer Benutzer es erwarten würde.
4. Um eines der verschiedenen integrierten Formate zu verwenden, ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **FormatDate** in diese Formel:
   <br>**Text(DateValue(ArrivalDate.Text), DateTimeFormat.LongDate)**
   
    **FormatDate** zeigt den Tag der Woche, den Monat, den Tag und das Jahr an.
5. Um ein benutzerdefiniertes Format zu verwenden, ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **FormatDate** in diese Formel:
   <br>**Text(DateValue(ArrivalDate.Text), "yy/mm/dd")**
   
    **FormatDate** zeigt das Datum in dem von Ihnen angegebenen Format an.

## <a name="format-a-time-using-datetimevalue"></a>Formatieren einer Uhrzeit mithilfe von „DateTimeValue“

1. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement namens **ArrivalTime** hinzu, und geben Sie **6:15 AM** in das Feld ein.

2. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) namens **ShowTime** hinzu.

3. Um eines der verschiedenen integrierten Formate zu verwenden, ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **ShowTime** in diese Formel:
   <br>**Text(DateTimeValue(ArrivalTime.Text), DateTimeFormat.LongTime)**
   
    **ShowTime** zeigt die von Ihnen angegebene Uhrzeit einschließlich der Sekunden an.
4. Um ein benutzerdefiniertes Format zu verwenden, ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **ShowTime** in diese Formel:
   <br>**Text(DateTimeValue(ArrivalTime.Text), "hh:mm:ss.fff AM/PM")**
   
    **ShowTime** zeigt die von Ihnen angegebene Uhrzeit einschließlich der Sekunden und Millisekunden an.
   
   > [!TIP]
   > Um die Uhrzeit auf das nächste Zehntel oder Hundertstel einer Sekunde zu runden, geben Sie in der Formel **hh:mm:ss.f** oder **hh:mm:ss.ff** an.
   > 
   > 

## <a name="show-the-time-between-dates"></a>Anzeigen der Zeitspanne zwischen Datumsangaben

1. Fügen Sie zwei **[Texteingabe](controls/control-text-input.md)**-Steuerelemente namens **Start** und **End** hinzu.

2. Geben Sie in **Start** den Wert **4/1/2015** und in **End** den Wert **1/1/2016** ein.

3. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) mit dem Namen **DateDiff** hinzu, und legen Sie dessen Eigenschaft **[Text](controls/properties-core.md)** auf diese Formel fest:
   <br>**DateDiff(DateValue(Start.Text), DateValue(End.Text))**
   
    ![Vergleichen zweier Datumsangaben](./media/show-text-dates-times/date-diff.png)
   
    **DateDiff** zeigt **275** an. Dies ist die Anzahl von Tagen zwischen dem 1. April 2015 und dem 1. Januar 2016.
4. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **DateDiff** auf diese Formel fest:  <br>**DateDiff(DateValue(Start.Text), DateValue(End.Text), Months)**
   
    **DateDiff** zeigt **9** an. Dies ist die Anzahl von Monaten zwischen dem 1. April 2015 und dem 1. Januar 2016. Ersetzen Sie **Months** durch **Quarters** oder **Years**, um die Zeit in Monaten, Quartalen oder Jahren anzuzeigen.

## <a name="identify-a-date-before-or-after-another-date"></a>Identifizieren eines Datums vor oder nach einem anderen Datum

1. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement namens **Start** hinzu, und geben Sie den Wert **5/10/1985** darin ein.

2. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) mit dem Namen **DateAdd** hinzu, und legen Sie dessen Eigenschaft **[Text](controls/properties-core.md)** auf diese Formel fest:
   <br>**DateAdd(DateValue(Start.Text), 3)**
   
    ![Hinzufügen von drei Tagen](./media/show-text-dates-times/date-add.png)
   
    **DateAdd** zeigt **5/13/1985**. Dieses Datum liegt drei Tage nach dem Datum in **Start**.
3. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **DateAdd** auf diese Formel fest:
   <br>**DateAdd(DateValue(Start.Text), -3)**
   
    ![Subtrahieren von drei Tagen](./media/show-text-dates-times/date-subtract.png)
   
    **DateAdd** zeigt **5/7/1985**. Dieses Datum liegt drei Tage vor dem Datum in **Start**.
4. Ändern Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **DateAdd** in diese Formel:
   <br>**DateAdd(DateValue(Start.Text), 3, Months)**
   
    ![Hinzufügen von drei Monaten](./media/show-text-dates-times/date-add-months.png)
   
    Die Bezeichnung zeigt **8/10/1985**. Dieses Datum liegt drei Monate nach dem Datum in **Start**. Ersetzen Sie **Months** durch **Quarters** oder **Years**, um ein Datum zu identifizieren, das die angegebene Anzahl von Quartalen oder Jahren vor oder nach dem Datum in **Start** liegt.

## <a name="calculate-dates-based-on-years-months-and-days"></a>Berechnen von Datumsangaben basierend auf Jahren, Monaten und Tagen

1. Fügen Sie drei **[Dropdown](controls/control-drop-down.md)**-Steuerelemente namens **Year**, **Month** und **Day** hinzu.

2. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft von **Year** auf diese Formel fest:
   <br>**Table({Year:"2014"}, {Year:"2015"}, {Year:"2016"})**

3. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft von **Month** auf diese Formel fest:
   <br>**Table({Month:"1"}, {Month:"2"}, {Month:"3"}, {Month:"4"}, {Month:"5"}, {Month:"6"}, {Month:"7"}, {Month:"8"}, {Month:"9"}, {Month:"10"}, {Month:"11"}, {Month:"12"})**

4. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft von **Day** auf diese Formel fest:
   <br>**Table({Day:"1"}, {Day:"2"}, {Day:"3"}, {Day:"4"}, {Day:"5"}, {Day:"6"}, {Day:"7"}, {Day:"8"}, {Day:"9"}, {Day:"10"}, {Day:"11"}, {Day:"12"}, {Day:"13"}, {Day:"14"}, {Day:"15"}, {Day:"16"}, {Day:"17"}, {Day:"18"}, {Day:"19"}, {Day:"20"}, {Day:"21"}, {Day:"22"}, {Day:"23"}, {Day:"24"}, {Day:"25"}, {Day:"26"}, {Day:"27"}, {Day:"28"}, {Day:"29"}, {Day:"30"}, {Day:"31"})**

5. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**Text(Date(Value(Year.Selected.Value), Value(Month.Selected.Value), Value(Day.Selected.Value)), DateTimeFormat.LongDate)**
   
    Standardmäßig wird **Wednesday, January 1, 2014** aufgeführt. Wählen Sie in den **[Dropdown](controls/control-drop-down.md)**-Steuerelementen verschiedene Werte aus, um das Datum im **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) zu ändern.

Möglicherweise müssen Sie Daten konvertieren, die Sie nicht erwartet haben. Wenn Sie anstelle von **[Dropdown](controls/control-drop-down.md)**-Steuerelementen **[Texteingabe](controls/control-text-input.md)**-Steuerelemente hinzufügen, gibt der Benutzer möglicherweise ein falsches Datum ein, wie z.B. Mai 45. Die **[Date](functions/function-date-time.md)**-Funktion verarbeitet atypische Datumsangaben folgendermaßen:

* Wenn ein Jahreswert zwischen 0 und 1899 (einschließlich) liegt, fügt die Funktion diesen Wert zu 1900 hinzu, um das Jahr zu berechnen.
* Wenn ein Jahreswert zwischen 1900 und 9999 (einschließlich) liegt, verwendet die Funktion diesen Wert als Jahr.
* Wenn ein Jahr kleiner ist als 0 oder größer oder gleich 10000, gibt die Funktion einen Fehlerwert aus.
* Wenn ein Monatswert größer ist als 12, fügt die Funktion diese Anzahl von Monaten zum ersten Monat des angegebenen Jahres hinzu.
* Wenn ein Monatswert größer ist als 1, subtrahiert die Funktion diese Anzahl von Monaten plus 1 vom ersten Monat des angegebenen Jahres.
* Wenn ein Tageswert größer ist als die Anzahl von Tagen im angegebenen Monat, fügt die Funktion diese Anzahl von Tagen zum ersten Tag des Monats hinzu und gibt das entsprechende Datum von einem folgenden Monat zurück.
* Wenn ein Tageswert kleiner ist als 1, subtrahiert die Funktion diese Anzahl von Tagen plus 1 vom ersten Tag des angegebenen Monats.

## <a name="calculate-times-based-on-hours-minutes-and-seconds"></a>Berechnen von Uhrzeitangaben basierend auf Stunden, Minuten und Sekunden

1. Fügen Sie zwei **Dropdown**-Listen namens **Hour** und **Minute** hinzu.

2. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft von **Hour** auf diese Formel fest:
   <br>**Table({Hour:"9"}, {Hour:"10"}, {Hour:"11"}, {Hour:"12"}, {Hour:"13"}, {Hour:"14"}, {Hour:"15"}, {Hour:"16"}, {Hour:"17"})**

3. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft von **Minute** auf diese Formel fest:
   <br>**Table({Minute:"0"}, {Minute:"15"}, {Minute:"30"}, {Minute:"45"})**

4. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:  
   <br>**Text(Time(Value(Hour.Selected.Value), Value(Minute.Selected.Value), 0), DateTimeFormat.ShortTime)**

5. Wählen Sie für **Hour** den Wert **15** und für **Minute** den Wert **45** aus.
   
    Das **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) zeigt **15:45 h** an.
   
    Sie können Einträge zu **Hour** und **Minute** hinzufügen, damit Benutzer aus einem größeren Bereich an Stunden und eine genauere Anzahl von Minuten auswählen können. Sie können auch ein drittes **[Dropdown](controls/control-drop-down.md)**-Steuerelement hinzufügen, damit Benutzer die Sekunden angeben können. Wenn Sie eine dritte Liste hinzufügen, legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft des **[Label](controls/control-text-box.md)**-Steuerelements (Bezeichnung) auf den folgenden Ausdruck fest:<br>**Text(Time(Value(Hour.Selected.Value), Value(Minute.Selected.Value), Value(Second.Selected.Value)), DateTimeFormat.LongTime)**

