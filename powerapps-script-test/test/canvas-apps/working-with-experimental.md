---
title: Informationen zu Vorschaufeatures und experimentellen Features | Microsoft-Dokumentation
description: Testen Sie neue Features, und übernehmen Sie diese nach und nach.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/16/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 741cec402c6a5b5ea30700badd265f5e950203e9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42858473"
---
# <a name="understand-experimental-and-preview-features-in-powerapps"></a>Informationen zu Vorschaufeatures und experimentellen Features

Mit jedem Release nehmen wir Änderungen vor und fügen neue Features hinzu, um sicherzustellen, dass PowerApps immer Ihren Anforderungen entspricht. Wir verbessern das Produkt kontinuierlich.  

Abwärtskompatibilität ist ein sehr wichtiger Aspekt für uns. Es kann jedoch vorkommen, dass durch eine Änderung oder eine Verbesserung unbeabsichtigte Nebeneffekte auftreten und Ihre App nicht mehr wie bisher funktioniert.

Größere Features durchlaufen mehrere Phasen, um Verbesserungen und Auswirkungen auf vorhandene Apps gegeneinander abwägen zu können. In diesem Artikel wird dieser Prozess beschrieben. Außerdem erfahren Sie, wie Sie mit in der Entwicklungsphase befindlichen Features umgehen können.

## <a name="feature-roll-out-stages"></a>Einführungsphasen von Features

Features durchlaufen drei verschiedene Phasen, bevor sie offizieller Bestandteil des Produkts werden:

1. **Experimentell:** Das Feature befindet sich noch in der Bearbeitung. Verlassen Sie sich nicht auf dieses Feature. Es kann sein, dass es sich noch deutlich verändert.
1. **Vorschau:** Das Feature ist fast fertig und funktioniert stabil. Sie können mit der Migration vorhandener Apps beginnen.
1. **Ausgeliefert:** Das Feature ist fertig. Das Feature ist für alle Apps aktiviert, und Sie können es nicht deaktivieren.

Mit jeder Phase steigt die Zahl an Benutzern des Features, sodass wir überprüfen können, ob Bedarf für dieses Feature besteht und ob es in den frühen Phasen noch Nebeneffekte gibt.

**Für diesen Prozess ist Ihr Feedback wesentlich.**  Veröffentlichen Sie Ihr Feedback im [Forum der PowerApps-Community](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).

Wie lange befindet sich ein Feature in einer der oben genannten Phasen? Das kann sich von Feature zu Feature unterscheiden. Dabei werden sehr viele Faktoren berücksichtigt, z.B. die Anzahl der Apps, die das Feature verwenden, die Anzahl der gemeldeten Probleme und die Dringlichkeit des Features. Features können sich Wochen aber auch Monate in einer Phase befinden.

Anhand dieser Tabelle können Sie entscheiden, wann es für Sie am sinnvollsten ist, mit der Verwendung von Features zu beginnen: 

| Phase | Wann sollte ich diese verwenden? | Ist es zuverlässig? | Ist es standardmäßig für neue Apps aktiviert? | 
|----|----|----|-----|------|
| **Experimentell** | Wenn Sie ein Early Adopter sind, ein Feature nützlich für Sie sein könnte, oder Sie beim Testen des Features helfen möchten | Nein.  Experimentelle Features können sich noch deutlich verändern oder im Laufe der Zeit wieder vollständig verschwinden. | Nein. Sie müssen sich explizit für das Feature entscheiden.  |  
| **Vorschau** | Neue Apps beinhalten dieses Feature automatisch.  Sie können das Feature in vorhandenen Apps aktivieren und testen, da es irgendwann auch für vorhandene Apps aktiviert wird. | Ja. Dieses Feature soll ein permanenter Bestandteil des Produkts werden.  | Ja. Sie sollten es deaktivieren, wenn ein Problem auftritt.  Melden Sie uns diese Probleme, denn genau aus diesem Grund befindet sich das Feature noch in der Vorschauphase. | 
| **Ausgeliefert** (wird nicht mehr in den **erweiterten Einstellungen** angezeigt) | Alle Apps verfügen über dieses Feature. | Ja. | Ja.  Die meisten können nicht deaktiviert werden.  |  

