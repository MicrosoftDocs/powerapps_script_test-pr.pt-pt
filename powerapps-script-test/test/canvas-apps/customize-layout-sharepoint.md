---
title: Tutorial – Anpassen eines Katalogs in einer generierten App | Microsoft-Dokumentation
description: In diesem Tutorial passen Sie die Daten an, die in der Galerie und anderen Elementen einer App angezeigt werden, die in PowerApps automatisch generiert wurde.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: tutorial
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6e77ddfcc572a776e80ab90d3907aaa7b67f01ea
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864770"
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>Tutorial: Anpassen eines Katalogs in PowerApps

Im Rahmen dieses Tutorials passen Sie eine Liste von Datensätzen an, die Katalog genannt wird, und nehmen andere Änderungen in einer App vor, die in Microsoft PowerApps automatisch generiert wurde. Benutzer können auch dann Daten in der App verwalten, wenn Sie diese Änderungen nicht vornehmen, jedoch ist die App einfacher zu verwenden, wenn Sie sie den Anforderungen Ihres Unternehmens anpassen.

Zum Beispiel entspricht der Katalog für dieses Tutorial standardmäßig der folgenden Abbildung. Die E-Mail-Adresse wird deutlicher dargestellt als andere Arten von Daten, und Benutzer können den Katalog basierend auf dem Text in dieser Adresse sortieren oder filtern:

![Standardkatalog](./media/customize-layout-sharepoint/gallery-before.png)

Wenn Ihre Benutzer allerdings mehr Interesse am Kontonamen als an der E-Mail-Adresse haben, konfigurieren Sie den Katalog neu, sodass basierend auf den Schlüsseldaten hervorgehoben, sortiert und gefiltert wird. Darüber hinaus ändern Sie den Titel des Standardbildschirms, um ihn von den anderen Bildschirmen der App zu unterscheiden.

![Endgültiger Katalog](./media/customize-layout-sharepoint/gallery-after.png)

Außerdem fügen Sie eine Scrollleiste hinzu, damit Benutzer, die weder Touchscreens noch Mausräder verwenden, den gesamten Katalog durchsuchen können.

> [!div class="checklist"]
> * Ändern des Kataloglayouts
> * Ändern des im Katalog angezeigten Datentyps
> * Ändern der Spalten, nach denen Benutzer die Daten sortieren und durchsuchen können
> * Ändern des Bildschirmtitels
> * Anzeigen einer Scrollleiste

Dieses Tutorial beginnt mit einer App, die von einer bestimmten Datenquelle aus generiert wurde. Dieselben Konzepte gelten jedoch für jede App, die Sie in PowerApps erstellen, unabhängig davon, ob sie aus einer SharePoint-Liste, einer Excel-Tabelle oder einer anderen Datenquelle stammen.

