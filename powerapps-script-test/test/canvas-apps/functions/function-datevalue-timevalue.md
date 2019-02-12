---
title: Funktionen „DateValue“, „TimeValue“ und „DateTimeValue“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „DateValue“, „TimeValue“ und „DateTimeValue“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c1f11be30f56859ede0950feebc27dd1be39d011
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834725"
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-powerapps"></a>Die Funktionen „DateValue“, „TimeValue“ und „DateTimeValue“ in PowerApps
Konvertiert ein Datum und/oder eine Uhrzeit in einer Zeichenfolge in einen Datum/Uhrzeit-Wert

## <a name="description"></a>Beschreibung
Die **DateValue**-Funktion konvertiert eine Datumzeichenfolge (z.B. „10/01/2014“) in einen Datum/Uhrzeit-Wert.

Die **TimeValue**-Funktion konvertiert eine Uhrzeitzeichenfolge (z.B. „12:15 PM“) in einen Datum/Uhrzeit-Wert.

Die **DateTimeValue**-Funktion konvertiert eine Datums- und Uhrzeitzeichenfolge (z.B. „January 10, 2013 12:13 AM“) in einen Datum/Uhrzeit-Wert.

Die **DateValue**-Funktion ignoriert Zeitinformationen in der Datumzeichenfolge, und die **TimeValue**-Funktion ignoriert Datuminformationen in der Uhrzeitzeichenfolge.

Standardmäßig wird die Sprache des aktuellen Benutzers verwendet; Sie können dies außer Kraft setzen, um sicherzustellen, dass Zeichenfolgen ordnungsgemäß interpretiert werden. Beispielsweise wird „10/1/1920“ als der 1. Oktober in „en“ und als 10. Januar in „fr“ interpretiert.

Datumsangaben müssen eines der folgenden Formate aufweisen:

* MM/TT/JJJJ
* TT/MM/JJJJ
* TT Mon JJJJ
* Monat DD, YYYY

Weitere Informationen zum Konvertieren der numerischen Komponenten Datum, Monat und Jahr, und Stunde, Minute und Sekunde finden Sie unter den **[Date](function-date-time.md)**- und **[Time](function-date-time.md)**-Funktionen.

Weitere Informationen finden Sie unter [Working with dates and times (Arbeiten mit Datums- und Uhrzeitangaben)](../show-text-dates-times.md).

Informationen zum Konvertieren von Zahlen finden Sie unter der **[Value](function-value.md)**-Funktion.

## <a name="syntax"></a>Syntax
**DateValue**( *String* [, *Language* ])<br>**DateTimeValue**( *String* [, *Language* ])<br>**TimeValue**( *String* [, *Language* ])

* *Zeichenfolge*: erforderlich.  Eine Textzeichenfolge, die einen Datum-, Uhrzeit- oder einen Datum/Uhrzeit-Wert enthält.
* *Sprache*: optional.  Eine Sprachzeichenfolge, wie man sie durch die ersten beiden Zeichen des Rückgabewertes der **[Language](function-language.md)**-Funktion erhält.  Wenn nicht anders angegebenen, wird die Sprache des Clients des aktuellen Benutzers verwendet.  

## <a name="examples"></a>Beispiele
### <a name="datevalue"></a>DateValue
Wenn Sie **10/11/2014** in ein Texteingabe-Steuerelement mit dem Namen **StartDate** eingegeben haben, und Sie dann die **[Text](../controls/properties-core.md)**-Eigenschaft einer Bezeichnung für diese Funktion festgelegt haben, gibt es mehrere Möglichkeiten:

* **Text(DateValue(Startdate.Text), DateTimeFormat.LongDate)**
  
    Die Bezeichnung zeigt **Saturday, October 11, 2014** an, wenn das Gebietsschema Ihres Computers auf **en** festgelegt wurde.
  
    > [!NOTE]
  > Sie können mehrere Optionen mit dem **DateTimeFormat**-Parameter verwenden, allerdings nicht **LongDateTime**. Geben Sie den Parameter, unmittelbar gefolgt von einem Ausrufezeichen, in das Funktionsfeld ein, um eine Liste dieser Optionen anzuzeigen.
* **Text(DateValue(Startdate.Text, "fr"), DateTimeFormat.LongDate)**
  
    Die Bezeichnung zeigt **Monday, November 10, 2014** an.

Wenn Sie dasselbe für **October 20, 2014** durchgeführt haben:

* **DateDiff(DateValue(Startdate.Text), Today())**
  
    Wenn die Sprache Ihres Computers auf **en** festgelegt wurde, zeigt die Bezeichnung **9** an, was die Anzahl der Tage zwischen dem 11. und 20. Oktober ist. Die **[DateDiff](function-dateadd-datediff.md)**-Funktion kann auch die Differenz in Monaten, Quartalen oder Jahren angezeigt.

### <a name="datetimevalue"></a>DateTimeValue
Wenn Sie **10/11/2014 1:50:24.765 PM** in ein Texteingabe-Steuerelement mit dem Namen **Start** eingegeben haben, und Sie anschließend die **[Text](../controls/properties-core.md)**-Eigenschaft einer Bezeichnung auf folgende Funktion festgelegt haben, gibt es mehrere Möglichkeiten:

* **Text(DateTimeValue(Start.Text), DateTimeFormat.LongDateTime)**
  
    Die Bezeichnung zeigt **Saturday, October 11, 2014 1:50:24 PM**, wenn das Gebietsschema Ihres Computers auf „en“ konfiguriert wurde.
  
    > [!NOTE]
  > Sie können mehrere Optionen mit dem **DateTimeFormat**-Parameter verwenden, allerdings nicht **LongDateTime**. Geben Sie den Parameter, unmittelbar gefolgt von einem Ausrufezeichen, in das Funktionsfeld ein, um eine Liste dieser Optionen anzuzeigen.
* **Text(DateTimeValue(Start.Text, "fr"), DateTimeFormat.LongDateTime)**
  
    Die Bezeichnung zeigt **Monday, November 10, 2014 1:50:24 PM** an.
* **Text(DateTimeValue(Start.Text), "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM")**
  
    Die Bezeichnung zeigt **Saturday, October 11, 2014 01:50:24:765 PM**, wenn das Gebietsschema Ihres Computers auf **en** festgelegt ist.
  
    Als Alternative können Sie **hh:mm:ss.f** oder **hh:mm:ss.ff** angeben, um die Zeit auf das nächste Zehntel oder Hundertstel einer Sekunde zu runden.

### <a name="timevalue"></a>TimeValue
Benennen Sie ein Texteingabe-Steuerelement **FinishedAt**, und legen Sie die **[Text](../controls/properties-core.md)**-Eigenschaft einer Bezeichnung auf folgende Funktion fest:

**If(TimeValue(FinishedAt.Text)<TimeValue("5:00:00.000 PM"), "You made it!", "Too late!")**

* Wenn Sie **4:59:59.999 PM** in das **FinishedAt**-Steuerelement eingegeben haben, zeigt die Bezeichnung „You made it!“ (Geschafft!) an
* Wenn Sie **5:00:00.000 PM** in das **FinishedAt**-Steuerelement eingeben, zeigt die Bezeichnung „Too late!“ (Zu spät!) an

