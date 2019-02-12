---
title: Generieren einer Canvas-App zum Verarbeiten von Projektanforderungen | Microsoft-Dokumentation
description: In dieser Aufgabe generieren wir eine einfache Canvas-App mit drei Bildschirmen direkt aus einer SharePoint-Liste.
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
ms.openlocfilehash: 4466d8f42a0ba9c9a162353bc214abf6d9d9ef83
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834257"
---
# <a name="generate-a-canvas-app-to-handle-project-requests"></a>Generieren einer Canvas-App zum Verarbeiten von Projektanforderungen
> [!NOTE]
> Dieser Artikel ist Teil einer Reihe von Tutorials zur Verwendung von PowerApps, Microsoft Flow und Power BI mit SharePoint Online. Lesen Sie unbedingt die [Einführung zur Reihe](sharepoint-scenario-intro.md) durch, um sich einen allgemeinen Überblick zu verschaffen und auf die zugehörigen Downloads zuzugreifen.

Da jetzt die SharePoint-Listen vorhanden sind, können wir unsere erste App erstellen und anpassen. PowerApps ist in SharePoint integriert, deshalb lässt sich bequem eine einfache *App mit drei Bildschirmen* direkt aus einer Liste generieren. Mit dieser App können Sie Übersichts- und Detailinformationen für jedes Listenelement anzeigen, vorhandene Listenelemente aktualisieren und neue Listenelemente erstellen. Wenn Sie eine App direkt aus einer Liste erstellen, wird die App als *Ansicht* für diese Liste angezeigt. Anschließend können Sie die App in einem Browser sowie auf einem Mobiltelefon ausführen.

