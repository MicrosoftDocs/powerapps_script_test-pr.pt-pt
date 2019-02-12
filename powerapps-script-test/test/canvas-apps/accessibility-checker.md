---
title: Überprüfen einer Canvas-App auf Barrierefreiheit | Microsoft-Dokumentation
description: Suchen nach Methoden, um eine Canvas-App für Benutzer zugänglicher zu machen, die eine Sehschwäche oder Hörschwäche oder eine andere Beeinträchtigung haben
author: emcoope-msft
ms.service: powerapps
ms.topic: article
ms.date: 07/05/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 11ec805a713743e2524651128b036ccaaade69e3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42842530"
---
# <a name="review-a-canvas-app-for-accessibility-in-powerapps"></a>Überprüfen einer Canvas-App in PowerApps auf Barrierefreiheit

Benutzer, die eine Sehschwäche, Hörschwäche oder eine andere Beeinträchtigung haben, können Ihre Canvas-App einfacher und erfolgreicher nutzen, wenn Sie die Barrierefreiheit berücksichtigen, während Sie das Design und das Verhalten der App entwerfen. Wenn Sie nicht sicher sind, wie Sie Ihre App barrierefreier gestalten können, können Sie die Barrierefreiheitsüberprüfung in PowerApps Studio ausführen. Dieses Tool kann nicht nur mögliche Probleme bei der Barrierefreiheit erkennen, es erläutert auch, warum jedes Problem ein potentielles Problem für Benutzer darstellen kann, die eine bestimmte Beeinträchtigung haben, und schlägt mögliche Lösungen vor.
Die Barrierefreiheitsüberprüfung erkennt Probleme bei der Sprachausgabe und Tastatureingabe. Außerdem stellt sie Informationen zur Behebung von Farbkontrastprobleme durch [barrierefreie Farben](accessible-apps-color.md) bereit.

Mit der Barrierefreiheitsüberprüfung können Sie Einstellungen identifizieren, die Sie ändern sollten. Ziehen Sie jedoch immer die Vorschläge im Kontext der Aufgabe Ihrer App in Betracht. Viele Vorschläge lohnen sich möglicherweise, Sie können aber jene ignorieren, die mehr Nach- als Vorteile haben.

## <a name="find-accessibility-issues"></a>Ermitteln von Problemen mit der Barrierefreiheit

1. Klicken Sie in der oberen rechten Ecke von PowerApps Studio auf das Symbol für die App-Überprüfung.

    ![Symbol für die App-Überprüfung](./media/accessibility-checker/app-checker-icon.png)

2. Wählen Sie im angezeigten Menü die Option **Barrierefreiheit**.

    ![Liste der Optionen im Bereich „App-Überprüfung“](./media/accessibility-checker/app-checker-menu.png)

    Es wird eine Liste der Probleme angezeigt, die nach Schweregrad und dann nach Anzeige geordnet ist.

    ![Barrierefreiheitsüberprüfungsbereich und Liste der Probleme](./media/accessibility-checker/accessibility-checker-pane.png)

3. Wählen Sie den Pfeil neben einem Element aus, um Informationen darüber anzuzeigen.

    ![Informationen der Barrierefreiheitsprüfung](./media/accessibility-checker/details-pane.png)

4. Wählen Sie den Pfeil „Zurück“ aus, um zur Elementliste zurückzukehren.

5. Wenn Sie ein Problem behandeln möchten, wählen Sie es aus, um die betroffene Eigenschaft zu öffnen.

6. Nachdem Sie eine oder mehrere Eigenschaften geändert haben, wählen Sie **Re-check** (Erneut überprüfen) aus, um die Liste mit den Probleme zu aktualisieren.

    Gelöste Probleme verschwinden aus der Liste, es können aber neue Probleme dazukommen.

## <a name="severity-of-issues"></a>Schweregrad von Problemen

Die Barrierefreiheitsüberprüfung klassifiziert jedes Problem auf Grundlage des Fehlerschweregrads als Fehler, Warnung oder Tipp.

- **Fehler** sind Probleme, die die Nutzung oder das Verständnis der App für Benutzer mit Behinderung erschweren oder unmöglich machen.
- **Warnungen** sind Probleme, die die Nutzung oder das Verständnis der App für die meisten aber nicht alle Benutzer mit Behinderung schwierig gestalten.
- **Tipps** helfen Ihnen bei der Verbesserung der Servicequalität für Benutzer, die eine Behinderung haben.

## <a name="types-of-issues"></a>Fehlertypen

