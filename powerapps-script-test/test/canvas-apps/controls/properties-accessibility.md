---
title: Eigenschaften von Bedienungshilfen | Microsoft-Dokumentation
description: Enthält Referenzinformationen zu Eigenschaften, z.B. TabIndex, QuickInfo.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/26/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4d75fcd4c0605e295c1e61c5232ba747203d1647
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42854145"
---
# <a name="accessibility-properties-in-powerapps"></a>Eigenschaften von Bedienungshilfen in PowerApps
Hier geht es um die Konfiguration von Eigenschaften, die für Benutzer mit Sehschwäche als Hilfe für alternative Interaktionsmöglichkeiten mit Steuerelementen dienen.

### <a name="properties"></a>Eigenschaften
**AccessibleLabel**: Bezeichnung für Sprachausgaben. Durch einen leeren Wert für Bild-, Symbol- und Formsteuerelemente werden diese für die Bildschirmsprachausgabe unsichtbar und als Dekoration behandelt.

**TabIndex**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

Mit dem Standardwert 0 wird die Standardaktivierreihenfolge basierend auf der XY-Koordinate des Steuerelements angegeben.  Wenn Sie einen höheren Wert als 0 wählen, wird die Aktivierreihenfolge für alle Steuerelemente mit den Standardwerten entsprechend verschoben.  Ein Steuerelement mit einem TabIndex-Wert von 2 hat in der Aktivierreihenfolge Vorrang vor einem Steuerelement mit dem TabIndex-Wert 3 oder höher.

Beachten Sie, dass bei Containern, z.B. Formular- und Katalog-Steuerelementen, immer erst alle Elemente des Containers durchlaufen werden, bevor die Steuerelemente außerhalb des Containers an die Reihe kommen.  Die Aktivierreihenfolge des Containers entspricht der Reihenfolge des niedrigsten TabIndex-Werts eines untergeordneten Steuerelements.

Durch Festlegen von TabIndex auf den Wert -1 wird der Registerkartenzugriff auf das Steuerelement deaktiviert; im Fall von Bildern, Symbolen und Formen werden diese zu nicht interaktiven Elementen.