> [!TIP]
> Das [Downloadpaket](https://aka.ms/o4ia0f) für dieses Szenario enthält eine vollständige Version dieser App: project-requests-app.msapp.

## <a name="step-1-generate-an-app-from-a-sharepoint-list"></a>Schritt 1: Generieren einer App aus einer SharePoint-Liste

1. Klicken oder tippen Sie in der von Ihnen erstellten Liste **Project Requests** (Projektanforderungen) auf **PowerApps** und dann auf **App erstellen**.
   
    ![Erstellen einer App](./media/sharepoint-scenario-generate-app/02-01-01-create-app.png)

2. Geben Sie der App einen Namen, z.B. „Project Requests app“ (Projektanforderungen-App), und klicken oder tippen Sie dann auf **Erstellen**. Wenn die App fertiggestellt wurde, wird sie in PowerApps Studio geöffnet.
   
    ![Einen Namen für die App angeben](./media/sharepoint-scenario-generate-app/02-01-02-create-app-name.png)

## <a name="step-2-review-the-app-in-powerapps-studio"></a>Schritt 2: Überprüfen der App in PowerApps Studio

1. Auf der linken Navigationsleiste von PowerApps Studio wird standardmäßig eine hierarchische Ansicht der Bildschirme und Steuerelemente in der App angezeigt.
   
    ![PowerApps Studio mit hierarchischer Ansicht](./media/sharepoint-scenario-generate-app/02-02-01-studio-screens-hierarchy.png)

2. Klicken oder tippen Sie auf das Symbol „Miniaturansicht“, um die Ansicht zu wechseln.
   
    ![Ansichtsauswahl in PowerApps Studio](./media/sharepoint-scenario-generate-app/02-02-02-studio-view-selector.png)

3. Klicken oder tippen Sie auf jeden Bildschirm, um ihn im mittleren Bereich anzuzeigen. Es gibt drei Bildschirme:
   
    (a). Der **Bildschirm zum Durchsuchen**, in dem Sie die aus der Liste importierten Daten durchsuchen, sortieren und filtern können.
    
    (b). Der **Detailbildschirm**, in dem Sie weitere Informationen zu einem Element anzeigen können.
    
    (c). Der **Bildschirm zum Bearbeiten/Erstellen**, in dem sie vorhandene Elemente bearbeiten oder neue Elemente erstellen können.
      
      ![PowerApps Studio mit Miniaturansicht](./media/sharepoint-scenario-generate-app/02-02-03-studio-screens-thumbnails.png)

## <a name="step-3-customize-the-apps-browse-screen"></a>Schritt 3: Anpassen des App-Bildschirms zum Durchsuchen

1. Klicken oder tippen Sie auf den Bildschirm zum Durchsuchen.
   
    Das *Layout* dieses Bildschirms enthält einen *Katalog* zum Anzeigen von Listenelementen sowie weitere *Steuerelemente*, z.B. eine Suchleiste und eine Sortierschaltfläche.

2. Wählen Sie den Katalog **BrowseGallery1** durch Klicken oder Tippen auf einen beliebigen Eintrag außer dem ersten aus.
   
    ![In Katalog suchen](./media/sharepoint-scenario-generate-app/02-03-01-browse-gallery.png)

3. Klicken oder tippen Sie im rechten Bereich unter **Eigenschaften** auf **Projektanforderungen**. 

4. Aktualisieren Sie die Felder entsprechend der folgenden Liste:
   
   * **RequestDate**

   * **Requestor**

   * **Title**

     ![Katalogfelder](./media/sharepoint-scenario-generate-app/02-03-02-gallery-fields.png)

5. Wählen Sie, während **BrowseGallery1** noch ausgewählt ist, die **Items**-Eigenschaft aus.
   
    ![Items-Eigenschaft](./media/sharepoint-scenario-generate-app/02-03-03-items.png)

6. Ändern Sie die Formel in **SortByColumns(Filter('Project Requests', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))**.
   
    ![Die Bearbeitungsleiste](./media/sharepoint-scenario-generate-app/02-03-04-formula.png)
   
    Dies ermöglicht Ihnen das Sortieren und Suchen nach dem Feld **Title** (Titel) statt nach dem von PowerApps ausgewählten Standardfeld. Weitere Informationen finden Sie unter [Detaillierte Erläuterungen zu Formeln](#formula-deep-dive).

6. Klicken oder tippen Sie auf **Datei** und anschließend auf **Speichern**. Klicken oder tippen Sie auf ![Symbol „Zurück zur App“](./media/sharepoint-scenario-generate-app/icon-back-to-app.png), um zur App zurückzukehren.

## <a name="step-4-review-the-apps-details-screen-and-edit-screen"></a>Schritt 4: Überprüfen des Detailbildschirms und Bearbeitungsbildschirms der App
1. Klicken oder tippen Sie auf den Detailbildschirm.
   
    Dieser Bildschirm hat ein anderes Layout, das ein *Anzeigeformular* enthält, um die Details für ein im Katalog ausgewähltes Element anzuzeigen. Es enthält Steuerelemente zum Bearbeiten und Löschen von Elementen und ein Steuerelement, mit dem Sie zum Bildschirm zum Durchsuchen zurückkehren können.
   
    ![Formular zum Anzeigen von Details](./media/sharepoint-scenario-generate-app/02-04-01-details.png)

4. Klicken oder tippen Sie auf den Bearbeitungsbildschirm.
   
    Dieser Bildschirm enthält ein *Bearbeitungsformular* zum Bearbeiten des ausgewählten Elements oder Erstellen eines neuen Elements (wenn Sie vom Bildschirm zum Durchsuchen direkt zu diesem Bildschirm wechseln). Es enthält Steuerelemente zum Speichern oder Verwerfen von Änderungen.

    ![Bearbeitungsformular](./media/sharepoint-scenario-generate-app/02-04-03-edit.png)

## <a name="step-5-run-the-app-from-the-list"></a>Schritt 5: Ausführen der App aus der Liste

1. Klicken oder tippen Sie in der Liste **Project Requests**  (Projektanforderungen) auf **Alle Elemente** und dann auf **Project Requests app** (Projektanforderungen-App).
   
    ![Projektanforderungen-App anzeigen](./media/sharepoint-scenario-generate-app/02-05-01-view-app.png)
2. Klicken Sie auf **Öffnen**, um die App in einer neuen Browserregisterkarte zu öffnen.
   
    ![Projektanforderungen-App öffnen](./media/sharepoint-scenario-generate-app/02-05-02-open-app.png)

3. Klicken oder tippen Sie in der App auf ![Symbol „Zur App wechseln“](./media/sharepoint-scenario-generate-app/icon-details-arrow.png) für das erste Element im Katalog zum Durchsuchen.
   
    ![Erstes Katalogelement](./media/sharepoint-scenario-generate-app/02-05-04-first-item.png)

4. Klicken oder tippen Sie auf ![Stift-Bearbeitungssymbol](./media/sharepoint-scenario-generate-app/icon-pencil.png) um das Element zu bearbeiten.

5. Aktualisieren Sie das Feld **Description** (Beschreibung) – ändern Sie das letzte Wort „Gruppe“ in „Team“, und klicken oder tippen Sie dann auf ![Häkchensymbol](./media/sharepoint-scenario-generate-app/icon-check-mark.png).
   
   ![Feld „Description“ (Beschreibung) aktualisieren](./media/sharepoint-scenario-generate-app/02-05-07-edit.png)

6. Schließen Sie die Browserregisterkarte.

7. Kehren Sie zur Liste **Project Requests** (Projektanforderungen) zurück, klicken oder tippen Sie auf **Project Requests app** (Projektanforderungen-App) und dann auf **Alle Elemente**.
   
   ![Alle Elemente anzeigen](./media/sharepoint-scenario-generate-app/02-05-08-view-all.png)
8. Überprüfen Sie die Änderung, die Sie in der App vorgenommen haben.
   
    ![Bearbeitung überprüfen](./media/sharepoint-scenario-generate-app/02-05-09-verify-edit.png)

Dies ist eine recht einfache App, und wir haben nur einige grundlegende Anpassungen vorgenommen. Sie sehen aber, dass sich schnell etwas Interessantes erstellen lässt. Wir fahren jetzt mit der nächsten Aufgabe fort. Wenn Sie möchten, können Sie sich jedoch die App etwas genauer anschauen, um zu sehen, wie die Steuerelemente und Formeln das Verhalten der App steuern.

## <a name="formula-deep-dive"></a>Detaillierte Erläuterung zu Formeln
Dieser Abschnitt ist optional, er bietet Ihnen jedoch ein tieferes Verständnis der Funktionsweise von Formeln. In Schritt 3 dieser Aufgabe haben wir die Formel für die **Items**-Eigenschaft von **BrowseGallery1** geändert. Diese Änderung bewirkte, dass beim Sortieren und Suchen das Feld **Title** (Titel) statt des von PowerApps ausgewählten Felds verwendet wird. Dies ist die geänderte Formel:

**SortByColumns ( Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text ) ), "Title", If ( SortDescending1, Descending, Ascending ) )**