| Problemtitel                            | Schweregrad | Problembeschreibung  | Vorgehensweise zur Behebung | Warum eine Behebung notwendig ist|
| ------------------------------         |:---------| -----| ------|------ |
| **Barrierefreie Bezeichnung fehlt.**           | Fehler    | Wenn die Eigenschaft „accessible-label“ eines interaktiven Steuerelements keinen Text enthält. Ein interaktives Steuerelement kann grundsätzlich interaktiv sein, eine Schaltfläche sein oder über interaktive Eigenschaften verfügen. Sie haben z.B. die Eigenschaft **OnSelect** eines Bilds oder dessen **TabIndex**-Eigenschaft auf 0 oder höher festgelegt.  | Bearbeiten Sie die accessible-label-Eigenschaft, um das Element zu definieren. | Wenn in der accessible-label-Eigenschaft kein Text vorhanden ist, wissen Personen, die den Bildschirm nicht sehen können, nicht, was in Bildern und Steuerelementen dargestellt wird. |
| **Fokus wird nicht angezeigt.**                | Fehler    | Wenn die **FocusBorderThickness** eines Steuerelements auf 0 festgelegt ist. Es wird empfohlen, auf einen deutlichen Farbkontrast zwischen dem Fokusrahmen und dem Steuerelement zu achten, damit es deutlich sichtbar ist. | Ändern Sie die Eigenschaft **FocusedBorderThickness** in einen Wert größer als 0.  | Wenn der Fokus nicht sichtbar ist, können Personen, die keine Maus verwenden, ihn nicht sehen, während sie mit der App interagieren.   |
| **Untertitel fehlen.**                   | Warnung  | Wenn die Eigenschaft **ClosedCaptionsURL** eines **Audio**- oder **Video**-Steuerelements leer ist. | Legen Sie die **ClosedCaptionsURL**-Eigenschaft auf die URL für Untertitel fest. | Ohne Untertitel können Personen mit Behinderungen die Informationen in einem Video- oder Audiosegment möglicherweise nicht verstehen. |
| **Hilfreiche Steuerelementeinstellungen fehlen.**   | Warnung  | Wenn mehrere Einstellungen deaktiviert sind (z.B. die Anzeige von Bezeichnungen und Marker für Diagramme und die Anzeige von Standardsteuerelementen für **Audio**-, **Video**- und **Stifteingabe**-Steuerelemente). | Wählen Sie die Warnung aus, und legen Sie die Eigenschaft auf **true** fest. | Indem Sie diese Eigenschafteneinstellung ändern, erhält der Benutzer hilfreichere Informationen über die Funktion der Steuerelemente in Ihrer App. |
| **HTML ist nicht barrierefrei.**           | Warnung  | Wenn ein anderes Steuerelement als ein HTML-Text HTML enthält. In diesem Fall unterstützt PowerApps nicht die Barrierefreiheit benutzerdefinierter HTML-Elemente. | Verwenden Sie eine andere Methode anstelle von HTML, oder entfernen Sie den HTML-Code aus diesem Element. | Ihre App funktioniert nicht ordnungsgemäß oder ist nicht barrierefrei, wenn Sie interaktive HTML-Elemente hinzufügen. |
| **Automatischen Start deaktivieren.**                 | Warnung  | Wenn die **Autostart**-Eigenschaft eines **Audio**- oder **Video**-Steuerelements auf **true** festgelegt ist. | Legen Sie die **Autostart**-Eigenschaft auf **false** fest. | Video- und Audiodateien, die automatisch wiedergegeben werden, können Benutzer ablenken. Lassen Sie Benutzer entscheiden, ob sie einen Clip abspielen möchten. |
| **Namen des Bildschirms überarbeiten.**                 | Tipp      | Wenn ein Bildschirm über einen Standardnamen verfügt, der von Sprachausgaben vorgelesen wird, wenn Benutzer in der App navigieren. | Geben Sie dem Bildschirm einen Namen, der beschreibt, was auf dem Bildschirm angezeigt oder wofür er verwendet wird.| Personen, die blind oder sehbehindert sind oder eine Lese-/Rechtschreibschwäche besitzen, verlassen sich bei der Navigation auf die Bildschirmnamen und die Sprachausgabe. |
| **Hinweistext für Zustand hinzufügen.**          | Tipp      |  Wenn ein Steuerelement zwar über einen Status verfügt (z.B. eine Umschaltfläche), für das aber die Wertbezeichnungen deaktiviert sind. | Legen Sie die Eigenschaft **ShowValue** des Steuerelements auf **true** fest, um den aktuellen Status anzuzeigen. | Benutzer erhalten keine Bestätigung ihrer Aktionen, wenn der Zustand des Steuerelements nicht angezeigt wird. |
| **Reihenfolge der Bildschirmelemente überprüfen**| Tipp      | Wenn die Eigenschaft **TabIndex** größer als 1 ist. App-Entwickler können benutzerdefinierte Registerkartenreihenfolgen festlegen, indem Sie die **TabIndex**-Eigenschaft auf einen numerischen Wert wie 1, 2, 3 und 4 festlegen. Dieser Tipp erinnert Sie daran, die interaktive Reihenfolge für diesen Bildschirm zu überprüfen. Es hat sich bewährt, ein Design zu verwenden, in dem die **TabIndex**-Eigenschaft 0 ist.  | Stellen Sie sicher, dass die Bildschirmelemente in der Reihenfolge vorliegen, in der Sie sie durchlaufen möchten. | Wenn eine Sprachausgabe die Elemente einer App vorliest, sollten diese in der Reihenfolge dargestellt werden, in der ein Benutzer sie sehen würde und nicht in einer weniger intuitiven Reihenfolge.  |
| **Andere Eingabemethode hinzufügen.**           | Tipp      | Wenn eine App ein **Stift**-Steuerelement enthält. Dieser Tipp erinnert Sie daran, eine separate Eingabemethode einzuschließen. | Fügen Sie zusätzlich zum **Stiftsteuerelement** ein **Texteingabesteuerelement** hinzu, um eine barrierefreie Lösung anzubieten. | Einige Benutzer können keinen Stift verwenden und benötigen eine weitere Möglichkeit zur Eingabe von Informationen (Beispiel: die Eingabe einer Unterschrift). |

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen barrierefreier Apps](accessible-apps.md)
- [Barrierefreie Farben](accessible-apps-color.md)
- [Accessibility properties (Eigenschaften der Barrierefreiheit)](controls/properties-accessibility.md)
