---
title: 'Shape-Steuerelemente und Symbole für Steuerelemente: Referenz | Microsoft-Dokumentation'
description: Informationen einschließlich Eigenschaften und Beispielen für Shape-Steuerelemente und Symbole für Steuerelemente
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
ms.openlocfilehash: 34e76821a10ef5803028bc7fd31bbd70c2845b36
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849200"
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Shape-Steuerelemente und Symbole für Steuerelemente in PowerApps
Grafiken, deren Eigenschaften wie Aussehen und Verhalten Sie konfigurieren können

## <a name="description"></a>Beschreibung
Diese Steuerelemente umfassen Pfeile, geometrische Formen, Aktionssymbole und Symbole, deren Eigenschaften wie Füllung, Größe und Position sich konfigurieren lassen. Sie können auch die Eigenschaft **[OnSelect](properties-core.md)** konfigurieren, damit die App reagiert, wenn der Benutzer auf das Steuerelement klickt oder tippt.

## <a name="key-properties"></a>Haupteigenschaften
**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen

[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>Beispiel

1. Nennen Sie das **[Bildschirm](control-screen.md)**-Standardsteuerelement **Target**, fügen Sie ein **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie anschließend die  **[Text](properties-core.md)**-Eigenschaft so fest, dass **Target** angezeigt wird.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

2. Fügen Sie ein **[Bildschirm](control-screen.md)**-Steuerelement hinzu, und nennen Sie es **Source**.
3. Fügen Sie in **Source** ein **Shape**-Steuerelement hinzu, und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>**Navigate(Target, ScreenTransition.Fade)**
4. Drücken Sie F5, und klicken oder tippen Sie anschließend auf das **Shape**-Steuerelement.

    Der Bildschirm **Target** wird angezeigt.

5. (optional) Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren, fügen Sie ein **Shape**-Steuerelement zu **Target** hinzu, und legen Sie die **[OnSelect](properties-core.md)**-Eigenschaft des **Shape**-Steuerelements auf diese Formel fest:
   <br>**Navigate(Source, ScreenTransition.Fade)**


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="color-contrast"></a>Farbkontrast

Folgendes gilt nur für Grafiken, die als Schaltflächen oder nicht allein zu Darstellungszwecken verwendet werden.

Für Symbole:
* **[Color](properties-color-border.md)** und **[Fill](properties-color-border.md)**
* Es gelten die [Standardanforderungen für Farbkontraste](../accessible-apps-color.md), wenn das Steuerelement als Schaltfläche verwendet wird.

Für Formen mit Rahmen:
* **[BorderColor](properties-color-border.md)** und die Farbe außerhalb des Steuerelements
* **[FocusedBorderColor](properties-color-border.md)** und die Farbe außerhalb des Steuerelements, wenn dieses als Schaltfläche verwendet wird

Für Formen ohne Rahmen:
* **[Fill](properties-color-border.md)** und die Farbe außerhalb des Steuerelements
* **[PressedFill](properties-color-border.md)** und die Farbe außerhalb des Steuerelements, wenn dieses als Schaltfläche verwendet wird
* **[HoverFill](properties-color-border.md)** und die Farbe außerhalb des Steuerelements, wenn dieses als Schaltfläche verwendet wird

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein, wenn die Grafik als Schaltfläche oder zumindest nicht nur der Dekoration dient.
* **[AccessibleLabel](properties-accessibility.md)** muss leer sein oder der leeren Zeichenfolge **""** entsprechen, wenn die Grafik ausschließlich Dekoration ist. Dadurch wird die Grafik von der Sprachausgabe ignoriert.
* **[AccessibleLabel](properties-accessibility.md)** kann leer sein oder der leeren Zeichenfolge **""** entsprechen, falls die Grafik redundante Informationen enthält.

    Beispielsweise ein Symbol **Einstellungen**, für das **[AccessibleLabel](properties-accessibility.md)** auf **Einstellungen** festgelegt ist. Dieses Symbol wird nicht als Schaltfläche verwendet. Es befindet sich neben einer **[Bezeichnung](control-text-box.md)**, die ebenfalls den Namen **Einstellungen** hat. Sprachausgaben lesen erst das Symbol und dann die Bezeichnung als **Einstellungen**. Dies ist zu ausführlich. In diesem Fall benötigt das Symbol keine **[AccessibleLabel](properties-accessibility.md)**-Eigenschaft.

    > [!IMPORTANT]
    > Sprachausgaben lesen alle Symbole oder Formen, deren **[TabIndex](properties-accessibility.md)**-Wert gleich 0 (null) oder größer ist, selbst wenn **[AccessibleLabel](properties-accessibility.md)** leer ist. Dies liegt daran, dass sie als Schaltflächen gerendert werden. Wenn kein **[AccessibleLabel](properties-accessibility.md)** bereitgestellt wird, lesen Sprachausgaben die Grafik als **Schaltfläche**.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss 0 (null) oder größer sein, wenn die Grafik als Schaltfläche verwendet wird. So können Benutzer über die Tastatur dorthin navigieren.
* Fokusindikatoren müssen übersichtlich angezeigt werden, wenn die Grafik als Schaltfläche verwendet wird. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.

    > [!NOTE]
  > Wenn **[TabIndex](properties-accessibility.md)** gleich 0 (null) oder größer ist, werden das Symbol oder die Form als Schaltfläche gerendert. Dadurch erfolgt keine Änderung der visuellen Darstellung. Die Sprachausgabe erkennt das Bild jedoch richtig als Schaltfläche. Ist **[TabIndex](properties-accessibility.md)** kleiner als 0 (null), wird das Symbol oder die Form als Bild erkannt.
