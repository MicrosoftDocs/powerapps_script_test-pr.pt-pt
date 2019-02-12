---
title: Barrierefreiheit und Farben in Canvas-Apps | Microsoft-Dokumentation
description: Richtlinien für Farbkontraste für Canvas-Apps in PowerApps
author: tahoon
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/23/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 96a04cdda99f379c799ccd68e2442572ac929d39
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862908"
---
# <a name="accessible-colors-for-canvas-apps-in-powerapps"></a>Barrierefreiheit und Farben für Canvas-Apps in PowerApps
In einer App sollten nur Farben verwendet werden, die für barrierefreien Zugriff für farbenblinde und sehbehinderte Benutzer geeignet sind. Alle PowerApps-Designs sind standardmäßig barrierefrei. Beachten Sie diese Richtlinien, wenn Sie die in einer App verwendeten Farben ändern, um weiterhin Barrierefreiheit sicherzustellen. Online stehen mehrere Tools zur Verfügung, die Sie beim Bestimmen von Farbkontrasten unterstützen können.

## <a name="minimum-contrast-for-text"></a>Minimaler Kontrast bei Text
* Text und Hintergrund müssen zumindest ein Kontrastverhältnis von 4,5:1 aufweisen.
* Großer Text muss zumindest ein Kontrastverhältnis von 3:1 aufweisen.
* Für deaktivierten Text bestehen keine Kontrastanforderungen.

Praktisch müssen alle interaktiven Steuerelemente einen ausreichenden Farbkontrast aufweisen zwischen:
* **[Color](controls/properties-color-border.md)** und **[Fill](controls/properties-color-border.md)**
* **[PressedColor](controls/properties-color-border.md)** und **[PressedFill](controls/properties-color-border.md)**
* **[HoverColor](controls/properties-color-border.md)** und **[HoverFill](controls/properties-color-border.md)**

## <a name="minimum-contrast-for-non-text"></a>Minimaler Kontrast bei Nichttextinhalten

> [!NOTE]
> Die Kontrastanforderungen im Standard [WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html) gelten nur für Text. Um die Barrierefreiheit zu steigern, beachten Sie die kommenden [WCAG 2.1-Kontrastrichtlinien](https://www.w3.org/TR/WCAG21/#non-text-contrast) für wichtige Benutzeroberflächenkomponenten wie Symbolschaltflächen. Ein minimales Verhältnis von 3:1 wird für diese Komponenten empfohlen. Die in diesem Abschnitt beschriebenen Richtlinien sind für die WCAG 2.0-Kompatibilität **optional**.

### <a name="user-interface-components"></a>Benutzeroberflächenkomponenten
Alle interaktiven Steuerelemente müssen einen ausreichenden Farbkontrast aufweisen zwischen:
* **[FocusedBorderColor](controls/properties-color-border.md)** und der Farbe außerhalb des Steuerelements

Zusätzliche Überprüfungen des Farbkontrasts sind für Steuerelemente erforderlich, wo der gesamte Bereich interaktiv oder informativ ist. Beispiel: eine **[Schaltfläche](controls/control-button.md)** oder ein als Schaltfläche verwendetes **[Symbol](controls/control-shapes-icons.md)**. So wird sichergestellt, dass die Grenzen des Steuerelements deutlich sind, und Benutzer wissen, wo sie klicken oder tippen können.

Wenn ein solches Steuerelement einen Rahmen hat, sollte der Farbkontrast ausreichend sein zwischen:
* **[BorderColor](controls/properties-color-border.md)** und der Farbe außerhalb des Steuerelements
* **[PressedBorderColor](controls/properties-color-border.md)** und der Farbe außerhalb des Steuerelements
* **[HoverBorderColor](controls/properties-color-border.md)** und der Farbe außerhalb des Steuerelements

Wenn kein Rahmen vorhanden ist, sollte der Farbkontrast ausreichend sein zwischen:
* **[Fill](controls/properties-color-border.md)** und der Farbe außerhalb des Steuerelements
* **[PressedFill](controls/properties-color-border.md)** und der Farbe außerhalb des Steuerelements
* **[HoverFill](controls/properties-color-border.md)** und der Farbe außerhalb des Steuerelements

### <a name="graphical-objects"></a>Grafikobjekte
Wenn ein Bild wichtige Informationen vermittelt, achten Sie besonders auf etwaige Kontrastprobleme. Dies gilt für Steuerelemente, in denen ein Bild angezeigt werden kann: **[Audio](controls/control-audio-video.md)**, **[Image](controls/control-image.md)**, **[Mikrofon](controls/control-microphone.md)** und **[Video](controls/control-audio-video.md)**.

Überprüfen Sie Videoinhalte auf Kontrastprobleme. Stellen Sie alternativ oder darüber hinaus [Untertitel](controls/control-audio-video.md) bereit, die das Video beschreiben.

## <a name="provide-other-visual-cues"></a>Bereitstellen anderer visueller Hinweise
Stellen Sie sicher, dass die App keine Informationen einfach nur über Farbe vermittelt. Rotgrün farbenblinde Benutzer können beispielsweise keine rote Fehlermeldung von einer grünen Erfolgsmeldung unterscheiden.

Zusätzliche Hinweise wie ein **[Symbol](controls/control-shapes-icons.md)** oder Textformate wie **[Kursiv](controls/properties-text.md)** und **[Unterstrichen](controls/properties-text.md)** können helfen, Bedeutungen zu vermitteln.

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie mehr zu [Barrierefreiheitseigenschaften](controls/properties-accessibility.md) in PowerApps-Steuerelementen und zum [Verwenden der Barrierefreiheitsprüfung](accessibility-checker.md).
