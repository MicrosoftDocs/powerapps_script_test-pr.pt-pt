---
title: 'Schaltflächen-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Schaltflächen-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d4cde32e52240e04a3499444d2c1325d0105a945
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42855425"
---
# <a name="button-control-in-powerapps"></a>Schaltflächen-Steuerelement in PowerApps
Ein Steuerelement, mit dem Benutzer durch Klicken oder Tippen mit der App interagieren können.

## <a name="description"></a>Beschreibung
Konfigurieren Sie die **[OnSelect](properties-core.md)**-Eigenschaft eines **Schaltflächen**-Steuerelements, um eine oder mehrere Formeln auszuführen, wenn der Benutzer auf das Steuerelement klickt oder tippt.

## <a name="key-properties"></a>Haupteigenschaften
**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[Text](properties-core.md)** – Text, der in einem Steuerelement angezeigt wird oder von einem Benutzer in ein Steuerelement eingegeben wird.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**AutoDisableOnSelect** – Deaktiviert das Steuerelement automatisch, solange das **OnSelect**-Verhalten erfolgt.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[PaddingBottom](properties-size-location.md)** – Der Abstand zwischen dem Text in einem Steuerelement und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)** – Der Abstand zwischen dem Text in einem Steuerelement und dem oberen Rand des Steuerelements.

**Pressed** – *True*, wenn das Steuerelement gedrückt ist, andernfalls *false*.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[RadiusBottomLeft](properties-size-location.md)** – Der Grad der Rundung der linken unteren Ecke eines Steuerelements.

**[RadiusBottomRight](properties-size-location.md)** – Der Grad der Rundung der rechten unteren Ecke eines Steuerelements.

**[RadiusTopLeft](properties-size-location.md)** – Der Grad der Rundung der linken oberen Ecke eines Steuerelements.

**[RadiusTopRight](properties-size-location.md)** – Der Grad der Rundung der rechten oberen Ecke eines Steuerelements.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[VerticalAlign](properties-text.md)** – Die Position des Texts in einem Steuerelement in Relation zur vertikalen Mitte des Steuerelements.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
**[Navigate( *ScreenName*, *ScreenTransitionValue* )](../functions/function-navigate.md)**

## <a name="examples"></a>Beispiele
### <a name="add-a-basic-formula-to-a-button"></a>Hinzufügen einer einfachen Formel zu einer Schaltfläche
1. Fügen Sie ein **[Texteingabe](control-text-input.md)**-Steuerelement hinzu, und benennen Sie es **Source**.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein **Schaltflächen**-Steuerelement hinzu, legen Sie dessen **[Text](properties-core.md)**-Eigenschaft auf „Hinzufügen“ und dessen **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **UpdateContext({Total:Total + Value(Source.Text)})**
   
    Benötigen Sie weitere Informationen zur **[UpdateContext](../functions/function-updatecontext.md)**-Funktion oder zu [anderen Funktionen](../formula-reference.md)?
3. Fügen Sie ein **[Bezeichnung](control-text-box.md)**-Steuerelement hinzu, legen Sie dessen **[Text](properties-core.md)**-Eigenschaft auf **Summe** fest, und drücken Sie dann **F5**.
4. Löschen Sie den Standardtext aus **Quelle**, geben Sie eine Zahl ein, und klicken oder tippen Sie dann auf **Hinzufügen**.
   
    Im **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) wird die von Ihnen eingegebene Zahl angezeigt.
5. Löschen Sie die Zahl aus **Quelle**, geben Sie eine andere Zahl ein, und klicken oder tippen Sie dann auf **Hinzufügen**.
   
    Im **[Bezeichnung](control-text-box.md)**-Steuerelement wird die Summe der von Ihnen eingegebenen beiden Zahlen angezeigt.
6. (Optional) Wiederholen Sie den vorherigen Schritt einmal oder mehrmals.
7. Um zum Standardarbeitsbereich zurückzukehren, drücken Sie die ESC-TASTE (oder klicken oder tippen rechts oben auf das Symbol X).

### <a name="configure-a-button-with-multiple-formulas"></a>Konfigurieren einer Schaltfläche mit mehreren Formeln
Fügen Sie eine Formel hinzu, die das **Texteingabe**-Steuerelement zwischen Einträgen löscht.

1. Legen Sie die **[HintText](control-text-input.md)**-Eigenschaft von **Quelle** auf „Eine Zahl eingeben“ fest.
2. Legen Sie die **[OnSelect](properties-core.md)**-Eigenschaft von **Hinzufügen** auf die folgende Formel fest:
   
    **UpdateContext({Total:Total + Value(Source.Text)});<br>UpdateContext({ClearInput: ""})**
   
    > [!NOTE]
   > Trennen Sie mehrere Formeln durch ein Semikolon „**;**“.
3. Legen Sie die **[Default](properties-core.md)**-Eigenschaft von **Quelle** auf **ClearInput** fest.
4. Drücken Sie **F5**, und testen Sie dann die App, indem Sie mehrere Werte addieren.

