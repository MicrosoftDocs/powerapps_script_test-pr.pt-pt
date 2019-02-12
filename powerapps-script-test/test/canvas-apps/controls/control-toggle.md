---
title: 'Umschalten-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Umschalten-Steuerelement
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
ms.openlocfilehash: 6ab5ddf93351547afb752e838ab4929c7138df87
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849223"
---
# <a name="toggle-control-in-powerapps"></a>Umschalten-Steuerelement in PowerApps
Ein Steuerelement, das die Benutzer durch Verschieben des Handles aktivieren oder deaktivieren können.

## <a name="description"></a>Beschreibung
Umschalten wurde für aktuelle GUIs entwickelt, verhält sich jedoch genauso wie ein Kontrollkästchen.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)** – Der Anfangswert eines Steuerelements, bevor es vom Benutzer geändert wird.

**[Value](properties-core.md)**: Gibt den Wert des Eingabesteuerelements an.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**FalseFill**: Die Füllfarbe der Umschaltfläche, wenn sie deaktiviert ist.

**FalseHoverFill**: Die Hoverfüllfarbe der Umschaltfläche, wenn sie deaktiviert ist.

**FalseText**: Der Text, der angezeigt wird, wenn die Umschaltfläche deaktiviert ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**HandleFill**: die Füllfarbe des Handles „Schalter“.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**OnCheck**: Wie eine App reagiert, wenn sich der Wert eines Kontrollkästchens oder von Umschalten auf **TRUE** ändert.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnUncheck**: Wie eine App reagiert, wenn sich der Wert eines Kontrollkästchens oder von Umschalten auf **FALSE** ändert.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**RailFill**: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **FALSE** ist, oder die Farbe der Linie auf der rechten Seite des Handles in einem Schieberegler-Steuerelement.

**RailHoverFill**: Wenn Sie auf das Umschalten-Steuerelement oder den Schieberegler zeigen: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **false** ist, oder die Farbe der Linie auf der rechten Seite des Handles in einem Schieberegler-Steuerelement.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**ShowLabel**: Gibt an, ob neben dem Umschalt-Steuerelement eine Textbezeichnung angezeigt werden soll.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**TextPosition**: Gibt an, ob sich die Bezeichnung links oder rechts neben dem Umschalt-Steuerelement befindet.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**TrueFill**: Die Füllfarbe der Umschaltfläche, wenn sie aktiviert ist.

**TrueHoverFill**: Die Hoverfüllfarbe der Umschaltfläche, wenn sie aktiviert ist.

**TrueText**: Der Text, der angezeigt wird, wenn die Umschaltfläche aktiviert ist.

**ValueFill**: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **true** ist, oder die Farbe der Linie auf der linken Seite des Handles in einem Schieberegler-Steuerelement.

**ValueHoverFill**: Wenn Sie mit dem Mauszeiger auf das Umschalten-Steuerelement oder den Schieberegler zeigen: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **TRUE** ist, oder die Farbe der Linie auf der linken Seite des Handles in einem Schieberegler-Steuerelement.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>Beispiel
1. Fügen Sie Umschalten hinzu, und nennen Sie es **MemberDiscount**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](properties-core.md)** auf diese Funktion fest:
   <br>**If(MemberDiscount.Value = true, "Preis: $75", "Preis: $100")**

    Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
3. Drücken Sie F5, und ändern Sie den Wert der **MemberDiscount**.

    Die Bezeichnung zeigt einen anderen Preis, je nachdem, ob **MemberDiscount** aktiviert oder deaktiviert ist.
4. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **HandleFill** und **FalseFill**
* **HandleFill** und **FalseHoverFill**
* **HandleFill** und **TrueFill**
* **HandleFill** und **TrueHoverFill**
* **FalseFill** und die Farbe außerhalb des Steuerelements
* **FalseHoverFill** und die Farbe außerhalb des Steuerelements
* **TrueFill** und die Farbe außerhalb des Steuerelements
* **TrueHoverFill** und Farbe außerhalb des Steuerelements

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.
* Die **FalseText**-Eigenschaft muss vorhanden sein.
* Die **TrueText**-Eigenschaft muss vorhanden sein.

### <a name="low-vision-support"></a>Unterstützte Anpassungen für Menschen mit Sehbehinderungen
* Sie sollten **ShowLabel** auf **TRUE** festlegen, damit Benutzer den Wert des Schalters schnell festlegen können.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
