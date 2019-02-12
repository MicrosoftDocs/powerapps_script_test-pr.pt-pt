---
title: Funktionen „DateAdd“, „DateDiff“ und „TimeZoneOffset“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „DateAdd“, „DateDiff“ und „TimeZoneOffset“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b70026e84eb7dfee67583abe26665bf78a566b76
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865252"
---
# <a name="dateadd-datediff-and-timezoneoffset-functions-in-powerapps"></a>Die Funktionen „DateAdd“, „DateDiff“ und „TimeZoneOffset“ in PowerApps
Dienen zum Hinzufügen zu oder Auffinden des Unterschiedes bei Datum-/Uhrzeit-Werten und Konvertieren zwischen Ortszeit und UTC.

## <a name="description"></a>Beschreibung
Die **DateAdd**-Funktion fügt einem Datum/Uhrzeit-Wert eine Anzahl von Einheiten hinzu. Das Ergebnis ist ein neuer Datum/Uhrzeit-Wert. Sie können auch eine Anzahl von Einheiten von einem Datum/Uhrzeit-Wert subtrahieren, indem Sie einen negativen Wert angeben.

Die **DateDiff**-Funktion gibt die Differenz zwischen zwei Datum/Uhrzeit-Werten zurück. Das Ergebnis ist eine Anzahl von Einheiten.

Mögliche Einheiten für beide Funktionen sind **Millisekunden**, **Sekunden**, **Minuten**, **Stunden**, **Tage**, **Monate**, **Quartale** oder **Jahre**.  Beide Funktionen verwenden standardmäßig **Tage** als Einheiten.

Die **TimeZoneOffset**-Funktion gibt die Anzahl der Minuten zwischen Ortszeit des Benutzers und UTC (Coordinated Universal Time) zurück.   

Sie können **DateAdd** mit **TimeZoneOffset** zum Konvertieren zwischen der Ortszeit des Benutzers und UTC (Coordinated Universal Time) verwenden.  Durch Hinzufügen von **TimeZoneOffset** wird eine Ortszeit in UTC konvertiert, und durch Subtrahieren (Hinzufügen eines negativen Werts) wird UTC in die Ortszeit konvertiert.

Weitere Informationen finden Sie unter [Working with dates and times (Arbeiten mit Datums- und Uhrzeitangaben)](../show-text-dates-times.md).

## <a name="syntax"></a>Syntax
**DateAdd**( *DateTime*, *Addition* [, *Units* ] )

* *DatumUhrzeit*: erforderlich. Der zu verarbeitende Datum/Uhrzeit-Wert
* *Addition*: erforderlich. Die *DateTime* hinzuzufügende Anzahl in *Einheiten*.
* *Einheiten*: optional. Mögliche Typen von *Einheiten* sind **Millisekunden**, **Sekunden**, **Minuten**, **Stunden**, **Tage**, **Monate**, **Quartale** oder **Jahre**.  Wenn nicht angegeben, werden **Tage** verwendet.

**DateDiff**( *StartDateTime*, *EndDateTime* [, *Units* ] )

* *AnfangDatumUhrzeit*: erforderlich. Der Anfangs-Datum/Uhrzeit-Wert
* *EndeDatumUhrzeit*: erforderlich. Der End-Datum/Uhrzeit-Wert
* *Einheiten*: optional. Mögliche Typen von *Einheiten* sind **Millisekunden**, **Sekunden**, **Minuten**, **Stunden**, **Tage**, **Monate**, **Quartale** oder **Jahre**.  Wenn nicht angegeben, werden **Tage** verwendet.

**TimeZoneOffset**( [ *DateTime* ] )

* *DateTime*: Optional.  Datum/Uhrzeit-Wert, für den der Offset zurückgegeben werden soll.  Standardmäßig wird der aktuelle Datum/Uhrzeit-Wert verwendet.

