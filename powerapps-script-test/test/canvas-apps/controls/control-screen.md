---
title: 'Bildschirm-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Bildschirm-Steuerelement
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d90c82b29ebc77b67731903d7a950790e13661e1
ms.sourcegitcommit: 6851486b8a44d76b6d87837952b7a7f38a8752b6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/18/2018
ms.locfileid: "53570395"
---
# <a name="screen-control-in-powerapps"></a>Bildschirm-Steuerelement in PowerApps
Ein Benutzeroberflächenelement, das in einer App ein oder mehrere Steuerelemente enthält

## <a name="description"></a>Beschreibung
Die meisten Apps verfügen über mehrere **Bildschirm**-Steuerelemente, die **[Bezeichnung](control-text-box.md)**-Steuerelemente, **[Schaltflächen-](control-button.md)** und andere Steuerelemente enthalten und Daten anzeigen sowie die Navigation unterstützen.

## <a name="key-properties"></a>Haupteigenschaften
**[BackgroundImage](properties-visual.md)** : der Name einer Bilddatei, die im Hintergrund eines Bildschirms angezeigt wird

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[ImagePosition](properties-visual.md)**: Die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Bilds auf einem Bildschirm oder in einem Steuerelement, wenn die Größe nicht mit der Bildgröße identisch ist.

**OnHidden**: Das Verhalten einer App, wenn der Benutzer zu einer anderen Bildschirmansicht wechselt.

**OnVisible**: Das Verhalten einer App, wenn der Benutzer zu einem Bildschirm navigiert.

**OnStart**: Das Verhalten einer App, wenn sie vom Benutzer geöffnet wird.

* Die Formel, auf die diese Eigenschaft festgelegt ist, wird vor dem Anzeigen des ersten Bildschirms der App ausgeführt. Rufen Sie die [**Navigate**](../functions/function-navigate.md)-Funktion zum Ändern des Bildschirms auf, der beim Start der App zuerst angezeigt wird.
* Sie können mit der [**UpdateContext**](../functions/function-updatecontext.md)-Funktion keine [Kontextvariablen](../working-with-variables.md) festlegen, da noch kein Bildschirm angezeigt wurde. Sie können Kontextvariablen allerdings an die **Navigate**-Funktion übergeben und eine [Sammlung](../working-with-variables.md) mithilfe der [**Collect**](../functions/function-clear-collect-clearcollect.md)-Funktion erstellen und auffüllen.
* Wenn Sie eine App aktualisieren, wird die Formel, auf die diese Eigenschaft festgelegt ist, beim Laden der App in PowerApps Studio ausgeführt. Um die Auswirkungen einer Änderung dieser Eigenschaft anzuzeigen, müssen Sie Ihre App speichern, schließen und neu laden.
* Die **OnStart**-Eigenschaft ist tatsächlich eine Eigenschaft der App und nicht des Bildschirms. Zur Vereinfachung der Bearbeitung wird sie als Eigenschaft auf dem ersten Bildschirm Ihrer App angezeigt und geändert. Wenn Sie den ersten Bildschirm entfernen oder Bildschirme neu anordnen, kann diese Eigenschaft schwer zu finden sein. In diesem Fall sollten Sie Ihre App speichern, schließen und neu laden, woraufhin die Eigenschaft wieder als Eigenschaft auf dem ersten Bildschirm angezeigt wird.

## <a name="related-functions"></a>Verwandte Funktionen
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein**[Optionsfeld](control-radio.md)**-Steuerelement hinzu, nennen Sie es **ScreenFills**, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf folgenden Wert fest:<br>
   **["Red", "Green"]**
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Nennen Sie die das **Bildschirm**-Standardsteuerelement **Source**, fügen Sie ein weiteres **Bildschirm**-Steuerelement hinzu, und nennen Sie es **Target**.
3. Fügen Sie in **Source** ein **[Shape](control-shapes-icons.md)**-Steuerelement (z.B. einen Pfeil) hinzu, und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **Navigate(Target, ScreenTransition.Fade)**
   
    Benötigen Sie weitere Informationen zur **[Navigate](../functions/function-navigate.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
4. Fügen Sie in **Target** ein **[Shape](control-shapes-icons.md)**-Steuerelement hinzu (z.B. einen Pfeil), und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **Navigate(Source, ScreenTransition.Fade)**
5. Legen Sie die **[Fill](properties-color-border.md)**-Eigenschaft von **Target** auf diese Formel fest:<br>
   **If("Red" in ScreenFills.Selected.Value, RGBA(255, 0, 0, 1), RGBA(54, 176, 75, 1))**
6. Drücken Sie von **Source** auf F5, klicken oder tippen Sie auf eine der Optionen im **[Optionsfeld](control-radio.md)**-Steuerelement, und klicken oder tippen Sie anschließend auf das **[Shape](control-shapes-icons.md)**-Steuerelement.
   
    **Target** wird in der von Ihnen ausgewählten Farbe angezeigt.
7. Klicken oder tippen Sie in **Target** auf das **[Shape](control-shapes-icons.md)**-Steuerelement, um zu **Source** zurückzukehren.
8. (optional) Klicken oder tippen Sie auf die andere Option im  **[Optionsfeld](control-radio.md)-Steuerelement** , und klicken oder tippen Sie anschließend auf das **[Shape](control-shapes-icons.md)** -Steuerelement, um zu bestätigen, dass  **Target** in einer anderen Farbe angezeigt wird.
9. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Wenn die **Anzeige** als Hintergrund für Text gilt, muss zwischen den folgenden Eigenschaften ein angemessener Farbkontrast bestehen:
* **[Fill](properties-color-border.md)** und Text
* (Ggf.) **[BackgroundImage](properties-visual.md)** und Text

Wenn beispielsweise eine **Anzeige** eine **[Bezeichnung](control-text-box.md)** enthält und die Füllung der Bezeichnung durchsichtig ist, wird diese **[Füllung](properties-color-border.md)** als Hintergrundfarbe für die Bezeichnung verwendet.

Sie sollten nicht nur den Text überprüfen, sondern auch den Farbkontrast mit grundlegenden graphischen Objekten wie Bildern mit Sternen in einem **[Bewertungs](control-rating.md)**-Steuerelement.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Jeder **Ansicht** muss ein eindeutiger Name zugewiesen sein. Der Anzeigename kann auf dieselbe Weise wie andere Steuerelemente angezeigt und bearbeitet werden, also entweder in der Strukturansicht des Bereichs „Steuerelemente“ oder im Header im Bereich „Eigenschaften“.

    > [!NOTE]
  > Wenn eine neue **Anzeige** geladen wird, nennt die Sprachausgabe deren Namen. 
