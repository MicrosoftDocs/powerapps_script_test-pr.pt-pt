---
title: Erstellen einer Canvas-App anhand von Excel-Daten | Microsoft-Dokumentation
description: In diesem Tutorial erstellen Sie eine Canvas-App mit zwei Bildschirmen, damit Benutzer Datensätze erstellen, bearbeiten und löschen können.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/23/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c398bb7a916c98aa769e39477fe889a74fce32c
ms.sourcegitcommit: c1f58a16f8dcd309a1d5fc4658ca16d82c615994
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/23/2018
ms.locfileid: "51333994"
---
# <a name="create-an-canvas-app-from-scratch-based-on-excel-data"></a>Erstellen einer Canvas-App anhand von Excel-Daten

Erstellen Sie Ihre eigene Canvas-App auf Grundlage von Excel-Daten im Tabellenformat, und fügen Sie auf Wunsch Daten aus anderen Quellen hinzu. Mithilfe dieses Tutorials können Sie eine App erstellen, die zwei Bildschirme enthält. Auf einem Bildschirm können Benutzer eine Reihe von Datensätzen durchsuchen. Auf dem anderen Bildschirm können Benutzer einen Datensatz erstellen, ein oder mehrere Felder in einem Datensatz aktualisieren oder einen vollständigen Datensatz löschen. Dieser Ansatz ist zeitaufwändiger als das [automatische Generieren einer App](get-started-create-from-data.md), aber erfahrene App-Entwickler können damit die beste App für ihre Anforderungen erstellen.

## <a name="prerequisites"></a>Voraussetzungen

Damit Sie die Schritte in diesem Tutorial genau ausführen können, erstellen Sie zunächst eine Excel-Datei mit diesen Beispieldaten.

1. Kopieren Sie diese Daten, und fügen Sie sie in eine Excel-Datei ein.

    | StartDay | StartTime | Volunteer | Backup |
    | --- | --- | --- | --- |
    | Saturday |10am-noon |Vasquez |Kumashiro |
    | Saturday |noon-2pm |Ice |Singhal |
    | Saturday |2pm-4-pm |Myk |Mueller |
    | Sunday |10am-noon |Li |Adams |
    | Sunday |10am-noon |Singh |Morgan |
    | Sunday |10am-noon |Batye |Nguyen |

2. Formatieren Sie diese Daten als Tabelle mit dem Namen **Schedule**, sodass die Informationen von PowerApps analysiert werden können.

    Weitere Informationen finden Sie unter [Formatieren einer Tabelle in Excel](how-to-excel-tips.md).

3. Speichern Sie die Datei unter dem Namen **eventsignup.xls**, schließen Sie sie, und laden Sie sie dann in ein [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md) wie z.B. OneDrive hoch.

> [!IMPORTANT]
> Sie können Ihre eigene Excel-Datei verwenden und dieses Tutorial nur für allgemeine Konzepte durchsehen. Die Daten in der Excel-Datei müssen jedoch als Tabelle formatiert sein. Weitere Informationen finden Sie unter [Formatieren einer Tabelle in Excel](how-to-excel-tips.md).

