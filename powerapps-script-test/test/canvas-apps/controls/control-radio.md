---
title: 'Radio-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Radio-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 447cda7a1d8d4f27c8be2b943abd2b5d6b431d49
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42853680"
---
# <a name="radio-control-in-powerapps"></a>Radio-Steuerelement in PowerApps

Ein Eingabesteuerelement, das mehrere Optionen anzeigt, aus der Benutzer jeweils nur eine auswählen können.

## <a name="description"></a>Beschreibung

Ein **Radio**-Steuerelemente, ein standardmäßiges HTML-Eingabesteuerelement, funktioniert am besten, wenn nur ein paar wenige Optionen, die sich gegenseitig ausschließen, verwendet werden.

Das Steuerelement kann über ein horizontales oder vertikales Layout verfügen.

## <a name="key-properties"></a>Haupteigenschaften

**[Default](properties-core.md)**: Der Wert eines Steuerelements, bevor es vom Benutzer geändert wird.

**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**Layout**: Gibt an, ob die Optionen vertikal oder horizontal angeordnet werden.

**[Value](properties-core.md)**: Gibt den Wert eines Eingabesteuerelements an.

## <a name="all-properties"></a>Alle Eigenschaften

**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[LineHeight](properties-text.md)**: Der Abstand zwischen Elementen, z.B. Textzeilen oder Elementen in einer Liste.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**RadioBackgroundFill**: Die Farbe des Hintergrunds der Kreise in einem Steuerelement der Radioschaltfläche.

**RadioBorderColor**: Die Farbe des Kreises für jede Option in einem Steuerelement der Radioschaltfläche.

**RadioSelectionFill**: Die Farbe, die innerhalb des Kreises, der ausgewählten Option in einem Steuerelement der Radioschaltfläche angezeigt wird.

**RadioSize**: Der Durchmesser der Kreise in einem Steuerelement der Radioschaltfläche.

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

[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Beispiel

1. Fügen Sie das **Radio**-Steuerelement hinzu, nennen Sie es **Pricing**, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf die folgende Formel fest:

    **["Standard", "Premium"]**

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?

2. Fügen Sie ein Steuerelement **[Label](control-text-box.md)** (Bezeichnung) hinzu, verschieben Sie es unter das **Radio**-Steuerelement (Optionsfeld) und legen Sie die Eigenschaft **[Text](properties-core.md)** des Steuerelements **[Label](control-text-box.md)** auf diese Formel fest:

    **If("Premium" in Pricing.Selected.Value, "$200 pro Tag", "$150 pro Tag")**

    Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?

3. Halten Sie die ALT-TASTE gedrückt, und wählen Sie im **Radio**-Steuerelement eine der Optionen aus.

    Das Steuerelement **[Label](control-text-box.md)** (Bezeichnung) zeigt den entsprechenden Text Ihrer Wahl.

4. Optional: Halten Sie die ALT-TASTE gedrückt, und wählen Sie die andere Option aus, um zu bestätigen, dass der entsprechende Text angezeigt wird.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="color-contrast"></a>Farbkontrast

Stellen Sie zusätzlich zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md) ausreichenden Farbkontrast zwischen folgenden Farben sicher:

* **RadioSelectionFill** und **RadioBackgroundFill**
* **RadioBackgroundFill** und **[Fill](properties-color-border.md)**

### <a name="screen-reader-support"></a>Sprachausgabeunterstützung

* Stellen Sie sicher, dass jede Option einen **[Wert](properties-core.md)** hat.
* Sie sollten direkt vor dem Steuerelement **Radio** eine **[Bezeichnung](control-text-box.md)** hinzufügen, die als Titel dienen soll.

### <a name="keyboard-support"></a>Tastaturunterstützung

* Legen Sie die Eigenschaft **[TabIndex](properties-accessibility.md)** auf 0 (null) oder größer fest, damit Tastaturbenutzer dorthin navigieren können.
* Legen Sie die Eigenschaften **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** fest, damit Fokusindikatoren deutlich sichtbar sind.
