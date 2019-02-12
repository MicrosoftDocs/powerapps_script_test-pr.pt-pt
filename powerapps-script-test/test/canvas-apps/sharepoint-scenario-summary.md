---
title: Vollständige exemplarische Vorgehensweise für das Szenario der SharePoint Online-Integration | Microsoft-Dokumentation
description: Befolgen Sie die vollständige exemplarische Vorgehensweise für das Szenario, das wir in dieser Reihe von Tutorials entwickelt haben.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: mblythe
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: df3c186bb41621e7ec6087a9da55fc037e286b1a
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42850188"
---
# <a name="walk-end-to-end-through-the-completed-sharepoint-online-integration-scenario"></a>Vollständige exemplarische Vorgehensweise für das komplette Szenario der SharePoint Online-Integration
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

Wir haben in dieser Reihe von Tutorials eine enorme Anzahl von Themen behandelt – vom Erstellen von Apps und Flows bis hin zum Erstellen von Berichten und dem Einbetten dieser Berichte in SharePoint. Wir hoffen, dass Sie viel gelernt haben und jetzt wissen, wie diese Technologien ineinandergreifen, sodass Sie Canvas-Apps, Flows und Berichte entsprechend Ihren Anforderungen in SharePoint integrieren können. Vor dem Abschluss dieser Reihe möchten wir das Szenario vollständig durchgehen und betrachten, wie alle Teile zusammenwirken.

## <a name="step-1-add-a-project-to-the-project-requests-list"></a>Schritt 1: Hinzufügen eines Projekts zur Liste „Project Requests“ (Projektanforderungen)
1. Klicken oder tippen Sie in der Liste **Project Requests**  (Projektanforderungen) auf **Alle Elemente** und dann auf **Project Requests app** (Projektanforderungen-App).
   
    ![Ansicht „Project Requests app“ (Projektanforderungen-App)](./media/sharepoint-scenario-summary/09-00-01-view-app.png)
2. Klicken Sie auf **Öffnen**, um die App in einer neuen Browserregisterkarte zu öffnen.
   
    ![Projektanforderungen-App öffnen](./media/sharepoint-scenario-summary/09-00-02-open-app.png)
3. Klicken oder tippen Sie in der App auf ![Symbol „Element hinzufügen“](./media/sharepoint-scenario-summary/icon-add-item.png) , um ein neues Element zu erstellen.
4. Füllen Sie das Formular mit den folgenden Werten aus:
   
   * **Title** = "Mobile devices for design team" (Mobile Geräte für das Entwurfsteam)

   * **Approved** = "Pending" (Ausstehend)

   * **Description** = "The design team will now use Contoso-supplied devices" (Das Entwurfsteam verwendet jetzt von Contoso bereitgestellte Geräte)

   * **EstimatedDays** = "30"

   * **ProjectType** = "New hardware"

   * **RequestDate** = "03/01/2017"

   * **Requestor** = "Emily Braun"
     
     ![Bearbeitungsformular für Projektanforderungen](./media/sharepoint-scenario-summary/09-01-01-app-new.png)
5. Klicken oder tippen Sie auf ![Häkchensymbol](./media/sharepoint-scenario-summary/icon-check-mark.png), und schließen Sie dann die Browserregisterkarte.
6. Kehren Sie zur Liste **Project Requests** (Projektanforderungen) zurück, klicken oder tippen Sie auf **Project Requests app** (Projektanforderungen-App) und dann auf **Alle Elemente**.
   
    ![Alle Elemente anzeigen](./media/sharepoint-scenario-summary/09-01-01a-view-all.png)
7. Überprüfen Sie den neuen Eintrag in der Liste.
   
    ![SharePoint-Liste mit neuem Eintrag](./media/sharepoint-scenario-summary/09-01-02-list-new.png)

## <a name="step-2-approve-the-project"></a>Schritt 2: Genehmigen des Projekts
1. Wenn Sie in Schritt 1 das Element hinzufügen, wird der Flow ausgeführt und eine Genehmigungs-E-Mail gesendet. Überprüfen Sie im E-Mail-Konto des Genehmigers den Posteingang.
   
    ![E-Mail mit Genehmigungsanforderung](./media/sharepoint-scenario-summary/09-02-01-allan-email.png)
2. Klicken Sie auf **Genehmigen**. Der Flow führt einen weiteren Prozess aus, und Sie erhalten direkt in der E-Mail Feedback wie das folgende.
   
    ![Aktion abgeschlossen](./media/sharepoint-scenario-summary/09-02-01a-action-complete.png)