## <a name="open-a-blank-app"></a>Öffnen einer leeren App
1. Melden Sie sich bei [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

    Sie können eine App von Grund auf neu für Telefone oder andere Geräte (z.B. Tablets) entwerfen. Dieses Thema konzentriert sich auf den Entwurf einer App für Telefone.

1. Zeigen Sie unter **Eigene App erstellen** auf die Kachel **Mit leerer App starten** für Canvas-Apps, wählen Sie das Telefonsymbol und anschließend **Diese App erstellen** aus.

    ![Kachel für leere App](./media/get-started-create-from-blank/start-from-blank.png)

    PowerApps Studio erstellt eine leere App für Telefone.

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** geöffnet wird, wählen Sie **Überspringen** aus.

## <a name="connect-to-data"></a>Herstellen einer Datenverbindung
1. Wählen Sie in der Mitte des Bildschirms **Mit Daten verbinden** aus.

1. Wählen Sie im Bereich **Daten** die Verbindung für Ihr Cloudspeicherkonto aus, wenn es angezeigt wird. Gehen Sie andernfalls folgendermaßen vor, um eine Verbindung hinzuzufügen:

    1. Wählen Sie **neue Verbindung**, die Kachel für Ihr Cloudspeicherkonto und dann **Erstellen** aus.
    2. Wenn Sie dazu aufgefordert werden, geben Sie Ihre Anmeldeinformationen für dieses Konto ein.

1. Um die Liste zu filtern, geben bzw. fügen Sie unter **Excel-Datei auswählen** die ersten Buchstaben von **eventsignup** ein, und wählen Sie dann die Datei aus, die Sie hochgeladen haben.

1. Aktivieren Sie unter **Eine Tabelle auswählen** das Kontrollkästchen für **Schedule**, und wählen Sie dann **Verbinden** aus.

## <a name="create-the-view-screen"></a>Erstellen des Anzeigebildschirms

1. Wählen Sie auf der Registerkarte **Home** den Pfeil nach unten neben **Neuer Bildschirm** aus, um eine Liste der Bildschirmtypen zu öffnen, und wählen Sie dann **Listenbildschirm** aus.

    ![Hinzufügen einer Listenanzeige](./media/get-started-create-from-blank/add-list-screen.png)

    Es wird ein Bildschirm mit mehreren Standardsteuerelementen hinzugefügt, wie etwa einem Suchfeld und einem **[Katalog](controls/control-gallery.md)**-Steuerelement. Der Katalog deckt den gesamten Bildschirm unter dem Suchfeld ab.

2. Wählen Sie den Katalog durch Klicken oder Tippen in der Nähe seiner Mitte aus.

    Ein Auswahlrahmen mit Ziehpunkten umgibt den Katalog.

    ![Hinzufügen einer Listenanzeige](./media/get-started-create-from-blank/select-gallery.png)

3. Wählen Sie im rechten Bereich **CustomGallerySample** aus, um den Bereich **Daten** zu öffnen.

    ![Bereich „Daten“ öffnen](./media/get-started-create-from-blank/custom-gallery-sample.png)

4. Wählen Sie unter **Datenquelle** den Pfeil nach unten aus, um die Liste der Datenquellen für die App zu öffnen, und wählen Sie dann **Schedule** aus.

    ![Datenquelle auswählen](./media/get-started-create-from-blank/select-schedule.png)

5. Wählen Sie unter **Layout** den Pfeil nach unten aus, um die Liste der Layouts zu öffnen, und wählen Sie dann **Titel, Untertitel und Text** aus.

    ![Auswählen des Layouts](./media/get-started-create-from-blank/select-layout.png)

6. Ändern Sie unter **Title2** die angezeigte Spalte von **Backup** in **Volunteer**.

     ![Spalte in Bezeichnung ändern](./media/get-started-create-from-blank/change-title2.png)

7. Schließen Sie den Bereich **Daten**, indem Sie in der oberen rechten Ecke das Symbol zum Schließen auswählen.

    Der Katalog zeigt den Namen jedes Freiwilligen sowie Tag und Uhrzeit seiner Schicht an.

    ![Die unsortierten „Schedule“-Daten im Katalog](./media/get-started-create-from-blank/show-data-unsorted.png)

8. Wählen Sie den Katalog aus, und vergewissern Sie sich, dass die Eigenschaftenliste **[Items](controls/properties-core.md)** anzeigt.

    Wie in die Bearbeitungsleiste gezeigt, hat diese Eigenschaft den Wert **Schedule**.

    ![Die unsortierten „Schedule“-Daten im Katalog](./media/get-started-create-from-blank/set-property.png)

9. Ändern Sie den Wert der Eigenschaft **Items**, indem Sie diese Formel kopieren und in die Bearbeitungsleiste einfügen:

    **SortByColumns(Search(Schedule, TextSearchBox1.Text, "Volunteer"), "Volunteer", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))**

    Der Katalog zeigt Daten in alphabetischer Reihenfolge nach den Namen der Freiwilligen an.

    ![Die sortierten „Schedule“-Daten im Katalog](./media/get-started-create-from-blank/show-data-sorted.png)

    Benutzer können den Katalog nach den Namen der Freiwilligen basierend auf den Funktionen **SortByColumns** und **Search** in dieser Formel sortieren und filtern.

   - Wenn ein Benutzer mindestens einen Buchstaben in das Suchfeld eingibt, zeigt der Katalog nur die Datensätze an, bei denen das Feld **Volunteer** den Text enthält, den der Benutzer eingibt.
   - Wenn ein Benutzer die Sortierschaltfläche auswählt, zeigt der Katalog die Datensätze in aufsteigender oder absteigender Reihenfolge (je nachdem, wie häufig der Benutzer die Schaltfläche auswählt) basierend auf dem Feld **Volunteer** an.

     Weitere Informationen zu diesen und anderen Funktionen finden Sie unter [formula reference (Formelreferenz)](formula-reference.md).

