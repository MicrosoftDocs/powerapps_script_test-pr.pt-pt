---
title: Anpassen eines Formulars in einer Canvas-App | Microsoft-Dokumentation
description: Geben Sie in PowerApps an, welche Daten in einem Canvas-App-Formular in welcher Reihenfolge und in welchen Steuerelementen angezeigt werden sollen.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bb6f8edb35bd6f19bff06516f6fb9d22de1320a0
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42852667"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>Anpassen eines Canvas-App-Formulars in PowerApps

Passen Sie in einer Canvas-App ein **Anzeigeformular**-Steuerelement und ein **Bearbeitungsformular**-Steuerelement an, sodass die wichtigsten Daten in der intuitivsten Reihenfolge angezeigt werden, damit Benutzer die Daten leicht verstehen und aktualisieren können.

Jedes Formular umfasst eine oder mehrere Karten, die jeweils Daten aus einer bestimmten Spalte in der Datenquelle anzeigen. Wenn Sie die in diesem Artikel beschriebenen Schritte ausführen, können Sie angeben, welche Karten in einem Formular angezeigt werden, und Karten innerhalb eines Formulars nach oben oder unten verschieben.

Wenn Sie mit PowerApps nicht vertraut sind, finden Sie Grundlagen unter [Einführung in PowerApps](getting-started.md).

## <a name="prerequisites"></a>Voraussetzungen

[Generieren einer App](data-platform-create-app.md) aus Common Data Service und [Anpassen des Katalogs](customize-layout-sharepoint.md) in dieser App.

## <a name="show-and-hide-cards"></a>Karten ein- und ausblenden

1. Melden Sie sich bei [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

    ![Startseite der PowerApps-Website](./media/customize-forms-sharepoint/sign-in.png)


1. Öffnen Sie die App, die Sie generiert und angepasst haben.

1. Geben Sie auf der Navigationsleiste links in der Suchleiste **D** ein, um die Liste der Elemente zu filtern, klicken oder tippen Sie dann auf **DetailForm1**, um dieses Element auszuwählen.

    ![Detailbildschirm auswählen](./media/customize-forms-sharepoint/select-detailform.png)

1. Klicken oder tippen Sie im rechten Bereich auf **Accounts** (Konten), um den Bereich **Data** (Daten) anzuzeigen.

    ![Bereich „Daten“ anzeigen](./media/customize-forms-sharepoint/show-data-pane.png)

1. Deaktivieren Sie im Bereich **Daten** die Kontrollkästchen **Hauptkontakt**, **Beschreibung** und **Address 1: Street 2** (Adresse 1: Straße 2), um diese Felder auszublenden.

    ![Liste der Felder](./media/customize-forms-sharepoint/hide-fields.png)

1.  Aktivieren Sie im Bereich **Daten** das Kontrollkästchen **Address 1: ZIP/Postal code** (Adresse 1: PLZ), um dieses Feld anzuzeigen.

    ![Liste der Felder](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>Karten anordnen
1. Ziehen Sie im Bereich **Daten** das Feld **Kontoname** an die oberste Stelle in der Liste der Felder.

    ![Karte verschieben](./media/customize-forms-sharepoint/move-card.png)

    Die Karten in **DetailForm1** stellen die gleiche Änderung dar.

    ![Karten neu angeordnet](./media/customize-forms-sharepoint/reordered-card.png)

1. Ordnen Sie die anderen Karten in der folgenden Reihenfolge neu an:

    - Kontoname
    - Adresse 1: Straße 1
    - Adresse 1: Stadt
    - Adresse 1: PLZ
    - Anzahl der Mitarbeiter
    - Jahresumsatz

1. Geben Sie auf der Navigationsleiste links in der Suchzeile **Ed** ein, und klicken oder tippen Sie dann auf **EditForm1**, um dieses Element auszuwählen.

1. Wiederholen Sie die Schritte dieser und der vorherigen Prozedur, damit die Felder in **EditForm1** denen in **DetailForm1** gleichen.

## <a name="run-the-app"></a>Ausführen der App
1. Geben Sie in der Navigationsleiste links **Br** ein, um die Liste zu filtern, und klicken oder tippen Sie dann auf **BrowseScreen1**, um dieses Element auszuwählen.

2. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Auswählen des Symbols **Preview** in der Nähe der oberen rechten Ecke).

    ![„Preview“-Symbol](./media/customize-forms-sharepoint/open-preview.png)

3. In der oberen rechten Ecke klicken oder tippen Sie auf das Pluszeichen zum Hinzufügen eines Datensatzes in **EditScreen1**.

    ![Hinzufügen eines Datensatzes](./media/customize-forms-sharepoint/add-record.png)

4. Fügen Sie beliebige Daten hinzu, und klicken oder tippen Sie auf das Häkchen in der oberen rechten Ecke, um Ihre Änderungen zu speichern und zu **BrowseScreen1** zurückzukehren.

    ![Datensatz speichern](./media/customize-forms-sharepoint/save-record.png)

5. Klicken oder tippen Sie auf den Pfeil für das Element, das Sie gerade erstellt haben, um Details zu diesem Element in **DetailScreen1** anzuzeigen.  

    ![Pfeil nach rechts](./media/customize-forms-sharepoint/right-arrow.png)

6. In der oberen rechten Ecke klicken oder tippen Sie auf das Bearbeiten-Symbol zum Aktualisieren des Datensatzes in **EditScreen1**.

    ![Datensatz bearbeiten](./media/customize-forms-sharepoint/edit-record.png)

7. Ändern Sie die Informationen in mindestens einem Feld, und klicken oder tippen Sie auf das Häkchen in der oberen rechten Ecke, um Ihre Änderungen in der SharePoint-Liste zu speichern und zu **DetailScreen1** zurückzukehren.  

    ![Änderungen speichern](./media/customize-forms-sharepoint/save-record.png)

8. Klicken oder tippen Sie in der Nähe der oberen rechten Ecke auf das Papierkorb-Symbol, um den Datensatz zu löschen, den Sie gerade aktualisiert haben, und um wieder zu **BrowseScreen1** zurückzukehren.

    ![Datensatz löschen](./media/customize-forms-sharepoint/delete-record.png)

9. Schließen Sie den Vorschaumodus, indem Sie die ESC-TASTE drücken (oder indem Sie in der oberen rechten Ecke auf das Symbol zum Schließen klicken oder tippen).

## <a name="next-steps"></a>Nächste Schritte
- [Speichern und Veröffentlichen](save-publish-app.md) Ihrer App.
- [Customize a card (Anpassen einer Karte)](customize-card.md) in Ihrer App.
