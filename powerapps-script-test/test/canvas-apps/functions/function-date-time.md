---
title: Funktionen „Date“ und „Time“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktionen „Date“ und „Time“ in PowerApps
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
ms.openlocfilehash: 869c0fcff6e519281e527c832305d74f2e7fd78f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864097"
---
# <a name="date-and-time-functions-in-powerapps"></a>Date- und Time-Funktionen in PowerApps
Konvertiert Datums- und Zeitkomponenten in einen Datums- oder Uhrzeitwert

## <a name="description"></a>Beschreibung
Die **Date**-Funktion konvertiert einzelne Werte für Jahr, Monat und Tag in einen Datums- oder Uhrzeitwert.  Der Uhrzeitanteil ist Mitternacht.

* Wenn der Wert für „Year“ zwischen 0 und 1899 (einschließlich) liegt, fügt die Funktion den Wert zu 1900 hinzu, um das Jahr zu berechnen.  **70** wird auf diese Weise zu **1970**.
* Wenn der Wert für „Month“ kleiner als 1 oder größer als 12 ist, subtrahiert oder addiert das Ergebnis die entsprechende Anzahl von Monaten ab dem Anfang des angegebenen Jahres.
* Wenn der Wert für „Day“ größer als die Anzahl der Tage im angegebenen Monat ist, fügt die Funktion die jeweilige Anzahl von Tagen dem ersten Tag des Monats hinzu und gibt das entsprechende Datum aus einem nachfolgenden Monat zurück.  Wenn der Wert für „Day“ kleiner als 1 ist, subtrahiert die Funktion die entsprechende Anzahl von Tagen plus 1 vom ersten Tag des angegebenen Monats.

Die **Time**-Funktion konvertiert die einzelnen Werte für Stunde, Minute und Sekunde in einen Datums- oder Uhrzeitwert.  Dem Ergebnis ist kein Datum zugeordnet.

Weitere Informationen dazu, wie Sie eine Zeichenkette in einen Wert konvertieren, finden Sie unter den  **[DateValue](function-datevalue-timevalue.md)**,  **[TimeValue](function-datevalue-timevalue.md)** und  **[DateTimeValue](function-datevalue-timevalue.md)**-Funktionen.  

Weitere Informationen finden Sie unter [Working with dates and times (Arbeiten mit Datums- und Uhrzeitangaben)](../show-text-dates-times.md).

## <a name="syntax"></a>Syntax
**Date**( *Year*, *Month*, *Day* )

* *Year*: erforderlich.  Zahlen größer als 1899 werden als absolute Zahlen interpretiert (1980 wird als 1980 interpretiert), Zahlen zwischen 0 und 1899 werden als relativ zu 1900 interpretiert. (So wird beispielsweise 80 als 1980 interpretiert.)
* *Month*: erforderlich.  Eine Zahl zwischen 1 und 12.
* *Day*: erforderlich. Eine Zahl zwischen 1 und 31.

**Time**( *Hour*, *Minute*, *Second* )

* *Hour*: erforderlich.  Eine Zahl zwischen 0 (12:00 Uhr) und 23 (23:00 Uhr).
* *Minute*: erforderlich. Eine Zahl zwischen 0 und 59.
* *Second*: erforderlich. Eine Zahl zwischen 0 und 59.

## <a name="examples"></a>Beispiele
### <a name="date"></a>Date
Wenn ein Benutzer **1979** in ein Texteingabe-Steuerelement mit dem Namen **HireYear** eingibt, die Zahl **3** in ein Texteingabe-Steuerelement mit dem Namen **HireMonth** und die Zahl **17** in ein Texteingabe-Steuerelement mit dem Namen **HireDay**, würde diese Funktion als das Datum **3/17/1979** zurückgeben:

**Date(Value(HireYear.Text), Value(HireMonth.Text), Value(HireDay.Text))**

### <a name="time"></a>Uhrzeit
Wenn ein Benutzer **14** in ein Texteingabe-Steuerelement mit dem Namen **BirthHour**, **50** in ein Texteingabe-Steuerelement mit dem Namen **BirthMinute** und **24** in ein Texteingabe-Steuerelement mit dem Namen **BirthSecond** eingibt, gibt diese Funktion **02:50:24 p** zurück.

**Text(Time(Value(BirthHour.Text), Value(BirthMinute.Text), Value(BirthSecond.Text)), "hh:mm:ss a/p")**