## <a name="examples"></a>Beispiele
Bei allen diesen Beispielen wird davon ausgegangen, dass der Datum/Uhrzeit-Wert der **15. Juli 2013, 13:02 Uhr** ist.

### <a name="simple-dateadd"></a>Einfache DateAdd-Funktion

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text( DateAdd( Now(), 3 ),<br>"dd-mm-yyyy hh:mm" )** |Dem aktuellen Datum/Uhrzeit-Wert werden drei Tage (Standardeinheiten) hinzugefügt. |"18-07-2013 13:02" |
| **Text( DateAdd( Now(), 4, Stunden ),<br>"dd-mm-yyyy hh:mm" )** |Dem aktuellen Datum/Uhrzeit-Wert werden vier Stunden hinzugefügt. |"15-07-2013 17:02" |
| **Text( DateAdd( Today(), 1, Monate ),<br>"dd-mm-yyyy hh:mm" )** |Fügt dem aktuellen Datum einen Monat hinzu. Ohne Uhrzeit als **Today** wird keine Zeitangabe zurückgegeben. |"15-08-2013 00:00" |
| **Text( DateAdd( Now(), &#8209;30, Minuten ),<br>"dd-mm-yyyy hh:mm" )** |Subtrahiert 30 Minuten vom dem aktuellen Datum/Uhrzeit-Wert. |"15-07-2013 12:32" |

### <a name="simple-datediff"></a>Einfache DateDiff-Funktion

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **DateDiff( Now(), DateValue("1/1/2014") )** |Gibt die Differenz zwischen den zwei Einheiten in der Standardeinheit **Tage** zurück. |170 |
| **DateDiff( Now(), DateValue("1/1/2014"), Monate )** |Gibt die Differenz zwischen den beiden Werten in **Monaten** zurück. |6 |
| **DateDiff( Now(), Today(), Minuten )** |Gibt die Differenz zwischen dem aktuellen Datum/Uhrzeit-Wert und dem aktuellen Datum nur in Minuten (ohne Uhrzeit) zurück.  Da **Now** (jetzt) später als **Today** (heute) ist, ist das Ergebnis negativ. |-782 |

### <a name="converting-to-utc"></a>Konvertieren in UTC
Fügen Sie zum Konvertieren in UTC (Coordinated Universal Time) **TimeZoneOffset** der angegebenen Uhrzeit hinzu.  

Angenommen, der aktuelle Datum/Uhrzeit-Wert ist der **15. Juli 2013, 13:02 Uhr** in Pacific Daylight Time (PDT, UTC-7).  Verwenden Sie zum Bestimmen der aktuellen Uhrzeit in UTC Folgendes:

* **DateAdd( Now(), TimeZoneOffset(), Minuten )**

**TimeZoneOffset** ist standardmäßig auf die aktuelle Uhrzeit festgelegt, sodass Sie kein Argument dafür übergeben müssen.

Um das Ergebnis anzuzeigen, verwenden Sie die **Text**-Funktion im Format *dd-mm-yyyy hh:mm*, die **15-07-2013 20:02** zurückgibt.

### <a name="converting-from-utc"></a>Konvertieren aus UTC
Zum Konvertieren aus UTC subtrahieren Sie **TimeZoneOffset** (durch Hinzufügen eines negativen Werts) von der angegebenen Uhrzeit.

Angenommen, das UTC-Datum und die Uhrzeit **15. Juli 2013, 20:02 Uhr** werden in einer Variablen namens **StartTime** gespeichert. Verwenden Sie zum Anpassen der Zeit für die Zeitzone des Benutzers Folgendes:

* **DateAdd( StartTime, -TimeZoneOffset( StartTime ), Minuten )**

Beachten Sie das negative Vorzeichen vor **TimeZoneOffset**, damit der Offset subtrahiert und nicht addiert wird.

Um das Ergebnis anzuzeigen, verwenden Sie die **Text**-Funktion im Format *dd-mm-yyyy hh:mm*, die **15-07-2013 13:02** in der PDT-Zeit zurückgibt.

