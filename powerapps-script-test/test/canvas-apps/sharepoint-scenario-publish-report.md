---
title: Veröffentlichen des Power BI-Projektberichts und Erstellen eines Dashboards | Microsoft-Dokumentation
description: In dieser Aufgabe veröffentlichen wir unser Dataset und den Bericht im Power BI-Dienst. Anschließend wird auf der Grundlage des Berichts ein Dashboard erstellt.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/30/2018
ms.author: mblythe
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f5a39ec04015fe360bc550d9ea4f708d887ba34c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833872"
---
# <a name="publish-the-power-bi-project-report-and-create-a-dashboard"></a>Veröffentlichen des Power BI-Projektberichts und Erstellen eines Dashboards
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

In dieser Aufgabe veröffentlichen wir unser Dataset und den Bericht im Power BI-Dienst. Anschließend wird auf der Grundlage des Berichts ein Dashboard erstellt. Ein Bericht enthält häufig eine große Anzahl von Visualisierungen, und im Dashboard wird lediglich eine Teilmenge davon verwendet. In diesem Fall werden dem Dashboard alle vier Visualisierungen hinzugefügt.

## <a name="step-1-publish-the-dataset-and-report"></a>Schritt 1: Veröffentlichen des Datasets und des Berichts
1. Klicken oder tippen Sie in Power BI Desktop auf der Registerkarte **Start** auf **Veröffentlichen**.
   
    ![Veröffentlichen des Datasets und des Berichts](./media/sharepoint-scenario-publish-report/06-01-01-publish.png)
2. Wenn Sie noch nicht beim Power BI-Dienst angemeldet sind, geben Sie ein Konto ein, und klicken oder tippen Sie dann auf **Anmelden**.
   
    ![Anmelden beim Konto](./media/sharepoint-scenario-publish-report/06-01-02-account.png)
3. Geben Sie ein Kennwort ein, klicken oder tippen Sie auf **Anmelden**.
   
    ![Eingeben des Kennworts für das Konto](./media/sharepoint-scenario-publish-report/06-01-03-password.png)
