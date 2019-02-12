---
title: 'Image-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Image-Steuerelement
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
ms.openlocfilehash: d5765c1e425a3196b5e560bb621f391d36f6580c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42841591"
---
# <a name="image-control-in-powerapps"></a>Image-Steuerelement in PowerApps
Ein Steuerelement, das ein Image aus einer lokalen Datei oder einer Datenquelle anzeigt

## <a name="description"></a>Beschreibung
Wenn Sie ein oder mehrere **Image**-Steuerelemente in Ihrer App hinzufügen, können Sie einzelne Images, die nicht Teil eines Datensatzes sind, anzeigen oder Images von Datensätzen in Datenquellen integrieren.

## <a name="key-properties"></a>Haupteigenschaften
**[Image](properties-visual.md)** : der Name des Images, das in einem Image-, Audio- oder Mikrofon-Steuerelement angezeigt wird

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**ApplyEXIFOrientation**: Gibt an, ob Ausrichtung, die in den im Bild eingebetteten EXIF-Daten angegeben ist, automatisch angewendet wird.

**AutoDisableOnSelect**: Deaktiviert das Steuerelement automatisch, während das OnSelect-Verhalten ausgeführt wird.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**CalculateOriginalDimensions**: aktiviert die **OriginalHeight** und **OriginalWidth**-Eigenschaften.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**FlipHorizontal**: Gibt an, ob das Bild vor der Anzeige horizontal gekippt werden soll.

**FlipVertical**: Gibt an, ob das Bild vor der Anzeige vertikal gekippt werden soll.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[ImagePosition](properties-visual.md)**: Die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Bilds auf einem Bildschirm oder in einem Steuerelement, wenn die Größe nicht mit der Bildgröße identisch ist.

**ImageRotation**: Gibt an, wie das Bild vor der Anzeige gedreht werden soll.  Zulässige Werte sind „none“, „clockwise (CW) 90 degrees“, „counter-clockwise (CCW) 90 degrees“ und „clockwise 180 degrees“.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OriginalHeight**: gibt die ursprüngliche Höhe eines Images an, wobei die **CalculateOriginalDimensions**-Eigenschaft aktiviert ist.

**OriginalWidth**: gibt die ursprüngliche Breite eines Images an, wobei die **CalculateOriginalDimensions**-Eigenschaft aktiviert ist.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[RadiusBottomLeft](properties-size-location.md)** – Der Grad der Rundung der linken unteren Ecke eines Steuerelements.

**[RadiusBottomRight](properties-size-location.md)** – Der Grad der Rundung der rechten unteren Ecke eines Steuerelements.

**[RadiusTopLeft](properties-size-location.md)** – Der Grad der Rundung der linken oberen Ecke eines Steuerelements.

**[RadiusTopRight](properties-size-location.md)** – Der Grad der Rundung der rechten oberen Ecke eines Steuerelements.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**Transparency**: gibt an, inwieweit Steuerelemente hinter einem Bild sichtbar bleiben.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Remove**( *DataSource*, ThisItem)](../functions/function-remove-removeif.md)

## <a name="examples"></a>Beispiele
### <a name="show-an-image-from-a-local-file"></a>Anzeigen eines Images aus einer lokalen Datei
1. Klicken oder tippen Sie im Menü **File** (Datei) auf die Option **Media** (Medien), und klicken oder tippen Sie anschließend auf **Browse** (Durchsuchen).
2. Klicken oder tippen Sie auf die Image-Datei, die Sie hinzufügen möchten, und klicken oder tippen Sie auf **Open** (Öffnen). Drücken Sie anschließend ESC, um in den Standardarbeitsbereich zurückzukehren.
3. Fügen Sie ein **Image**-Steuerelement hinzu, und legen Sie dessen **Image**-Eigenschaft auf den Namen der Datei fest, die Sie hinzugefügt haben.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

    Das **Image**-Steuerelement zeigt das von Ihnen angegebene Image an.

