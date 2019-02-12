---
title: 'Kamera-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Kamera-Steuerelement
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
ms.openlocfilehash: bffbc86dda86c0b179634d2f59e0fb4f5d063ecd
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42842622"
---
# <a name="camera-control-in-powerapps"></a>Kamera-Steuerelement in PowerApps
Ein Steuerelement, mit dem der Benutzer mithilfe der Kamera des Geräts Fotos aufnehmen kann.

## <a name="description"></a>Beschreibung
Wenn Sie dieses Steuerelement hinzufügen, kann der Benutzer eine Datenquelle mit einem oder mehreren Fotos vom aktuellen Ort, an dem die App ausgeführt wird, aktualisieren.

## <a name="key-properties"></a>Haupteigenschaften
**Camera** – Auf einem Gerät mit mehreren Kameras ist dies die ID der von der App verwendeten Kamera.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben Sollte beschreiben, warum ein Bild aufgenommen werden soll.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**Brightness** – Bestimmt die Helligkeit, die von einem Benutzer voraussichtlich im Bild wahrgenommen wird.

**Contrast** – Gibt an, wie leicht ähnliche Farben in einem Bild für den Benutzer voneinander zu unterscheiden sind.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnStream** – Legt fest, wie die App reagiert, wenn die **Stream**-Eigenschaft aktualisiert wird.

**Photo** – Das Bild, das aufgenommen wird, wenn der Benutzer ein Foto macht.

**Stream** – Das automatisch entsprechend der **StreamRate**-Eigenschaft aktualisierte Bild.

**StreamRate** – Gibt an, wie oft das Bild in der **Stream**-Eigenschaft aktualisiert wird (in Millisekunden).  Dieser Wert kann zwischen 100 (einer Zehntelsekunde) und 3.600.000 (eine Stunde) liegen.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Beispiel
### <a name="add-photos-to-an-image-gallery-control"></a>Hinzufügen von Fotos zu einem Bildkatalog-Steuerelement
1. Fügen Sie ein **Kamera**-Steuerelement hinzu, benennen Sie es **MyCamera**, und legen Sie dessen **[OnSelect](properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>
   **Collect(MyPix, MyCamera.Photo)**

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?

    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
2. Drücken Sie F5, und nehmen Sie dann ein Foto auf, indem Sie auf **MyCamera** klicken oder tippen.
3. Fügen Sie ein **[vertikaler Katalog](control-gallery.md)**-Steuerelement hinzu, und passen Sie dann die Größe des zugehörigen **[Bild](control-image.md)**-Steuerelements, seiner Vorlage und des **Bildkatalog**-Steuerelements so an, dass sie den Bildschirm ausfüllen.
4. Legen Sie die **[Items](properties-core.md)**-Eigenschaft des **Bildkatalog**-Steuerelements auf den folgenden Ausdruck fest:<br>**MyPix**.
5. Legen Sie die **[Image](properties-visual.md)**-Eigenschaft des **Bild**-Steuerelements im Katalog auf den folgenden Ausdruck fest:<br>
   **ThisItem.Url**

    Das aufgenommene Foto wird im **Bildkatalog**-Steuerelement angezeigt.
6. Machen Sie beliebig viele Fotos, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.
7. (optional) Legen Sie die **OnSelect**-Eigenschaft des **Bild**-Steuerelements im **Bildkatalog**-Steuerelement auf **Remove(MyPix, ThisItem)** fest, drücken Sie F5, und klicken oder tippen Sie dann auf ein Foto, um dieses zu entfernen.

Verwenden Sie die **[SaveData](../functions/function-savedata-loaddata.md)**-Funktion, um die Fotos lokal zu speichern, oder die **[Patch](../functions/function-patch.md)**-Funktion, um eine Datenquelle zu aktualisieren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
Das gesamte Steuerelement „Kamera“ zeigt nicht nur den Kamerafeed an, sondern dient auch als Schaltfläche, die Bilder aufnimmt. Daher gelten ähnliche Aspekte im Hinblick auf die Barrierefreiheit wie bei Schaltflächen.

### <a name="video-alternatives"></a>Videoalternativen
* Sie sollten eine alternative Eingabemöglichkeit für Benutzer hinzufügen, die eine Sehbehinderung haben. Sie können z.B. die Option **[Bild hinzufügen](control-add-picture.md)** hinzufügen, damit Benutzer ein Bild auf Ihrem Gerät hochladen können.

### <a name="color-contrast"></a>Farbkontrast
Zwischen folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **[FocusedBorderColor](properties-color-border.md)** und die äußere Farbe

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
