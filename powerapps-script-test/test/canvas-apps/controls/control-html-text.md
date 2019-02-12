---
title: 'HTML-Textsteuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das HTML-Textsteuerelement
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
ms.openlocfilehash: d41ef04d3cd070373f6772bdfced029a7d09e244
ms.sourcegitcommit: ebd39753e2a0b60c1d8c016e38c00dd1accf5d0c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49307859"
---
# <a name="html-text-control-in-powerapps"></a>HTML-Textsteuerelement in PowerApps
Ein Feld, in dem Text angezeigt wird und in dem HTML-Tags in Textformatierungen konvertiert werden.

## <a name="description"></a>Beschreibung
In einem Steuerelement für **HTML-Text** werden nicht nur Klartext und Zahlen angezeigt, sondern auch HTML-Tags konvertiert, wie etwa geschützte Leerzeichen.

## <a name="key-properties"></a>Haupteigenschaften
**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**HtmlText**: Text, der in einem HTML-Textsteuerelement angezeigt wird und HTML-Tags enthalten kann.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[QuickInfo](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Find**( *FindString*, *WithinString* )](../functions/function-find.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, geben Sie ihm den Namen **Quelle**, und geben Sie als Wert für die **[Text](properties-core.md)**-Eigenschaft diese Zeichenfolge ein:

„\<p> Uns ist eine besonders \&nbsp; \&quot; weitreichende \&quot; Globalisierung und Lokalisierung gelungen.\<p>“

Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?

1. Fügen Sie ein **HTML-Text**-Steuerelement hinzu, und legen Sie die **HtmlText**-Eigenschaft auf diesen Wert fest:<br>
   **Source.Text**
   
     Das **HTML-Text**-Steuerelement zeigt denselben Text wie das **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) an. Allerdings werden Tags in die entsprechenden Zeichen umgewandelt.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
**HTML-Text** soll nicht interaktiv sein. Dieses Steuerelement sollte nur zum Anzeigen von Text verwendet werden.

### <a name="color-contrast"></a>Farbkontrast
Zwischen folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **[Color](properties-color-border.md)** und **[Fill](properties-color-border.md)**
* Text mit benutzerdefinierten Farben und dessen Hintergrund

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **HtmlText** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **HtmlText** sollte keine interaktiven Elemente wie `<button>`, `<a>` oder `<input>` enthalten. Das **[TabIndex](properties-accessibility.md)**-System in PowerApps ignoriert Elemente in **HtmlText**.