10. Geben Sie ein **i** in das Suchfeld ein, wählen Sie die Sortierschaltfläche durch Klicken oder Tippen aus, und wählen Sie sie noch einmal aus (oder eine ungerade Anzahl weiterer Male).

     Der Katalog zeigt diese Ergebnisse an.

     ![Sortieren und Filtern der Galerie](./media/get-started-create-from-blank/sort-filter.png)

11. Löschen Sie den gesamten Text im Suchfeld.

12. Wählen Sie am oberen Rand des Bildschirms das Steuerelement **[Bezeichnung](controls/control-text-box.md)** aus, und ersetzen Sie dann **[Titel]** durch **Datensätze anzeigen**.

     ![Ändern der Titelleiste](./media/get-started-create-from-blank/change-title-bar.png)

## <a name="create-the-change-screen"></a>Erstellen des Änderungsbildschirms
1. Wählen Sie auf der Registerkarte **Home** den Pfeil nach unten neben **Neuer Bildschirm** und dann **Formularbildschirm** aus.

     ![Formularbildschirm hinzufügen](./media/get-started-create-from-blank/add-form-screen.png)

1. Wählen Sie im Bildschirm, den Sie gerade hinzugefügt haben, **Mit Daten verbinden** aus, um den Bereich **Daten** zu öffnen, und legen Sie als Datenquelle **Schedule** fest.

1. Aktivieren Sie unter **Felder** alle Kontrollkästchen, um alle Felder im Formular anzuzeigen.

     ![Felder anzeigen](./media/get-started-create-from-blank/show-fields.png)

1. Ziehen Sie das Feld **Volunteer** nach oben, sodass es am oberen Rand der Liste der Felder angezeigt wird.

     ![Felder neu anordnen](./media/get-started-create-from-blank/reorder-fields.png)

1. Wählen Sie das Formular aus, und legen Sie für seine Eigenschaft **Item** diesen Ausdruck fest, indem Sie ihn in die Bearbeitungsleiste eingeben oder einfügen:<br>**BrowseGallery1.Selected**

1. Wählen Sie am oberen Rand des Bildschirms das Steuerelement **[Bezeichnung](controls/control-text-box.md)** aus, und ersetzen Sie dann **[Titel]** durch **Datensätze ändern**.

    ![Ändern der Titelleiste](./media/get-started-create-from-blank/change-title-bar2.png)

## <a name="delete-and-rename-screens"></a>Löschen und Umbenennen von Bildschirmen
1. Wählen Sie in der linken Navigationsleiste die Auslassungspunkte (...) für **Screen1** und dann **Löschen** aus.

    ![Bildschirm löschen](./media/get-started-create-from-blank/delete-screen.png)

1. Wählen Sie die Auslassungspunkte (...) für **Screen2** aus, wählen Sie **Umbenennen** aus, und geben bzw. fügen Sie dann **ViewScreen** ein.

1. Wählen Sie die Auslassungspunkte (...) für **Screen3** aus, wählen Sie **Umbenennen** aus, und geben bzw. fügen Sie dann **ChangeScreen** ein.

## <a name="configure-icons-on-the-view-screen"></a>Konfigurieren von Symbolen auf dem Anzeigebildschirm
1. Wählen Sie am oberen Rand des **ViewScreen** das Gebogener-Pfeil-Symbol aus.

    ![Hinzufügen eines Datensatzes](./media/get-started-create-from-blank/refresh-icon.png)

1. Legen Sie die Eigenschaft **OnSelect** für dieses Symbol auf die folgende Formel fest:<br>**Refresh(Schedule)**

    Wenn der Benutzer dieses Symbol auswählt, werden die Daten von **Schedule** auf Basis der Excel-Datei aktualisiert.

    Weitere Informationen zu diesen und anderen Funktionen finden Sie in der [Referenz zu Formeln für PowerApps](formula-reference.md).

1. Wählen Sie in der oberen rechten Ecke des **ViewScreen** das Plussymbol aus.

    ![Hinzufügen eines Datensatzes](./media/get-started-create-from-blank/add-record.png)

1. Legen Sie die Eigenschaft **OnSelect** für dieses Symbol auf die folgende Formel fest:<br>**NewForm(EditForm1);Navigate(ChangeScreen,ScreenTransition.None)**

    Wenn der Benutzer dieses Symbol auswählt, wird der **ChangeScreen** angezeigt, wobei jedes Feld leer ist, damit der Benutzer einen Datensatz einfacher erstellen kann.

