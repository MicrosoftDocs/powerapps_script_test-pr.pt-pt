---
title: Einrichten von Listen für die Integration von SharePoint Online in PowerApps, Microsoft Flow und Power BI | Microsoft-Dokumentation
description: In dieser Aufgabe richten wir SharePoint-Listen als Datenquelle für Apps, Flows, Berichte und Dashboards ein.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/19/2017
ms.author: mblythe
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9e1694a3190740c788eb9cd53de1187ed32d0fbc
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833318"
---
# <a name="set-up-lists-for-sharepoint-online-integration-with-powerapps-microsoft-flow-and-power-bi"></a>Einrichten von Listen für die Integration von SharePoint Online in PowerApps, Microsoft Flow und Power BI
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

SharePoint bietet zahllose Features für Freigabe und Zusammenarbeit, für dieses Szenario konzentrieren wir uns jedoch auf [SharePoint-Listen](https://support.office.com/article/Introduction-to-lists-0A1C3ACE-DEF0-44AF-B225-CFA8D92C52D7). Eine Liste ist einfach eine Sammlung von Daten, die Sie für Teammitglieder und andere Websitebenutzer freigeben können. Wir beschreiben die für dieses Szenario verwendeten Listen. Anschließend können Sie sie auf der eigenen SharePoint Online-Website erstellen.

## <a name="step-1-understand-the-lists"></a>Schritt 1: Verstehen der Listen
Die erste Liste lautet **Project Requests** (Projektanforderungen). Dieser fügt ein Projektanforderer eine Anforderung hinzu. Anschließend überprüft der Projektgenehmiger die Anforderung und genehmigt sie oder lehnt sie ab.

| **Listenspalte** | **Datentyp** | **Anmerkungen** |
| --- | --- | --- |
| Title |Eine Textzeile |Standardspalte, wird für den Projektnamen verwendet |
| Beschreibung |Eine Textzeile | |
| ProjectType |Eine Textzeile |Werte: „New hardware“ (Neue Hardware), „Hardware update“ (Hardwareaktualisierung), „New software“ (Neue Software), „Software update“ (Softwareupdate) |
| RequestDate |Datum | |
| Requestor (Anforderer) |Eine Textzeile | |
| EstimatedDays |Number |Ermöglicht den Vergleich zwischen dem Schätzwert des Anforderers, dem Schätzwert des Projektmanagers und dem tatsächlichen Wert |
| Approved (Genehmigt) |Eine Textzeile |Werte: „Ausstehend“, „Ja“, „Nein“ |

> [!NOTE]
> Wir verwenden zudem die Spalte **ID**. Diese wird von SharePoint generiert und ist standardmäßig ausgeblendet. Der Einfachheit halber verwenden wir Basisdatentypen, jedoch werden in einer realen App eventuell komplexere Typen verwendet, z.B. **Person oder Gruppe** für die Spalte **Requestor** (Anforderer). Informationen zu den von PowerApps unterstützten Datentypen finden Sie unter [Herstellen einer Verbindung zwischen Microsoft PowerApps und SharePoint](connections/connection-sharepoint-online.md#known-issues).

Die zweite Liste lautet **Project Details** (Projektdetails). In dieser werden Details für alle genehmigten Projekte, z.B. der zugewiesene Projektmanager, nachverfolgt.

| **Listenspalte** | **Datentyp** | **Anmerkungen** |
| --- | --- | --- |
| Title |Eine Textzeile |Standardspalte, wird für den Projektnamen verwendet |
| RequestID |Number |Entspricht dem Wert in der Spalte **ID** der Liste **Project Requests** (Projektanforderungen). |
| ApprovedDate (Genehmigungsdatum) |Datum | |
| Status |Eine Textzeile |Werte: „Not started“ (Nicht gestartet), „In progress“ (In Bearbeitung), „Completed“ (Abgeschlossen) |
| ProjectedStartDate |Datum |Das vom Projektmanager geschätzte Startdatum des Projekts |
| ProjectedEndDate |Datum |Das vom Projektmanager geschätzte Enddatum des Projekts |
| ProjectedDays |Number |Arbeitstage. Diese werden in der Regel berechnet, jedoch nicht in diesem Szenario. |
| ActualDays (Tatsächliche Anzahl von Tagen) |Number |Für abgeschlossene Projekte |
| PMAssigned |Eine Textzeile |Projektmanager |

## <a name="step-2-create-and-review-the-lists"></a>Schritt 2: Erstellen und Überprüfen der Listen
Um mit dem Szenario fortzufahren, müssen Sie die beiden SharePoint-Listen erstellen und mit Beispieldaten auffüllen. Um Sie dabei anzuleiten, erstellen wir die Liste und fügen Beispieldaten in sie ein. Stellen Sie sicher, dass Sie über die Excel-Dateien aus dem [Downloadpaket](https://aka.ms/o4ia0f) verfügen.

> [!NOTE]
> Verwenden Sie für diesen Schritt Internet Explorer.

### <a name="create-the-lists"></a>Die Listen erstellen

1. Klicken oder tippen Sie in Internet Explorer auf Ihrer SharePoint-Website auf **Neu** und dann auf **Liste**.
   
    ![Neue SharePoint-Liste erstellen](./media/sharepoint-scenario-setup/01-01-01-new-list.png)

2. Geben Sie den Namen „Project Requests“ (Projektanforderungen) ein, und klicken oder tippen Sie dann auf **Erstellen**.
   
    ![Namen für neue Liste angeben](./media/sharepoint-scenario-setup/01-01-02-create-list.png)
   
    Die Liste **Project Requests** (Projektanforderungen) wird erstellt, mit dem Standardfeld **Title** (Titel).
   
    ![Liste „Project Requests“ (Projektanforderungen)](./media/sharepoint-scenario-setup/01-01-03-initial-list.png)

### <a name="add-columns-to-the-list"></a>Spalten zur Liste hinzufügen

1. Klicken oder tippen Sie auf ![Symbol „Neues Element“](./media/sharepoint-scenario-setup/icon-new.png) und dann auf **Eine Textzeile**.
   
    ![Feld „Eine Textzeile“ hinzufügen](./media/sharepoint-scenario-setup/01-01-04-add-column.png)

2. Geben Sie den Namen „Description“ (Beschreibung) ein, und klicken oder tippen Sie dann auf **Speichern**.
   
3. Wiederholen Sie die Schritte **1.** und **2.** für die anderen Spalten in der Liste:
   
   1. **Eine Textzeile** > "ProjectType"
   2. **Datum** > "RequestDate"
   3. **Eine Textzeile** > "Requestor" (Anforderer)
   4. **Anzahl** > "EstimatedDays"
   5. **Eine Textzeile** > "Approved" (Genehmigt)

### <a name="copy-data-into-the-list"></a>Kopieren von Daten in die Liste
1. Klicken oder tippen Sie auf **QuickEdit**.
   
    ![QuickEdit für Liste](./media/sharepoint-scenario-setup/01-01-06-quick-edit.png)
2. Wählen Sie die Zellen im Raster aus.
   
    ![Liste mit allen Spalten](./media/sharepoint-scenario-setup/01-01-07-empty-grid.png)
3. Öffnen Sie die Arbeitsmappe „project-requests.xlsx“, und wählen Sie alle Daten (nicht die Spaltenüberschriften) aus.
   
    ![Excel-Tabelle für „Project Requests“ (Projektanforderungen)](./media/sharepoint-scenario-setup/01-01-08-excel-table.png)
4. Kopieren Sie die Daten, fügen Sie sie in das Raster in SharePoint ein, und klicken oder tippen Sie dann auf **Fertig**.
   
    ![Vollständige Liste mit Daten](./media/sharepoint-scenario-setup/01-01-09-full-grid.png)
5. Wiederholen Sie unter Verwendung der Arbeitsmappe „project-details.xlsx“ die Schritte zum Erstellen der Liste und Kopieren der Daten für die Liste „Project Details“ (Projektdetails). Die Spaltennamen und Datentypen können Sie der Tabelle „Project Details“ (Projektdetails) in [Schritt 1: Verstehen der Listen](#step-1-understand-the-lists) entnehmen.

## <a name="step-3-update-connections-to-samples---optional"></a>Schritt 3: Aktualisieren von Verbindungen mit den Beispielen – optional
Wie in der Einführung zu dieser Tutorialreihe erwähnt, enthält das [Downloadpaket](https://aka.ms/o4ia0f) zwei Beispiel-Apps und einen Beispielbericht. Sie können dieses Szenario ohne die Beispiele abschließen, wenn Sie jedoch die Beispiele verwenden möchten, müssen Sie die Verbindungen mit den SharePoint-Listen aktualisieren. Sie aktualisieren sie für die Verwendung *Ihrer* Listen statt unserer Listen als Datenquelle.

### <a name="update-connections-for-the-sample-apps"></a>Aktualisieren von Verbindungen für die Beispiel-Apps

1. Klicken oder tippen Sie in [PowerApps Studio](https://create.powerapps.com/studio/) im linken Bereich auf **Öffnen**. 

2. Klicken oder tippen Sie auf **Durchsuchen**, und öffnen Sie dann die heruntergeladene Datei **project-management-app.msapp**.

3. Klicken oder tippen Sie auf **Zulassen**, damit SharePoint von PowerApps verwendet werden kann.

4. Klicken oder tippen Sie im Menüband auf der Registerkarte **Ansicht** auf **Datenquellen**.

    ![PowerApps-Datenquellen](./media/sharepoint-scenario-setup/01-03-01-data-sources.png)
5. Klicken oder tippen Sie im Bereich **Daten** auf die Auslassungspunkte (**. . .**) neben **Project Details** (Projektdetails), und klicken oder tippen Sie dann auf **Entfernen**.
   
    ![Datenquelle „Project Details“ (Projektdetails) entfernen](./media/sharepoint-scenario-setup/01-03-02-remove.png)
6. Klicken oder tippen Sie auf **Datenquelle hinzufügen**.
   
    ![Datenquelle hinzufügen](./media/sharepoint-scenario-setup/01-03-03-add.png)

7. Je nachdem, ob von PowerApps bereits automatisch eine SharePoint-Verbindung hergestellt wurde, haben Sie zwei Möglichkeiten, eine Verbindung mit der Liste herzustellen: 

    * Wenn bereits eine SharePoint-Verbindung angezeigt wird, klicken oder tippen Sie auf die Verbindung.

        ![Vorhandene Verbindung](./media/sharepoint-scenario-setup/01-03-03aa-existing-connection.png)

    * Wenn keine SharePoint-Verbindung angezeigt wird, klicken oder tippen Sie auf **Neue Verbindung**.

        ![Neue Verbindung](./media/sharepoint-scenario-setup/01-03-03a-new-connection.png)

        Klicken oder tippen Sie dann auf **SharePoint**, und klicken oder tippen Sie auf **Erstellen**.
   
        ![SharePoint-Verbindung](./media/sharepoint-scenario-setup/01-03-03b-sharepoint.png)

8. Geben Sie die URL für die SharePoint Online-Website ein, die die von Ihnen erstellten Listen enthält, und klicken oder tippen Sie dann auf **Suche starten**.
   
    ![SharePoint-URL](./media/sharepoint-scenario-setup/01-03-03c-sharepoint-url.png)
9. Wählen Sie die Liste **Project Details** (Projektdetails) aus, und klicken oder tippen Sie auf **Verbinden**.
   
    ![Liste „Project Details“ (Projektdetails)](./media/sharepoint-scenario-setup/01-03-03d-project-details.png)
   
    Im Bereich **Daten** wird die eben erstellte Verbindung jetzt angezeigt.
   
    ![Datenquellen](./media/sharepoint-scenario-setup/01-03-03e-data-sources.png)

10. Klicken oder tippen Sie auf die Auslassungspunkte (**. . .**) neben **Project Details** (Projektdetails), und klicken oder tippen Sie dann auf **Aktualisieren**.
    
    ![Datenquelle „Project Details“ (Projektdetails) aktualisieren](./media/sharepoint-scenario-setup/01-03-02-remove.png)

11. Klicken Sie auf ![Symbol „App ausführen“](./media/sharepoint-scenario-setup/icon-run-arrow.png) in der rechten oberen Ecke, um die App auszuführen, und stellen Sie sicher, dass bei der Verbindung keine Fehler auftreten.

12. Klicken oder tippen Sie auf **Datei**, und speichern Sie die App dann in der Cloud. 

12. Wiederholen Sie die Schritte in diesem Abschnitt für **project-requests-app.msapp** unter Verwendung der Liste **Project Requests** (Projektanforderungen).

### <a name="update-connections-for-the-sample-report"></a>Aktualisieren von Verbindungen für den Beispielbericht
1. Öffnen Sie **project-analysis.pbix** in Power BI Desktop.

2. Klicken oder tippen Sie im Menüband auf der Registerkarte **Start** auf **Abfragen bearbeiten** und dann **Datenquelleneinstellungen**.
   
    ![Abfragen bearbeiten](./media/sharepoint-scenario-setup/01-03-04-edit-queries.png)

3. Klicken oder tippen Sie auf **Quelle ändern**.
   
    ![Datenquelleneinstellungen](./media/sharepoint-scenario-setup/01-03-05-settings.png)

4. Geben Sie die URL für Ihre SharePoint Online-Website ein, und klicken oder tippen Sie auf **OK** und dann auf **Schließen**.
   
    ![URL für SharePoint-Liste](./media/sharepoint-scenario-setup/01-03-06-list-url.png)

5. In Power BI Desktop wird unter dem Menüband ein Banner angezeigt, damit Sie Änderungen übernehmen und Daten aus der neuen Quelle importieren können. Klicken oder tippen Sie auf **Änderungen übernehmen**.
   
    ![Abfrageänderungen übernehmen](./media/sharepoint-scenario-setup/01-03-07-apply.png)

6. Melden Sie sich mit einem Microsoft-Konto (dem Konto, das Sie für den Zugriff auf SharePoint Online verwenden) an, und klicken oder tippen Sie dann auf **Verbinden**.
   
    ![Mit SharePoint Online verbinden](./media/sharepoint-scenario-setup/01-03-08-connect.png)

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Tutorialreihe ist das [Generieren einer App zum Behandeln von Projektanforderungen](sharepoint-scenario-generate-app.md).

