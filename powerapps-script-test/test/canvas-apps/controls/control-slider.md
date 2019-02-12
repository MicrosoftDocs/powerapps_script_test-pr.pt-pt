---
title: 'Schieberegler-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Schieberegler-Steuerelement
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
ms.openlocfilehash: 198275ef72129b17cbf73a5f4eb47fd342de3b24
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42830734"
---
# <a name="slider-control-in-powerapps"></a>Schieberegler-Steuerelement in PowerApps
Ein Steuerelement, mit dem der Benutzer durch Ziehen eines Handles einen Wert angeben kann

## <a name="description"></a>Beschreibung
Der Benutzer kann einen Wert zwischen einem Mindest- und einem Höchstwert eingeben. Ziehen Sie dazu den Handle des Schiebereglers von links nach rechts oder von unten nach oben, je nach ausgewählter Richtung.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)**: Der Anfangswert eines Steuerelements, bevor er vom Benutzer geändert wird.

**Max**: Der maximale Wert, auf den der Benutzer einen Schieberegler oder eine Bewertung festlegen kann.

**Min**: gibt den Mindestwert an, auf den der Benutzer einen Schieberegler festlegen kann.

**[Value](properties-core.md)**: Gibt den Wert eines Eingabesteuerelements an.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**HandleActiveFill**: gibt die Farbe des Handles für einen Schieberegler an, wenn der Benutzer seinen Wert ändert.

**HandleFill**: gibt die Farbe des Handles (das Element, das die Position ändert) in einem Umschalten- oder Schieberegler-Steuerelement an.

**HandleHoverFill**: gibt die Farbe des Handles in einem Schieberegler an, wenn der Benutzer mit der Maus darauf zeigt.

**HandleSize**: der Durchmesser des Handles

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**Layout**: gibt an, ob der Benutzer einen Bildlauf durch einen Katalog durchführt oder einen Schieberegler von oben nach unten anpasst (**Vertical**) oder von links nach rechts (**Horizontal**).

**[OnChange](properties-core.md)**: Gibt an, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**RailFill**: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **FALSE** ist, oder die Farbe der Linie auf der rechten Seite des Handles in einem Schieberegler-Steuerelement.

**RailHoverFill**: Wenn Sie auf ein Umschalten-Steuerelement oder einen Schieberegler zeigen, gibt dies die Hintergrundfarbe des Rechtecks in einem Umschalten-Steuerelement mit dem Wert **FALSE** an, oder die Farbe der Linie auf der rechten Seite des Handles in einem Schieberegler-Steuerelement.

**ReadOnly**: Gibt an, ob ein Benutzer den Wert eines Schiebereglers oder eines Bewertung-Steuerelements ändern kann.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**ShowValue**: Gibt an, ob ein Wert des Schiebereglers oder der Bewertung angezeigt wird, wenn der Benutzer diesen Wert ändert oder auf das Steuerelement zeigt.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**ValueFill**: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **TRUE** ist, oder die Farbe der Linie auf der linken Seite des Handles in einem Schieberegler-Steuerelement.

**ValueHoverFill**: Wenn Sie mit dem Mauszeiger auf das Umschalten-Steuerelement oder den Schieberegler zeigen: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **TRUE** ist, oder die Farbe der Linie auf der linken Seite des Handles in einem Schieberegler-Steuerelement.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Sum**( *Value1*, *Value2* )](../functions/function-aggregates.md)

## <a name="example"></a>Beispiel
1. Fügen Sie eine Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](properties-core.md)** auf diese Formel fest:
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
   
    Benötigen Sie weitere Informationen zur **[ClearCollect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
2. Drücken Sie F5, wählen Sie die Schaltfläche aus, und drücken Sie dann die ESC-TASTE.
3. Fügen Sie einen Schieberegler ein, verschieben Sie ihn unter die Schaltfläche, und nennen Sie ihn **MinPopulation**.
4. Legen Sie die **Max**-Eigenschaft des Schiebereglers auf **5000000** und seine **Min**-Eigenschaft auf **1000000** fest.
5. Fügen Sie einen Textkatalog in vertikaler/Hochformat-Ausrichtung ein, verschieben Sie ihn unten den Schieberegler, und legen Sie die **[Items](properties-core.md)**-Eigenschaft des Katalogs auf diese Formel fest:<br>
   **Filter(CityPopulations, Population > MinPopulation)**
6. Legen Sie im ersten Element des Katalogs die Eigenschaft **[Text](properties-core.md)** der obersten Bezeichnung auf **ThisItem.City** und die Eigenschaft **[Text](properties-core.md)** der untersten Bezeichnung auf diese Formel fest:<br> **Text(ThisItem.Population, "##,###")**
7. Drücken Sie F5, und passen Sie **MinPopulation** so an, dass nur Städte angezeigt werden, deren Einwohnerzahl die von Ihnen angegebene übersteigt.
8. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **ValueFill** und **RailFill**
* **ValueHoverFill** und **RailHoverFill**
* **[FocusedBorderColor](properties-color-border.md)** und die Farbe außerhalb des Steuerelements
* **ValueFill** und Hintergrundfarbe
* **RailFill** und Hintergrundfarbe
* **ValueHoverFill** und Hintergrundfarbe
* **RailHoverFill** und Hintergrundfarbe

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
* Der Wert des Schiebereglers muss bei der Interaktion mit der Tastatur angezeigt werden. Dafür können Sie eine der folgenden Methoden verwenden:
    * Legen Sie **ShowValue** auf **TRUE** fest.
    * Fügen Sie eine **[Bezeichnung](control-text-box.md)** hinzu, die an den Schieberegler grenzt. Legen Sie den **[Text](properties-core.md)** der Bezeichnung auf den **[Wert](properties-core.md)** des Schiebereglers fest.
