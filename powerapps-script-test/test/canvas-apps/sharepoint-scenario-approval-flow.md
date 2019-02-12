---
title: Erstellen eines Flows zum Verwalten von Projektgenehmigungen | Microsoft-Dokumentation
description: In dieser Aufgabe erstellen wir einen Flow für das Genehmigen von Projekten.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/09/18
ms.author: mblythe
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c17f4cbc4438057e68b1c2ff713a2bfd66228ce9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834595"
---
# <a name="create-a-flow-to-manage-project-approvals"></a>Erstellen eines Flows zum Verwalten von Projektgenehmigungen
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

In dieser Aufgabe erstellen wir einen Flow für das Genehmigen von Projekten. Microsoft Flow ist in SharePoint integriert, daher ist es einfach, einen Flow direkt aus einer Liste zu erstellen. Der Flow, den wir erstellen, wird ausgelöst, wenn der Liste **Project Requests** (Projektanforderungen) ein Element hinzugefügt wird. Der Flow sendet eine E-Mail an den Projektgenehmiger, der die Anforderung direkt in der E-Mail genehmigt oder ablehnt. Anschließend sendet der Flow eine Genehmigungs- oder Ablehnungs-E-Mail an den Projektanforderer und aktualisiert die SharePoint-Listen entsprechend.

## <a name="step-1-configure-the-flow-template"></a>Schritt 1: Konfigurieren der Flowvorlage
1. Klicken oder tippen Sie in der Liste **Project Requests** (Projektanforderungen) auf **Flow** und dann auf **Flow erstellen**.
   
    ![Erstellen eines Flows](./media/sharepoint-scenario-approval-flow/03-01-01-create-flow.png)
2. Klicken oder tippen Sie im rechten Bereich auf **Genehmigung starten, wenn ein neues Element hinzugefügt wird**.
   
    ![Erstellen eines Genehmigungsflows](./media/sharepoint-scenario-approval-flow/03-01-02-approval-flow.png)
3. Wenn Sie noch nicht angemeldet sind, melden Sie sich bei SharePoint und Outlook an, und klicken oder tippen Sie anschließend auf **Weiter**.
   
    ![Anmelden, um Vorlage zu verwenden](./media/sharepoint-scenario-approval-flow/03-01-03-continue.png)
   
    Jetzt wird die Vorlage für diesen Flow angezeigt, die Sie ausfüllen können. Die Felder im Flow stellen Schritte dar. Sie akzeptieren Eingaben aus vorherigen Schritten sowie Ihre Eingaben. Jeder Schritt kann dann die Ausgabe für nachfolgende Schritte bereitstellen.
   
    ![Genehmigungsvorlage](./media/sharepoint-scenario-approval-flow/03-01-04-template.png)
4. Geben Sie im Feld **Zugewiesen zu** einen Namen ein, der im Mandanten gültig ist.
   
    ![Genehmigungs-E-Mail-Kontakt](./media/sharepoint-scenario-approval-flow/03-01-05-approval-email.png)
   
    Das nächste Feld im Flow beantwortet die Entscheidung des Projektgenehmigers und leitet den Flow an eine von zwei *Verzweigungen* weiter: **Wenn ja** oder **Wenn nein**.
   
    ![Genehmigungsbedingung](./media/sharepoint-scenario-approval-flow/03-01-06-condition.png)

## <a name="step-2-create-actions-for-approve--yes"></a>Schritt 2: Erstellen von Aktionen für Genehmigen = ja
Standardmäßig wird mit dieser Verzweigung eine Genehmigungs-E-Mail an den Anforderer gesendet. Wir aktualisieren zudem die Liste **Project Requests** (Projektanforderungen) und fügen der Liste **Project Details** (Projektdetails) ein Element hinzu, da das Projekt genehmigt wurde.

1. Klicken oder tippen Sie in der Verzweigung **Wenn ja** auf **Inform item creator of approval** (Elementersteller über Genehmigung informieren) und dann auf **Bearbeiten**, um die Standardoptionen für die an den Anforderer gesendete E-Mail anzuzeigen.
   
    ![E-Mail-Einstellungen bearbeiten](./media/sharepoint-scenario-approval-flow/03-01-07-yes-email.png)
