---
title: Erstellen einer Canvas-App zum Verwalten von Projekten | Microsoft-Dokumentation
description: In dieser Aufgabe erstellen wir eine Canvas-App von Grund auf neu. Mithilfe dieser App kann ein Benutzer Projekten einen Manager zuweisen und Projektdetails aktualisieren.
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
ms.openlocfilehash: 6b55fe94e7d781147e3e3511769c4d72ca3d90de
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42842369"
---
# <a name="create-a-canvas-app-to-manage-projects"></a>Erstellen einer Canvas-App zum Verwalten von Projekten
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

In dieser Aufgabe erstellen wir eine Canvas-App von Grund auf neu. Mithilfe dieser App kann ein Benutzer Projekten einen Manager zuweisen und Projektdetails aktualisieren. Sie werden feststellen, dass teilweise die gleichen Steuerelemente und Formeln wie in der ersten App verwendet werden. Dieses Mal erstellen Sie jedoch selbstständig einen größeren Teil der App. Der Prozess mag zwar komplexer sein, Sie werden jedoch mehr lernen – unserer Meinung nach ist dies ein guter Kompromiss.

> [!TIP]
> Das [Downloadpaket](https://aka.ms/o4ia0f) für dieses Szenario enthält eine vollständige Version dieser App: „project-details-app.msapp“.

## <a name="quick-review-of-powerapps-studio"></a>Kurzübersicht über PowerApps Studio
PowerApps Studio enthält drei Bereiche und ein Menüband, durch die das Erstellen einer App mit dem Erstellen einer Foliengruppe in PowerPoint vergleichbar ist:

1. Auf der linken Navigationsleiste werden eine hierarchische Ansicht sämtlicher Bildschirme und Steuerelemente der App sowie Vorschauminiaturen der Bildschirme angezeigt.
2. Der mittlere Bereich enthält den App-Bildschirm, in dem Sie derzeit arbeiten.
3. Im rechten Bereich können Sie Optionen wie Layout und Datenquellen festlegen.
4. In der Dropdownliste „Eigenschaft“ wählen Sie die Eigenschaften aus, auf die Formeln angewendet werden.
5. Auf der Bearbeitungsleiste fügen Sie Formeln (wie in Excel) hinzu, mit denen das App-Verhalten definiert wird.
6. Über das Menüband fügen Sie Steuerelemente hinzu und passen Designelemente an.

![PowerApps Studio](./media/sharepoint-scenario-build-app/04-00-00-powerapps-studio.png)

## <a name="step-1-create-screens"></a>Schritt 1: Erstellen von Bildschirmen
Lassen Sie uns nun nach dem kurzen Überblick mit dem Erstellen einer App beginnen.

### <a name="create-and-save-the-app"></a>Erstellen und Speichern der App
1. Klicken oder tippen Sie in PowerApps Studio auf **Neu**, und klicken oder tippen Sie unter **Leere App** auf **Telefonlayout**.
   
    ![Leere App – Telefonlayout](./media/sharepoint-scenario-build-app/04-01-01-blank-phone-app.png)
2. Klicken oder tippen Sie auf **Datei**. Das Dialogfeld wird mit der Registerkarte **App-Einstellungen** geöffnet. Geben Sie den Namen „Project Management app“ (Projektverwaltungs-App) ein.
   
    ![Name der App](./media/sharepoint-scenario-build-app/04-01-02-app-name.png)
3. Klicken oder tippen Sie auf **Speichern unter**, vergewissern Sie sich, dass die App in der Cloud gespeichert wird, und klicken Sie in der rechten unteren Ecke auf **Speichern**.
   
    ![Speichern in der Cloud](./media/sharepoint-scenario-build-app/04-01-03-save-to-cloud.png)

4. Klicken oder tippen Sie auf ![Symbol „Zurück zur App“](./media/sharepoint-scenario-build-app/icon-back-to-app.png) um zur App zurückzukehren.

### <a name="add-four-screens-to-the-app"></a>Hinzufügen von vier Bildschirmen zur App
In diesem Schritt erstellen wir vier leere Bildschirme für die App. Dabei verwenden wir je nach Zweck des jeweiligen Bildschirms unterschiedliche Bildschirmlayouts. Diese werden den Bildschirmen in späteren Schritten hinzugefügt.

| **Bildschirm** | **Zweck** |
| --- | --- |
| **SelectTask** |Begrüßungsbildschirm; Navigation zu anderen Bildschirmen |
| **AssignManager** |Zuweisen eines Managers zu einem genehmigten Projekt |
| **ViewProjects** |Anzeigen einer Liste von Projekten mit Zusammenfassungsinformationen |
| **UpdateDetails** |Anzeigen und Aktualisieren der Details für ein Projekt |

1. Klicken oder tippen Sie auf der Registerkarte **Start** auf **NewScreen** und anschließend auf **Scrollbarer Bildschirm**.
   
    ![Scrollbarer Bildschirm](./media/sharepoint-scenario-build-app/04-01-03a-scrollable-screen.png)
2. Benennen Sie den Bildschirm in **SelectTask** um.
   
    ![Umbenennen des Bildschirms](./media/sharepoint-scenario-build-app/04-01-04-rename-screen.png)
3. Erstellen und Umbenennen weiterer Bildschirme:
   
   1. Klicken oder tippen Sie auf **NewScreen** und anschließend auf **Scrollbarer Bildschirm**. Benennen Sie den Bildschirm in **AssignManager** um.
   2. Klicken oder tippen Sie auf **NewScreen** und anschließend auf **Listenbildschirm**. Benennen Sie den Bildschirm in **ViewProjects** um.
   3. Klicken oder tippen Sie auf **NewScreen** und anschließend auf **Formularbildschirm**. Benennen Sie den Bildschirm in **UpdateDetails** um.
4. Wählen Sie die Auslassungspunkte (**. . .**) neben **Screen1** aus, und klicken oder tippen Sie auf **Löschen**.
   
    ![Bildschirm löschen](./media/sharepoint-scenario-build-app/04-01-04a-delete-screen.png)

Die App sollte nun wie in der folgenden Abbildung aussehen.

![Alle App-Bildschirme](./media/sharepoint-scenario-build-app/04-01-05-all-screens.png)

## <a name="step-2-connect-to-a-sharepoint-list"></a>Schritt 2: Verbinden mit einer SharePoint-Liste
In diesem Schritt stellen wir eine Verbindung mit der SharePoint-Liste **Product Details** (Produktdetails) her. Wir verwenden in dieser App lediglich eine Liste, Sie könnten jedoch auch problemlos eine Verbindung mit beiden herstellen, wenn Sie die App erweitern möchten.

1. Klicken oder tippen Sie in der linken Navigationsleiste auf den Bildschirm **SelectTask**.
2. Klicken oder tippen Sie im rechten Bereich auf **Datenquelle hinzufügen**.
   
    ![Herstellen einer Datenverbindung](./media/sharepoint-scenario-build-app/04-02-01-connect.png)
3. Klicken oder tippen Sie auf **Neue Verbindung**.
   
    ![Neue Verbindung](./media/sharepoint-scenario-build-app/04-02-02-new-connection.png)
4. Klicken oder tippen Sie auf **SharePoint**.
   
    ![SharePoint-Verbindung](./media/sharepoint-scenario-build-app/04-02-03-sharepoint-connection.png)
5. Wählen Sie **Direkte Verbindung (Clouddienste)** aus, und klicken oder tippen Sie dann auf **Erstellen**.
   
    ![Direkte Verbindung (Clouddienste)](./media/sharepoint-scenario-build-app/04-02-03a-sharepoint-cloud.png)
6. Geben Sie eine SharePoint-URL ein, und klicken oder tippen Sie auf **Starten**.
   
    ![SharePoint-URL für Verbindung](./media/sharepoint-scenario-build-app/04-02-04-sharepoint-url.png)
7. Wählen Sie die Liste **Project Details** (Projektdetails) aus, und klicken oder tippen Sie auf **Verbinden**.
   
    ![Auswählen der Liste „Project Details“ (Projektdetails)](./media/sharepoint-scenario-build-app/04-02-05-sharepoint-lists.png)
   
    Auf der Registerkarte **Datenquellen** im rechten Bereich wird nun die erstellte Verbindung angezeigt.
   
    ![Registerkarte „Datenquellen“](./media/sharepoint-scenario-build-app/04-02-06-data-sources.png)

## <a name="step-3-build-the-selecttask-screen"></a>Schritt 3: Erstellen des Bildschirms „SelectTask“
In diesem Schritt richten wir eine Möglichkeit der Navigation zu den anderen Bildschirmen in der App ein. Dabei arbeiten wir mit einigen der Steuerelemente, Formeln und Formatierungsoptionen in PowerApps.

### <a name="update-the-title-and-insert-introductory-text"></a>Aktualisieren des Titels und Einfügen von Einführungstext
1. Wählen in der linken Navigationsleiste den Bildschirm **SelectTask** aus.
2. Wählen Sie im mittleren Bereich den standardmäßigen **[Title]** (Titel) aus, und aktualisieren Sie anschließend in der Bearbeitungsleiste die **Text**-Eigenschaft auf den Wert „Contoso Project Management“.
   
    ![Text-Eigenschaft in der Bearbeitungsleiste](./media/sharepoint-scenario-build-app/04-03-02-text-property.png)
3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Bezeichnung**, und ziehen Sie die Bezeichnung unter das oberste Banner.
   
    ![Bezeichnung hinzufügen](./media/sharepoint-scenario-build-app/04-03-03-text-default.png)
4. Legen Sie in der Bearbeitungsleiste die folgenden Eigenschaften für die Bezeichnung fest:
   
   * **Color**-Eigenschaft = **DarkGray**

   * **Size**-Eigenschaft = **18**

   * **Text**-Eigenschaft = **"Click or tap a task to continue..."** (Klicken oder tippen Sie auf eine Aufgabe, um fortzufahren ...)
     
     ![Aktualisieren des Bezeichnungstexts](./media/sharepoint-scenario-build-app/04-03-04-text-updated.png)

### <a name="add-two-navigation-buttons"></a>Hinzufügen von zwei Navigationsschaltflächen
1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Schaltfläche**, und ziehen Sie die Schaltfläche unter die Bezeichnung.
   
    ![Hinzufügen einer Schaltfläche](./media/sharepoint-scenario-build-app/04-03-05-button-default.png)
2. Legen Sie in der Bearbeitungsleiste die folgenden Eigenschaften für die Schaltfläche fest:
   
   * **OnSelect**-Eigenschaft = **Navigate(AssignManager, Fade)**. Wenn Sie die App ausführen und auf diese Schaltfläche klicken, wechseln Sie zum zweiten Bildschirm in der App, mit einem Ausblendübergang zwischen den Bildschirmen.

   * **Text**-Eigenschaft = **"Assign Manager"**

3. Ändern Sie die Größe der Schaltfläche, um sie an den Text anzupassen.
   
    ![Aktualisieren des Schaltflächentexts](./media/sharepoint-scenario-build-app/04-03-06-button-updated.png)
4. Einfügen einer weiteren Schaltfläche mit den folgenden Eigenschaften:
   
   * **OnSelect**-Eigenschaft = **Navigate(ViewProjects, Fade)**.

   * **Text**-Eigenschaft = **"Update Details"**
     
     ![Aktualisieren des Schaltflächentexts](./media/sharepoint-scenario-build-app/04-03-08-buttons-final.png)
     
     > [!NOTE]
     > Die Schaltfläche ist mit **Update Details** (Details aktualisieren) beschriftet, zunächst wechseln wir jedoch zum Bildschirm **ViewProjects**, um ein zu aktualisierendes Projekt auszuwählen.

### <a name="run-the-app"></a>Ausführen der App
Noch ist der Funktionsumfang der App recht begrenzt, Sie können sie jedoch trotzdem ausführen:

1. Klicken oder tippen Sie auf die Anzeige **SelectTask** (die App wird immer mit der Anzeige gestartet, die im Vorschaumodus in PowerApps Studio ausgewählt ist).

2. Klicken oder tippen Sie auf ![Symbol „App ausführen“](./media/sharepoint-scenario-build-app/icon-run-arrow.png) in der rechten oberen Ecke, um die App auszuführen.

3. Klicken oder tippen Sie auf eine der Schaltflächen, um zu einem anderen Bildschirm zu wechseln.

4. Klicken oder tippen Sie auf ![Symbol „App-Vorschau schließen“](./media/sharepoint-scenario-build-app/icon-close-preview.png) in der rechten oberen Ecke, um die App zu schließen.

## <a name="step-4-build-the-assignmanager-screen"></a>Schritt 4: Erstellen des Bildschirms „AssignManager“
In diesem Schritt zeigen wir mit einem Katalog alle Projekte an, die genehmigt wurden, denen jedoch noch kein Manager zugewiesen wurde. Wir fügen weitere Steuerelemente hinzu, sodass Sie einen Manager zuweisen können.

> [!NOTE]
>  Wir erstellen später in der App eine Seite, auf der Sie sämtliche Felder für ein Projekt (einschließlich des Felds für den Manager) bearbeiten können, es erschien uns jedoch angebracht, auch diesen Bildschirm zu erstellen.

1. Speichern Sie die bisher vorgenommenen Änderungen.

2. Klicken oder tippen Sie in der linken Navigationsleiste auf den Bildschirm **AssignManager**.

### <a name="update-the-title-and-insert-introductory-text"></a>Aktualisieren des Titels und Einfügen von Einführungstext

1. Ändern Sie den Text **[Title]** (Titel) in **Assign Manager** (Manager zuweisen).

2. Fügen Sie eine Bezeichnung mit den folgenden Eigenschaften hinzu:
   
   * **Color**-Eigenschaft = **DarkGray**

   * **Size**-Eigenschaft = **18**

   * **Text**-Eigenschaft = **"Select a project, then assign a manager"** (Projekt auswählen, anschließend einen Manager zuweisen)
     
     ![Layout von „Assign Manager“ (Manager zuweisen)](./media/sharepoint-scenario-build-app/04-04-01-layout.png)

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>Hinzufügen eines Rückwärtspfeils, um zum Bildschirm „SelectTask“ zurückzukehren

1. Klicken oder tippen Sie auf die blaue Leiste am oberen Bildschirmrand.

2. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Symbole**, und klicken oder tippen Sie auf **Left** (Nach links).
   
    ![Einfügen eines Pfeils nach links](./media/sharepoint-scenario-build-app/04-04-02-icon-left.png)

3. Verschieben Sie den Pfeil auf die linke Seite der blauen Leiste, und legen Sie die folgenden Eigenschaften fest:
   
   * **Color**-Eigenschaft = **White**

   * **Height**-Eigenschaft = **40**

   * **OnSelect**-Eigenschaft = **Navigate(SelectTask, Fade)**

   * **Width**-Eigenschaft = **40**
     
     ![Hinzufügen einer Schaltfläche „Zurück“](./media/sharepoint-scenario-build-app/04-04-03-left-arrow.png)

### <a name="add-and-modify-a-gallery"></a>Hinzufügen und Ändern eines Katalogs

1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Katalog** und anschließend auf **Vertikal**.
   
    ![Hinzufügen eines vertikalen Katalogs](./media/sharepoint-scenario-build-app/04-04-04-gallery.png)

2. Wählen Sie im Menü **Layout** im rechten Bereich die Option **Titel, Untertitel und Text** aus. 
   
    ![Ändern des Kataloglayouts](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    Der Katalog verfügt nun über das richtige Layout, weist jedoch immer noch den standardmäßigen Beispieltext auf. Dies korrigieren wir im nächsten Schritt.
   
    ![Katalog mit Standardtext](./media/sharepoint-scenario-build-app/04-04-05-gallery-default.png)

3. Legen Sie die folgenden Eigenschaften für den Katalog fest:
   
   * **BorderThickness**-Eigenschaft = **1**

   * **BorderStyle**-Eigenschaft = **Dotted**

   * **Items**-Eigenschaft = **Filter('Project Details', PMAssigned="Unassigned")**. Im Katalog sind nur Projekte enthalten, denen kein Manager zugewiesen ist.
     
     ![Katalog mit Text aus der Liste](./media/sharepoint-scenario-build-app/04-04-06-gallery-updated.png)

4. Aktualisieren Sie im rechten Bereich die Felder entsprechend der folgenden Liste:
   
   * **ApprovedDate**

   * **Status**

   * **Title**
     
     ![Katalogfelder](./media/sharepoint-scenario-build-app/04-04-07-gallery-fields.png)

5. Passen Sie die Größe der Bezeichnungen im Katalog entsprechend an, und entfernen Sie den Pfeil vom ersten Katalogelement (dieser Katalog wird nicht mehr verlassen).
   
    ![Entfernen des Pfeilsymbols](./media/sharepoint-scenario-build-app/04-04-07a-remove-arrow.png)
   
    Der Bildschirm entspricht nun etwa dem in der folgenden Abbildung.
   
    ![Formatierter Katalog](./media/sharepoint-scenario-build-app/04-04-07b-gallery-size-text.png)

### <a name="change-the-color-of-an-item-if-its-selected"></a>Ändern der Farbe eines Elements, wenn dieses ausgewählt ist

1. Wählen Sie den Katalog aus, und legen Sie anschließend die **TemplateFill**-Eigenschaft auf **If (ThisItem.IsSelected=true, Orange, White)** fest.

2. Wählen Sie ein Element im Katalog aus. Der Bildschirm entspricht nun etwa dem in der folgenden Abbildung.
   
    ![Katalog mit ausgewähltem Element](./media/sharepoint-scenario-build-app/04-04-08-gallery-selected.png)

### <a name="add-a-label-text-input-and-ok-button-to-submit-manager-assignments"></a>Hinzufügen einer Bezeichnung, einer Texteingabe und einer Schaltfläche „OK“ für das Übermitteln von Managerzuweisungen

1. Klicken Sie oder tippen Sie auf eine Stelle außerhalb des Katalogs, an dem Sie gearbeitet haben.

2. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Bezeichnung**. Ziehen Sie die Bezeichnung unter den Katalog auf die linke Seite. Legen Sie die folgenden Eigenschaften für die Bezeichnung fest:
   
   * **Size**-Eigenschaft = **20**

   * **Text**-Eigenschaft = **"Manager:"**
   
   ![Hinzufügen der Bezeichnung „Manager“](./media/sharepoint-scenario-build-app/04-04-09-controls-text.png)

3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Text** und anschließend auf **Texteingabe**. Ziehen Sie die Texteingabe mittig unter den Katalog. Legen Sie die folgenden Eigenschaften für das Dropdown fest:
   
   * **Default**-Eigenschaft = **""**

   * **Height**-Eigenschaft = **60**

   * **Size**-Eigenschaft = **20**

   * **Width**-Eigenschaft = **250**
   
   ![Hinzufügen einer Texteingabe](./media/sharepoint-scenario-build-app/04-04-10-controls-text-box.png)

4. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Schaltfläche**. Ziehen Sie die Schaltfläche unter den Katalog auf die rechte Seite. Legen Sie die folgenden Eigenschaften für die Schaltfläche fest:
   
   * **Height**-Eigenschaft = **60**

   * **OnSelect**-Eigenschaft = **Patch('Project Details', LookUp('Project Details', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1.Text})**. Weitere Informationen finden Sie unter [Detaillierte Erläuterungen zu Formeln](#formula-deep-dive).

   * Mit dieser Formel wird die Liste **Project Details** (Projektdetails) aktualisiert, und es wird ein Wert für das Feld „PMAssigned“ festgelegt.

   * **Size**-Eigenschaft = **20**

   * **Text**-Eigenschaft = **"OK"**

   * **Width**-Eigenschaft = **80**
   
   ![Hinzufügen der Schaltfläche „OK“](./media/sharepoint-scenario-build-app/04-04-11-controls-button.png)

Der fertige Bildschirm sollte nun etwa dem in der folgenden Abbildung entsprechen.

![Fertiger Bildschirm „Assign Manager“ (Manager zuweisen)](./media/sharepoint-scenario-build-app/04-04-12-complete.png)

## <a name="step-5-build-the-viewprojects-screen"></a>Schritt 5: Erstellen des Bildschirms „ViewProjects“
In diesem Schritt ändern wir die Eigenschaften des Katalogs im Bildschirm **ViewProjects**. In diesem Katalog werden Elemente aus der Liste **Project Details** (Projektdetails) angezeigt. Sie wählen zunächst in diesem Bildschirm ein Element aus, dann bearbeiten Sie die Details im Bildschirm **UpdateDetails**.

1. Klicken oder tippen Sie in der linken Navigationsleiste auf den Bildschirm **ViewProjects**.

2. Ändern Sie **[Title]** (Titel) in **„View Projects“** (Projekte anzeigen).

3. Klicken oder tippen Sie in der linken Navigationsleiste unter **ViewProjects** auf **BrowserGallery1**.

4. Wählen Sie im Menü **Layout** im rechten Bereich die Option **Titel, Untertitel und Text** aus. 
   
    ![Ändern des Kataloglayouts](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    Der Katalog verfügt nun über das richtige Layout, weist aber immer noch den standardmäßigen Beispieltext auf.
   
    ![Katalog mit Standardtext](./media/sharepoint-scenario-build-app/04-04-04b-gallery-default.png)

5. Wählen Sie die Aktualisierungsschaltfläche ![Aktualisierungssymbol](./media/sharepoint-scenario-build-app/icon-refresh.png) aus, und legen Sie ihre **OnSelect**-Eigenschaft auf **Refresh('Project Details')** fest.

6. Wählen Sie die Schaltfläche für neue Elemente ![Neues Element hinzufügen](./media/sharepoint-scenario-build-app/icon-add-item.png) aus, und legen Sie ihre **OnSelect**-Eigenschaft auf **NewForm(EditForm1); Navigate(UpdateDetails, ScreenTransition.None)** fest.

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>Hinzufügen eines Rückwärtspfeils, um zum Bildschirm „SelectTask“ zurückzukehren

1. Klicken oder tippen Sie in der linken Navigationsleiste auf den Bildschirm **AssignManager**.

2. Wählen Sie den hier hinzugefügten Rückwärtspfeil aus, und kopieren Sie ihn.

3. Fügen Sie den Pfeil im Bildschirm **ViewProjects** ein, und positionieren Sie ihn links von der Aktualisierungsschaltfläche. 
   
    ![Schaltfläche „Zurück“](./media/sharepoint-scenario-build-app/04-05-04-left-arrow-v.png)
   
    Alle Eigenschaften werden mit übernommen, einschließlich der **OnSelect**-Eigenschaft mit dem Wert **Navigate(SelectTask, Fade)**.

### <a name="change-the-data-source-for-the-browsegallery1-gallery"></a>Ändern der Datenquelle für den Katalog „BrowseGallery1“

1. Wählen Sie den Katalog **BrowseGallery1** aus, und legen Sie die **Items**-Eigenschaft des Katalogs auf **SortByColumns(Filter('Project Details', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))** fest.
   
    Dadurch wird die Datenquelle des Katalogs auf die Liste **Project Details** (Projektdetails) festgelegt, und für Such- und Sortiervorgänge wird das Feld **Title** (Titel) verwendet.

2. Wählen Sie das ![Details-Pfeilsymbol](./media/sharepoint-scenario-build-app/icon-details-arrow.png) im ersten Katalogelement aus, und legen Sie die **OnSelect**-Eigenschaft auf **Navigate(UpdateDetails, None)** fest.
   
    ![ Katalog „Projekte anzeigen“ – erstes Element ausgewählt](./media/sharepoint-scenario-build-app/04-05-05b-gallery-arrow-v.png)

3. Aktualisieren Sie im rechten Bereich die Felder entsprechend der folgenden Liste:
   
   * **Status**

   * **PMAssigned**

   * **Title**
     
     ![Katalogfelder](./media/sharepoint-scenario-build-app/04-05-06-gallery-fields.png)
     
     Der fertige Bildschirm sollte nun etwa dem in der folgenden Abbildung entsprechen.
     
     ![Fertiger Bildschirm „View Project“ (Projekte anzeigen)](./media/sharepoint-scenario-build-app/04-05-07-viewprojects-final.png)

## <a name="step-6-build-the-updatedetails-screen"></a>Schritt 6: Erstellen des Bildschirms „UpdateDetails“
In diesem Schritt verbinden wir das Bearbeitungsformular im Bildschirm **UpdateDetails** mit der Datenquelle, zudem nehmen wir einige Änderungen an Eigenschaften und Feldern vor. In diesem Bildschirm bearbeiten Sie Details für ein Projekt, das Sie im Bildschirm **View Projects** (Projekte anzeigen) ausgewählt haben.

1. Klicken oder tippen Sie in der linken Navigationsleiste auf den Bildschirm **UpdateDetails**.

2. Ändern Sie **[Title]** (Titel) in **„Details aktualisieren“**.

3. Klicken oder tippen Sie in der linken Navigationsleiste unter **UpdateDetails** auf **EditForm1**.

4. Legen Sie die folgenden Eigenschaften für das Formular fest:
   
   * **DataSource**-Eigenschaft = **'Project Details'**

   * **Item**-Eigenschaft = **BrowseGallery1.Selected**

5. Lassen Sie das Formular ausgewählt, und klicken oder tippen Sie auf das Kontrollkästchen für die folgenden Felder. Beachten Sie dabei die angegebene Reihenfolge:
   
   * **Title**

   * **PMAssigned**

   * **Status**

   * **ProjectedStartDate**

   * **ProjectedEndDate**

   * **ProjectedDays**

   * **ActualDays**
     
     ![Bearbeiten der Felder des Formulars](./media/sharepoint-scenario-build-app/04-06-03-edit-fields.png)
6. Klicken Sie auf die Schaltfläche zum Abbrechen ![Symbol „Abbrechen“](./media/sharepoint-scenario-build-app/icon-cancel.png), und legen Sie ihre **OnSelect**-Eigenschaft auf **ResetForm(EditForm1); Back()** fest.

7. Wählen Sie die Schaltfläche zum Speichern ![Häkchensymbol „Speichern“](./media/sharepoint-scenario-build-app/icon-check-mark.png) aus, und probieren Sie die **OnSelect**-Formel aus – **SubmitForm(EditForm1)**. Da wir das Steuerelement zum Bearbeiten von Formularen verwenden, können wir **Submit()** und nicht wie früher **Patch()** verwenden.

Der fertige Bildschirm sollte nun wie der in der unten stehenden Abbildung aussehen (wenn die Felder leer sind, müssen Sie im Bildschirm **Projekte anzeigen** ein Element auswählen).

![Fertiger Bildschirm „Update Details“](./media/sharepoint-scenario-build-app/04-06-06-edit-final.png)

## <a name="step-7-run-the-app"></a>Schritt 7: Ausführen der App
Die App ist nun fertig gestellt – führen wir sie aus, um ihre Funktionsweise zu überprüfen. Wir fügen auf der SharePoint-Website einen Link zur App hinzu. Sie können die App dann im Browser ausführen, Sie müssen die App jedoch ggf. für andere Personen freigeben, damit sie von diesen ausgeführt werden kann. Weitere Informationen finden Sie unter [Freigeben von Apps](https://powerapps.microsoft.com/guided-learning/learning-manage-share-apps).

### <a name="add-a-link-to-the-app"></a>Hinzufügen eines Links zur App
1. Klicken oder tippen Sie im Office 365-App-Startfeld auf **PowerApps**.
   
    ![PowerApps im App-Startfeld von Office 365](./media/sharepoint-scenario-build-app/04-07-02a-waffle.png)

2. Klicken oder tippen Sie in PowerApps auf die Auslassungspunkte (**. . .**) für die **Project Management app** (Projektverwaltungs-App) und anschließend auf **Öffnen**.
   
    ![Auswählen der Projektverwaltungs-App](./media/sharepoint-scenario-build-app/04-07-02b-select-app.png)

3. Kopieren Sie die Adresse (URL) für die App in den Browser.
   
    ![Kopieren der App-URL](./media/sharepoint-scenario-build-app/04-07-02ba-copy-url.png)

4. Klicken oder tippen Sie in SharePoint auf **VERKNÜPFUNG BEARBEITEN**.
   
    ![Bearbeiten von Links auf der SharePoint-Website](./media/sharepoint-scenario-build-app/04-07-02c-edit-links.png)

5. Klicken oder tippen Sie auf **(+) Verknüpfung**.
   
    ![Hinzufügen einer App-Verknüpfung zur SharePoint-Website](./media/sharepoint-scenario-build-app/04-07-02d-add-link.png)

6. Geben Sie „Projektverwaltungs-App“ ein, und fügen Sie die Adresse für die App ein.
   
    ![Bearbeiten der Verknüpfungseigenschaften](./media/sharepoint-scenario-build-app/04-07-02e-link-dialog.png)

7. Klicken oder tippen Sie auf **OK** und anschließend auf **Speichern**.
   
    ![Speichern der Änderungen an der Verknüpfung](./media/sharepoint-scenario-build-app/04-07-02f-save.png)

### <a name="assign-a-manager-to-a-project"></a>Zuweisen eines Managers zu einem Projekt
Nun ist die App auf der SharePoint-Website vorhanden, und wir übernehmen die Rolle des Projektgenehmigers. Wir suchen nach allen Projekten, denen kein Manager zugewiesen ist, und weisen einem der Projekte einen Manager zu. Anschließend übernehmen wir die Rolle des Projektmanagers und fügen einige Informationen über ein Projekt hinzu, das uns zugewiesen wurde.

1. Betrachten wir zunächst die Liste **Project Details** (Projektdetails) in SharePoint. Zwei Projekte weisen in der Spalte **PMAssigned** den Wert **Unassigned** auf. Diese sehen wir in der App.
   
    ![Nicht zugewiesene Projekte in der SharePoint-Liste](./media/sharepoint-scenario-build-app/04-07-01-unassigned.png)

2. Klicken oder tippen Sie auf den Link, den Sie für die App erstellt haben.

3. Klicken oder tippen Sie im ersten Bildschirm auf **Assign Manager** (Manager zuweisen).
   
    ![Begrüßungsbildschirm der App](./media/sharepoint-scenario-build-app/04-07-03-intro-screen.png)

4. Im Bildschirm **Assign Manager** (Manager zuweisen) werden die beiden nicht zugewiesenen Projekte aus der Liste angezeigt. Wählen Sie das Projekt **New BI software** (Neue BI-Software) aus.
   
    ![Katalog mit ausgewähltem Element](./media/sharepoint-scenario-build-app/04-07-04-selected.png)

5. Geben Sie im Textfeld **Manager** den Namen „Joni Sherman“ ein, und klicken Sie dann auf **OK**.
   
    Die Änderung wird auf die Liste angewendet, und der Katalog wird aktualisiert, sodass nur das noch nicht zugewiesene Projekt angezeigt wird.
   
    ![Manager dem Projekt zuweisen](./media/sharepoint-scenario-build-app/04-07-05-updated.png)

6. Wechseln Sie zurück zur SharePoint-Liste, und aktualisieren Sie die Seite. Sie werden feststellen, dass der Projekteintrag mit dem Namen des Projektmanagers aktualisiert wurde.
   
    ![Zugewiesener Projektmanager in der SharePoint-Liste](./media/sharepoint-scenario-build-app/04-07-07-assigned.png)

### <a name="update-details-for-the-project"></a>Aktualisieren der Details für das Projekt

1. Klicken oder tippen Sie auf ![Symbol „Zurück“](./media/sharepoint-scenario-build-app/icon-back.png), um zum ersten Bildschirm zurückzukehren, und klicken oder tippen Sie dann auf **Update Details** (Details aktualisieren).
   
   ![Begrüßungsbildschirm der App](./media/sharepoint-scenario-build-app/04-07-08-intro-screen.png)

2. Geben Sie im Bildschirm **View Projects** (Projekte anzeigen) im Suchfeld „Neu“ ein.
   
   ![Durchsuchen des App-Katalogs](./media/sharepoint-scenario-build-app/04-07-09-search-new.png)

3. Klicken Sie auf ![Pfeilsymbol „Details“](./media/sharepoint-scenario-build-app/icon-details-arrow.png) für das Element **New BI software** (Neue BI-Software).
   
   ![Ausgewähltes Katalogelement](./media/sharepoint-scenario-build-app/04-07-10-select-project.png)

4. Legen Sie im Bildschirm **Update Details** (Details aktualisieren) die folgenden Werte fest:
   
   * Das Feld **ProjectedStartDate** = "3/6/2017"

   * Das Feld **ProjectedEndDate** = "3/24/2017"

   * Das Feld **ProjectedDays** = "15"
   
   ![Aktualisieren der Elementdetails](./media/sharepoint-scenario-build-app/04-07-11-update.png)

5. Klicken oder tippen Sie auf ![Häkchensymbol](./media/sharepoint-scenario-build-app/icon-check-mark.png) , um die Änderung auf die SharePoint-Liste anzuwenden.

6. Schließen Sie die App, und kehren Sie zur Liste zurück. Sie stellen fest, dass der Projekteintrag mit den Datums- und Tagesanzahländerungen aktualisiert wurde.
   
    ![Aktualisierte SharePoint-Liste](./media/sharepoint-scenario-build-app/04-07-11-updated-list.png)

## <a name="formula-deep-dive"></a>Detaillierte Erläuterung zu Formeln
Dies ist der zweite optionale Abschnitt für PowerApps Formeln. In der ersten detaillierten Erläuterung haben wir eine der Formeln betrachtet, die von PowerApps für den durchsuchbaren Katalog in einer App mit drei Bildschirmen generiert wird. In dieser detaillierten Erläuterung betrachten wir eine Formel, die wir für den Bildschirm **AssignManager** der zweiten App verwenden. Die Formel lautet wie folgt:

**Patch ( 'Project Details', LookUp ( 'Project Details', ID = Gallery1.Selected.ID ), {PMAssigned: TextInput1.Text} )**

Welche Aktionen führt diese Formel aus? Wenn Sie ein Element im Katalog auswählen und auf die Schaltfläche **OK** klicken, aktualisiert die Formel die Liste **Project Details** (Projektdetails), wobei die Spalte **PMAssigned** auf den Wert festgelegt wird, der in der Texteingabe angegeben ist. Die Formel führt ihre Aufgaben mithilfe von Funktionen aus:

* Die [**Patch**-Funktion](functions/function-patch.md) ändert einen oder mehrere Datensätze einer Datenquelle.

* Die [**LookUp**-Funktion](functions/function-filter-lookup.md) sucht den ersten Datensatz in einer Tabelle, der eine Formel erfüllt.

Folgendes geschieht, wenn Sie die Funktionen in der Formel kombinieren:

1. Wenn Sie auf die Schaltfläche **OK** klicken, wird die **Patch**-Funktion aufgerufen, um die Liste **Project Details** (Projektdetails) zu aktualisieren.

2. Innerhalb der **Patch**-Funktion ermittelt die **LookUp**-Funktion, welche Zeile der Liste **Project Details** (Projektdetails) aktualisiert werden muss. Dazu wird die ID des ausgewählten Katalogelements mit der ID in der Liste verglichen. Die ID 12 bedeutet beispielsweise, dass der Eintrag **New BI software** (Neue BI-Software) aktualisiert werden muss.

3. Wenn die **Patch**-Funktion über die richtige ID verfügt, aktualisiert sie das Feld **PMAssigned** mit dem Wert in **TextInput1.Text**.

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in diesem Tutorial besteht im [Erstellen eines Power BI-Berichts zum Analysieren von Projekten](sharepoint-scenario-build-report.md).