Am Ende der Vorschauphase wird ein Feature möglicherweise für alle Apps aktiviert, und dann befindet es sich in der **abschließenden Überprüfung**.  Durch diese Änderungen haben auch die Letzten die Möglichkeit, das Feature auszuprobieren, während es noch deaktiviert werden kann. Zeitnahe Rückmeldung ist in dieser Phase essentiell, da das Feature in der nächsten Phase ausgeliefert wird und nicht mehr deaktiviert werden kann.  

## <a name="documentation"></a>Dokumentation

Wo werden Informationen zu diesen Features veröffentlicht?  Vorschaufeatures werden als abgeschlossene Features angesehen, und Sie können dort mehr über diese Features erfahren, wo Sie auch Informationen zu jedem anderen Feature erhalten: 
- [in der PowerApps-Dokumentation](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started). Hier erhalten Sie grundlegende Informationen zum neuen Feature: zu den Vorteilen, den ersten Schritte und zu Referenzinformationen.
- [im Forum der PowerApps-Community](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).  Sie lernen das neue Feature gemeinsam mit anderen Benutzern kennen. Hier können Sie sich austauschen und voneinander lernen.
- [im PowerApps-Blog](https://powerapps.microsoft.com/blog/).  Die meiste Zeit, allerdings nicht immer, wir mit einem neuen Feature auch ein dazugehöriger Blogbeitrag veröffentlicht.

Das ist bei experimentellen Features anders.  Sie befinden sich noch in Bearbeitung und werden nicht als fertig angesehen. Die kurze Beschreibung im Bereich **App-Einstellungen** (siehe unten) kann die einzige Stelle sein, an der Sie Informationen zu diesen Features erhalten. Experimentelle Features werden normalerweise nicht in der Dokumentation behandelt. Das Communityforum ist in diesem Fall Ihre beste Informationsquelle.  In einigen Fällen wird das Feature in einem frühen Blogbeitrag beschrieben.  Wenn Sie nicht ausreichend Informationen finden können, stellen Sie im Forum eine Frage, oder warten Sie, bis das Feature in die Vorschauphase übergeht.

## <a name="controlling-which-features-are-enabled"></a>Aktivieren und Deaktivieren von Features

Experimentelle Features und Vorschaufeatures werden in den **erweiterten Einstellungen** der App aufgeführt.  Klicken Sie in der App auf das Menü **Datei**, wählen Sie **App-Einstellungen** und dann **Erweiterte Einstellungen**. Scrollen Sie nach unten zu den Bereichen **Preview Features** (Vorschaufeatures) und **Experimental Features** (Experimentelle Features):

![](media/working-with-experimental/advanced-settings.png)

Jedes Feature hat einen Umschalter.  Wenn **Off** (Aus) angezeigt wird, ist das Feature deaktiviert.  Standardmäßig stehen alle Umschalter auf „Off“. So können Sie Ihre App am sichersten ausführen.

In einigen Fällen kann es nötig sein, die App zu schließen und neu zu starten, nachdem Sie Änderungen vorgenommen haben.  Sollte dieser Schritt erforderlich sein, wird dies in der Featurebeschreibung angegeben.

Im oberen Bereich der **erweiterten Einstellungen** finden Sie Einstellungen für vollständig ausgelieferte Features, die sich nicht mehr in der experimentellen oder Vorschauphase befinden und die zuverlässig funktionieren. 

Diese Einstellungen unterscheiden sich je nach App. Wenn Sie einen Umschalter betätigen, wirkt sich das deshalb nur auf die App aus, die Sie gerade geöffnet haben. Wenn Sie eine App erstellen, werden die Umschalter auf die Standardeinstellungen für diese App zurückgesetzt.