Aber welche Aktionen führt diese Formel aus? Sie bestimmt die Quelle der im Katalog angezeigten Daten, filtert die Daten anhand des im Suchfeld eingegebenen Texts und sortiert die Ergebnisse basierend auf der Sortierschaltfläche in der App. Die Formel führt ihre Aufgaben mithilfe von *Funktionen* aus. Funktionen akzeptieren Parameter (die Eingabe), führen einen Vorgang (z.B. Filtern) aus und geben einen Wert zurück (die Ausgabe):

* Die [**SortByColumns**-Funktion](functions/function-sort.md) sortiert eine Tabelle nach einer oder mehreren Spalten.
* Die [**Filter**-Funktion ](functions/function-filter-lookup.md) sucht die Datensätze in einer Tabelle, die die Bedingungen einer von Ihnen angegebenen Formel erfüllen.
* Die [**StartsWith**-Funktion](functions/function-startswith.md) testet, ob eine Zeichenfolge mit einer anderen beginnt.
* Die [**If**-Funktion](functions/function-if.md) gibt einen Wert zurück, wenn für eine Bedingung „true“ gilt, und gibt einen anderen Wert zurück, wenn für die gleiche Bedingung „false“ gilt.

Folgendes geschieht, wenn Sie die Funktionen in der Formel kombinieren:

1. Wenn Sie Text im Suchfeld eingeben, vergleicht die **StartsWith**-Funktion den Text mit dem Anfang jeder Zeichenfolge in der Spalte **Title** (Titel) der Liste.
   
    **StartsWith ( Title, TextSearchBox1.Text )**
   
    Wenn Sie z.B. im Suchfeld „ge“ eingeben, werden vier Ergebnisse angezeigt, einschließlich Elementen, die mit „Gebiet“ und „Gerät“ beginnen. „Mobile Geräte“ wird nicht angezeigt, da dieses Element nicht mit „ge“ *beginnt*.

2. Mit der **Filter**-Funktion werden Zeilen aus der Tabelle **Project Requests** (Projektanforderungen) *zurückgegeben*. Wenn das Suchfeld keinen zu vergleichenden Text enthält, gibt die **Filter**-Funktion alle Zeilen zurück.
   
    **Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text )**

3. Die **If**-Funktion überprüft, ob die Variable **SortDescending1** auf „true“ oder „false“ festgelegt ist (wird durch die Sortierschaltfläche in der App festgelegt). Die Funktion gibt dann den Wert **Descending** oder **Ascending** zurück.
   
    **If ( SortDescending1, Descending, Ascending )**

4. Jetzt kann die **SortByColumns**-Funktion den Katalog sortieren. In diesem Fall erfolgt die Sortierung nach dem Feld **Title** (Titel), dies kann jedoch ein anderes Feld als das für die Suche verwendete Feld sein.

Wir hoffen, dass Sie nach diesen Erläuterungen ein besseres Verständnis der Funktionsweise dieser Formel haben und jetzt genauer wissen, wie Sie durch das Kombinieren von Funktionen und anderen Elementen das gewünschte Verhalten Ihrer Apps erzielen. Weitere Informationen finden Sie unter [Referenz zu Formeln für PowerApps](formula-reference.md).

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Tutorialreihe ist das [Erstellen eines Flows zum Verwalten von Projektgenehmigungen](sharepoint-scenario-approval-flow.md).

