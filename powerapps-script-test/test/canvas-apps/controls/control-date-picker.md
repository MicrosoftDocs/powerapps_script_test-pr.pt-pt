---
title: 'Datumsauswahl-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Datumsauswahl-Steuerelement
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
ms.openlocfilehash: ddb15340c9532e82d95f1bea70959dc59cdc7283
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42853817"
---
# <a name="date-picker-control-in-powerapps"></a>Datumsauswahl-Steuerelement in PowerApps
Ein Steuerelement, mit dem Benutzer durch Klicken oder Tippen ein Datum angeben können.

## <a name="description"></a>Beschreibung
Wenn Sie ein **Datumsauswahl**-Steuerelement anstatt eines **[Texteingabe](control-text-input.md)**-Steuerelements verwenden, geben Benutzer das Datum in jedem Fall im richtigen Format an.

## <a name="key-properties"></a>Haupteigenschaften
**DefaultDate** – Der Anfangswert eines Datum-Steuerelements, es sei denn, der Benutzer ändert ihn.

**SelectedDate** – Das Datum, das in einem Datum-Steuerelement ausgewählt ist.

**Format** – Das Textformat, in dem das Steuerelement das Datum zeigt und der Benutzer das Datum angibt. Sie können diese Eigenschaft auf **ShortDate** (Standard) oder **LongDate** festlegen, um Datumsangaben basierend auf der **Language**-Eigenschaft dieses Steuerelements zu formatieren. Sie können diese Eigenschaft auf einen Ausdruck festlegen, z. B. **TT.MM.JJJJ**, wenn Sie dasselbe Format ungeachtet der Sprache wünschen. Beispiel:

* Das Steuerelement zeigt **12/31/2017**, wenn der Benutzer auf den letzten Tag von 2017 klickt oder tippt. Die **Format**-Eigenschaft ist auf **ShortDate**, die **Language**-Eigenschaft auf **en-us** festgelegt.
* Das Steuerelement zeigt **dimanche 31 decembre 2017**, wenn der Benutzer auf den letzten Tag von 2017 klickt oder tippt. Die **Format**-Eigenschaft ist auf **LongDate**, die **Language**-Eigenschaft auf **fr-fr** festgelegt.

**Sprache** – Bestimmt die Sprache, die zum Formatieren von Datumsangaben, einschließlich der Namen von Monaten, verwendet wird. Wenn diese Eigenschaft nicht angegeben ist, wird die Sprache von der Geräteeinstellung des Benutzers bestimmt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt („Edit“, Bearbeiten), ob nur Daten angezeigt werden („View“, Anzeigen) oder ob das Steuerelement deaktiviert ist („Disabled“, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**EndYear** – Das letzte Jahr, auf das Benutzer den Wert eines Steuerelements für die Datumsauswahl festlegen können.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**IconFill:** die Vordergrundfarbe eines Symbols für die Datumsauswahl.

**IconBackground:** die Hintergrundfarbe eines Symbols für die Datumsauswahl.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**StartYear** – Das früheste Jahr, auf das Benutzer den Wert eines Steuerelements für die Datumsauswahl festlegen können.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
**[Year](../functions/function-datetime-parts.md)**( *DateTimeValue* )

## <a name="example"></a>Beispiel
1. Fügen Sie ein **Datumsauswahl**-Steuerelement hinzu, und benennen Sie es **Deadline**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**DateDiff(Today(), Deadline.SelectedDate) & " days to go!"**

    Benötigen Sie weitere Informationen zur **[DateDiff](../functions/function-dateadd-datediff.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
3. Drücken Sie F5, legen Sie für **Deadline** ein Datum fest, und klicken oder tippen Sie dann auf **OK**.

    Im **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) wird angezeigt, wie viele Tage zwischen dem aktuellen und dem gewählten Datum verbleiben.
4. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
* Es gelten die [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