4. Wählen Sie ein Ziel für den Bericht aus, und klicken oder tippen Sie auf **Auswählen**. Es wird empfohlen, den Bericht in einem Gruppenarbeitsbereich zu veröffentlichen, um den Zugriff auf den Bericht in SharePoint zu erleichtern. In diesem Fall veröffentlichen wir den Bericht im Gruppenarbeitsbereich **Projektmanagement**. Weitere Informationen finden Sie unter [Zusammenarbeit in Ihrem Power BI-App-Arbeitsbereich](https://docs.microsoft.com/power-bi/service-collaborate-power-bi-workspace).
   
    ![Zielarbeitsbereich](./media/sharepoint-scenario-publish-report/06-01-04-workspace.png)
5. Klicken oder tippen Sie nach abgeschlossener Veröffentlichung auf **„project-analysis.pbx“ in Power BI öffnen**.
   
    ![Erfolgreiche Veröffentlichung](./media/sharepoint-scenario-publish-report/06-01-05-open-report.png)
6. Der Power BI-Dienst lädt den Bericht in einem Browser. Wenn der linke Navigationsbereich nicht angezeigt wird, klicken oder tippen Sie auf das Menü oben links **(a)**, um ihn einzublenden.
   
    ![Bericht im Power BI-Dienst](./media/sharepoint-scenario-publish-report/06-01-06-service-report.png)
   
    Sie stellen fest, dass von Power BI Desktop beim Veröffentlichen ein Dataset **(d)** und einen Bericht **(c)** hochgeladen wurde. Sie erstellen Dashboards im Dienst, nicht Power BI Desktop, und in diesem Arbeitsbereich sind noch keine Dashboards vorhanden **(b)**. Wir werden in Kürze eines erstellen.

## <a name="step-2-configure-credentials-for-refresh"></a>Schritt 2: Konfigurieren von Anmeldeinformationen für die Aktualisierung
1. Klicken oder tippen Sie im Dienst in der rechten oberen Ecke auf das ![Zahnradsymbol](./media/sharepoint-scenario-publish-report/icon-gear.png), und klicken oder tippen Sie anschließend auf **Einstellungen**.
2. Klicken oder tippen Sie auf **Datasets** und anschließend auf **project-analysis**.
   
    ![Dataset „project-analysis“](./media/sharepoint-scenario-publish-report/06-01-07-dataset.png)
3. Erweitern Sie **Datenquellen-Anmeldeinformationen**, und klicken oder tippen Sie auf **Anmeldeinformationen bearbeiten**.
   
    ![Bearbeiten der Datenquellen-Anmeldeinformationen](./media/sharepoint-scenario-publish-report/06-01-08-credentials.png)
4. Wählen Sie als Authentifizierungsmethode **OAuth2** aus, und klicken oder tippen Sie dann auf **Anmelden**.
   
    ![Anmelden bei SharePoint](./media/sharepoint-scenario-publish-report/06-01-09-sign-in.png)
5. Wählen Sie ein Konto aus, bzw. melden Sie sich bei einem Konto an, das über Berechtigungen für die SharePoint-Listen verfügt.
   
    ![Angemeldet bei Office 365](./media/sharepoint-scenario-publish-report/06-01-10-account.png)
   
    Bei Abschluss des Prozesses wird im Dienst die folgende Meldung ausgegeben.
   
    ![Datenquelle aktualisiert](./media/sharepoint-scenario-publish-report/06-01-11-updated.png)

## <a name="step-3-create-a-dashboard"></a>Schritt 3: Erstellen eines Dashboards

1. Um zum Bericht zurückzukehren, klicken oder tippen Sie unter **BERICHTE** auf **project-analysis**.

1. Klicken oder tippen Sie auf das Diagramm oben links, und klicken oder tippen Sie dann auf ![Anheften-Symbol](./media/sharepoint-scenario-publish-report/icon-pin.png).
   
    ![Diagramm anheften](./media/sharepoint-scenario-publish-report/06-01-12-pin-projected.png)
2. Geben Sie einen Namen für das Dashboard ein, an welches das Diagramm angeheftet werden soll, und klicken oder tippen Sie auf **Anheften**.
   
    ![Anheften des Diagramms an das neue Dashboard](./media/sharepoint-scenario-publish-report/06-01-13-pin-new.png)
3. Klicken oder tippen Sie auf das Diagramm oben rechts, und klicken oder tippen Sie dann auf ![Anheften-Symbol](./media/sharepoint-scenario-publish-report/icon-pin.png).
   
    ![Diagramm anheften](./media/sharepoint-scenario-publish-report/06-01-14-pin-variance.png)
4. Wählen Sie das vorhandene Dashboard aus, und klicken oder tippen Sie dann auf **Anheften**.
   
    ![Anheften des Diagramms an das vorhandene Dashboard](./media/sharepoint-scenario-publish-report/06-01-15-pin-existing.png)

5. Wiederholen Sie den Anheftvorgang für die übrigen beiden Visuals.

6. Klicken oder tippen Sie im linken Navigationsbereich auf den Namen des Dashboards.
   
    ![Neues Dashboard in der Websitenavigation](./media/sharepoint-scenario-publish-report/06-01-16-dashboard-menu.png)

7. Überprüfen Sie das Dashboard. Wenn Sie auf eine Kachel klicken, kehren Sie zurück zum Bericht.
   
    ![Fertiges Dashboard](./media/sharepoint-scenario-publish-report/06-01-17-dashboard-completed.png)

Damit ist der Großteil der Arbeiten in Power BI abgeschlossen. Wenn dies das erste Mal war, dass Sie Berichte und Dashboards erstellt haben – herzlichen Glückwunsch! Wenn Sie bereits ein Profi sind, haben Sie diese Aufgabe hoffentlich schnell durchgearbeitet. Nun fügen wir Warnungen hinzu, um sicherzustellen, dass wir ggf. benachrichtigt werden, falls das Dashboard unsere Aufmerksamkeit benötigt.

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Reihe von Tutorials besteht im [Einrichten von Datenwarnungen für den Power BI-Projektbericht](sharepoint-scenario-alerts-flow.md).