3. Überprüfen Sie im E-Mail-Konto des Anforderers den Posteingang. Dort sollte eine Genehmigungs-E-Mail angezeigt werden.
   
    ![Genehmigungs-E-Mail an den Anforderer](./media/sharepoint-scenario-summary/09-02-02-megan-email.png)
4. Überprüfen Sie den aktualisierten Eintrag in der Liste.
   
    ![SharePoint-Liste mit aktualisiertem Eintrag](./media/sharepoint-scenario-summary/09-02-03-yes.png)

## <a name="step-3-assign-a-manager-to-the-project"></a>Schritt 3: Zuweisen eines Managers zum Projekt
1. Betrachten wir zunächst die Liste **Project Details** (Projektdetails) in SharePoint. Das neue Projekt hat in der Spalte **PMAssigned** den Wert **Nicht zugewiesen**.
   
    ![SharePoint-Listenelement „Nicht zugewiesen“](./media/sharepoint-scenario-summary/09-03-01-unassigned.png)
2. Klicken oder tippen Sie auf der SharePoint-Website im linken Navigationsbereich auf **Project Management app** (Projektmanagement-App).
3. Klicken oder tippen Sie im ersten Bildschirm auf **Assign Manager** (Manager zuweisen).
   
    ![Manager dem Projekt zuweisen](./media/sharepoint-scenario-summary/09-03-02-intro-screen.png)
4. Im Bildschirm **Assign Manager** (Manager zuweisen) werden die beiden nicht zugewiesenen Projekte aus der Liste angezeigt. Wählen Sie das Projekt **Mobile devices for design team** (Mobile Geräte für das Entwurfsteam) aus.
   
    ![In App ausgewähltes Projekt, das nicht zugewiesen ist](./media/sharepoint-scenario-summary/09-03-03-selected.png)
5. Geben Sie im Textfeld **Manager** den Namen „Joni Sherman“ ein, und klicken Sie dann auf **OK**.
   
    Die Änderung wird auf die Liste angewendet, und der Katalog wird aktualisiert, sodass nur das noch nicht zugewiesene Projekt angezeigt wird.
   
    ![Dem Projekt zugewiesener Manager](./media/sharepoint-scenario-summary/09-03-04-updated.png)
6. Schließen Sie die App, und kehren Sie zur SharePoint-Liste zurück. Sie werden feststellen, dass der Projekteintrag mit dem Namen des Projektmanagers aktualisiert wurde.
   
    ![Zugewiesenes SharePoint-Listenelement](./media/sharepoint-scenario-summary/09-03-05-assigned.png)

## <a name="step-4-add-time-estimates-for-the-project"></a>Schritt 4: Hinzufügen von geschätzten Zeiten für das Projekt
1. Klicken oder tippen Sie auf ![Symbol „Zurück“](./media/sharepoint-scenario-summary/icon-back.png), um zum ersten Bildschirm zurückzukehren, und klicken oder tippen Sie dann auf **Update Details** (Details aktualisieren).
   
    ![Projektdetails aktualisieren](./media/sharepoint-scenario-summary/09-04-00-intro-screen.png)
2. Geben Sie im Bildschirm **View Projects** (Projekte anzeigen) im Suchfeld „Mobil“ ein.
   
    ![In der App suchen](./media/sharepoint-scenario-summary/09-04-01-search-mobile.png)
3. Klicken Sie für das Element **Mobile devices for design team** (Mobile Geräte für das Entwurfsteam) auf ![Pfeilsymbol „Details“](./media/sharepoint-scenario-summary/icon-details-arrow.png).
   
    ![Zu aktualisierendes Projekt auswählen](./media/sharepoint-scenario-summary/09-04-02-select-project.png)
4. Legen Sie im Bildschirm **Update Details** (Details aktualisieren) die folgenden Werte fest:
   
   * Das Feld **Status** = "Not started" (Nicht gestartet)

   * Das Feld **ProjectedStartDate** = "3/6/2017"

   * Das Feld **ProjectedEndDate** = "3/24/2017"

   * Das Feld **ProjectedDays** = "15"
     
     ![Projektdetails aktualisieren](./media/sharepoint-scenario-summary/09-04-03-update.png)
5. Klicken oder tippen Sie auf ![Häkchensymbol](./media/sharepoint-scenario-summary/icon-check-mark.png) , um die Änderung auf die SharePoint-Liste anzuwenden.
6. Schließen Sie die App, und kehren Sie zur Liste zurück. Sie werden feststellen, dass der Projekteintrag mit den Änderungen der Datumsangaben und Tagesanzahl aktualisiert wurde.
   
   ![In SharePoint-Liste aktualisierte Details](./media/sharepoint-scenario-summary/09-04-04-updated-list.png)

