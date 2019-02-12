---
title: 'Säulendiagramm-Steuerelement und Liniendiagramm-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Säulendiagramm-Steuerelement und das Liniendiagramm-Steuerelement
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
ms.openlocfilehash: 9c290d28db7ae35d33f4ceb2cd56c3a3ad79b01c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42832834"
---
# <a name="column-chart-and-line-chart-controls-in-powerapps"></a>Steuerelemente für Säulendiagramme und Liniendiagramme in PowerApps
Steuerelemente, die Daten in Form eines Diagramms mit X- und Y-Achse darstellen.

## <a name="description"></a>Beschreibung
**Column chart** und **Line chart** sind gruppierte Steuerelemente. Jede Gruppe enthält drei Steuerelemente: eine **[Bezeichnung](control-text-box.md)** für den Titel, ein Diagramm und eine **Legende**.

## <a name="chart-key-properties"></a>Kerneigenschaften des Diagramms
**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**NumberOfSeries** – Gibt an, wie viele Datenspalten in einem Säulen- oder Liniendiagramm widergespiegelt werden.

## <a name="additional-chart-properties"></a>Zusätzliche Diagrammeigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**GridStyle** – Gibt an, ob für ein Säulen- oder Liniendiagramm die x-Achse, die y-Achse, beide Achsen oder keine Achse angezeigt wird.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**ItemColorSet** – Die Farbe jedes Datenpunkts eines Diagramms.

**ItemsGap** – Der Abstand zwischen Spalten in einem Säulendiagramm.

* Die **ItemsGap**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**Markers** – Gibt an, ob in einem Säulen- oder Liniendiagramm der Wert der einzelnen Datenpunkte angezeigt wird.

**MarkerSuffix** – Text, der nach den einzelnen Werten in einem Säulendiagramm angezeigt wird, für das die **Markers**-Eigenschaft auf **true** festgelegt ist.

* Die **MarkerSuffix**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**MinimumBarWidth** – Die geringstmögliche Breite von Säulen in einem Säulendiagramm.

* Die **MinimumBarWidth**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**SeriesAxisMax** – Der höchste Wert für die y-Achse eines Säulen- oder Liniendiagramms.

* Die **SeriesAxisMax**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**SeriesAxisMin** – Eine Zahl, mit der der niedrigste Wert der y-Achse eines Säulendiagramms angegeben wird.

* Die **SeriesAxisMin**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**XLabelAngle** – Der Winkel der Beschriftungen unterhalb der x-Achse eines Säulen- oder Liniendiagramms.

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**YAxisMax** – Der höchste Wert der y-Achse eines Liniendiagramms.

* Die **YAxisMax**-Eigenschaft ist nur für das **Liniendiagramm**-Steuerelement verfügbar, beim **Spaltendiagramm**-Steuerelement kann sie nicht verwendet werden.

**YAxisMin** – Der niedrigste Wert der y-Achse eines Liniendiagramms.

* Die **YAxisMin**-Eigenschaft ist nur beim **Liniendiagramm**-Steuerelement verfügbar, beim **Spaltendiagramm**-Steuerelement kann sie nicht verwendet werden.

**YLabelAngle** – Der Winkel der Beschriftungen neben der y-Achse eines Linien- oder Säulendiagramms.

## <a name="related-functions"></a>Verwandte Funktionen
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein **[Button](control-button.md)**-Steuerelement (Schaltfläche) hinzu, und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **Collect(Revenue, {Year:"2013", Europa:24000, Ganymede:22300, Callisto:21200}, {Year:"2014", Europa:26500, Ganymede:25700, Callisto:24700},{Year:"2014", Europa:27900, Ganymede:28300, Callisto:25600})**
   
    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
2. Drücken Sie F5, klicken oder tippen Sie auf das **[Schaltflächen](control-button.md)**-Steuerelement, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.
3. Fügen Sie ein **Säulendiagramm**-Steuerelement oder ein **Liniendiagramm**-Steuerelement hinzu, und legen Sie für die **[Items](properties-core.md)**-Eigenschaft den Wert **Revenue** sowie für die **NumberOfSeries**-Eigenschaft den Wert **3** fest.
   
    Das Steuerelement zeigt die Umsatzdaten jedes Produkts aus drei Jahren an.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* jedes Element in **ItemColorSet**
* jedes Element in **ItemColorSet** und die Hintergrundfarbe
* **[Farbe](properties-color-border.md)** und die Hintergrundfarbe

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Vor dem Diagramm muss eine **[Bezeichnung](control-text-box.md)** hinzugefügt werden, die als Titel dienen soll.
* Sie sollten eine Zusammenfassung des Diagramms hinzufügen. Z.B: „Das Liniendiagramm zeigt zwischen März und August dieses Jahres einen konstanten Anstieg bei den Verkäufen an.“

    > [!NOTE]
  > Diagramme und **Legenden** werden für Benutzer der Sprachausgabe ausgeblendet. Für sie werden stattdessen die Daten in Tabellenform dargestellt. Außerdem können sie zwischen Steuerelementen wechseln, die Daten aus dem Diagramm auswählen.

### <a name="low-vision-support"></a>Unterstützte Anpassungen für Menschen mit Sehbehinderungen
* Wenn mehr als eine Reihe angezeigt wird, muss eine **Legende** vorhanden sein.
* Sie sollten **GridStyle** auf GridStyle.All festlegen, damit beide Achsen angezeigt werden. Dadurch können alle Benutzer die Staffelung der Daten genau bestimmen.
* Für das **Spaltendiagramm**-Steuerelement sollten Sie **Marker** auf **TRUE** festlegen. Dadurch können Benutzer mit Sehbehinderung den Wert einer Spalte bestimmen.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.

    > [!NOTE]
  > Wenn Benutzer über eine Tastatur zu dem Diagramm navigieren, können sie zwischen Schaltflächen wechseln, die Daten aus dem Diagramm auswählen.