2. Standardmäßig wird eine E-Mail an die Person gesendet, die das Listenelement erstellt hat, mit der Betreffzeile und dem Nachrichtentext, die angezeigt werden. Sie können diese bei Bedarf aktualisieren.
   
    ![E-Mail-Standardeinstellungen](./media/sharepoint-scenario-approval-flow/03-01-07a-yes-email-defaults.png)
3. Klicken oder tippen Sie auf **Aktion hinzufügen**.
   
    ![Aktion hinzufügen](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. Suchen Sie unter **Aktion auswählen** nach „SharePoint“, und klicken oder tippen Sie dann auf **SharePoint – Element aktualisieren**.
   
    ![Aktion „Element aktualisieren“](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. Geben Sie die URL der SharePoint-Website und den Namen der SharePoint-Liste ein.
   
    ![Parameter für „Element aktualisieren“](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. Wählen Sie das Kästchen **Id** aus, und klicken oder tippen Sie dann im Dialogfeld für *dynamischen Inhalt* auf **ID**.
   
    ![Listen-ID – dynamischer Inhalt](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
   
    Dynamische Inhalte sind im gesamten Flow basierend auf den vorherigen Schritten verfügbar. In diesem Fall sind die SharePoint-Listeninformationen verfügbar, und wir können sie in den von uns erstellten Aktionen verwenden.
7. Wählen Sie das Feld **Title**  (Titel) aus, suchen Sie im Dialogfeld für dynamischen Inhalt nach „Title“, und klicken oder tippen Sie dann auf **Title**.
   
    ![Listentitel – dynamischer Inhalt](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. Geben Sie im Feld **Approved** (Genehmigt) „Ja“ ein. Dieser Teil des Flows sollte jetzt wie in der folgenden Abbildung aussehen.
   
    ![Listenaktualisierung](./media/sharepoint-scenario-approval-flow/03-01-08-yes-update-complete.png)
9. Klicken oder tippen Sie erneut auf **Aktion hinzufügen**. Dieses Mal fügen wir der Liste **Project Details** (Projektdetails) für das von uns genehmigte Projekt ein Element hinzu.
   
    ![Aktion hinzufügen](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
10. Suchen Sie unter **Aktion auswählen** nach „SharePoint“, und wählen Sie dann **SharePoint – Element erstellen** aus.
    
    ![Aktion „Element erstellen“](./media/sharepoint-scenario-approval-flow/03-01-09-create.png)
11. Geben Sie die URL der SharePoint-Website und den Namen der SharePoint-Liste ein.
    
    ![Parameter für „Element erstellen“](./media/sharepoint-scenario-approval-flow/03-01-10-yes-create-list.png)
12. Wählen Sie das Feld **Title**  (Titel) aus, suchen Sie im Dialogfeld für dynamischen Inhalt nach „Title“, und klicken oder tippen Sie dann auf **Title**.
    
    ![Listentitel – dynamischer Inhalt](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
13. Wählen Sie das Kästchen **RequestId** aus, und klicken oder tippen Sie dann im Dialogfeld für dynamischen Inhalt auf **ID**.
    
    ![Listen-ID – dynamischer Inhalt](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
14. Geben Sie im Feld **PMAssigned** (PM zugewiesen) „Nicht zugewiesen“ ein. Dieser Teil des Flows sollte jetzt wie in der folgenden Abbildung aussehen.
    
    ![Erstellen von Element abgeschlossen](./media/sharepoint-scenario-approval-flow/03-01-11-yes-create-complete.png)

## <a name="step-3-review-action-for-approve--no"></a>Schritt 3: Überprüfen der Aktion für Genehmigen = nein
Standardmäßig wird mit dieser Verzweigung eine Ablehnungs-E-Mail an den Anforderer gesendet. Wir aktualisieren zudem die Liste **Project Requests** (Projektanforderungen). Da das Projekt nicht fortgesetzt wird, fügen wir der Liste **Project Details** (Projektdetails) kein Element hinzu.

1. Klicken oder tippen Sie in der Verzweigung **Wenn nein** auf **Inform item creator of rejection** (Elementersteller über Ablehnung informieren) und dann auf **Bearbeiten**, um die Standardoptionen für die an den Anforderer gesendete E-Mail anzuzeigen.
   
    ![E-Mail-Einstellungen bearbeiten](./media/sharepoint-scenario-approval-flow/03-01-12-no-email.png)
2. Standardmäßig wird eine E-Mail an die Person gesendet, die das Listenelement erstellt hat, mit der Betreffzeile und dem Nachrichtentext, die angezeigt werden. Sie können diese bei Bedarf aktualisieren.
   
    ![E-Mail-Standardeinstellungen](./media/sharepoint-scenario-approval-flow/03-01-13-no-email-defaults.png)
3. Klicken oder tippen Sie auf **Aktion hinzufügen**.
   
    ![Aktion hinzufügen](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. Suchen Sie unter **Aktion auswählen** nach „SharePoint“, und klicken oder tippen Sie dann auf **SharePoint – Element aktualisieren**.
   
    ![Aktion „Element aktualisieren“](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. Geben Sie die URL der SharePoint-Website und den Namen der SharePoint-Liste ein.
   
    ![Parameter für „Element aktualisieren“](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. Wählen Sie das Kästchen **Id** aus, und klicken oder tippen Sie dann im Dialogfeld für dynamischen Inhalt auf **ID**.
   
    ![Listen-ID – dynamischer Inhalt](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
7. Wählen Sie das Feld **Title**  (Titel) aus, suchen Sie im Dialogfeld für dynamischen Inhalt nach „Title“, und klicken oder tippen Sie dann auf **Title**.
   
    ![Listentitel – dynamischer Inhalt](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. Geben Sie im Feld **Approved** (Genehmigt) „Nein“ ein. Dieser Teil des Flows sollte jetzt wie in der folgenden Abbildung aussehen.
   
    ![Listenaktualisierung](./media/sharepoint-scenario-approval-flow/03-01-08-no-update-complete.png)
9. Klicken oder tippen Sie am rechten oberen Rand des Bildschirms auf **Flow erstellen**.
   
    Der Flow ist jetzt abgeschlossen, und er sollte wie in der folgenden Abbildung aussehen, wenn Sie die Felder reduzieren.
   
    ![Abgeschlossener Flow](./media/sharepoint-scenario-approval-flow/03-01-16-flow-complete.png)

10. Klicken oder tippen Sie am rechten oberen Rand des Bildschirms auf **Fertig**.
   
    ![Schaltfläche „Fertig“](./media/sharepoint-scenario-approval-flow/03-01-15a-done-button.png)

## <a name="step-4-run-the-approval-flow"></a>Schritt 4: Ausführen des Genehmigungsflows
1. Klicken Sie in der Liste **Project Requests** (Projektanforderungen) auf **QuickEdit**, und fügen Sie das folgende Element hinzu:
   
   * **Title** = "New monitor for Megan" (Neuer Monitor für Megan)

   * **Description** = "Megan needs a 24" monitor" (Megan benötigt einen 24"-Monitor)

   * **ProjectType** = "New hardware"

   * **RequestDate** = "02/03/2017"

   * **Requestor** = "Megan Bowen"

   * **EstimatedDays** = "1"

   * **Approved** = "Pending" (Ausstehend)

     ![Der Liste hinzugefügtes Element](./media/sharepoint-scenario-approval-flow/03-02-01-list-add.png)
2. Klicken Sie am oberen Rand der Seite auf **Fertig**, wenn Sie den Vorgang abgeschlossen haben.
   
    ![Häkchen für „Fertig“](./media/sharepoint-scenario-approval-flow/03-02-02-done.png)
3. Überprüfen Sie im E-Mail-Konto des Genehmigers den Posteingang. Sie sollten jetzt über eine E-Mail wie die folgende verfügen.
   
    ![E-Mail an Allan Deyoung](./media/sharepoint-scenario-approval-flow/03-02-03-allan-email.png)
4. Nachdem Sie auf **Genehmigen** oder **Ablehnen** geklickt haben, führt der Flow einen weiteren Prozess aus, und Sie erhalten direkt in der E-Mail Feedback wie das folgende.
   
    ![Genehmigungsaktion abgeschlossen](./media/sharepoint-scenario-approval-flow/03-02-04-action-complete.png)
5. Der Flow sendet eine E-Mail mit Allans Antwort an Megan, wie in der folgenden Abbildung. Diese E-Mail wird *von* Megan gesendet, da sie die Besitzerin des Flows ist.
   
    ![E-Mail an Megan Bowen](./media/sharepoint-scenario-approval-flow/03-02-05-megan-email.png)

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Tutorialreihe ist das [Erstellen einer App zum Verwalten von Projekten](sharepoint-scenario-build-app.md).