### <a name="add-another-button-to-reset-the-total"></a>Hinzufügen einer weiteren Schaltfläche zum Zurücksetzen der Summe
Fügen Sie eine zweite Schaltfläche hinzu, um die Summe zwischen Berechnungen zu löschen.

1. Fügen Sie ein weiteres **Schaltflächen**-Steuerelement hinzu, legen Sie dessen **[Text](properties-core.md)**-Eigenschaft auf „Löschen“ und dessen **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **UpdateContext({Total:0})**
2. Drücken Sie **F5**, addieren Sie mehrere Zahlen, und klicken oder tippen Sie dann auf **Löschen**, um die Summe zurückzusetzen.

### <a name="change-a-buttons-appearance"></a>Ändern der Darstellung einer Schaltfläche
#### <a name="change-a-buttons-shape"></a>Ändern der Form einer Schaltfläche
PowerApps erstellt standardmäßig ein rechteckiges **Schaltflächen**-Steuerelement mit abgerundeten Ecken. Sie können einfache Änderungen an der Form eines **Schaltflächen**-Steuerelements vornehmen, indem Sie dessen Eigenschaften **[Height](properties-size-location.md)**, **[Width](properties-size-location.md)** und **[Radius](properties-size-location.md)** festlegen.

> [!NOTE]
> [Symbole und Formen](control-shapes-icons.md) bieten eine Vielzahl von Designs und können einige derselben Grundfunktionen wie **Schaltflächen**-Steuerelemente ausführen. Allerdings haben **[Symbole und Formen](control-shapes-icons.md)** keine **[Text](properties-core.md)**-Eigenschaft.

1. Fügen Sie ein **Schaltflächen**-Steuerelement hinzu, und legen Sie die Eigenschaften **[Height](properties-size-location.md)** und **[Width](properties-size-location.md)** auf **300** fest, um eine große quadratische Schaltfläche zu erstellen.
2. Ändern Sie die Eigenschaften **[RadiusTopLeft](properties-size-location.md)**, **[RadiusTopRight](properties-size-location.md)**, **[RadiusBottomLeft](properties-size-location.md)** und **[RadiusBottomRight](properties-size-location.md)**, um den Grad der Krümmung jeder Ecke anzupassen. Es folgen einige Beispiele verschiedener Formen, die alle von einer quadratischen Schaltfläche mit den Maßen 300 x 300 ausgehen:
   
   * Legen Sie alle vier **[Radius](properties-size-location.md)**-Werte auf**150** fest, um einen Kreis zu erstellen.
   * Legen Sie die Werte für **[RadiusTopLeft](properties-size-location.md)** und **[RadiusBottomRight](properties-size-location.md)** auf **300** fest, um eine blattförmige **Schaltfläche** zu erstellen.
   * Legen Sie die Werte für **[RadiusTopLeft](properties-size-location.md)** und **[RadiusTopRight](properties-size-location.md)** auf **300** und die Werte für **[RadiusBottomLeft](properties-size-location.md)** und **[RadiusBottomRight](properties-size-location.md)** auf **100** fest, um eine schlaufenförmige Schaltfläche zu erstellen.

#### <a name="change-a-buttons-color-when-you-hover-over-it"></a>Ändern der Farbe einer Schaltfläche, wenn darauf gezeigt wird
Standardmäßig wird die Füllfarbe eines **Schaltflächen**-Steuerelements um 20 % abgeblendet, wenn Sie mit der Maus darauf zeigen. Sie können dieses Verhalten anpassen, indem Sie die **[HoverFill](properties-color-border.md)**-Eigenschaft ändern, die die **[ColorFade](../functions/function-colors.md)**-Funktion nutzt. Wenn Sie die **[ColorFade](../functions/function-colors.md)**-Formel auf einen positiven Prozentsatz festlegen, wird die Schaltfläche heller, sobald Sie darauf zeigen, während sie bei einem negativen Prozentsatz dunkler wird.

* Ändern Sie den **[ColorFade](../functions/function-colors.md)**-Prozentsatz der **[HoverFill](properties-color-border.md)**-Eigenschaft einer der Schaltflächen, die Sie erstellt haben, und beobachten Sie die Auswirkungen.

Sie können die Farbe eines **Schaltflächen**-Steuerelements auch durch Festlegen seiner **[HoverFill](properties-color-border.md)**-Eigenschaft auf eine Formel angeben, die die **[ColorValue](../functions/function-colors.md)**-Funktion anstelle der **[ColorFade](../functions/function-colors.md)**-Funktion enthält, wie z. B. in **ColorValue("Red")**.

> [!NOTE]
> Der Farbwert kann eine beliebige CSS-Farbdefinition sein: entweder ein Name oder ein hexadezimaler Wert.

* Ersetzen Sie auf einer der Schaltflächen, die Sie erstellt haben, die **[ColorFade](../functions/function-colors.md)**-Funktion durch eine **[ColorValue](../functions/function-colors.md)**-Funktion, und beobachten die Auswirkungen.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
* Es gelten die [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Die **[Text](properties-core.md)**-Eigenschaft muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
 
