---
title: Funktionen „Now“, „Today“ und „IsToday“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Now“, „Today“ und „IsToday“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/09/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 748f76835e9a66281f4723b88ed7249a7a07e091
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843444"
---
# <a name="now-today-and-istoday-functions-in-powerapps"></a>Die Funktionen „Now“, „Today“ und „IsToday“ in PowerApps
Gibt das aktuelle Datum und die Uhrzeit zurück und prüft, ob ein Datum/Uhrzeit-Wert heute ist

## <a name="description"></a>Beschreibung
Die **Now**-Funktion gibt das aktuelle Datum und die Uhrzeit als Datum/Uhrzeit-Wert zurück.

Die **Today**-Funktion gibt das aktuelle Datum als Datum/Uhrzeit-Wert zurück. Der Uhrzeitanteil ist Mitternacht. **Today** hat den gesamten Tag (ab Mitternacht heute bis Mitternacht morgen) den gleichen Wert.

Die **IsToday**-Funktion testet, ob ein Datum/Uhrzeit-Wert zwischen Mitternacht heute und Mitternacht morgen liegt. Diese Funktion gibt einen booleschen Wert zurück (**TRUE** oder **FALSE**).

Alle diese Funktionen funktionieren mit der lokalen Zeit des aktuellen Benutzers.

Weitere Informationen finden Sie unter [Arbeiten mit Datums- und Uhrzeitangaben](../show-text-dates-times.md).

## <a name="volatile-functions"></a>Veränderliche Funktionen
**Now** und **Today** sind veränderliche Funktionen.  Immer wenn eine dieser Funktionen ausgewertet wird, wird ein anderer Wert zurückgegeben.  

Wird eine veränderliche Funktion in einer Datenflussformel verwendet, gibt sie nur dann einen anderen Wert zurück, wenn die Formel, in der sie vorkommt, erneut ausgewertet wird.  Wenn nichts in der Formel geändert wird, bleibt der Wert während der Ausführung der App derselbe.

Ein Bezeichnungssteuerlement mit **Label1.Text = Now()** ändert sich nicht, solange die App aktiv ist.  Neue Werte werden nur beim Schließen und erneuten Öffnen der App generiert.

Die Funktion wird neu ausgewertet, wenn sie Teil einer Formel ist, in der sich etwas anderes geändert hat.  Wenn in das Beispiel z.B. ein Schieberegler-Steuerelement mit **Label1.Text = DateAdd( Now(), Slider1.Value, Minutes )** aufgenommen wird, wird die aktuelle Uhrzeit jedes Mal abgerufen, wenn sich der Wert des Schieberegler-Steuerelements ändert und der Eigenschaftentext der Bezeichnung neu ausgewertet wird.

Bei der Verwendung in einer [Verhaltensformel](../working-with-formulas-in-depth.md) werden veränderliche Funktionen immer zusammen mit der Verhaltensformel ausgewertet.  Ein Beispiel finden Sie weiter unten.

## <a name="syntax"></a>Syntax
**Now**()

**Today**()

**IsToday**( *DateTime* )

* *DatumUhrzeit*: erforderlich.  Der zu prüfende Datum/Uhrzeit-Wert.

