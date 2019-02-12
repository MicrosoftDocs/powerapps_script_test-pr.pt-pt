---
title: 'Dropdown-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen über das Dropdown-Steuerelement, einschließlich Eigenschaften und Beispielen
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
ms.openlocfilehash: f5e4e0ad13280783b7b6cd00121b4dc05cca6df8
ms.sourcegitcommit: e4fe4b27651b62edb67e5995fc5955577d8ac5b8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075378"
---
# <a name="drop-down-control-in-powerapps"></a>Dropdown-Steuerelement in PowerApps
Eine Liste, die nur das erste Element anzeigt, bis der Benutzer sie öffnet.

## <a name="description"></a>Beschreibung
Ein **Dropdown**-Steuerelement ist platzsparend und eignet sich besonders für umfangreiche Listen. Das Steuerelement beansprucht nur eine Zeile, bis der Benutzer den Abwärtspfeil auswählt, um weitere Optionen einzublenden.  Das Steuerelement zeigt maximal 500 Elemente an.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)**: Der Anfangswert eines Steuerelements, bevor der Benutzer einen anderen Wert angibt.

**[Items](properties-core.md)**: Die Datenquelle, welche die im Steuerelement angezeigten Elemente enthält. Wenn die Quelle mehrere Spalten besitzt, stellen Sie die **Value**-Eigenschaft des Steuerelements auf die Datenspalte ein, die Sie anzeigen möchten.
  
**Value**: Die Datenspalte, die Sie im Steuerelement anzeigen möchten (z.B., wenn eine Datenquelle mehrere Spalten besitzt).

**Selected**: Das ausgewählte Element.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**ChevronBackground** – Die Farbe im Hintergrund des Abwärtspfeils einer Dropdownliste.

**ChevronFill** – Die Farbe des Abwärtspfeils in einer Dropdownliste.

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

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**[SelectionColor](properties-color-border.md)**: Die Textfarbe des ausgewählten Elements oder der Elemente in einer Liste oder die Farbe des Auswahltools in einem Stift-Steuerelement.

**[SelectionFill](properties-color-border.md)** – Die Hintergrundfarbe des ausgewählten Elements oder der Elemente in einer Liste oder eines ausgewählten Bereichs eines Stift-Steuerelements.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel

### <a name="simple-list"></a>Einfache Liste

1. Fügen Sie ein **Dropdown**-Steuerelement hinzu, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf diesen Ausdruck fest:

    ```["Seattle", "Tokyo", "London", "Johannesburg", "Rio de Janeiro"]```

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?

1. Zeigen Sie die Elemente in der Liste an, indem Sie auf den Abwärtspfeil des Steuerelements klicken und gleichzeitig die ALT-Taste drücken.

### <a name="list-from-a-data-source"></a>Liste aus einer Datenquelle
Die Prinzipien in diesem Verfahren gelten für jede [Datenquelle, die Tabellen enthält (data source that provides tables)](../connections-list.md#tables). Um diese Schritte jedoch genau auszuführen, müssen Sie eine Umgebung öffnen, für die eine Datenbank für Common Data Service für Apps erstellt wurde und Beispieldaten hinzugefügt wurden.

1. [Öffnen einer leeren App](../data-platform-create-app-scratch.md#open-a-blank-app) (Open a blank app), dann [Angeben des **(specify the )** Elements](../data-platform-create-app-scratch.md#specify-an-entity) (entity) des Kontos.

1. Fügen Sie ein **Dropdown**-Steuerelement hinzu, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf diese Formel fest:

    ```Distinct(Accounts, address1_city)```

    Diese Formel zeigt alle Städte in dem Element **Konten** (Accounts) an. Wenn mehr als ein Datensatz die gleiche Stadt besitzt, versteckt die **[Distinct](../functions/function-distinct.md)**-Funktion die Duplizierung in Ihrem Dropdown-Steuerelement.

1. (optional) Benennen Sie Ihr **Dropdown**-Steuerelement in **Cities** (Städte) um, fügen Sie ein vertikales **Gallery**-Steuerelement (Katalog) hinzu, und legen Sie die **[Items](properties-core.md)**-Eigenschaft des Katalogs auf diese Formel fest:

    ```Filter(Accounts, address1_city = Cities.Selected.Value)```

    Diese **[Filter](../functions/function-filter-lookup.md)**-Funktion zeigt nur die Datensätze im **Accounts**-Element (Konten) an, bei denen die Stadt zu dem ausgewählten Wert im Steuerelement **Cities** (Städte) passt.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **ChevronFill** und **ChevronBackground**
* **ChevronHoverFill** und **ChevronHoverBackground**
* **SelectionColor** und **SelectionFill**
* **SelectionFill** und **[Fill](properties-color-border.md)**

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
