---
title: Einbetten des Power BI-Projektberichts in SharePoint Online | Microsoft-Dokumentation
description: In dieser Aufgabe betten wir den Power BI-Bericht in die gleiche SharePoint Online-Website ein, auf der auch die zwei Listen gehostet werden.
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
ms.openlocfilehash: 9d15001795cc33d163e85b358a52aba759c83021
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865434"
---
# <a name="embed-the-power-bi-project-report-in-sharepoint-online"></a>Einbetten des Power BI-Projektberichts in SharePoint Online
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

Jetzt betten wir den Power BI-Bericht in die gleiche SharePoint Online-Website ein, auf der auch die zwei Listen gehostet werden. Power BI unterstützt eine Vielzahl von Ansätzen für das Einbetten, einschließlich der direkten Integration in SharePoint-Seiten für Webansichten und mobile Ansichten.

Bei dieser Art von Einbettung bettet Power BI den Bericht als Webpart ein, gewährt Benutzern den entsprechenden Zugriff und ermöglicht das Durchklicken vom eingebetteten Bericht zum Bericht auf „powerbi.com“. Zunächst generieren wir einen Einbettungslink in Power BI, und anschließend wird dieser Link auf einer erstellten Seite verwendet. Weitere Informationen zum Einbetten finden Sie unter [Einbetten mit Berichts-Webpart in SharePoint Online](https://docs.microsoft.com/power-bi/service-embed-report-spo).

## <a name="step-1-generate-an-embed-link"></a>Schritt 1: Generieren eines Einbettungslinks
1. Melden Sie sich bei Power BI an, und klicken oder tippen Sie dann im linken Navigationsbereich auf den Namen des Berichts.
   
    ![Navigieren zum Bericht](./media/sharepoint-scenario-embed-report/08-01-01-reports.png)
2. Klicken oder tippen Sie auf **Datei** und dann auf **In SharePoint Online einbetten**.
   
    ![In SharePoint Online einbetten](./media/sharepoint-scenario-embed-report/08-01-02-embed-spo.png)
3. Kopieren Sie den Einbettungslink aus dem Dialogfeld in eine Datei, und klicken oder tippen Sie dann auf **Schließen**. Wir verwenden den Link nach dem Erstellen einer SharePoint-Seite.
   
    ![Einbettungslink für SharePoint](./media/sharepoint-scenario-embed-report/08-01-03-embed-url.png)

## <a name="step-2-embed-the-report"></a>Schritt 2: Einbetten des Berichts
1. Melden Sie sich bei SharePoint an, und klicken oder tippen Sie auf **Websiteinhalte**.
   
    ![„Websiteinhalte“ in SharePoint](./media/sharepoint-scenario-embed-report/08-01-04-site-contents.png)
2. Sie können einfach einen Bericht auf der Teamstartseite einschließen. Hier wird jedoch veranschaulicht, wie Sie auch eine separate Seite für den Bericht erstellen können. Klicken oder tippen Sie auf **Neu** und dann auf **Seite**.
   
    ![Neue SharePoint-Seite](./media/sharepoint-scenario-embed-report/08-01-05-new-page.png)
3. Geben Sie einen Namen für die Seite ein, beispielsweise „Project Analysis“.
4. Klicken oder tippen Sie auf das ![Pluszeichen](./media/sharepoint-scenario-embed-report/icon-plus.png) und anschließend auf **Power BI**.
   
    ![Webpart für Power BI-Seite](./media/sharepoint-scenario-embed-report/08-01-06-add-page-part.png)
5. Klicken oder tippen Sie auf **Bericht hinzufügen**.
   
    ![Bericht hinzufügen](./media/sharepoint-scenario-embed-report/08-01-07-add-report.png)
6. Kopieren Sie im rechten Bereich die Einbettungs-URL in das Feld **Power BI report link** (Power BI-Berichtslink). Legen Sie die Optionen **Filterbereich anzeigen** und **Navigationsbereich anzeigen** auf **Ein** fest.
   
    ![Berichtseinstellungen](./media/sharepoint-scenario-embed-report/08-01-08-report-settings.png)
7. Der Bericht ist nun auf der Seite eingebettet. Klicken Sie auf **Veröffentlichen**, um ihn für alle Personen zugänglich zu machen, die auf den zugrunde liegenden Bericht zugreifen können.
   
    ![Einbetten des Berichts abgeschlossen](./media/sharepoint-scenario-embed-report/08-01-09-report-complete.png)

## <a name="step-3-grant-access-to-the-report"></a>Schritt 3: Gewähren des Zugriffs auf den Bericht.
Bei Verwendung von Office 365-Gruppen (dies wird empfohlen) müssen Sie sicherstellen, dass Benutzer, die Zugriff benötigen, Mitglieder des Gruppenarbeitsbereichs im Power BI-Dienst sind. Dadurch ist sichergestellt, dass Benutzer den Inhalt dieser Gruppe anzeigen können. Weitere Informationen finden Sie unter [Zusammenarbeit in Ihrem Power BI-App-Arbeitsbereich](https://docs.microsoft.com/power-bi/service-collaborate-power-bi-workspace).

Damit sind unsere Aufgaben in Power BI für dieses Szenario abgeschlossen. Sie haben begonnen, indem Sie Daten aus unseren SharePoint-Listen in Power BI abgerufen haben, und der Kreis schließt sich nun, da Sie Ihren Power BI-Bericht wieder in SharePoint eingebettet haben.

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Reihe von Tutorials besteht im [Durchlaufen des Workflows von Anfang bis Ende](sharepoint-scenario-summary.md).