## <a name="examples"></a>Beispiele
Für die Beispiele in diesem Abschnitt ist die aktuelle Uhrzeit **3:59 Uhr** am **12. Februar 2015**, und die Sprache ist **En-US**.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text( Now(), "mm/dd/yyyy hh:mm:ss" )** |Ruft das aktuelle Datum und die Uhrzeit ab und zeigt sie als Zeichenfolge an |„02/12/2015 03:59:00“ |
| **Text( Today(), "mm/dd/yyyy hh:mm:ss" )** |Ruft nur das aktuelle Datum ab, sodass der Zeitanteil auf Mitternacht festgelegt bleibt, und zeigt dieses als Zeichenfolge an |„02/12/2015 00:00:00“ |
| **IsToday( Now() )** |Prüft, ob das aktuelle Datum und die Uhrzeit zwischen Mitternacht heute und Mitternacht morgen liegen |**TRUE** |
| **IsToday( Today() )** |Prüft, ob das aktuelle Datum zwischen Mitternacht heute und Mitternacht morgen liegt |**TRUE** |
| **Text( DateAdd( Now(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |Ruft das aktuelle Datum und die Uhrzeit ab, fügt dem aktuellen Datum 12 Tage hinzu und zeigt es als Zeichenfolge an |„02/24/2015 03:59:00“ |
| **Text( DateAdd( Today(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |Ruft das aktuelle Datum ab, das Ergebnis 12 Tage hinzugefügt, und zeigt ihn als Zeichenfolge |„02/24/2015 00:00:00“ |
| **IsToday( DateAdd( Now(), 12 ) )** |Prüft, ob das aktuelle Datum und die Uhrzeit plus 12 Tage zwischen Mitternacht heute und Mitternacht morgen liegen |**FALSE** |
| **IsToday( DateAdd( Today(), 12 ) )** |Prüft, ob das aktuelle Datum plus 12 Tage zwischen Mitternacht heute und Mitternacht morgen liegt |**FALSE** |

#### <a name="display-a-clock-that-updates-in-real-time"></a>Anzeigen einer Uhr, die sich in Echtzeit aktualisiert

1. Fügen Sie ein **[Timer](../controls/control-timer.md)**-Steuerelement hinzu, und legen Sie dessen Eigenschaft **Dauer** auf **1000** und die Eigenschaft **Wiederholen** auf **TRUE** fest.

    Der Timer wird eine Sekunde lang ausgeführt, beginnt automatisch von Neuem und setzt dieses Muster fort. 

1. Legen Sie die Eigenschaft **OnTimerEnd** des Steuerelements auf diese Formel fest:

    **Set( CurrentTime, Now() )**

    Jedes Mal, wenn der Timer (nach einer Sekunde) neu startet, legt diese Formel die globale Variable **CurrentTime** auf den aktuellen Wert der **Now**-Funktion fest.

    ![Bildschirm mit einem Timer-Steuerelement mit der Formel OnTimerEnd = Set(CurrentTime, Now())](media/function-now-today-istoday/now-set-currenttime.png)

1. Fügen Sie ein **[Bezeichnungssteuerelement](../controls/control-text-box.md)** hinzu, und legen Sie dessen **Text**-Eigenschaft auf diese Formel fest:

    **Text( CurrentTime, LongTime24 )**

    Formatieren Sie das Datum und die Uhrzeit mithilfe der **[Text](function-text.md)**-Funktion nach Bedarf, oder legen Sie diese Eigenschaft einfach auf **CurrentTime** fest. Es werden dann nur noch Minuten und keine Sekunden mehr angezeigt.

    ![Anzeige mit einem Bezeichnungssteuerelement, dessen Eigenschaft „Text“ auf „Text( CurrentTime, LongTime24)“ festgelegt ist](media/function-now-today-istoday/now-use-currenttime.png)

1. Zeigen Sie eine Vorschau der App an, indem Sie F5 drücken. Klicken oder tippen Sie anschließend auf den Timer, um ihn zu starten.

    Die Bezeichnung zeigt immer sekundengenau die aktuelle Uhrzeit an.

    ![Vier Bildschirme mit vier Zeitwerten (13: 50:22, 13:50:45 13:51:03 und 13:51:25)](media/function-now-today-istoday/now-four-times.png)

1. Legen Sie die Timer-Eigenschaften **Automatisch starten** und **Sichtbar** auf **TRUE** bzw. **FALSE** fest.

    Der Timer ist nicht sichtbar und startet automatisch.

1. Legen Sie die **[OnStart](../controls/control-screen.md)**-Eigenschaft des Bildschirms fest, damit die Variable **CurrentTime** wie in diesem Beispiel über einen gültigen Wert verfügt:

    **Set(CurrentTime, Now())**

    Sobald die App gestartet wird (bevor der Timer eine ganze Sekunde lang ausgeführt wird), wird die Bezeichnung angezeigt.