1. Wählen Sie für den ersten Datensatz im Katalog den nach rechts weisenden Pfeil aus.

    ![Pfeil auswählen](./media/get-started-create-from-blank/select-arrow.png)

1. Legen Sie die Eigenschaft **OnSelect** für den Pfeil auf die folgende Formel fest:<br>**EditForm(EditForm1); Navigate(ChangeScreen, ScreenTransition.None)**

    Wenn der Benutzer dieses Symbol auswählt, wird in **ChangeScreen** jedes Feld mit den Daten für den ausgewählten Datensatz angezeigt, sodass der Benutzer den Datensatz leichter bearbeiten oder löschen kann.

## <a name="configure-icons-on-the-change-screen"></a>Konfigurieren von Symbolen auf dem Änderungsbildschirm
1. Wählen Sie auf **ChangeScreen** das „X“-Symbol in der oberen linken Ecke aus.

    ![Symbol „Abbrechen“](./media/get-started-create-from-blank/cancel-icon.png)

1. Legen Sie die Eigenschaft **OnSelect** für dieses Symbol auf die folgende Formel fest:<br>**ResetForm(EditForm1);Navigate(ViewScreen, ScreenTransition.None)**

    Wenn der Benutzer dieses Symbol auswählt, werden alle Änderungen verworfen, die er in diesem Bildschirm vorgenommen hat, und der Anzeigebildschirm wird geöffnet.

1. Wählen Sie in der oberen rechten Ecke das Häkchensymbol aus.

    ![Häkchensymbol](./media/get-started-create-from-blank/checkmark-icon.png)

1. Legen Sie die Eigenschaft **OnSelect** für das Häkchen auf die folgende Formel fest:<br>**SubmitForm(EditForm1); Navigate(ViewScreen, ScreenTransition.None)**

    Wenn der Benutzer dieses Symbol auswählt, werden alle Änderungen gespeichert, die er in diesem Bildschirm vorgenommen hat, und der Anzeigebildschirm wird geöffnet.

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole** und dann das **Papierkorbsymbol** aus.

1. Legen Sie für die Eigenschaft **Farbe** des neuen Symbols **Weiß** fest, und verschieben Sie das neue Symbol, sodass es neben dem Häkchensymbol angezeigt wird.

    ![Papierkorbsymbol](./media/get-started-create-from-blank/trash-icon.png)

1. Legen Sie die Eigenschaft **OnSelect** für das Papierkorbsymbol auf die folgende Formel fest:<br>**Remove(Schedule, BrowseGallery1.Selected); Navigate(ViewScreen, ScreenTransition.None)**

    Wenn der Benutzer dieses Symbol auswählt, wird der ausgewählte Datensatz aus der Datenquelle gelöscht, und der Anzeigebildschirm wird geöffnet.

## <a name="test-the-app"></a>Testen der App
1. Wählen Sie den **ViewScreen** aus, und rufen Sie die Vorschau durch Drücken von F5 auf (oder durch Auswählen des **Vorschausymbols** in der Nähe der oberen rechten Ecke).

    ![Öffnen des Vorschaumodus](./media/get-started-create-from-blank/open-preview.png)

1. Fügen Sie einen Datensatz hinzu.

1. Aktualisieren Sie den hinzugefügten Datensatz, und speichern Sie die Änderungen.

1. Aktualisieren Sie den hinzugefügten Datensatz, und widerrufen Sie die Änderungen.

1. Löschen Sie den hinzugefügten Datensatz.

1. Schließen Sie den Vorschaumodus durch Drücken von ESC (oder durch Auswählen des Schließsymbols in der Nähe der oberen rechten Ecke).

## <a name="next-steps"></a>Nächste Schritte

- Drücken Sie STRG+S, um Ihre App in der Cloud zu speichern, sodass Sie sie auf anderen Geräten ausführen können.
- Sie können die [App freigeben](share-app.md), damit sie von anderen Personen ausgeführt werden kann.
- Erfahren Sie mehr über [Funktionen](working-with-formulas.md) wie **Patch**, mit denen Sie Daten verwalten können, ohne ein Standardformular zu erstellen.
- [Verknüpfen Sie diese App mit einer Projektmappe](add-app-solution.md), damit Sie diese beispielsweise in einer anderen Umgebung bereitstellen oder sie auf AppSource veröffentlichen können.
