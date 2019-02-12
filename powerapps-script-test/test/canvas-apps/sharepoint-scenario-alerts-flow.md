---
title: Einrichten von Datenwarnungen für das Power BI-Dashboard | Microsoft-Dokumentation
description: In dieser Aufgabe wird Power BI eine Warnung hinzugefügt, die mitteilt, ob die Genehmigung ausstehender Projekte zu lange dauert, sowie ein Flow, der bei Auftreten dieser Warnung reagiert.
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
ms.openlocfilehash: 6426dedc9ce9d1a4648f9c880a53337767ec53d3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836393"
---
# <a name="set-up-data-alerts-for-the-power-bi-dashboard"></a>Einrichten von Datenwarnungen für das Power BI-Dashboard
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

In dieser Aufgabe wird Power BI eine Warnung hinzugefügt, mit der informiert wird, ob die Genehmigung ausstehender Projekte zu lange dauert, sowie einen Flow, der bei Auftreten dieser Warnung reagiert. Weitere Informationen zu Warnungen finden Sie unter [Datenwarnungen im Power BI-Dienstservice](https://docs.microsoft.com/power-bi/service-set-data-alerts).

## <a name="step-1-create-an-alert"></a>Schritt 1: Erstellen einer Warnung
1. Öffnen Sie im Power BI-Dienst das Dashboard, das Sie in der vorherigen Aufgabe erstellt haben.
2. Klicken oder tippen Sie auf der Karte mit der Zahl auf die Auslassungspunkte (**. . .**).
   
    ![Karte „Max days pending approval“ (Max. Anzahl Tage ausstehende Genehmigung)](./media/sharepoint-scenario-alerts-flow/07-01-01-tile-ellipsis.png)
3. Klicken oder tippen Sie auf ![Glockensymbol](./media/sharepoint-scenario-alerts-flow/icon-bell.png).
   
    ![Kachel-Menü](./media/sharepoint-scenario-alerts-flow/07-01-02-tile-bell.png)
4. Klicken oder tippen Sie im rechten Bereich auf **Warnungsregel hinzufügen**.
   
    ![Warnungsregel hinzufügen](./media/sharepoint-scenario-alerts-flow/07-01-03-add-alert.png)
5. Betrachten Sie die Optionen, die für Warnungen verfügbar sind, beispielsweise die Häufigkeit für die Ausführung einer Warnung. Geben Sie für **Schwellenwert** den Wert 25 ein, und klicken oder tippen Sie anschließend auf **Speichern und schließen**.
   
    ![Festlegen und Speichern eines Schwellenwerts für Warnungen](./media/sharepoint-scenario-alerts-flow/07-01-04-save-alert.png)

Die Warnung wird nicht sofort ausgelöst, obwohl der Wert 56 über dem Schwellenwert 25 liegt. Sie wird beim Aktualisieren der Daten ausgelöst. Dies wird beim [vollständigen Durcharbeiten des Szenarios](sharepoint-scenario-summary.md) veranschaulicht.

Beim Auslösen der Warnung sendet Power BI eine E-Mail an den Ersteller der Warnung, und im nächsten Schritt erfahren Sie, wie zusätzliche E-Mails mit Microsoft Flow gesendet werden.

## <a name="step-2-create-a-flow-that-responds-to-the-alert"></a>Schritt 2: Erstellen eines Flows, der auf die Warnung reagiert
1. Melden Sie sich bei flow.microsoft.com an, und klicken oder tippen Sie auf **Dienste** und anschließend auf **Power BI**.
   
    ![Power BI in Microsoft Flow](./media/sharepoint-scenario-alerts-flow/07-01-05-power-bi.png)
2. Klicken oder tippen Sie auf **Eine E-Mail an eine beliebige Zielgruppe senden, sobald durch Power BI-Daten eine Warnung ausgelöst wird**.
   
    ![Eine E-Mail an eine beliebige Zielgruppe senden, sobald durch Power BI-Daten eine Warnung ausgelöst wird](./media/sharepoint-scenario-alerts-flow/07-01-06-alert-flow.png)
3. Klicken oder tippen Sie auf **Diese Vorlage verwenden**.
4. Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Outlook und Power BI an, und klicken oder tippen Sie anschließend auf **Weiter**.
   
    ![Anmelden und fortfahren](./media/sharepoint-scenario-alerts-flow/07-01-08-continue.png)
5. Wählen Sie in der Dropdownliste **Warnungs-ID** den Eintrag **Alert for Max days pending approval** (Warnung für Max. Anzahl Tage ausstehende Genehmigung) aus.
   
    ![Angeben und Warnung als Trigger](./media/sharepoint-scenario-alerts-flow/07-01-09-choose-alert.png)
6. Geben Sie im Feld **An** eine gültige E-Mail-Adresse ein.
   
    ![Angeben des Empfängers der E-Mail](./media/sharepoint-scenario-alerts-flow/07-01-10-choose-email.png)
7. Klicken oder tippen Sie auf **Bearbeiten**, um weitere Felder einzublenden, die bearbeitet werden können.
   
    ![Bearbeiten der E-Mail-Adresse für Warnungen](./media/sharepoint-scenario-alerts-flow/07-01-11-email-full.png)
8. Klicken Sie am rechten oberen Rand des Bildschirms auf **Flow erstellen** und anschließend auf **Fertig**.
   
    ![Schaltfläche „Fertig“](./media/sharepoint-scenario-alerts-flow/07-01-12-done.png)

Die Flowausführung wird beim [vollständigen Durcharbeiten des Szenarios](sharepoint-scenario-summary.md) veranschaulicht. Kommen wir nun zur letzten Aufgabe in diesem Szenario – zum Einbetten eines Power BI-Berichts in SharePoint.

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Reihe von Tutorials besteht im [Einbetten des Power BI-Projektberichts in SharePoint Online](sharepoint-scenario-embed-report.md).

