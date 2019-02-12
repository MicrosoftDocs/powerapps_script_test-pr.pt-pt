---
title: Erstellen einer Regel | Microsoft-Dokumentation
description: Eine schrittweise Anleitung zum Entwerfen von App-Logik durch Erstellen von Regeln
author: karthik-1
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/10/2017
ms.author: sharik
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 32643de711321e7c604ef9e3ffc82c2502234a1f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42860391"
---
# <a name="create-a-rule-in-powerapps"></a>Erstellen einer Regel in PowerApps
Erstellen Sie Regeln, damit eine App automatisch auf Grundlage der von Ihnen angegebenen Kriterien geändert wird. Beispielsweise können Listenelemente je nach ihrem Status in Rot, Gelb oder Grün angezeigt werden, oder eine Genehmigungsschaltfläche kann nur für bestimmte Benutzer (z.B. Manager) angezeigt werden.

Sie können vielen verschiedenen Steuerelementen Regeln hinzufügen. In diesem Thema fügen Sie eine Regel hinzu, um die Textfarbe eines **Label**-Steuerelements (Bezeichnung) zu ändern, wenn der Wert eines **Slider**-Steuerelements (Schieberegler) größer als 70 ist.

## <a name="add-a-rule"></a>Regel hinzufügen
1. Wählen Sie ein Steuerelement aus (oder fügen Sie ein Steuerelement hinzu, und lassen sie es ausgewählt).

    In diesem Thema [fügen Sie ein Label- und ein Slider-Steuerelement hinzu](add-configure-controls.md), legen die **Text**-Eigenschaft des Label-Steuerelements auf **Slider1.Value** fest, und wählen dann das Slider-Steuerelement aus.

1. Klicken oder tippen Sie im rechten Bereich auf **Regeln**, und klicken oder tippen Sie dann auf **Neue Regel**.

    ![Neue Regel erstellen](./media/working-with-rules/new-rule.png)

    Wenn Sie ein Steuerelement auswählen, für das bereits eine oder mehrere Regeln definiert wurden, können Sie diese bearbeiten, indem Sie darauf klicken oder tippen.  

## <a name="add-a-condition"></a>Bedingung hinzufügen
Eine Bedingung ist ein Ausdruck, der als „true“ oder „false“ ausgewertet wird, z.B. die Bedingung, dass ein Wert größer als 70 ist. Sie können den Ausdruck anhand einer Vorlage oder vollständig neu schreiben, und Sie können den Ausdruck gemäß der Anleitung auf der Benutzeroberfläche (IntelliSense) anpassen.

1. Klicken oder tippen Sie auf **Bedingung hinzufügen**, und klicken Sie dann auf eine Vorlage oder auf **Benutzerdefinierte Bedingung**.

    In diesem Thema klicken oder tippen Sie auf **Größer als**.

    ![Bedingung hinzufügen](./media/working-with-rules/rule-conditions.png)

1. Aktualisieren Sie den Ausdruck, um zu definieren, wann die Regel angewendet wird.

    Ändern Sie im Rahmen dieses Themas 0 in 70, sodass Sie über folgenden Ausdruck verfügen:  <br>**Slider1.Value > 70**

## <a name="add-an-action"></a>Aktion hinzufügen
Aktionen definieren, was geschieht, wenn die Regel angewendet wird. In PowerApps können Aktionen automatisch basierend auf den Änderungen erstellt werden, die Sie an Steuerelementen vornehmen.

1. Klicken oder tippen Sie auf **Aktionen definieren**.

    ![Aktionen definieren](./media/working-with-rules/rule-define-actions.png)

1. Klicken oder tippen Sie im Bestätigungsdialogfeld auf **Los geht's**, damit PowerApps Ihre nächste(n) Änderung(en) als eine oder mehrere Aktionen aufzeichnet.

1. Konfigurieren Sie ein oder mehrere Steuerelemente entsprechend Ihren Erwartungen für den Fall, dass die Bedingung zutrifft.

    In diesem Thema ändern Sie die Farbe der Bezeichnung.

    ![Eigenschaften erfassen](./media/working-with-rules/rule-capture-properties.png)

1. (Optional) Überprüfen Sie die Änderungen, indem Sie auf **Aktionen anzeigen** tippen oder klicken.

    ![Aktionen überprüfen](./media/working-with-rules/rule-review-actions.png)

1. Wenn Sie alle Aktionen hinzugefügt haben, klicken oder tippen Sie auf **Fertig**.

1. Überprüfen Sie die Bedingung und die Aktionen für die Regel.

    ![Regel überprüfen](./media/working-with-rules/rule-review.png)

## <a name="rename-the-rule"></a>Umbenennen der Regel

1. Zeigen Sie auf **Regel1**, und klicken oder tippen Sie auf die Schaltfläche „Bearbeiten“.

    ![Zeigen Sie auf den Regelnamen.](./media/working-with-rules/hover-over-rules_name.png)

1. Geben Sie einen neuen Namen für die Regel ein.

    ![Regel umbenennen](./media/working-with-rules/rename-rule.png)

1. Klicken oder tippen Sie auf **Fertig**, um den Editor zu schließen.

## <a name="test-the-rule"></a>Testen der Regel
1. Drücken Sie F5 (oder klicken Sie rechts oben auf die Wiedergabeschaltfläche), um die App im Vorschaumodus anzuzeigen.

    ![Vorschau öffnen](./media/working-with-rules/open-preview.png)

1. Sorgen Sie dafür, dass die von Ihnen angegebene Bedingung zutrifft, und vergewissern Sie sich dann, dass die Aktionen wie erwartet ausgeführt werden.

    In diesem Thema schieben Sie den Schieberegler auf einen Wert, der größer als 70 ist. Vergewissern Sie sich dann, dass sich die Farbe des Bezeichnungstexts ändert.

## <a name="see-all-rules"></a>Alle Regeln anzeigen
In der Standardeinstellung werden auf der Registerkarte **Regeln** nur die Regeln für das ausgewählte Steuerelement und die untergeordneten Steuerelemente angezeigt, die in einer Regelbedingung oder -aktion verwendet werden. Um alle Regeln in der App anzuzeigen, deaktivieren Sie das Kontrollkästchen **Nur Regeln für dieses Steuerelement anzeigen**.

![Filter entfernen](./media/working-with-rules/rules-filter.png)

## <a name="known-limitations"></a>Bekannte Einschränkungen
Zum Zeitpunkt der Erstellung dieses Dokuments:

* Sie können die **ThisItem**-Eigenschaft eines Formulars oder Katalogs nicht als Teil einer Bedingung angeben.