## <a name="step-5-review-report-data-for-existing-projects"></a>Schritt 5: Überprüfen der Berichtsdaten für vorhandene Projekte
1. Klicken oder tippen Sie in SharePoint Online auf **Websiteinhalte** und dann auf **Websiteseiten**.
2. Öffnen Sie die Seite **Project Analysis** (Projektanalyse), die wir zuvor erstellt haben.
   
    ![Eingebetteter Projektanalysebericht](./media/sharepoint-scenario-summary/09-05-01-report-complete.png)
3. Überprüfen Sie die Visualisierung der Varianz.
   
    ![Diagramm, in dem die Varianz angezeigt wird](./media/sharepoint-scenario-summary/09-05-02-chart-variance.png)
   
    Wie bereits beim Erstellen dieser Visualisierung festgestellt, gibt es noch weitaus mehr Varianz für Projekte, die von Irvin Sayers/Joni Sherman ausgeführt wurden.
4. Wenn Sie einen Drilldown der Visualisierung ausführen, stellen Sie fest, dass ein großer Anteil der Varianz aus Projekten stammt, für die weitaus mehr Zeit als erwartet benötigt wurde.
   
    ![Diagramm, in dem Varianzdetails angezeigt werden](./media/sharepoint-scenario-summary/09-05-03-chart-variance-drill.png)
5. Überprüfen Sie die Tabelle, in der angezeigt wird, wie viel Zeit zwischen der Genehmigung von Projekten bis zum voraussichtlichen Startdatum liegt.
   
    ![Tabelle, in der Unterschiede beim Startdatum angezeigt werden](./media/sharepoint-scenario-summary/09-05-04-chart-diff-completed.png)
   
    Wie bereits beim Erstellen dieser Visualisierung festgestellt, benötigen die Projekte, die Irvin Sayers zugewiesen sind, mehr Zeit bis zum Start, und zwei Projekte erfordern viel mehr Zeit als die restlichen Projekte.

## <a name="step-6-respond-to-pending-project-delays"></a>Schritt 6: Reagieren auf Verzögerungen bei ausstehenden Projekten
1. Klicken oder tippen Sie im Power BI-Dienst auf das Dataset **project-analysis** und dann auf **JETZT AKTUALISIEREN**. Die Aktualisierung löst die Warnung aus, die wir für ausstehende Projekte eingerichtet haben.
   
    ![Dataset jetzt aktualisieren](./media/sharepoint-scenario-summary/09-06-01-refresh.png)
2. Nach dem Abschluss der Aktualisierung wird in der **Mitteilungszentrale** rechts oben ein neues Benachrichtigungssymbol angezeigt.
   
    ![Power BI-Mitteilungszentrale](./media/sharepoint-scenario-summary/09-06-02-alert.png)
   
    Dies kann einige Zeit dauern. Überprüfen Sie daher die Mitteilungszentrale später erneut, wenn das Symbol nicht sofort angezeigt wird.
3. Öffnen Sie die Mitteilungszentrale, um die Details der ausgelösten Warnung anzuzeigen.
   
    ![Benachrichtigung für Datenwarnung](./media/sharepoint-scenario-summary/09-06-03-notification.png)
4. Überprüfen Sie den Posteingang der Person, von der die Warnung erstellt wurde (in unserem Fall Megan Bowen).
   
    ![Benachrichtigungs-E-Mail von Power BI](./media/sharepoint-scenario-summary/09-06-04-email-powerbi.png)
5. Überprüfen Sie den Posteingang der Person, die Sie im Flow für Datenwarnungen hinzugefügt haben (in unserem Fall Allan DeYoung).
   
    ![Benachrichtigungs-E-Mail von Microsoft Flow](./media/sharepoint-scenario-summary/09-06-05-email-flow.png)
6. Da Sie jetzt über Informationen zu ausstehenden Projekten verfügen, können Sie zurückkehren und Projekte genehmigen, deren Bearbeitung durch Sie noch aussteht.

Damit gelangen wir zum Abschluss der vollständigen exemplarischen Vorgehensweise und dieser Reihe von Tutorials. Wir empfehlen Ihnen den Besuch der folgenden Websites:

* [PowerApps](http://www.powerapps.com/)
* [Microsoft Flow](http://flow.microsoft.com)
* [Power BI](http://www.powerbi.com)
* [Poweruser-Community](https://powerusers.microsoft.com/)
* [SharePoint](http://sharepoint.microsoft.com)
* [Technische Microsoft-Community](https://techcommunity.microsoft.com/)

In den Kommentaren können Sie Feedback zu dieser Reihe geben und uns Vorschläge für Ergänzungen oder Ideen für zusätzliche Inhalte, die Ihnen die Arbeit mit den hier behandelten Technologien erleichtern, mitteilen.

