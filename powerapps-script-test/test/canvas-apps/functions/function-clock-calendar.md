---
title: Funktionen „Calendar“ und „Clock“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Calendar“ und „Clock“ in PowerApps
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
ms.openlocfilehash: 6625df3f822462c86de1f720b7a310f5e516a6ca
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849869"
---
# <a name="calendar-and-clock-functions-in-powerapps"></a>Die Funktionen „Calendar“ und „Clock“ in PowerApps
Ruft Kalender- und Uhrzeitinformationen zum aktuellen Gebietsschema ab

## <a name="description"></a>Beschreibung
Die **Calendar**- und **Clock**-Funktionen sind ein Satz von Funktionen, die Informationen über das aktuelle Gebietsschema abrufen.

Sie können diese Funktionen verwenden, um Daten und Uhrzeiten in der Sprache des aktuellen Benutzers anzuzeigen.  Die von der **Calendar**- und **Clock**-Funktion zurückgegebenen einspaltigen Tabellen können direkt mit der **[Items](../controls/properties-core.md)**-Eigenschaft des Dropdown- und Listbox-Steuerelements verwendet werden.

| Funktion | Beschreibung |
| --- | --- |
| **Calendar.MonthsLong()** |Eine einspaltige Tabelle mit den vollständigen Namen eines jeden Monats, beginnend mit „January“ (Januar) |
| **Calendar.MonthsShort()** |Eine einspaltige Tabelle mit den abgekürzten Namen eines jeden Monats, beginnend mit „Jan“ für Januar |
| **Calendar.WeekdaysLong()** |Eine einspaltige Tabelle mit den vollständigen Namen der einzelnen Wochentage, beginnend mit „Sunday“ (Sonntag) |
| **Calendar.WeekdaysShort()** |Eine einspaltige Tabelle mit den vollständigen Namen eines jeden Wochentags, beginnend mit „Sun“ für Sonntag |
| **Clock.AmPm()** |Eine einspaltige Tabelle, die die langen Bezeichnung für die Großbuchstaben „AM“ und „PM“ enthält.  Wenn die Sprache ein 24-Stunden-Format verwendet, ist die Tabelle leer. |
| **Clock.AmPmShort()** |Eine einspaltige Tabelle, die die kurzen Bezeichnungen „A“ und „P“ enthält.  Wenn die Sprache ein 24-Stunden-Format verwendet, ist die Tabelle leer. |
| **Clock.IsClock24()** |Boolescher Wert, der angibt, wenn ein 24-Stunden-Format in diesem Gebietsschema verwendet wird |

Verwenden Sie die **[Text](function-text.md)**-Funktion zur Formatierung von Datums- und Uhrzeitwerten mit den gleichen Angaben.  Die **[Language](function-language.md)**-Funktion gibt den Code der aktuelle Sprache und Region zurück.

## <a name="syntax"></a>Syntax
**Calendar.MonthsLong**()

**Calendar.MonthsShort**()

**Calendar.WeekdaysLong**()

**Calendar.WeekdaysShort**()

**Clock.AmPm**()

**Clock.AmPmShort**()

**Clock.IsClock24**()

## <a name="examples"></a>Beispiele
1. Fügen Sie ein Dropdown-Steuerelement ein.
2. Legen Sie die Formel für die **[Items](../controls/properties-core.md)**-Eigenschaft auf Folgendes fest:
   
   * **Calendar.MonthsLong()**
3. Benutzer Ihrer App können nun einen Monat in ihrer eigenen Sprache auswählen.  **MonthsLong** kann durch eine beliebige einspaltige von **Calendar** zurückgegebene Tabellen ersetzt werden, um eine Wochentags- und Zeitauswahl zu erstellen.

In den USA gibt **[Language](function-language.md)** „en-US“ zurück, und die **Calendar**-Funktion gibt Folgendes zurück:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Calendar.MonthsLong()** |Der Rückgabewert enthält den vollständigen Namen eines jeden Monats, beginnend mit „January“. |[ „January“, „February“, „March“, „April“, „May“, „June“, „July“, „August“, „September“, „October“, „November“, „December“ ] |
| **Calendar.MonthsShort()** |Der Rückgabewert enthält die abgekürzten Namen eines jeden Monats, beginnend mit „January“. |[ „Jan“, „Feb“, „Mar“, „Apr“, „May“, „Jun“, „Jul“, „Aug“, „Sep“, „Oct“, „Nov“, „Dec“ ] |
| **Calendar.WeekdaysLong()** |Der Rückgabewert enthält den vollständigen Namen eines jeden Wochentags, beginnend mit „Sunday“. |[ „Sunday“, „Monday“, „Tuesday“, „Wednesday“, „Thursday“, „Friday“, „Saturday“ ] |
| **Calendar.WeekdaysShort()** |Der Rückgabewert enthält die abgekürzten Namen eines jeden Wochentags, beginnend mit „Sunday“. |[ „Sun“, „Mon“, „Tue“, „Wed“, „Thu“, „Fri“, „Sat“ ] |
| **Clock.AmPm()** |Diese Sprache verwendet ein 12-Stunden-Format.  Der Rückgabewert enthält die Großbuchstaben der vollständigen AM/PM-Bezeichnungen. |[ „AM“, „PM“ ] |
| **Clock.AmPmShort()** |Diese Sprache verwendet ein 12-Stunden-Format.  Der Rückgabewert enthält die Großbuchstaben der kurzen AM/PM-Bezeichnungen. |[ "A", "P" ] |
| **Clock.IsClock24()** |Diese Sprache verwendet ein 12-Stunden-Format. |**FALSE** |

