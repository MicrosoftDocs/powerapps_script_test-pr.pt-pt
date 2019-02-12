---
title: 'Steuerelement für Bewertungen: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Steuerelement für Bewertungen
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
ms.openlocfilehash: 1979ad63ce9cd5fbe3f3a9a3fa5a56df5e80966e
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42830869"
---
# <a name="rating-control-in-powerapps"></a>Steuerelement für Bewertungen in PowerApps
Ein Steuerelement, mit dem Benutzer einen Wert zwischen 1 und einer maximalen Anzahl, die Sie festlegen, angeben können.

## <a name="description"></a>Beschreibung
Mit diesem Steuerelement kann der Benutzer z.B. angeben, wie gut ihm etwas gefallen hat, indem er eine bestimmte Anzahl von Sternen auswählt.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)**: Der Anfangswert eines Steuerelements, bevor er vom Benutzer geändert wird.

**Max**: Der maximale Wert, auf den der Benutzer einen Schieberegler oder eine Bewertung festlegen kann.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**RatingFill**: Die Farbe der Sterne in einem Steuerelement für Bewertungen.

**ReadOnly**: Gibt an, ob ein Benutzer den Wert eines Schiebereglers oder eines Bewertung-Steuerelements ändern kann.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**ShowValue**: Gibt an, ob ein Wert des Schiebereglers oder der Bewertung angezeigt wird, wenn der Benutzer diesen Wert ändert oder auf das Steuerelement zeigt.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Average**( *Value1*, *Value2,* ... )](../functions/function-aggregates.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein Steuerelement **Rating** hinzu, und nennen Sie es **Quantitative**.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein Steuerelement **[Text input](control-text-input.md)** hinzu, nennen Sie es **Qualitative**, und verschieben Sie es unter das Steuerelement **Rating**.
3. Legen Sie die Eigenschaft **[Default](properties-core.md)** des Steuerelements **[Text input](control-text-input.md)** auf **""** fest, und legen Sie sein **HintText** auf diese Formel fest:
   <br>**If(Quantitative.Value > 3, „Was hat Ihnen besonders gefallen?“, „Wie können wir es besser machen?“)**
   
    Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
4. Drücken Sie F5, und klicken oder tippen Sie anschließend auf entweder vier oder fünf Sterne im Steuerelement **Rating** (Bewertung).
   
    Der Hinweistext im Steuerelement **[Text input](control-text-input.md)** wird geändert, um die hohe Bewertung zu reflektieren.
5. Klicken oder tippen Sie in **Quantitative** auf weniger als vier Sterne.
   
    Der Hinweistext im Steuerelement **[Text input](control-text-input.md)** wird geändert, um die niedrige Bewertung zu reflektieren.
6. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **RatingFill** und **[Fill](properties-color-border.md)**

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

    > [!NOTE]
  > Das **Bewertungs**-Steuerelement wird von der Sprachausgabe wie ein Optionsfeld behandelt.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
* Wenn es zu viele Sterne gibt, sollten Sie ein anderes Steuerelement verwenden. Die Navigation mit der Tastatur kann mühsam sein, und bei einem Touchscreen ist es kompliziert, eine genaue Auswahl zu treffen.

    > [!NOTE]
  > Für das**Bewertungs**-Steuerelement können die gleichen Tastenkombinationen wie für Optionsfelder verwendet werden.
