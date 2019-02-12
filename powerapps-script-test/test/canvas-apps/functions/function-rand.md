---
title: Funktion „Rand“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Rand“ in PowerApps
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
ms.openlocfilehash: abb64d57e53f292dc42cb44ef2b1c9f35bbad944
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42850220"
---
# <a name="rand-function-in-powerapps"></a>Funktion „Rand“ in PowerApps
Gibt eine pseudozufällige Zahl zurück.

## <a name="description"></a>Beschreibung
Die Funktion **Rand** gibt eine Pseudo-Zufallszahl zurück, die größer als oder gleich 0 (null) und kleiner als 1 ist.

## <a name="volatile-functions"></a>Veränderliche Funktionen
**Rand** ist eine veränderliche Funktion.  Immer wenn die Funktion ausgewertet wird, wird ein anderer Wert zurückgegeben.  

Wird eine veränderliche Funktion in einer Datenflussformel verwendet, gibt sie nur dann einen anderen Wert zurück, wenn die Formel, in der sie vorkommt, erneut ausgewertet wird.  Wenn nichts in der Formel geändert wird, bleibt der Wert während der Ausführung der App derselbe.

Ein Bezeichnungssteuerelement mit **Label1.Text = Rand()** ändert sich nicht, solange die App aktiv ist.  Neue Werte werden nur beim Schließen und erneuten Öffnen der App generiert.

Die Funktion wird neu ausgewertet, wenn sie Teil einer Formel ist, in der sich etwas anderes geändert hat.  Wenn in das Beispiel z.B. ein Schieberegler-Steuerelement mit **Label1.Text = Slider1.Value + Rand()** aufgenommen wird, wird jedes Mal, wenn sich der Wert des Schieberegler-Steuerelements ändert und der Eigenschaftentext der Bezeichnung neu ausgewertet wird, eine neue Zufallszahl generiert.  Das Beispiel finden Sie weiter unten.

Bei der Verwendung in einer [Verhaltensformel](../working-with-formulas-in-depth.md) wird **Rand** immer zusammen mit der Verhaltensformel ausgewertet.  Ein Beispiel finden Sie weiter unten.

## <a name="syntax"></a>Syntax
**Rand**()

## <a name="examples"></a>Beispiele

#### <a name="display-a-different-random-number-as-user-input-changes"></a>Anzeigen einer anderen Zufallszahl, da sich die Benutzereingabe geändert hat
1. Fügen Sie ein **[Schieberegler](../controls/control-slider.md)**-Steuerelement hinzu, und benennen Sie es in **Slider1** um, wenn es nicht bereits so heißt.

1. Fügen Sie ein **[Bezeichnungssteuerelement](../controls/control-text-box.md)** hinzu, und legen Sie dessen **Text**-Eigenschaft auf diese Formel fest:

    **Slider1.Value + Rand()**

    Die Bezeichnung zeigt **50** (Standardwert des Schiebereglers) plus eine zufällige Dezimalzahl an:

    ![Bildschirm, der ein Bezeichnungssteuerelement mit dem Wert „50,741“ anzeigt](media/function-rand/rand-slider-1.png)

1. Ändern Sie den Wert des Schiebereglers, während Sie die ALT-TASTE gedrückt halten.

    Jedes Mal, wenn Sie den Wert des Schiebereglers ändern, wird in den Nachkommastellen der Bezeichnung eine andere Zufallszahl angezeigt:

    ![Vier Bildschirme, die eine Bezeichnung mit vier verschiedenen zufälligen Dezimalwerten für jede der vier Schiebereglereinstellungen anzeigen: 70,899, 84,667, 90,134 und 99,690](media/function-rand/rand-slider-results.png)

#### <a name="create-a-table-of-random-numbers"></a>Erstellen einer Tabelle mit Zufallszahlen
1. Fügen Sie ein **[Button](../controls/control-button.md)**-Steuerelement (Schaltfläche) hinzu, und legen Sie seine **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:

    **ClearCollect( RandomNumbers, ForAll( [ 1, 2, 3, 4, 5 ], Rand() ))**

    Diese Formel erstellt eine Tabelle mit einer Spalte, mit der eine fünfmalige Iteration ausgeführt wird. Das Ergebnis sind fünf Zufallszahlen.

1. Fügen Sie eine **[Datentabelle](../controls/control-data-table.md)** hinzu, legen Sie deren Eigenschaft **Elemente** auf **RandomNumbers** fest, und zeigen Sie das Feld **Wert** an.

    ![Anzeige mit einer Tabelle mit fünf verschiedenen Dezimalwerten: 0,857, 0,105, 0,979, 0,167 und 0,814](media/function-rand/set-show-data.png)

1. Klicken oder tippen Sie auf die Schaltfläche, während Sie die ALT-TASTE gedrückt halten.

    Die Datentabelle zeigt fünf zufällige Dezimalzahlen an:

    ![Anzeige mit einer Tabelle mit fünf verschiedenen Dezimalwerten: 0,857, 0,105, 0,979, 0,167 und 0,814](media/function-rand/rand-collection-1.png)

1. Klicken Sie noch einmal auf die Schaltfläche, um eine andere Liste von Zufallszahlen anzuzeigen:

    ![Die gleiche Anzeige mit einer Tabelle mit fünf neuen Dezimalwerten: 0,414, 0,128, 0,860, 0,303 und 0,568](media/function-rand/rand-collection-2.png)

Um eine einzelne Zufallszahl statt einer Tabelle zu generieren, verwenden Sie **Set( RandomNumber, Rand() )**.
