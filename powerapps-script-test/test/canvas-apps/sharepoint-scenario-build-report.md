---
title: Erstellen eines Power BI-Berichts zum Analysieren von Projekten | Microsoft-Dokumentation
description: In dieser Aufgabe erstellen Sie einen Power BI-Bericht, der auf zwei SharePoint-Listen basiert.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/10/2018
ms.author: mblythe
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: adda4a7adae9961b77f01320e92527b53ac61e7f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42828775"
---
# <a name="create-a-power-bi-report-to-analyze-projects"></a>Erstellen eines Power BI-Berichts zum Analysieren von Projekten
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

In dieser Aufgabe Sie einen Power BI-Bericht, der auf den beiden SharePoint-Listen basiert. Wir übernehmen die Listendaten in Power BI Desktop und bereinigen sie ein wenig, führen eine grundlegende Datenmodellierung aus und erstellen eine Reihe von Visuals, die Aufschlüsse über die Daten geben.

> [!TIP]
> Das [Downloadpaket](https://aka.ms/o4ia0f) für dieses Szenario enthält eine vollständige Version dieses Berichts: „project-analysis.pbix“.

## <a name="quick-review-of-power-bi-desktop"></a>Kurzübersicht über Power BI Desktop
Bevor wir uns mit dem Erstellen von Berichten befassen, gehen wir kurz auf Power BI Desktop ein. Dies ist ein leistungsstarkes Tool mit einer Vielzahl von Funktionen, daher bieten wir einen schwerpunktmäßigen Überblick über die Bereiche, die wir in dieser Aufgabe verwenden werden. In Power BI Desktop gibt es drei Hauptarbeitsbereiche oder *Sichten*: die Sicht **Bericht**, die Sicht **Daten** und die Sicht **Beziehungen**. Power BI Desktop bietet außerdem einen **Abfrage-Editor**, der in einem separaten Fenster geöffnet wird.

In der folgenden Abbildung werden die Symbole für die drei Sichten entlang der linken Seite von Power BI Desktop gezeigt: **Bericht**, **Daten** und **Beziehungen** (von oben nach unten). Der gelbe Balken links zeigt die aktuelle Sicht an. In diesem Fall wird die Sicht **Bericht** angezeigt. Sie können zwischen den Sichten wechseln, indem Sie auf eines der drei Symbole klicken bzw. tippen.

![Sichten in Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-00-tabs.png)

Die Sicht **Bericht** umfasst fünf Hauptbereiche:

1. Das Menüband, in dem häufige Aufgaben in Zusammenhang mit Berichten und Visualisierungen angezeigt werden.
2. Die Sicht bzw. den Zeichenbereich **Bericht**. Hier werden Visualisierungen erstellt und angeordnet.
3. Den Registerkartenbereich **Seiten** am unteren Rand, in dem Sie eine Berichtsseite auswählen oder hinzufügen können.
4. Den Bereich **Visualisierungen**, in dem Sie Visualisierungen ändern, Farben oder Achsen anpassen, Filter anwenden, Felder ziehen und andere Vorgänge ausführen können.
5. Den Bereich **Felder**, in dem Abfrageelemente und Filter auf die Sicht **Bericht** oder in den Abschnitt **Filter** des Bereichs **Visualisierungen** gezogen werden können.

![Registerkarten, Sichten und Bereiche in Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-01-report.png)

Die Sicht **Daten** weist drei Hauptbereiche auf:

1. Das Menüband, in dem unten die Registerkarte **Modellierung** ausgewählt ist. Auf dieser Registerkarte erstellen Sie berechnete Tabellen und Spalten, und Sie nehmen andere Änderungen am Datenmodell vor.
2. Den mittleren Bereich, in dem Daten für die ausgewählte Tabelle angezeigt werden.
3. Den Bereich **Felder**, in dem Sie die Anzeige von Feldern in den Berichten konfigurieren.

![Sicht „Daten“ in Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-02-data.png)

In dieser Aufgabe wird die Registerkarte **Beziehungen** nicht verwendet, Sie können sich jedoch später damit vertraut machen, nachdem wir die Listendaten in Power BI Desktop übertragen haben.

Im **Abfrage-Editor** erstellen Sie Abfragen, und Sie transformieren Daten. Anschließend laden Sie das verfeinerte Datenmodell in Power BI Desktop. Der **Abfrage-Editor** besteht aus vier Hauptbereichen:

1. Das Menüband, das viele Optionen zum Strukturieren und Transformieren der übernommenen Daten enthält.
2. Der linke Bereich, in dem die aufgelisteten Abfragen ausgewählt, angezeigt und strukturiert werden können.
3. Der mittlere Bereich, in dem Daten aus der ausgewählten Abfrage angezeigt und strukturiert werden können.
4. Das Fenster **Abfrageeinstellungen**, in dem die Eigenschaften und die angewendeten Schritte zur Datentransformation aufgelistet werden.

![Abfrage-Editor von Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-03-query.png)

## <a name="step-1-get-data-into-power-bi-desktop"></a>Schritt 1: Übernehmen von Daten in Power BI Desktop
In diesem Schritt wird zunächst eine Verbindung mit den zwei Listen hergestellt. Anschließend müssen die Daten bereinigt werden, indem nicht für die Datenanalyse benötigte Spalten entfernt werden. Zudem ändern wir die Datentypen für einige der verbleibenden Spalten, damit die Berechnungen ordnungsgemäß ausgeführt werden können. Weitere Informationen zum Übernehmen und Bereinigen von Daten in Power BI Desktop finden Sie im Abschnitt zum [Abrufen von Daten](https://powerbi.microsoft.com/guided-learning/powerbi-learning-1-1-overview-of-power-bi-desktop) in unserem Kurs für geführtes Lernen.

### <a name="connect-to-sharepoint-lists"></a>Herstellen einer Verbindung mit SharePoint-Listen
1. Klicken oder tippen Sie in Power BI Desktop auf der Registerkarte **Start** auf **Daten abrufen** und anschließend auf **More…** (Mehr).
   
    ![Daten abrufen](./media/sharepoint-scenario-build-report/05-01-01-get-data.png)
2. Klicken oder tippen Sie im Dialogfeld **Daten abrufen** auf **SharePoint Online-Liste** und auf **Verbinden**.
   
    ![Verbinden mit SharePoint-Listen](./media/sharepoint-scenario-build-report/05-01-02-sharepoint-list.png)
3. Geben Sie die URL für Ihre SharePoint-Website ein, und klicken oder tippen Sie auf **OK**.
   
    ![URL für SharePoint-Liste](./media/sharepoint-scenario-build-report/05-01-03-sharepoint-url.png)
4. Wenn das folgende Dialogfeld angezeigt wird, vergewissern Sie sich, dass Sie mit den richtigen Anmeldeinformationen angemeldet sind, und klicken oder tippen Sie auf **Verbinden**.
   
    ![Anmeldeinformationen für SharePoint-Liste](./media/sharepoint-scenario-build-report/05-01-04-credentials.png)
5. Wählen Sie **Project Details** (Projektdetails) und **Project Requests** (Projektanforderungen) aus, und klicken oder tippen Sie auf **Bearbeiten**.
   
    ![Auswählen von SharePoint-Listen](./media/sharepoint-scenario-build-report/05-01-05-list-navigator.png)
   
    Die Listen werden nun im Abfrage-Editor als Tabellen angezeigt.
   
    ![Tabellen im Abfrage-Editor](./media/sharepoint-scenario-build-report/05-01-06-query-editor.png)

### <a name="remove-unnecessary-columns-from-the-tables"></a>Entfernen nicht benötigter Spalten aus den Tabellen
1. Klicken oder tippen Sie im linken Navigationsbereich auf **Project Details** (Projektdetails).
2. Wählen Sie im mittleren Bereich die Spalte **FileSystemObjectType** aus, und klicken oder tippen Sie auf **Spalten entfernen**.
   
    ![Spalten entfernen](./media/sharepoint-scenario-build-report/05-01-07-remove-column.png)
3. Entfernen Sie die zwei Spalten nach der Spalte **ID**: **ServerRedirectedEmbedURL** und **ContentTypeId**. 
   > [!TIP]
   > Mithilfe der Umschalttaste können Sie beide Spalten auswählen. Klicken oder tippen Sie anschließend auf **Spalten entfernen**.
4. Entfernen Sie alle Spalten rechts von der Spalte **PMAssigned** (insgesamt 22 Spalten). Die Tabelle sollte wie die in der folgenden Abbildung aussehen:
   
    ![Tabelle „Project Details“ (Projektdetails) im Abfrage-Editor](./media/sharepoint-scenario-build-report/05-01-08-table-details.png)
5. Wiederholen Sie den gerade ausgeführten Vorgang für **Project Requests**: Entfernen Sie **FileSystemObjectType**, **ServerRedirectedEmbedURL**, **ContentTypeId** und alle Spalten rechts von der Spalte **Approved** (insgesamt 22 Spalten). Die Tabelle sollte wie die in der folgenden Abbildung aussehen:
   
    ![ Tabelle „Project Requests“ (Projektanforderungen) im Abfrage-Editor](./media/sharepoint-scenario-build-report/05-01-09-table-requests.png)

### <a name="change-the-data-type-on-project-details-columns"></a>Ändern des Datentyps für Spalten von „Project Details“ (Projektdetails)
1. Wählen Sie die Spalte **ProjectedDays** aus, klicken oder tippen Sie auf **Datentyp: Beliebig** und dann auf **Ganze Zahl**.
   
    ![Ändern des Datentyps in „Ganze Zahl“](./media/sharepoint-scenario-build-report/05-01-10-datatype-number.png)
2. Wiederholen Sie den vorherigen Schritt für die Spalte **ActualDays**.
3. Wählen Sie die Spalte **ApprovedDate** aus, klicken oder tippen Sie auf **Datentyp: Beliebig** und anschließend auf **Datum**.
   
    ![ Ändern des Datentyps in „Datum“](./media/sharepoint-scenario-build-report/05-01-11-datatype-date.png)

4. Wiederholen Sie den vorherigen Schritt für die Spalten **ProjectedStartDate** und **ProjectedEndDate**.

### <a name="change-the-data-type-on-project-requests-columns"></a>Ändern des Datentyps für Spalten von „Project Requests“ (Projektanforderungen)

1. Wählen Sie die Spalte **EstimatedDays** aus, klicken oder tippen Sie auf **Datentyp: Beliebig** und anschließend auf **Ganze Zahl**.

2. Wählen Sie die Spalte **RequestDate** aus, klicken oder tippen Sie auf **Datentyp: Beliebig** und anschließend auf **Datum**.

### <a name="apply-and-save-changes"></a>Anwenden und Speichern der Änderungen

1. Klicken Sie auf der Registerkarte **Start** auf **Schließen und übernehmen**, um den Abfrage-Editor zu schließen und zum Hauptfenster von Power BI Desktop zurückzukehren.
   
    ![Schließen und Anwenden der Änderungen](./media/sharepoint-scenario-build-report/05-01-12-close-apply.png)

2. Klicken oder tippen Sie auf **Datei** und anschließend auf **Speichern**, und speichern Sie die Datei unter dem Namen „project-analysis.pbix“.

## <a name="step-2-improve-the-data-model"></a>Schritt 2: Verbessern des Datenmodells
Nach dem Abrufen der Daten aus den SharePoint-Listen in Power BI Desktop fahren wir mit der Datenmodellierung fort. Die Datenmodellierung kann ein zeitaufwendiger Prozess sein. Wir veranschaulichen jedoch kurz einige interessante Aktionen, die Sie ausführen können, um mehr aus den Listendaten in Power BI Desktop zu holen:

* Ändern der Beziehung zwischen den beiden Tabellen
* Hinzufügen einer Datumstabelle, sodass Berechnungen auf der Grundlage von Werktagen ausgeführt werden können
* Hinzufügen von berechneten Spalten zum Berechnen von Zeitspannen zwischen Projektmeilensteinen
* Hinzufügen von Measures zum Berechnen der Differenz zwischen der geplanten und der tatsächlichen Anzahl von Tagen für ein Projekt

Nach der Ausführung dieser Schritte können Visualisierungen erstellt werden, die von den Verbesserungen unseres Modells profitieren. Weitere Informationen zum Modellieren von Daten in Power BI Desktop finden Sie im Abschnitt [Modellierung](https://powerbi.microsoft.com/guided-learning/powerbi-learning-2-1-intro-modeling-data) in unserem Kurs für geführtes Lernen.

### <a name="change-table-relationships"></a>Ändern von Tabellenbeziehungen
Bei der Übernahme der Listen in Power BI Desktop wurde eine Beziehung zwischen ihnen erstellt, die auf der Spalte **ID** in beiden Tabellen basiert. Die Beziehung muss tatsächlich zwischen der Spalte **ID** in der Tabelle **Project Requests** (Projektanforderungen) und der Spalte **RequestId** in der Tabelle **Project Details** (Projektdetails) bestehen. Lassen Sie uns dieses Problem beheben:

1. Klicken oder tippen Sie auf das Symbol für die Sicht **Daten**.
   
    ![Datensicht](./media/sharepoint-scenario-build-report/05-02-01-data-view.png)

2. Klicken oder tippen Sie auf der Registerkarte **Modellierung** auf **Beziehungen verwalten**. Bei allen Schritten zur Datenmodellierung bleiben wir auf dieser Registerkarte in der Sicht **Daten**.
   
    ![Beziehungen verwalten](./media/sharepoint-scenario-build-report/05-02-02-manage-relationships.png)

3. Vergewissern Sie sich, dass die vorhandene Beziehung ausgewählt ist, klicken oder tippen Sie auf **Löschen** und anschließend zum Bestätigen noch einmal auf **Löschen**.
   
    ![Löschen der Beziehung](./media/sharepoint-scenario-build-report/05-02-03-delete-relationship.png)

4. Klicken Sie auf **Neu**, um eine andere Beziehung zu erstellen.

5. Im Dialogfeld **Beziehung erstellen**:
   
   1. Wählen Sie für die erste Tabelle **Project Requests** (Projektanforderungen) und die Spalte **Id** aus.
   
   2. Wählen Sie für die zweite Tabelle **Project Details** (Projektdetails) und die Spalte **RequestId** aus.
   
   3. Der Bildschirm entspricht nun etwa dem in der folgenden Abbildung. Wenn Sie bereit sind, klicken oder tippen Sie auf **OK** und dann auf **Schließen**.
      
       ![Beziehung erstellen](./media/sharepoint-scenario-build-report/05-02-04-create-relationship.png)

### <a name="add-a-date-table-to-make-date-based-calculations-easier"></a>Hinzufügen einer Datumstabelle, um datumsbasierte Berechnungen zu erleichtern
1. Klicken oder tippen Sie auf **Neue Tabelle**.
   
    ![Neue Tabelle](./media/sharepoint-scenario-build-report/05-02-05-modeling-table.png)
2. Geben Sie in der Bearbeitungsleiste diese Formel ein: **Dates = CALENDARAUTO()**.
   
    ![Bearbeitungsleiste mit „Dates = CALENDARAUTO()“](./media/sharepoint-scenario-build-report/05-02-06-formula-bar.png)
   
    Durch diese Formel wird die Tabelle **Dates** mit einer einzigen Datumsspalte erstellt. Die Tabelle umfasst alle Datumsangaben aus Ihren anderen Tabellen und wird automatisch aktualisiert, wenn weitere Datumsangaben hinzugefügt werden (d.h., wenn die Daten aktualisiert werden).
   
    Bei dieser und den anderen Formeln in diesem Abschnitt wird DAX (Data Analysis Expressions) verwendet, eine Formelsprache für Power BI und andere Technologien. Weitere Informationen finden Sie unter [DAX-Grundlagen in Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-quickstart-learn-dax-basics).
3. Drücken Sie die EINGABETASTE, um die Tabelle **Dates** zu erstellen.
   
    ![Tabelle „Dates“](./media/sharepoint-scenario-build-report/05-02-07-date-table.png)

### <a name="add-a-calculated-column-to-the-dates-table"></a>Hinzufügen einer berechneten Spalte zur Tabelle „Dates“
1. Klicken oder tippen Sie in der Tabelle mit Datumsangaben auf **Neue Spalte**.
   
    ![Neue Spalte](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. Geben Sie in der Bearbeitungsleiste die folgende Formel ein: **IsWeekDay = SWITCH(WEEKDAY(Dates[Date]), 1,0,7,0,1)**.
   
    Durch diese Formel wird bestimmt, ob es sich bei einem Datum in der Spalte **Date** um einen Werktag handelt. Wenn es sich bei dem Datum um einen Werktag handelt, erhält die Spalte **IsWeekDay** den Wert 1, andernfalls wird der Spalte der Wert 0 zugewiesen.
3. Drücken Sie die EINGABETASTE, um der Tabelle **Dates** die Spalte **IsWeekDay** hinzuzufügen.
   
    ![Hinzufügen der Spalte „IsWeekDay“](./media/sharepoint-scenario-build-report/05-02-08-column-isweekday.png)

### <a name="add-a-calculated-column-to-the-project-details-table"></a>Hinzufügen einer berechneten Spalte zur Tabelle „Project Details“ (Projektdetails)
1. Klicken oder tippen Sie im rechten Bereich auf die Tabelle **Project Details** (Projektdetails) und anschließend auf **Neue Spalte**.
   
    ![Neue Spalte](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. Geben Sie in der Bearbeitungsleiste diese Formel ein:
   
    ```
    ApprovedStartDiff = CALCULATE(SUM(Dates[IsWeekday]),
   
       DATESBETWEEN(Dates[Date],
   
          'Project Details'[ApprovedDate],
   
          'Project Details'[ProjectedStartDate]
   
      )
   
    )
    ```
   
    Durch diese Formel wird die Differenz (in Tagen) zwischen der Genehmigung eines Projekts und dem geplanten Start des Projekts berechnet. Die Spalte **IsWeekday** aus der Tabelle **Dates** wird verwendet, daher werden nur Werktage gezählt.
3. Drücken Sie die EINGABETASTE, um der Tabelle **Project Details** (Projektdetails) die Spalte **ApprovedStartDiff** hinzuzufügen.
   
    ![Hinzufügen der Spalte „ApprovedStartDiff“](./media/sharepoint-scenario-build-report/05-02-09-column-approvedstartdiff.png)

### <a name="add-a-calculated-column-to-the-project-requests-table"></a>Hinzufügen einer berechneten Spalte zur Tabelle „Project Requests“ (Projektanforderungen)
1. Klicken oder tippen Sie im rechten Bereich auf die Tabelle **Project Requests** (Projektanforderungen) und anschließend auf **Neue Spalte**.
   
    ![Neue Spalte](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. Geben Sie in der Bearbeitungsleiste diese Formel ein:
   
    ```
    RequestDateAge = CALCULATE(SUM(Dates[IsWeekday]),
   
       DATESBETWEEN(Dates[Date],
   
          'Project Requests'[RequestDate],
   
          NOW()
   
       )
   
    )
    ```
   
    Durch diese Formel wird die Differenz (in Tagen) zwischen der Anforderung eines Projekts und dem heutigen Datum (NOW()) berechnet. Durch die Formel werden wiederum nur Werktage gezählt. Anhand dieser Spalte wird nach dem Projekt gesucht, das am längsten aussteht.
3. Drücken Sie die EINGABETASTE, um der Tabelle **Project Requests** (Projektanforderungen) die Spalte **RequestDateAge** hinzuzufügen.
   
    ![Hinzufügen der Spalte „RequestDateAge“](./media/sharepoint-scenario-build-report/05-02-10-column-requestdateage.png)

### <a name="add-a-measure-to-the-project-details-table"></a>Hinzufügen eines Measure zur Tabelle „Project Details“
1. Klicken oder tippen Sie im rechten Bereich auf die Tabelle **Project Details** und anschließend auf **Neues Measure**.
   
    ![Neues Measure](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. Geben Sie in der Bearbeitungsleiste diese Formel ein:
   
    ```
    VarProjectedActual = DIVIDE(
   
        SUM('Project Details'[ActualDays]) - SUM('Project Details'[ProjectedDays]),
   
        SUM('Project Details'[ProjectedDays])
   
    )
    ```
   
    Durch diese Formel wird die Differenz zwischen tatsächlicher und veranschlagter Anzahl von Tagen für ein Projekt berechnet. Hier wird ein Measure und keine berechnete Spalte hinzugefügt, sodass die richtigen Ergebnisse unabhängig davon zurückgegeben werden, ob die Daten in einem Bericht gefiltert oder aggregiert sind.
3. Drücken Sie die EINGABETASTE, um der Tabelle **Project Details** (Projektdetails) das Measure **VarProjectedActual** hinzuzufügen.
   
    ![Hinzufügen des Measure „VarProjectedActual“](./media/sharepoint-scenario-build-report/05-02-11-measure-varprojectedactual.png)

### <a name="add-a-measure-to-the-project-requests-table"></a>Hinzufügen eines Measure zur Tabelle „Project Requests“ (Projektanforderungen)
1. Klicken oder tippen Sie im rechten Bereich auf die Tabelle **Project Requests** (Projektanforderungen) und anschließend auf **Neues Measure**.
   
    ![Neues Measure](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. Geben Sie in der Bearbeitungsleiste diese Formel ein:
   
    ```
    MaxDaysPending = MAXX(
   
        FILTER('Project Requests', 'Project Requests'[Approved]="Pending"),
   
        'Project Requests'[RequestDateAge]
   
    )
    ```
   
    Anhand dieser Formel wird nach dem am längsten ausstehenden Projekt gesucht, basierend auf der zuvor definierten berechneten Spalte.
3. Drücken Sie die EINGABETASTE, um der Tabelle **Project Requests** (Projektanforderungen) das Measure **MaxDaysPending** hinzuzufügen.
   
    ![Hinzufügen des Measure „MaxDaysPending“](./media/sharepoint-scenario-build-report/05-02-12-measure-maxdayspending.png)

## <a name="step-3-create-report-visualizations"></a>Schritt 3: Erstellen von Berichtsvisualisierungen
Nun kommen wir zu dem Schritt, der vielen bei der Datenanalyse zuerst in den Sinn kommt: das Erstellen von Visualisierungen, sodass Muster in den Daten aufgefunden werden können. In diesem Schritt erstellen wir vier Visualisierungen:

* Ein Säulendiagramm, in dem die geplanten Tage den tatsächlichen Tagen eines Projekts gegenübergestellt werden
* Ein Säulendiagramm, in dem die Differenz für die einzelnen Projekte veranschaulicht wird
* Eine Karte, auf der das am längsten ausstehende Projekt angezeigt wird
* Eine Tabelle mit der Zeitspanne zwischen der Genehmigung des Projekts und dem geplanten Startdatum

Nachdem wir diese Berichtsvisualisierungen Power BI Desktop erstellt haben, veröffentlichen wir die Daten und Berichte im Power BI-Dienst, sodass wir Dashboards erstellen und freigeben können. Weitere Informationen zum Erstellen von Berichten in Power BI Desktop finden Sie im Abschnitt [Visualisierungen](https://powerbi.microsoft.com/guided-learning/powerbi-learning-3-1-intro-visualizations) in unserem Kurs für geführtes Lernen.

### <a name="create-a-bar-chart-to-show-projected-versus-actual"></a>Erstellen eines Balkendiagramms zum Darstellen der geplanten und tatsächlichen Tage
1. Klicken oder tippen Sie auf das Symbol für die Sicht **Bericht**. Für die restliche Zeit in Power BI Desktop bleiben wir in dieser Sicht.
   
    ![Sicht „Bericht“](./media/sharepoint-scenario-build-report/05-03-01-report-view.png)
2. Klicken oder tippen Sie im Bereich **Visualisierungen** auf der rechten Seite auf **Säulendiagramm (gruppiert)**.
   
    ![Visualisierungen – Säulendiagramm (gruppiert)](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. Ziehen Sie **PMAssigned** und **Title** aus **Project Details** im Bereich **Felder** in **Achse** im Bereich **Visualisierungen**.
   
    ![„Achse“ im Bereich „Visualisierungen“](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. Ziehen Sie **ActualDays** und **ProjectedDays** aus **Project Details** im Bereich **Felder** in **Wert** im Bereich **Visualisierungen**.
   
    ![„Wert“ im Bereich „Visualisierungen“](./media/sharepoint-scenario-build-report/05-03-03-value-projected.png)
5. Die Visualisierung sollte nun wie in der folgenden Abbildung aussehen.
   
    ![ProjectedDays und ActualDays nach PMAssigned](./media/sharepoint-scenario-build-report/05-03-04-chart-projected.png)
6. Ziehen Sie **Status** aus **Project Details** (Projektdetails) im Bereich **Felder** in den Abschnitt **Filter** im Bereich **Visualisierungen**, und aktivieren Sie anschließend das Kontrollkästchen **Abgeschlossen**.
   
   ![Filtern nach Spalte „Status“](./media/sharepoint-scenario-build-report/05-03-05-filters-projected.png)
   
   Das Diagramm wird nun so gefiltert, dass nur abgeschlossene Projekte angezeigt werden. Dies ist sinnvoll, da geplante Tage mit den tatsächlichen Tagen verglichen werden.
7. Klicken Sie auf die Pfeile in der linken oberen Ecke des Diagramms, um die Hierarchie der Projektmanager und Projekte nach oben und unten zu verschieben. In der folgenden Abbildung wird der Drilldown in Projekte veranschaulicht.
   
   ![Drilldown in Säulendiagramm](./media/sharepoint-scenario-build-report/05-03-06-chart-projected-drill.png)

### <a name="create-a-bar-chart-to-show-variance-from-projected"></a>Erstellen eines Balkendiagramms zum Darstellen der Differenz von den geplanten Tagen
1. Klicken oder tippen Sie auf den Zeichenbereich außerhalb der soeben erstellten Visualisierung.
2. Klicken oder tippen Sie im Bereich **Visualisierungen** auf der rechten Seite auf **Säulendiagramm (gruppiert)**.
   
    ![Visualisierungen – Säulendiagramm (gruppiert)](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. Ziehen Sie **PMAssigned** und **Title** aus **Project Details** im Bereich **Felder** in **Achse** im Bereich **Visualisierungen**.
   
    ![„Achse“ im Bereich „Visualisierungen“](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. Ziehen Sie **VarProjectedActual** aus **Project Details** (Projektdetails) im Bereich **Felder** in **Wert** im Bereich **Visualisierungen**.
   
    ![„Wert“ im Bereich „Visualisierungen“](./media/sharepoint-scenario-build-report/05-03-07a-value-variance.png)
5. Ziehen Sie **Status** aus **Project Details** (Projektdetails) im Bereich **Felder** in den Abschnitt **Filter** im Bereich **Visualisierungen**, und aktivieren Sie anschließend das Kontrollkästchen **Abgeschlossen**.
   
    ![Filtern nach Spalte „Status“](./media/sharepoint-scenario-build-report/05-03-07b-filters-variance.png)
   
    Die Visualisierung sollte nun wie in der folgenden Abbildung aussehen.
   
    ![VarProjectedActual nach PMAssigned](./media/sharepoint-scenario-build-report/05-03-08-chart-variance.png)
   
    Anhand dieses Diagramms wird ersichtlich, wie viel größer die Variabilität der Projekte von Irvin Sayers als die der Projekte von Joni Sherman ist. Führen Sie einen Drilldown aus, um die Variabilität nach Projekten zu untersuchen und festzustellen, ob die geplante Anzahl von Tagen größer oder kleiner als die tatsächliche Anzahl von Tagen war.
   
    ![VarProjectedActual nach Title](./media/sharepoint-scenario-build-report/05-03-09-chart-variance-drill.png)
6. Bevor wir weitere Visualisierungen erstellen, verschieben Sie die bereits erstellten Visualisierungen, und ändern Sie deren Größe, sodass sie nebeneinander angezeigt werden können.
   
    ![Anpassen von Diagrammen für die Anzeige nebeneinander](./media/sharepoint-scenario-build-report/05-03-10-two-charts.png)

### <a name="create-a-card-that-shows-the-longest-pending-project"></a>Erstellen einer Karte, auf der das am längsten ausstehende Projekt angezeigt wird
1. Klicken oder tippen Sie auf den Zeichenbereich außerhalb der soeben erstellten Visualisierung.
2. Klicken oder tippen Sie im Bereich **Visualisierungen** auf der rechten Seite auf **Karte**.
   
    ![Visualisierungen – Karte](./media/sharepoint-scenario-build-report/05-03-11-visuals-card.png)
3. Ziehen Sie **MaxDaysPending** aus **Project Requests** (Projektanforderungen) im Bereich **Felder** in **Felder** im Bereich **Visualisierungen**.
   
    ![„Felder“ im Bereich „Visualisierungen“](./media/sharepoint-scenario-build-report/05-03-12-value-max.png)
4. Klicken oder tippen Sie auf **Format übertragen** (Malerrolle), und legen Sie **Rand** auf **Ein** fest.
   
    ![Format übertragen – Rand](./media/sharepoint-scenario-build-report/05-03-13a-format.png)
5. Legen Sie **Title** (Titel) auf **Ein** fest, und fügen Sie anschließend den Titel „Max days pending approval“ (Max. Anzahl Tage ausstehende Genehmigung) hinzu.
   
    ![Hinzufügen eines Titels](./media/sharepoint-scenario-build-report/05-03-13b-title.png)
   
    Die Visualisierung sollte nun wie in der folgenden Abbildung aussehen.
   
    ![ „Max days pending approval“ (Max. Anzahl Tage ausstehende Genehmigung)](./media/sharepoint-scenario-build-report/05-03-14-chart-max.png)
   
    Nachdem wir diesen Bericht veröffentlicht haben, lösen wir mit dieser Kachel eine Warnung aus, wenn der Maximalwert für ein ausstehendes Projekt einen bestimmten Schwellenwert erreicht.

### <a name="create-a-table-that-shows-the-time-between-project-approval-and-projected-start-date"></a>Erstellen einer Tabelle mit der Zeitspanne zwischen der Genehmigung des Projekts und dem geplanten Startdatum
1. Klicken oder tippen Sie auf den Zeichenbereich außerhalb der soeben erstellten Visualisierung.
2. Klicken oder tippen Sie im Bereich **Visualisierungen** auf der rechten Seite auf **Tabelle**.
   
    ![Visualisierungen – Tabelle](./media/sharepoint-scenario-build-report/05-03-15-visuals-table.png)
3. Ziehen Sie **PMAssigned**, **Title** und **ApprovedStartDiff** aus **Project Details** (Projektdetails) im Bereich **Felder** in **Werte** im Bereich **Visualisierungen**.
   
    ![„Werte“ im Bereich „Visualisierungen“](./media/sharepoint-scenario-build-report/05-03-16-value-diff.png)
4. Ziehen Sie **ProjectedStartDate** aus **Project Details** (Projektdetails) im Bereich **Felder** in den Abschnitt **Filter** des Bereichs **Visualisierungen**, und wählen Sie anschließend alle Datumsangaben außer **(Leer)** aus.
   
    ![Filtern nach ProjectedStartDate](./media/sharepoint-scenario-build-report/05-03-17-filters-diff.png)
5. Ändern Sie die Größe der Spalten der Tabelle, damit alle Daten angezeigt werden, und sortieren Sie absteigend nach **ApprovedStartDiff**. Die Visualisierung sollte nun wie in der folgenden Abbildung aussehen.
   
    ![Tabelle mit Werten für ApprovedStartDiff](./media/sharepoint-scenario-build-report/05-03-18-chart-diff.png)
6. Klicken oder tippen Sie im Bereich **Werte** auf den Pfeil nach unten für **ApprovedStartDiff**, und klicken oder tippen Sie anschließend auf **Durchschnitt**. Jetzt wird die durchschnittliche Zeitspanne von der Genehmigung des Projekts bis zum geplanten Startdatum angezeigt.
   
    ![Berechnen des Durchschnitts](./media/sharepoint-scenario-build-report/05-03-20a-average-menu.png)
7. Klicken oder tippen Sie erneut auf den Pfeil nach unten für **ApprovedStartDiff**, und klicken oder tippen Sie anschließend auf **Bedingte Formatierung** und dann auf **Skalen für die Hintergrundfarbe**.
   
   ![Bedingte Formatierung](./media/sharepoint-scenario-build-report/05-03-20b-conditional-menu.png)
8. Legen Sie die Farben in den Feldern **Minimum** und **Maximum** fest, wie unten dargestellt, und klicken oder tippen Sie dann auf **OK**.
   
   ![Optionen für „Bedingte Formatierung“](./media/sharepoint-scenario-build-report/05-03-21-conditional-dialog.png)
   
   Die Visualisierung sollte nun wie in der folgenden Abbildung aussehen.
   
   ![Abgeschlossene bedingte Formatierung](./media/sharepoint-scenario-build-report/05-03-22-chart-diff-completed.png)
   
   Sie stellen fest, dass von Irvin Sayers geleitete Projekte tendenziell viel später nach der Genehmigung beginnen. Möglicherweise gibt es andere Faktoren als den zugewiesenen Projektmanager, es erscheint jedoch sinnvoll, diesen Faktor eingehender zu untersuchen.

Damit kommen wir zum Ende des Berichtsabschnitts. Sie verfügen nun über einen kompletten Bericht, der auf den aus SharePoint importierten Daten basiert und Power BI Desktop bereinigt und modelliert wurde. Wenn alles plangemäß verlaufen ist, sieht ihr Bericht wie der in der folgenden Abbildung aus.

![Abgeschlossener Bericht](./media/sharepoint-scenario-build-report/05-03-23-report-completed.png)

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Reihe von Tutorials besteht im [Veröffentlichen des Power BI-Projektberichts und Erstellen eines Dashboards](sharepoint-scenario-publish-report.md).

