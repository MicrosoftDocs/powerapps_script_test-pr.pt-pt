---
title: 'Barcodescanner-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Barcodescanner-Steuerelement
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
ms.openlocfilehash: 853558273521491467fa7474688ce9c984ac5db6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862466"
---
# <a name="barcode-scanner-control-experimental-in-powerapps"></a>Barcodescanner-Steuerelement in PowerApps (experimentell)
Ein experimentelles Steuerelement, mit dem der Benutzer mithilfe des Barcodescanners auf seinem Gerät Fotos aufnehmen kann.

## <a name="description"></a>Beschreibung
Wenn Sie dieses Steuerelement hinzufügen, kann der Benutzer eine Datenquelle mit einem oder mehreren Fotos vom aktuellen Ort, an dem die App ausgeführt wird, aktualisieren.

## <a name="key-properties"></a>Haupteigenschaften
**barcode scanner** – Auf einem Gerät mit mehreren Barcodescannern die numerische ID des von der App verwendeten Barcodescanners.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**ShowLiveBarcodeDetection**: legt fest, ob visuelle Anhaltpunkte dargestellt werden, um den Status der Barcodeerkennung zu ermitteln. Gelbe Rechtecke stellen die Bereiche dar, die untersucht werden. Eine grüne Linie, die durch das Rechteck geht, zeigt an, dass die Barcodeerkennung erfolgreich war.

**Stream** – Das automatisch entsprechend der **StreamRate**-Eigenschaft aktualisierte Bild.

**StreamRate** – Gibt an, wie oft das Bild in der **Stream**-Eigenschaft aktualisiert wird (in Millisekunden).  Dieser Wert kann zwischen 100 (einer Zehntelsekunde) und 3.600.000 (eine Stunde) liegen.

**Text**: Barcodewert, der vom Scanner zuletzt erkannt wurde.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Beispiel
### <a name="add-photos-to-an-image-gallery-control"></a>Hinzufügen von Fotos zu einem Bildkatalog-Steuerelement
1. Fügen Sie ein **Barcodescanner**-Steuerelement hinzu, und benennen Sie es **Mybarcode scanner**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein **Bezeichnungs**-Steuerelement hinzu, und legen Sie dessen Ausgabe auf den **Text** des Barcodes fest.  
3. Scannen Sie einen Barcode des in der BarcodeType-Eigenschaft festgelegten Typs.
4. In der Bezeichnung wird der gescannte Barcode angezeigt.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="video-alternatives"></a>Videoalternativen
* Sie sollten eine **[Bezeichnung](control-text-box.md)** hinzufügen, deren **[Text](properties-core.md)** auf den **Text** des Barcodescanners festgelegt ist. Da der Barcodescanner nicht den ermittelten Barcodewert anzeigt, kann jeder Benutzer den Scanner verwenden und nicht nur Benutzer mit Sehbehinderung.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

    > [!NOTE]
  > Die Sprachausgabe meldet, wenn ein neuer Barcode gefunden wurde. Der Wert wird jedoch nicht genannt. Solange der Barcode angezeigt wird, erinnert die Sprachausgabe alle 5 Sekunden daran, dass immer noch derselbe Barcode ermittelt wird.
