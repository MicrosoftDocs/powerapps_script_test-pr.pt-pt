---
title: Funktionen „Day“, „Month“, „Year“, „Hour“, „Minute“, „Second“ und „Weekday“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Day“, „Month“, „Year“, „Hour“, „Minute“, „Second“ und „Weekday“ in PowerApps
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
ms.openlocfilehash: ab824432833614ba5b2002375a79e7899a8d7277
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42857901"
---
# <a name="day-month-year-hour-minute-second-and-weekday-functions-in-powerapps"></a>Die Funktionen „Day“, „Month“, „Year“, „Hour“, „Minute“, „Second“ und „Weekday“ in PowerApps
Gibt die einzelnen Bestandteile eines Datum/Uhrzeit-Werts zurück

## <a name="description"></a>Beschreibung
Die **Day**-Funktion gibt die Tageskomponente eines Datum/Uhrzeit-Werts zurück, die zwischen 1 und 31 liegt.

Die **Month**-Funktion gibt die Monatskomponente eines Datum/Uhrzeit-Werts zurück, die zwischen 1 und 12 liegt.

Die **Year**-Funktion gibt die Jahreskomponente eines Datum/Uhrzeit-Werts zurück, beginnend mit 1900.

Die **Hour**-Funktion gibt die Stundenkomponente eines Datum/Uhrzeit-Werts zurück, die zwischen 0 (00:00 Uhr) und 23 (23:00 Uhr) liegt.

Die **Minute**-Funktion gibt die Minutenkomponente eines Datum/Uhrzeit-Werts zurück, die zwischen 0 und 59 liegt.

Die **Second**-Funktion gibt die Sekundenkomponente eines Datum/Uhrzeit-Werts zurück, die zwischen 0 und 59 liegt.

Die **Weekday**-Funktion gibt den Wochentag eines Datum/Uhrzeit-Werts zurück.  Standardmäßig reicht das Ergebnis von 1 (Sonntag) bis 7 (Samstag).  Sie können mit einem Weekday-Funktionscode von Microsoft Excel oder mit einem StartOfWeek-Enumerationswert einen anderen Bereich angeben:

| Excel-Code | StartOfWeek-Enumeration | Beschreibung |
| --- | --- | --- |
| **1**, **17** |**StartOfWeek.Sunday** |Zahlen von 1 (Sonntag) bis 7 (Samstag).  Standard. |
| **2**, **11** |**StartOfWeek.Monday** |Zahlen von 1 (Montag) bis 7 (Sonntag) |
| **3** |**StartOfWeek.MondayZero** |Zahlen 0 (Montag) bis 6 (Sonntag) |
| **12** |**StartOfWeek.Tuesday** |Zahlen von 1 (Dienstag) bis 7 (Montag) |
| **13** |**StartOfWeek.Wednesday** |Zahlen von 1 (Mittwoch) bis 7 (Dienstag) |
| **14** |**StartOfWeek.Thursday** |Zahlen von 1 (Donnerstag) bis 7 (Mittwoch) |
| **15** |**StartOfWeek.Friday** |Zahlen von 1 (Freitag) bis 7 (Donnerstag) |
| **16** |**StartOfWeek.Saturday** |Zahlen von 1 (Samstag) bis 7 (Freitag) |

Alle Funktionen geben eine Zahl zurück.

Weitere Informationen finden Sie unter [Arbeiten mit Datums- und Uhrzeitangaben](../show-text-dates-times.md).

## <a name="syntax"></a>Syntax
**Day**( *DateTime* )<br>**Month**( *DateTime* )<br>**Year**( *DateTime* )<br>**Hour**( *DateTime* )<br>**Minute**( *DateTime* )<br>**Second**( *DateTime* )

* *DatumUhrzeit*: erforderlich.  Der zu verarbeitende Datum/Uhrzeit-Wert  

**Weekday**( *DateTime* [, *WeekdayFirst* ] )<br>

* *DatumUhrzeit*: erforderlich.  Der zu verarbeitende Datum/Uhrzeit-Wert 
* *ErsterWochentag*: optional.  Der Excel-Code, der angibt, mit welchem Tag die Woche beginnt.  Wenn nicht angegeben, wird 1 (Sonntag zuerst) verwendet.

## <a name="examples"></a>Beispiele
Im folgenden Beispiel ist die aktuelle Uhrzeit **3:59:37 PM** am **Donnerstag, 9. April 2015**.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Year(&nbsp;Now()&nbsp;)** |Gibt die Jahreskomponente der aktuellen Uhrzeit und des aktuellen Datums zurück |2015 |
| **Month(&nbsp;Now()&nbsp;)** |Gibt die Monatskomponente der aktuellen Uhrzeit und des aktuellen Datums zurück |4 |
| **Day(&nbsp;Now()&nbsp;)** |Gibt die Tageskomponente der aktuellen Uhrzeit und des aktuellen Datums zurück |9 |
| **Hour(&nbsp;Now()&nbsp;)** |Gibt die Stundenkomponente der aktuellen Uhrzeit und des aktuellen Datums zurück |15 |
| **Minute(&nbsp;Now()&nbsp;)** |Gibt die Minutenkomponente der aktuellen Uhrzeit und des aktuellen Datums zurück |59 |
| **Second(&nbsp;Now()&nbsp;)** |Gibt die Minutenkomponente der aktuellen Uhrzeit und des aktuellen Datums zurück |37 |
| **Weekday(&nbsp;Now()&nbsp;)** |Gibt die Wochentagkomponente der aktuellen Uhrzeit und des aktuellen Datums mit dem Standardwochenbeginn am Sonntag zurück |5 |
| **Weekday(&nbsp;Now(),&nbsp;14&nbsp;)** |Gibt die Wochentagkomponente der aktuellen Uhrzeit und des aktuellen Datums mit einem Excel-Code, der den Wochenbeginn auf Donnerstag festlegt, zurück |1 |
| **Weekday(&nbsp;Now(),&nbsp;StartOfWeek.Wednesday&nbsp;)** |Gibt die Wochentagkomponente der aktuellen Uhrzeit und des aktuellen Datums mithilfe einer **StartOfWeek**-Enumeration, die den Wochenbeginn auf Mittwoch festlegt, zurück |2 |

