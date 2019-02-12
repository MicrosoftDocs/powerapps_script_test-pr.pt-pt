---
title: 'Texteingabe-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Texteingabe-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a46635276f6598cf0591dc21ae5aeb855b6667c1
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42830545"
---
# <a name="text-input-control-in-powerapps"></a>Texteingabe-Steuerelement in PowerApps
Ein Feld, in das der Benutzer Text, Zahlen und andere Daten eingeben kann

## <a name="description"></a>Beschreibung
Der Benutzer kann Daten angeben, indem er Text in ein Texteingabe-Steuerelement eingibt. Abhängig davon, wie Sie die App konfigurieren, werden diese Daten möglicherweise zu einer Datenquelle hinzugefügt, dazu verwendet, einen temporären Wert zu berechnen oder auf eine andere Weise eingebunden.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)** – Der Anfangswert eines Steuerelements, bevor es vom Benutzer geändert wird.

**[Text](properties-core.md)** – Text, der in einem Steuerelement angezeigt wird oder von einem Benutzer in ein Steuerelement eingegeben wird.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**Clear**: Legt fest, ob ein Texteingabe-Steuerelement ein „X“ anzeigt, auf das der Benutzer tippen oder klicken kann, um den Inhalt dieses Steuerelements zu löschen.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**DelayOutput**: Wenn auf TRUE festgelegt, wird die Benutzereingabe mit einer Verzögerung von einer halben Sekunde registriert.  Dies ist nützlich für die Verzögerung von teuren Vorgängen, bis der Benutzer die Texteingabe abschließt (d.h. für die Filterung, wenn die Eingabe in anderen Formeln verwendet wird).

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**Format**: Legt fest, ob die Benutzereingabe auf Zahlen beschränkt ist, oder ob Text zulässig ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**HintText**: Hellgrauer Text, der in einem Texteingabe-Steuerelement erscheint, wenn dieses leer ist.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[LineHeight](properties-text.md)**: Der Abstand zwischen Elementen, z.B. Textzeilen oder Elementen in einer Liste.

**MaxLength**: Die Anzahl der Zeichen, die der Benutzer in ein Texteingabe-Steuerelement eingeben kann.

**Mode**: Das Steuerelement befindet sich im Modus **SingleLine**, **MultiLine** oder **Password**.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[RadiusBottomLeft](properties-size-location.md)** – Der Grad der Rundung der linken unteren Ecke eines Steuerelements.

**[RadiusBottomRight](properties-size-location.md)** – Der Grad der Rundung der rechten unteren Ecke eines Steuerelements.

**[RadiusTopLeft](properties-size-location.md)** – Der Grad der Rundung der linken oberen Ecke eines Steuerelements.

**[RadiusTopRight](properties-size-location.md)** – Der Grad der Rundung der rechten oberen Ecke eines Steuerelements.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**DateTimeValue**( *Zeichenfolge* )](../functions/function-datevalue-timevalue.md)

## <a name="examples"></a>Beispiele
### <a name="collect-data"></a>Sammeln von Daten
1. Fügen Sie zwei Texteingabe-Steuerelemente hinzu, und nennen Sie diese **inputFirst** und **inputLast**.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie eine Schaltfläche hinzu, legen Sie ihre **[Text](properties-core.md)**-Eigenschaft auf **Add** (Hinzufügen) und ihre **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **Collect(Names, {FirstName:inputFirst.Text, LastName:inputLast.Text})**
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
3. Fügen Sie einen Textkatalog im Hochformat hinzu, legen sie seine **[Items](properties-core.md)**-Eigenschaft auf **Names** und seine **[Text](properties-core.md)**-Eigenschaft von **Subtitle1** auf **ThisItem.FirstName** fest.
4. (Optional:) Löschen Sie im Vorlagenkatalog die untere Bezeichnung mit dem Namen **Body1**, und legen Sie die **[TemplateSize](control-gallery.md)**-Eigenschaft des Katalogs auf **80** fest.
5. Drücken Sie F5, geben Sie eine Textzeichenfolge in **inputFirst** und **inputLast** ein, und klicken oder tippen Sie anschließend auf die Schaltfläche **Hinzufügen**.
6. (Optional:) Fügen Sie der Sammlung mehr Namen hinzu, und drücken Sie anschließend die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren.

### <a name="prompt-for-a-password"></a>Aufforderung zur Kennworteingabe

1. Fügen Sie ein Texteingabe-Steuerelement hinzu, nennen Sie es **inputPassword**, und legen Sie seine **Mode**-Eigenschaft auf **Password** fest.

1. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](properties-core.md)** auf diese Funktion fest:<br>
   **If(inputPassword.Text = "P@ssw0rd", "Access granted", "Access denied")**

    Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?

1. Drücken Sie F5, und geben Sie anschließend **P@ssw0rd** in **inputPassword** ein.

    Wenn Sie mit der Eingabe des Kennworts fertig sind, zeigt die Bezeichnung nicht mehr **Access denied** (Zugriff verweigert) sondern **Access granted** (Zugriff gewährt) an.

1. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.

1. (Optional:) Fügen Sie ein Steuerelement wie z.B. einen Pfeil hinzu, konfigurieren Sie es so, dass es zu einem anderen Bildschirm navigiert, und lassen Sie es erst anzeigen, wenn der Benutzer das Kennwort eingegeben hat.

1. (Optional:) Fügen Sie eine Schaltfläche hinzu, konfigurieren Sie deren **[Text](properties-core.md)**-Eigenschaft so, dass **Anmelden** angezeigt wird, fügen Sie einen Zeitgeber hinzu, und deaktivieren Sie das Textsteuerelement für einen bestimmten Zeitraum, wenn der Benutzer das falsche Kennwort eingibt und anschließend auf die Schaltfläche **Anmelden** klickt oder tippt.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
* Es gelten die [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
 