Wenn Sie noch nicht bei PowerApps registriert sind, [registrieren Sie sich zuerst kostenlos](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="prerequisites"></a>Voraussetzungen

[Generieren Sie eine App](data-platform-create-app.md) aus der Entität **Konten** des Common Data Service (CDS) für Apps.

## <a name="open-the-generated-app"></a>Öffnen einer generierten App

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wählen Sie dann am linken Bildschirmrand **Apps** aus.

    [![PowerApps-Startseite](./media/customize-layout-sharepoint/sign-in.png)](./media/customize-layout-sharepoint/sign-in.png#lightbox)

1. Suchen Sie die App, die Sie generiert haben, und wählen Sie das Auslassungssymbol (**...** ) für sie und dann **Bearbeiten** aus.

    ![App zur Bearbeitung öffnen](./media/customize-layout-sharepoint/open-app.png)

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** angezeigt wird, klicken Sie auf **Überspringen**.

## <a name="change-the-layout"></a>Ändern des Layouts

1. Klicken Sie im linken Navigationsbereich auf **BrowseGallery1**.

    Wenn der Katalog ausgewählt ist, umgibt ihn ein Auswahlfeld mit Ziehpunkten.

    ![Katalog auswählen](media/customize-layout-sharepoint/select-gallery-1.png)

1. Wählen Sie in der Nähe des rechten Rands **Konten** aus, um den Bereich **Daten** zu öffnen.

    ![Öffnen Sie den Bereich **Daten**](./media/customize-layout-sharepoint/open-data-pane.png)

1. Öffnen Sie im Bereich **Daten** die Liste der Optionen unter **Layout**.

    ![Layoutoptionen anzeigen](./media/customize-layout-sharepoint/show-layouts.png)

1. Wählen Sie in der Liste der Optionen die Option aus, die nur einen Titel anzeigt.

    ![Layout auswählen, das nur von Titeln ausgeht](./media/customize-layout-sharepoint/choose-layout.png)

1. Öffnen Sie im Bereich **Daten** die Liste der Optionen für den Titel.

    Der Name dieses Steuerelements endet in einer Zahl, z.B. **Titel1**, die Zahl unterscheidet sich jedoch basierend auf anderen Aktionen, die Sie möglicherweise ausgeführt haben.

    ![Öffnen der Liste von Optionen für die Titelbezeichnung](./media/customize-layout-sharepoint/show-title-options.png)

1. Wählen Sie in der Liste der Optionen **Kontoname (Name)** aus, und schließen Sie dann den Bereich **Daten**.

    Der Katalog zeigt den Namen jedes Kontos an.

    ![Endgültiger Katalog](./media/customize-layout-sharepoint/final-gallery.png)

## <a name="change-sort-and-search-columns"></a>Sortier- und Suchspalten ändern

1. Wählen Sie den Katalog wie im vorherigen Abschnitt beschrieben aus.

    ![Katalog auswählen](./media/customize-layout-sharepoint/select-gallery-title.png)

1. Stellen Sie sicher, dass die Eigenschaftenliste in der Nähe der oberen linken Ecke **Items** anzeigt.

    ![Items-Eigenschaft](./media/customize-layout-sharepoint/items-property.png)

    Der Wert dieser Eigenschaft wird in der Bearbeitungsleiste angezeigt. Sie legen diese Eigenschaft nicht nur fest, um die Datenquelle für den Katalog anzugeben, sondern auch die Spalten, nach denen Benutzer die Daten sortieren und durchsuchen können.

1. Kopieren Sie diese Formel, und fügen Sie sie in die Bearbeitungsleiste ein.

    ```SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, Descending, Ascending))```

    Mit Verwendung dieser Formel stellen Sie Folgendes sicher:

    * Wenn ein Benutzer ein oder mehrere Zeichen in die Suchleiste eingibt, zeigt der Katalog nur Kontonamen an, die den vom Benutzer eingegebenen Text enthalten.
    * Wenn ein Benutzer das Sortiersymbol auswählt, wird der Katalog alphabetisch anhand des Kontonamens in aufsteigender oder absteigender Reihenfolge sortiert, je nachdem, wie oft der Benutzer das Symbol auswählt.

     Weitere Informationen zu diesen und anderen Funktionen finden Sie unter [formula reference (Formelreferenz)](formula-reference.md).

### <a name="test-sorting-and-searching"></a>Testen von Sortieren und Suchen

1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder Auswahl der Wiedergabeschaltfläche in der oberen rechten Ecke).

    ![Öffnen des Vorschaumodus](./media/customize-layout-sharepoint/open-preview.png)

1. Wählen Sie in der oberen rechten Ecke des Bildschirms zum Durchsuchen mindestens einmal die Schaltfläche „Sortieren“ aus, um die Einträge alphabetisch in aufsteigender oder absteigender Reihenfolge zu sortieren.

    ![Die Schaltfläche „Sortieren“ testen](./media/customize-layout-sharepoint/sort-button.png)

1. Geben Sie im Suchfeld **k** ein, um nur die Kontonamen anzuzeigen, die den Buchstaben enthalten, den Sie eingegeben haben.

    ![Testen der Suchleiste](./media/customize-layout-sharepoint/test-filter.png)

1. Löschen Sie den gesamten Text aus der Suchleiste. Schließen Sie anschließend den Vorschaumodus durch Drücken der ESC-TASTE (oder durch Auswahl des Schließsymbols in der oberen rechten Ecke).

## <a name="change-the-screen-title"></a>Ändern des Bildschirmtitels

1. Wählen Sie den Bildschirmtitel aus, indem Sie darauf klicken oder tippen.

    ![Auswählen des Bildschirmtitels](./media/customize-layout-sharepoint/select-title.png)

1. Stellen Sie sicher, dass die Eigenschaftenliste **Text** anzeigt, und ersetzen Sie anschließend in der Bearbeitungsleiste (unter Beibehalten der Anführungszeichen) **Konten** durch **Durchsuchen**.

    ![Aktualisieren des Bildschirmtitels](./media/customize-layout-sharepoint/change-screen-title.png)

    Der Bildschirm spiegelt die vorgenommene Änderung wider.

    ![Neuer Bildschirmtitel](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scrollbar"></a>Anzeigen einer Scrollleiste

Wenn die Geräte Ihrer Benutzer weder über Touchscreens noch Mausräder verfügen, konfigurieren Sie den Katalog so, dass eine Scrollleiste angezeigt wird, wenn der Benutzer mit der Maus darauf zeigt. So können Benutzer sogar alle Konten abrufen, wenn auf dem Bildschirm nicht alle Konten gleichzeitig angezeigt werden können.

1. Wählen Sie wie obenstehend beschrieben den Katalog aus.

    ![Katalog auswählen](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. Wählen Sie auf der Registerkarte **Katalog** die Option **Scrollleiste anzeigen** aus, und überprüfen Sie, ob der Wert der Eigenschaft sich in **TRUE** geändert hat.

    ![Scrollleiste anzeigen](./media/customize-layout-sharepoint/show-scrollbar.png)

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie den Katalog angepasst und andere Änderungen am Standardbildschirm zum Durchsuchen von Datensätzen in einer generierten App vorgenommen. Sie können außerdem die Standardanzeigen anpassen, damit Details angezeigt sowie Konten erstellt und aktualisiert werden können. Während der Bildschirm zum Durchsuchen einen Katalog enthält, enthalten die anderen beiden Bildschirme in der App Formulare. Sie können z.B. ändern, welche Datentypen die Formulare in welcher Reihenfolge anzeigen.

> [!div class="nextstepaction"]
> [Customize forms (Formulare anpassen)](customize-forms-sharepoint.md)
