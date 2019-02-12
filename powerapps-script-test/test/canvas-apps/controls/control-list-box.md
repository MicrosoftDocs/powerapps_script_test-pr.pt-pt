---
title: 'Listenfeld-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Listenfeld-Steuerelement
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
ms.openlocfilehash: a2cb87cf68457771605e78970b8d7a923af61fce
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42835170"
---
# <a name="list-box-control-in-powerapps"></a>Listenfeld-Steuerelement in PowerApps
Eine Liste, in der der Benutzer ein oder mehrere Elemente auswählen kann

## <a name="description"></a>Beschreibung
Ein **Listenfeld**-Steuerelement zeigt immer alle verfügbare Optionen an (im Gegensatz zu einem **[Dropdown](control-drop-down.md)**-Steuerelement), wobei der Benutzer mehr als ein Element gleichzeitig auswählen kann (im Gegensatz zu einem **[Optionsfeld](control-radio.md)**-Steuerelement).

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)** – Der Anfangswert eines Steuerelements, bevor es vom Benutzer geändert wird.

**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

Wenn Sie einen Katalog, eine Liste oder ein Diagramm hinzufügen, zeigt die Eigenschaftenliste standardmäßig **Items** an, sodass Sie ganz einfach die Daten angeben können, die das neue Steuerelement anzeigen soll. Sie können zum Beispiel die **Items**-Eigenschaft eines Katalogs auf die **Account**-Tabelle in Salesforce festlegen, eine Tabelle mit dem Namen **Inventory**, die Sie in Excel erstellt und in die Cloud hochgeladen haben, oder auf eine SharePoint-Liste mit dem Namen **ConferenceSpeakers**.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

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

**ItemPaddingLeft**: gibt den Abstand zwischen Text in einem Listenfeld und dem linken Rand an.

**[LineHeight](properties-text.md)**: Der Abstand zwischen Elementen, z.B. Textzeilen oder Elementen in einer Liste.

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

**[SelectionFill](properties-color-border.md)** : gibt die Hintergrundfarbe der ausgewählten Elemente in einer Liste oder eines ausgewählten Bereichs des Stift-Steuerelements an.

**SelectMultiple**: gibt an, ob ein Benutzer mehr als ein Element in einem Listenfeld auswählen kann.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein **Listenfeld**-Steuerungselement hinzu, nennen Sie es **CategoryList**, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf folgende Formel fest:<br>
   **["Carpet","Hardwood","Tile"]**
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
   
    ![Kategorien für den Bodenbelag im Listenfeld](./media/control-list-box/category-listbox.png)
2. Fügen Sie drei **[Dropdown](control-drop-down.md)**-Steuerelemente hinzu, verschieben Sie sie unter **CategoryList**, und nennen Sie diese **CarpetList**, **HardwoodList** und **TileList**.
3. Legen Sie die **[Items](properties-core.md)**-Eigenschaft jedes **[Dropdown](control-drop-down.md)**-Steuerelements auf einen der folgenden Werte fest:
   
   * CarpetList: **["Caserta Stone Beige", "Ageless Beauty Clay", "Lush II Tundra"]**
   * HardwoodList: **["Golden Teak","Natural Hickory", "Victoria Mahogany"]**
   * TileList: **["Honey Onyx Marble","Indian Autumn Slate", "Panaria Vitality Ceramic"]**
     
     ![Bezeichnungen der Bodenbeläge in Dropdownlisten](./media/control-list-box/flooring-names.png)
4. Legen Sie die **[Visible](properties-core.md)**-Eigenschaft jedes **[Dropdown](control-drop-down.md)** -Steuerelements auf einen der folgenden Werte fest:
   
   * CarpetList: **If("Carpet" in CategoryList.SelectedItems.Value, true)**
   * HardwoodList: **If("Hardwood" in CategoryList.SelectedItems.Value, true)**
   * TileList: **If("Tile" in CategoryList.SelectedItems.Value, true)**
     
     Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
5. Drücken Sie F5, und wählen Sie ein oder mehrere Elemente in **CategoryList** aus.
   
    Die entsprechenden  **[Dropdown](control-drop-down.md)**-Steuerelemente werden entsprechend Ihrer Wahl oder Ihren Optionen angezeigt.
   
    ![Bezeichnungen der Bodenbeläge in Dropdownlisten](./media/control-list-box/selected-lists.png)
6. (optional) Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **SelectionColor** und **SelectionFill**
* **SelectionFill** und **[Fill](properties-color-border.md)**
* **[HoverFill](properties-color-border.md)** und **[Fill](properties-color-border.md)**
* **[PressedFill](properties-color-border.md)** und **[Fill](properties-color-border.md)**

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.

    > [!NOTE]
  > Über die TAB-TASTE können Sie zum **Listenfeld** navigieren oder dieses schließen. Über die Pfeiltasten können Sie durch die Inhalte des **Listenfelds** navigieren.
