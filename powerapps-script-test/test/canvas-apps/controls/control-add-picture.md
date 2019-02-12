---
title: 'Steuerelement „Bild hinzufügen“: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Steuerelement „Bild hinzufügen“
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
ms.openlocfilehash: 1cc2b7c1752abe4f12e76c30f59978fc753f4ac5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42835649"
---
# <a name="add-picture-control-in-powerapps"></a>Steuerelement „Bild hinzufügen“ in PowerApps
Nimmt ein Foto auf oder lädt Bilder vom lokalen Gerät.

## <a name="description"></a>Beschreibung
Mit diesem Steuerelement können die Benutzer Fotos aufnehmen oder Bilddateien von ihrem Gerät laden und die Datenquelle mit diesem Inhalt aktualisieren. Auf einem mobilen Gerät wird für den Benutzer das Auswahldialogfeld des Geräts angezeigt, in dem zwischen dem Aufnehmen eines Fotos und dem Auswählen eines bereits verfügbaren Fotos gewählt werden kann.

Bei dem Steuerelement handelt es sich um ein gruppiertes Steuerelement mit zwei weiteren Steuerelementen: ein **Bild** und eine **Medien hinzufügen**-Schaltfläche. Das **Bild**-Steuerelement zeigt das hochgeladene Bild bzw. (wenn kein Bild hochgeladen wurde) einen Platzhalter an. Über die Schaltfläche **Medien hinzufügen** werden Sie dazu aufgefordert, ein Bild hochzuladen.

Weitere Informationen zu den **Bild**-Eigenschaften erhalten Sie in der [Referenz zu dem Steuerelement „Bild“](control-image.md).

## <a name="add-media-button-properties"></a>Eigenschaften der Schaltfläche „Medien hinzufügen“
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben Sollte beschreiben, warum ein Bild hochgeladen werden soll.

**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**ChangePictureText**: Text, der angezeigt wird, wenn ein Bild hochgeladen wurde.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**Error** – Falls beim Hochladen eines Bilds ein Problem auftritt, enthält diese Eigenschaft eine entsprechende Fehlerzeichenfolge.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**Media**: Ein Bezeichner für den Clip, der von einem Audio- oder Video-Steuerelement wiedergegeben wird.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[Padding](properties-size-location.md)** – Der Abstand zwischen dem Text auf einer Import- oder Exportschaltfläche und den Rändern der Schaltfläche.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Text](properties-core.md)**: Text, der angezeigt wird, wenn kein Bild hochgeladen wurde.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[VerticalAlign](properties-text.md)** – Die Position des Texts in einem Steuerelement in Relation zur vertikalen Mitte des Steuerelements.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="examples"></a>Beispiele
### <a name="add-images-to-an-image-gallery-control"></a>Hinzufügen von Bildern zu einem Bildkatalog-Steuerelement
1. Fügen Sie ein **Bild hinzufügen**-Steuerelement hinzu, und klicken Sie dann dreimal darauf.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Klicken oder tippen Sie im Dialogfeld **Öffnen** auf eine Bilddatei, und klicken oder tippen Sie dann auf **Öffnen**.
3. Fügen Sie ein **[Schaltfläche](control-button.md)**-Steuerelement hinzu, verschieben Sie es unter das Steuerelement **Bild hinzufügen**, und legen Sie die **[OnSelect](properties-core.md)**-Eigenschaft für das **[Schaltfläche](control-button.md)**-Steuerelement auf die folgende Formel fest:<br>
   **Collect(MyPix, AddMediaButton1.Media)**
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
4. Fügen Sie ein **Bildkatalog**-Steuerelement hinzu, und legen Sie dessen **[Items](properties-core.md)**-Eigenschaft auf **MyPix** fest.
5. Drücken Sie F5, und klicken oder tippen Sie auf das **[Schaltfläche](control-button.md)**-Steuerelement.
   
    Das Bild aus dem **Bild hinzufügen**-Steuerelement wird im Steuerelement **Bildkatalog** angezeigt. Wenn das Bild nicht das gleiche Seitenverhältnis wie das **[Bild](control-image.md)**-Steuerelement im **Bildkatalog**-Steuerelement aufweist, legen Sie die **[ImagePosition](properties-visual.md)**-Eigenschaft des **[Bild](control-image.md)**-Steuerelements auf **Fit** fest.
6. Klicken oder tippen Sie auf das **Bild hinzufügen**-Steuerelement, auf eine andere Bilddatei, auf **Öffnen** und dann auf das hinzugefügte **[Schaltfläche](control-button.md)**-Steuerelement.
   
    Das zweite Bild wird im **Bildkatalog**-Steuerelement angezeigt.
7. (optional) Wiederholen Sie den vorherigen Schritt beliebig oft, und kehren Sie dann zurück zum Standardarbeitsbereich, indem Sie ESC drücken.

Verwenden Sie die **[SaveData](../functions/function-savedata-loaddata.md)**-Funktion, um die Bilder lokal zu speichern, oder die **[Patch](../functions/function-patch.md)**-Funktion, um eine Datenquelle zu aktualisieren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
Es gelten für die **[Schaltfläche](control-button.md)** und das **[Bild](control-image.md)** dieselben Richtlinien. Ziehen Sie außerdem Folgendes in Betracht:

### <a name="color-contrast"></a>Farbkontrast
* Der Farbkontrast zwischen dem Text und dem Hintergrund der Schaltfläche **Medien hinzufügen** muss angemessen sein. Da die Farben des hochgeladenen Bilds unterschiedlich sein können, sollte die **[Füllfarbe](properties-color-border.md)** auf der Schaltfläche **Medien hinzufügen** undurchsichtig sein, damit der Kontrast immer gleich hoch ist.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Die Schaltfläche **Medien hinzufügen** muss die Eigenschaften **Text** und **ChangePictureText** aufweisen, über die der Benutzer aufgefordert wird, ein Bild hinzuzufügen oder zu ändern.

### <a name="keyboard-support"></a>Tastaturunterstützung
* Für die Schaltfläche **Medien hinzufügen** muss **[TabIndex](properties-accessibility.md)** gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Die Schaltfläche **Medien hinzufügen** muss für Fokusindikatoren deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
 
