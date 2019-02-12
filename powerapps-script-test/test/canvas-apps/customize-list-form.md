---
title: Anpassen eines SharePoint-Listenformulars | Microsoft-Dokumentation
description: Verwenden Sie PowerApps, um das Formular anzupassen, über das Benutzer Einträge in einer SharePoint-Liste erstellen und bearbeiten.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/11/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 218fb97f6cd523275c0ba296ea120d487cf67e4c
ms.sourcegitcommit: c26976af24a3e510e4eced78cf5c48cc2f71cae2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025669"
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>Anpassen eines SharePoint-Listenformulars mit PowerApps

Sie können das Formular für eine SharePoint-Liste leicht anpassen, wenn Sie PowerApps in einem Browser öffnen. Sie müssen keinen herkömmlichen Code (wie C#) schreiben oder eine weitere App (wie InfoPath) herunterladen. Wenn Sie Ihre Änderungen veröffentlichen, wird das Formular in die SharePoint-Liste eingebettet, sodass es von allen Benutzern verwendet werden kann. Sie können sich in PowerApps auch Analyseberichte ansehen, im Handumdrehen bedingte Formatierungen erstellen und eine Verbindung mit anderen Datenquellen herstellen.

Für die in diesem Artikel beschriebenen Schritte benötigen Sie eine einfache Liste, um nachvollziehen zu können, wie die Anpassung funktioniert. Anschließend können Sie diese Konzepte auf Ihre eigene Liste anwenden.

> [!NOTE]
> Wenn die Option **Formulare anpassen** nicht verfügbar ist oder nicht ordnungsgemäß für Ihre Liste ausgeführt wird, enthält diese möglicherweise Datentypen, die [von PowerApps nicht unterstützt werden](connections/connection-sharepoint-online.md#known-issues). Sie können Ihr Formular nicht in eine andere Liste oder [Umgebung](working-with-environments.md) verschieben.

## <a name="prerequisites"></a>Voraussetzungen

Erstellen Sie eine Liste auf einer SharePoint-Seite, und fügen Sie dann folgende Spalten ein:

- **ProductName** (einzeiliger Text)
- **Details** (ja/nein)
- **Price** (Währung)
- **Availability** (Datum ohne Uhrzeit)
- **Color** (Auswahl)

## <a name="open-the-form-in-powerapps"></a>Öffnen Sie das Formular in PowerApps

1. Öffnen Sie die von Ihnen erstellte Liste, und klicken Sie dann auf der Befehlsleiste auf **Neu**.

    Das Formular wird mit den von Ihnen hinzugefügten Feldern sowie **Title** und **Attachements** geöffnet.

1. Klicken Sie oben im Formular auf **Anpassen**.

    PowerApps Studio wird auf der gleichen Registerkarte im Browser geöffnet.

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** geöffnet wird, wählen Sie **Überspringen** aus.

## <a name="hide-extra-fields"></a>Ausblenden zusätzlicher Felder

In der Mitte des Bildschirms zeigt PowerApps Ihr Formular an. Dieses enthält jedoch Felder, die Sie nicht benötigen.

- Deaktivieren Sie im Bereich **Daten** die Kontrollkästchen für die Felder **Title** (Titel) und **Attachments** (Anlagen).

    Diese Felder werden im Formular danach nicht mehr angezeigt, sodass Sie nur noch die von Ihnen hinzugefügten Felder sehen.

    ![Feldliste](./media/customize-list-form/field-list.png)

## <a name="set-conditional-formatting"></a>Festlegen bedingter Formatierung

Sie können die Felder **Price**, **Availability** und **Colors** so konfigurieren, dass sie nur angezeigt werden, wenn **Details** auf „Yes“ (Ja) festgelegt ist.

1. Wählen Sie Karte **Price** (Preis) aus, indem Sie einmal darauf klicken oder tippen.

    ![Karte „Price“ auswählen](./media/customize-list-form/select-card.png)

1. Wählen Sie aus der Eigenschaftenliste **Visible** (Sichtbar) aus.

    ![Eigenschaft „Visible“ auswählen](./media/customize-list-form/select-property.png)

1. Geben Sie in der Formelleiste die folgende Formel ein (oder fügen Sie sie ein):

    **If(DataCardValue3.Value = true, true)**

    ![Wert der visible-Eigenschaft festlegen](./media/customize-list-form/build-formula.png)

1. Führen Sie diese Schritte auch für die Karten **Availability** und **Color** durch.

1. Halten Sie die ALT-TASTE gedrückt, und tippen oder klicken Sie mehrmals auf den Schalter **Details**.

    Die drei von Ihnen konfigurierten Felder werden angezeigt und wieder ausgeblendet.

1. Optional: Sie können Ihr Formular auch weiter anpassen, z.B. wie folgt:

    - Ändern Sie die Größe, Ausrichtung oder beides (Sie können das Formular z.B. [breiter machen](set-aspect-ratio-portrait-landscape.md))
    - Fügen Sie ein Steuerelement hinzu, sodass Benutzer [Anlagen hochladen können](controls/properties-text.md).
    - Erstellen Sie ein [Nachschlagefeld](sharepoint-lookup-fields.md).

## <a name="save-publish-and-show-the-form"></a>Speichern, veröffentlichen und zeigen Sie das Formular an

1. Öffnen Sie das Menü **Datei**, klicken Sie auf **Speichern**, und wählen Sie dann zweimal **In SharePoint veröffentlichen**.

1. Klicken Sie in der oberen linken Ecke auf den Zurück-Pfeil, und klicken Sie dann auf **Zurück zu SharePoint**.

1. Klicken Sie auf der Befehlsleiste auf **Neu**, um Ihr angepasstes Formular zu öffnen.

1. Klicken Sie mehrmals auf den Schalter **Details**, um die letzten drei Felder ein- oder auszublenden.

Gehen Sie zum [Anpassen Ihres Formulars](sharepoint-form-integration.md) folgendermaßen vor: Öffnen Sie das Formular, und klicken Sie oben im Formular auf **Anpassen**. Nehmen Sie dann Änderungen vor, und speichern und veröffentlichen Sie diese.

Wenn Sie mindestens ein Element mit diesem Formular erstellen, ist das Feld **Title** (Titel) leer. Sie können dieses Feld ausblenden, indem Sie die Standardansicht ändern.

## <a name="use-the-default-form"></a>Verwenden des Standardformulars

1. Öffnen Sie über Ihre Liste in SharePoint die Einstellungen (über das Zahnradsymbol in der oberen rechten Ecke), und klicken Sie dann auf **Listeneinstellungen**.

2. Wählen Sie unter **Allgemeine Einstellungen** **Formulareinstellungen** aus.

3. Wählen Sie eine der folgenden Optionen in den **Formulareinstellungen**, und klicken Sie dann auf **OK**.

    - **Das SharePoint-Standardformular verwenden**: Wenn ein Benutzer Ihre Liste öffnet und auf der Befehlsleiste auf **Neu** klickt, wird das Standardformular für die Liste angezeigt.

    - **Use a custom form created in PowerApps** (Das in PowerApps erstellte Formular verwenden): Wenn ein Benutzer Ihre Liste öffnet und auf der Befehlsleiste auf **Neu** klickt, wird Ihr benutzerdefiniertes Formular angezeigt. (Alternativ können Sie das Formular auch erneut in PowerApps veröffentlichen).

    Sie können nach Bedarf zwischen den Optionen wechseln.

    ![Optionen von „Formulareinstellungen“](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>Benutzerdefiniertes Formular löschen

1. Öffnen Sie über Ihre Liste in SharePoint die Einstellungen (über das Zahnradsymbol in der oberen rechten Ecke), und klicken Sie dann auf **Listeneinstellungen**.

1. Wählen Sie unter **Allgemeine Einstellungen** **Formulareinstellungen** aus.

1. Wählen Sie in den **Formulareinstellungen** **Das SharePoint-Standardformular verwenden** und dann **Delete custom form** (Benutzerdefiniertes Formular löschen) aus.

    ![Benutzerdefiniertes Formular löschen](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>Fragen und Antworten

### <a name="forms-vs-apps"></a>Vergleich: Formulare und Apps

**F:** Wie unterscheidet sich ein benutzerdefiniertes Formular von einer eigenständigen App, die ich in SharePoint oder PowerApps erstelle?

**A:** Wenn Sie das Formular für eine SharePoint-Liste anpassen, wird das Formular nicht als App in PowerApps Studio oder PowerApps Mobile angezeigt. Sie können das Formular nur über die Liste öffnen, für die es erstellt wurde.

**F:** Wann sollte ich ein Formular zum Verwalten von Daten in einer SharePoint-Liste anpassen, und wann sollte ich eine eigenständige App erstellen?

**A:** Passen Sie ein Formular an, wenn Sie möchten, dass Benutzer Daten in SharePoint verwalten (z.B. in einem Desktopbrowser). Erstellen Sie eine App, wenn Sie möchten, dass Benutzer Daten außerhalb von SharePoint verwalten (z.B. auf einem mobilen Gerät).

**F:** Kann ich ein Formular anpassen und für dieselbe Liste eine App erstellen?

**A:** Ja.

**F:** Kann ich eine Liste anpassen und eine App mit den gleichen Features erstellen?

**A:** Ja.

**F:** Kann ich ein Formular in einer anderen Umgebung als der Standardumgebung meiner Organisation anpassen?

**A:** Nein.

### <a name="manage-your-custom-form"></a>Verwalten des benutzerdefinierten Formulars

**F:** Wie kann ich mein Formular unkompliziert mit anderen teilen?

**A:** Öffnen Sie das Formular, klicken Sie auf **Link kopieren**, und schicken Sie den Link an jeden, der das Formular verwenden soll.

**F:** Kann ich ein Formular aktualisieren, ohne dass die Änderungen für andere Personen angezeigt werden?

**A:** Ja. Sie können das Formular so oft ändern und speichern, wie Sie möchten. Die Änderungen werden jedoch erst für andere Benutzer sichtbar, wenn Sie zweimal auf **In SharePoint veröffentlichen** klicken.

**F:** Kann ich eine frühere Version wiederherstellen, wenn mir beim Anpassen eines Listenformulars ein Fehler unterläuft?

**A:** Ja.

1. Öffnen Sie Ihre Liste, klicken Sie auf der Befehlsleiste auf **PowerApps**, und wählen Sie dann **Customize forms** (Formulare anpassen) aus.

1. Klicken Sie in PowerApps Studio auf **Datei** und dann auf **Alle Versionen anzeigen**. Die Seite **Versionen** wird in einer neuen Browserregisterkarte geöffnet.

    > [!NOTE]
    > Wenn die Schaltfläche **Alle Versionen anzeigen** nicht angezeigt wird, klicken Sie auf **Speichern**. Anschließend wird die Schaltfläche angezeigt.

1. Lassen Sie die Seite oder Browserregisterkarte **Versionen** geöffnet, und kehren Sie zur Seite **Speichern** auf der anderen Browserregisterkarte zurück. Klicken oder tippen Sie dann auf den Pfeil am oberen Rand des linken Navigationsbereichs, und klicken oder tippen Sie auf **Zurück zu SharePoint**, um das Formular zu entsperren und PowerApps Studio zu schließen.

1. Kehren Sie zur Seite **Versionen** auf der anderen Browserregisterkarte zurück, suchen Sie die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Wiederherstellen**.

    > [!NOTE]
    > Wenn Sie die Fehlermeldung erhalten, dass die Wiederherstellung fehlgeschlagen ist, da das Formular von einem anderen Benutzer gesperrt ist, warten Sie, bis der Benutzer das Formular entsperrt, und wiederholen Sie den Vorgang.

**F:** Kann ich mein Formular aus einer Liste in eine andere verschieben?

**A:** Nein.

### <a name="administer-your-custom-form"></a>Verwalten des benutzerdefinierten Formulars

**F:** Wie gebe ich mein Formular frei?

**A:** Sie müssen das Formular nicht freigeben – es erbt die Berechtigungen aus der SharePoint-Liste. Wenn Sie es angepasst haben, [veröffentlichen Sie es einfach wieder in SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint), damit es von anderen Benutzern verwendet werden kann.

**F:** Wer kann Formulare anpassen?

**A:** Jeder Benutzer mit SharePoint-Berechtigungen zum Verwalten, Entwerfen oder Bearbeiten der zugehörigen Liste.

**F:** Benötige ich eine PowerApps-Lizenz, um benutzerdefinierte Listenformulare zu erstellen und zu verwenden?

**A:** Sie benötigen [einen Office 365-Plan, der PowerApps beinhaltet](../../administrator/pricing-billing-skus.md#licenses).

**F:** Was geschieht, wenn Gastbenutzer auf eine Liste zuzugreifen, die ein benutzerdefiniertes Formular aufweist?

**A:** Gastbenutzer erhalten eine Fehlermeldung, wenn sie versuchen, auf ein Listenformular zuzugreifen, das mit PowerApps angepasst wurde.

**F:** Wie erhalte ich als Administrator eine Liste aller benutzerdefinierten Formulare in meiner Organisation?

**A:** Wenn Sie ein Mandantenadministrator für PowerApps sind oder über Umgebungsadministratorberechtigungen für die PowerApps-Standardumgebung Ihrer Organisation verfügen, gehen Sie wie folgt vor:

1. Wählen Sie im [PowerApps Admin Center](https://admin.powerapps.com) in der Liste der Umgebungen die Standardumgebung für Ihre Organisation aus.

1. Wählen Sie oben auf der Seite für die Standardumgebung **Ressourcen** aus.

1. Suchen Sie in der Liste der Apps nach Apps mit dem App-Typ **SharePoint-Formular** – dies sind die angepassten Formulare.

    ![Liste der benutzerdefinierten Formulare](./media/customize-list-form/all-customized-forms.png)