### <a name="show-a-set-of-images-from-a-data-source"></a>Anzeigen eines Satzes von Images aus einer Datenquelle
1. Laden Sie diese [Excel-Datei](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) herunter, und speichern Sie sie auf Ihrem lokalen Gerät.
2. Erstellen oder öffnen Sie in PowerApps Studio eine App, und klicken oder tippen Sie dann im rechten Bereich auf **Datenquelle hinzufügen**.

    Wenn im rechten Bereich **Datenquelle hinzufügen** nicht angezeigt wird, klicken oder tippen Sie auf der linken Navigationsleiste auf einen beliebigen Bildschirm.
3. Klicken oder tippen Sie auf **Add static data to your app** (Statische Daten zu Ihrer App hinzufügen), klicken oder tippen Sie auf die Excel-Datei, die Sie heruntergeladen haben, und klicken oder tippen Sie anschließend auf **Open** (Öffnen).
4. Aktivieren Sie das Kontrollkästchen **Flooring Estimates** (Kostenschätzungen für Bodenbeläge), und klicken oder tippen Sie auf **Connect** (Verbinden).
5. Fügen Sie ein **Katalog**-Steuerelement mit Bildern hinzu, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf **FlooringEstimates** (Kostenschätzungen für Bodenbeläge) fest.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

    Das **Katalog**-Steuerelement zeigt Bilder von Teppich-, Parkett- und Fliesenprodukten auf Basis von Links in der von Ihnen heruntergeladenen Excel-Datei.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
* Es gelten die [Standardanforderungen für Farbkontraste](../accessible-apps-color.md), wenn die Grafik als Schaltfläche verwendet wird.
* Prüfen Sie ggf. auf Kontrastprobleme im Bild, wenn es nicht nur dekorativen Zwecken dient.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein, wenn die Grafik als Schaltfläche oder zumindest nicht nur der Dekoration dient.
* **[AccessibleLabel](properties-accessibility.md)** muss leer sein oder der leeren Zeichenfolge **""** entsprechen, wenn die Grafik ausschließlich Dekoration ist. Dadurch wird die Grafik von der Sprachausgabe ignoriert.
* **[AccessibleLabel](properties-accessibility.md)** kann leer sein oder der leeren Zeichenfolge **""** entsprechen, falls die Grafik redundante Informationen enthält.
  * Beispiel: Ein **Bild** mit Zahnrädern, für das **[AccessibleLabel](properties-accessibility.md)** auf **Einstellungen** festgelegt ist und das nicht als Schaltfläche verwendet wird. Es befindet sich stattdessen neben einer **[Bezeichnung](control-text-box.md)**, die ebenfalls **Einstellungen** lautet. Sprachausgaben lesen das Bild als **Einstellungen** und die Bezeichnung auch als **Einstellungen**. Dies ist zu ausführlich. In diesem Fall benötigt das **Bild** kein **[AccessibleLabel](properties-accessibility.md)**.

    > [!IMPORTANT]
    > Sprachausgaben lesen alle **Bilder**, deren **[TabIndex](properties-accessibility.md)** 0 (null) oder größer entspricht, selbst wenn **[AccessibleLabel](properties-accessibility.md)** leer ist. Dies liegt daran, dass sie als Schaltflächen gerendert werden. Wenn kein **[AccessibleLabel](properties-accessibility.md)** bereitgestellt wird, lesen Sprachausgaben die Grafik als **Schaltfläche**.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss 0 (null) oder größer sein, wenn die Grafik als Schaltfläche verwendet wird. So können Benutzer über die Tastatur dorthin navigieren.
* Fokusindikatoren müssen übersichtlich angezeigt werden, wenn die Grafik als Schaltfläche verwendet wird. Mithilfe von **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Sie dies archivieren.

    > [!NOTE]
  > Wenn **[TabIndex](properties-accessibility.md)** 0 (null) oder größer ist, wird das **Bild** als Schaltfläche gerendert. Dadurch erfolgt keine Änderung der visuellen Darstellung. Die Sprachausgabe erkennt das Bild jedoch richtig als Schaltfläche. Ist **[TabIndex](properties-accessibility.md)** weniger als 0 (null), wird das **Bild** als solches erkannt.
