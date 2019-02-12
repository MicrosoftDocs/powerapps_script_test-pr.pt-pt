---
title: 'Bildkatalog-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Bildkatalog-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/25/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 710bc4a11e4de9921e0efa077cb0e18f58f09cb5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42831502"
---
# <a name="gallery-control-in-powerapps"></a>Bildkatalog-Steuerelement in PowerApps
Ein Steuerelement, das andere Steuerelemente enthält und einen Datensatz anzeigt.

## <a name="description"></a>Beschreibung
Ein **Bildkatalog**-Steuerelement kann mehrere Datensätze aus einer Datenquelle darstellen. Jeder Datensatz kann mehrere Datentypen enthalten. Ein **Bildkatalog**-Steuerelement kann beispielsweise mehrere Kontakte darstellen, wobei jedes Element Kontaktdaten wie den Namen, eine Adresse und eine Telefonnummer umfasst. Jedes Datenfeld wird in einem eigenen Steuerelement innerhalb des **Bildkatalog**-Steuerelements angezeigt. Sie können diese Steuerelemente mithilfe dieser Vorlage konfigurieren. Die Vorlage wird im Bildkatalog als erstes Element angezeigt. Sie finden sie am linken Rand des **Bildkatalog**-Steuerelements (Querformat bzw. horizontale Ausrichtung) bzw. an der Oberseite des **Bildkatalog**-Steuerelements (Hochformat bzw. vertikale Ausrichtung). Änderungen an der Vorlage beziehen sich auf das **Bildkatalog**-Steuerelement insgesamt.

Es stehen vordefinierte Bildkatalog-Vorlagen für die Darstellung von Bildern, von Text und von Elementen mit unterschiedlicher Höhe zur Verfügung.

## <a name="key-properties"></a>Haupteigenschaften
**[Default:](properties-core.md)** Das Element oder der Datensatz aus der Datenquelle, das bzw. der beim Starten der App im Katalog ausgewählt werden soll.

**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**Selected** – Das ausgewählte Element.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben Sollte die Elementliste beschreiben.

**AllItems** – Alle Elemente eines Katalogs, einschließlich zusätzlicher Steuerelementwerte, die Teil der Vorlage des Katalogs sind.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**Layout** – Gibt an, ob der Benutzer in einem Katalog scrollen oder einen Schieberegler von oben nach unten (**Vertical**) oder von links nach rechts (**Horizontal**) verschieben muss.

**NavigationStep** – Gibt an, wie weit in einem Katalog gescrollt werden kann, wenn die **ShowNavigation**-Eigenschaft auf **true** festgelegt ist und der Benutzer am Ende des Katalogs jeweils einen Navigationspfeil verwendet.

**ShowNavigation** – Gibt an, ob in einem Katalog an beiden Enden ein Pfeil angezeigt wird, damit Benutzer durch die Elemente scrollen können, indem Sie auf einen Pfeil klicken oder tippen.

**ShowScrollbar** – Gibt an, ob eine Bildlaufleiste angezeigt wird, wenn Benutzer auf einen Katalog zeigen.

**Snap** – Gibt an, ob in einem Katalog ein automatischer Sprung zum nächsten vollständigen Element durchgeführt wird, wenn Benutzer durch den Katalog scrollen.

**TemplateFill** – Die Hintergrundfarbe eines Katalogs.

**TemplatePadding** – Der Abstand zwischen den Elementen eines Katalogs.

**TemplateSize** – Die Höhe der Vorlage für einen Katalog im Hochformat (vertikal) bzw. die Breite der Vorlage für einen Katalog im Querformat (horizontal).

**Transition** – Der visuelle Effekt (**Pop**, **Push** oder **None**), wenn Benutzer im Katalog auf ein Element zeigen.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**WrapCount** – Die Anzahl der in einer Zeile oder Spalte angezeigten Elemente (je nachdem, ob ein horizontales oder vertikales Layout verwendet wird).

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Filter**( *DataSource*, *Formula* )](../functions/function-filter-lookup.md)

## <a name="examples"></a>Beispiele
### <a name="show-and-filter-data"></a>Anzeigen und Filtern von Daten
* [Anzeigen von Text](control-text-box.md#show-data-in-a-gallery)
* [Anzeigen von Bildern](control-image.md#show-a-set-of-images-from-a-data-source)
* [Filtern von Daten mithilfe einer Listenoption](control-drop-down.md#example)
* [Filtern von Daten mithilfe eines Schiebereglers](control-slider.md#example)

### <a name="get-data-from-the-user"></a>Abrufen von Daten eines Benutzers
* [Abrufen von Text](control-text-input.md#collect-data)
* [Abrufen von Bildern](control-add-picture.md#add-images-to-an-image-gallery-control)
* [Abrufen von Fotos](control-camera.md#example)
* [Abrufen von Tönen](control-microphone.md#example)
* [Abrufen von Zeichnungen](control-pen-input.md#create-a-set-of-images)


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Wenn ein Katalogelement aktiviert wird, indem man auf eine beliebige Stelle klickt, muss zwischen den folgenden Elementen ein angemessener Farbkontrast vorhanden sein:
* Zwischen **[BorderColor](properties-color-border.md)** und der Farbe außerhalb des Katalogs, wenn es einen Rahmen gibt
* Zwischen **[Fill](properties-color-border.md)** und der Farbe außerhalb des Katalogs, wenn es keinen Rahmen gibt

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

    > [!NOTE]
  > Die Sprachausgabe meldet, wenn Elemente im Katalog verändert werden. **AccessibleLabel** wird ebenfalls erwähnt. Dadurch wird die Meldung in einen Kontext gesetzt und hat eine noch wichtigere Funktion, wenn mehrere Kataloge gleichzeitig angezeigt werden.

### <a name="keyboard-support"></a>Tastaturunterstützung
* Sie sollten **ShowScrollbar** auf **TRUE** festlegen. Auf den meisten Geräten mit Touchscreen wird die Scrollleiste erst angezeigt, wenn der Benutzer mit dem Scrollen beginnt.
* Wenn ein Katalogelement aktiviert wird, indem man auf eine beliebige Stelle klickt, muss es auch eine Möglichkeit für Tastaturbenutzer geben, dieses Katalogelement auszuwählen. Sie können z.B. eine **[Schaltfläche](control-button.md)** hinzufügen, für die die **OnSelect**-Eigenschaft auf **Select(Parent)** festgelegt ist.

    > [!NOTE]
  > Steuerelemente, die sich außerhalb des Katalogs befinden, werden nicht in der Reihenfolge der Tastaturnavigation innerhalb des Katalogs abgefragt. Die **[TabIndex](properties-accessibility.md)**-Eigenschaft von Steuerelementen innerhalb eines Katalogs ist eingeschränkt. Weitere Informationen finden Sie unter [Eigenschaften von Bedienungshilfen in PowerApps](properties-accessibility.md).
