---
title: Erstellen einer Canvas-App von Grund auf mit Common Data Service für Apps | Microsoft-Dokumentation
description: Erstellen Sie in PowerApps eine Canvas-App, um Datensätze in Common Data Service für Apps hinzuzufügen, zu aktualisieren und zu löschen.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 710df8899fa11e46a83e4ba670c4081b04fa7bde
ms.sourcegitcommit: c1f58a16f8dcd309a1d5fc4658ca16d82c615994
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2018
ms.locfileid: "51333959"
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service-for-apps"></a>Erstellen einer Canvas-App von Grund auf mit Common Data Service für Apps

Erstellen Sie eine Canvas-App, um Daten zu verwalten, die in Common Data Service für Apps gespeichert sind. Verwenden Sie dazu (integrierte) Standardentitäten, (von Ihrem Unternehmen erstellte) benutzerdefinierte Entitäten oder beides.

Wenn Sie eine App in Common Data Service erstellen, müssen Sie keine Verbindung über PowerApps herstellen, wie dies bei Datenquellen wie SharePoint, Dynamics 365 und Salesforce erforderlich ist. Sie müssen lediglich angeben, welche Entitäten Sie anzeigen und verwalten oder für beide Aktivitäten in der App verwenden möchten.

## <a name="prerequisites"></a>Voraussetzungen

- Bevor Sie eine App von Grund auf neu erstellen, sollten Sie sich mit den PowerApps-Grundlagen vertraut machen, indem Sie erst eine [App generieren](data-platform-create-app.md) und anschließend den [Katalog](customize-layout-sharepoint.md), die [Formulare](customize-forms-sharepoint.md) und die [Karten](customize-card.md) der App anpassen.
- [Wechseln Sie in eine Umgebung](working-with-environments.md), in der mithilfe von einfachen Daten eine Datenbank erstellt wurde. Wenn Sie über eine entsprechende Lizenz verfügen, können Sie dafür eine [Umgebung erstellen](../../administrator/create-environment.md).

## <a name="open-a-blank-app"></a>Öffnen einer leeren App

1. Melden Sie sich bei [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

1. Zeigen Sie unter **Eigene App erstellen** auf die Kachel **Mit leerer App starten**, klicken oder tippen Sie erst auf das Telefonsymbol und anschließend auf **Diese App erstellen**.

    ![Kachel für leere App](./media/data-platform-create-app-scratch/start-from-blank.png)

    Sie können für Smartphones oder andere Geräte (wie Tablets) Apps von Grund auf neu erstellen. In diesem Artikel erfahren Sie, wie Sie Apps für Smartphone erstellen können.

## <a name="specify-an-entity"></a>Angeben einer Entität

1. Klicken oder tippen Sie in der Mitte des Bildschirms auf **Mit Daten verbinden** und dann im Bereich **Daten** auf die Verbindung **Common Data Service**.

1. Geben Sie im Suchfeld die ersten Buchstaben des Worts **Accounts** (Konten) ein (bzw. fügen Sie sie ein), um die Liste mit den Entitäten zu filtern. Aktvieren Sie das Kontrollkästchen **Konten**, und klicken oder tippen Sie auf **Verbinden**.

    ![Angeben der Entität „Accounts“](./media/data-platform-create-app-scratch/cds-connect.png)

1. Schließen Sie den Bereich **Daten**, indem Sie in der oberen rechten Ecke auf das Symbol zum Schließen klicken oder tippen.

## <a name="add-a-list-screen"></a>Hinzufügen einer Listenanzeige

1. Klicken oder tippen Sie auf der Registerkarte **Start** unter **Neuer Bildschirm** auf den Pfeil nach unten, und klicken oder tippen Sie dann auf **Bildschirmliste**.

    ![Hinzufügen einer Listenanzeige](./media/data-platform-create-app-scratch/list-screen.png)

1. Klicken oder tippen Sie in der Navigationsleiste auf der linken Seite auf **TemplateGalleryList1**, und legen Sie dann den Wert für die Eigenschaft **Items** auf die folgende Formel fest:

    `SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))`

    Diese Formel gibt Folgendes an:

   - Im Katalog sollten die Daten aus der Entität **Accounts** angezeigt werden.
   - Die Daten sollten in aufsteigender Reihenfolge angezeigt werden, bis der Benutzer auf die Schaltfläche „Sortieren“ klickt oder tippt, um die Reihenfolge zu ändern.
   - Wenn der Benutzer mindestens ein Zeichen in die Suchleiste eintippt (bzw. einfügt), werden in der Liste nur die Konten angezeigt, in denen die Namensfelder die vom Benutzer angegebenen Zeichen enthalten.

     Sie können [diese sowie viele weitere Funktionen](formula-reference.md) verwenden, um anzugeben, wie Ihre App angezeigt werden und sich verhalten soll.

     ![Festlegen der Items-Eigenschaft des Katalogs](./media/data-platform-create-app-scratch/gallery-items.png)

1. Legen Sie das Layout des Katalogs fest, damit nur die Namen der einzelnen Konten angezeigt werden, und konfigurieren Sie die Titelleiste, um das Wort **Durchsuchen** anzuzeigen. Dies wird unter [Customize a gallery (Anpassen eines Katalogs)](customize-layout-sharepoint.md) beschrieben.

    ![Bildschirm zum Durchsuchen](./media/data-platform-create-app-scratch/final-browse.png)

1. Klicken oder tippen Sie in der linken Navigationsleiste erst auf **Screen1**, dann auf die Auslassungspunkte (...) und anschließend auf **Löschen**.

1. Klicken oder tippen Sie in der linken Navigationsleiste erst auf **Screen2**, dann auf die Auslassungspunkte (...) und anschließend auf **Umbenennen**.

1. Geben bzw. fügen Sie **BrowseScreen** ein, und benennen Sie den Katalog in dieser Anzeige in **BrowseGallery** um.

    ![Katalog: Bildschirm zum Durchsuchen umbenennen](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>Hinzufügen eines Formularbildschirm

1. Wiederholen Sie den ersten Schritt des letzten Vorgangs, aber fügen Sie einen **Formularbildschirm** anstelle einer **Bildschirmliste** hinzu.

1. Legen Sie die **DataSource**-Eigenschaft des Kontos auf **Accounts** und die **Item**-Eigenschaft auf **BrowseGallery.Selected** fest. Dies wird auf der rechten Seite in der Registerkarte **Erweitert** angezeigt.

    ![Festlegen der Eigenschaften „Datasource“ und „Item“ des Formulars](./media/data-platform-create-app-scratch/form-datasource.png)

1. Klicken oder tippen Sie rechts auf der Registerkarte **Eigenschaften** auf **Konten**, um den Bereich **Daten** zu öffnen, und aktivieren Sie die Kontrollkästchen für diese Felder:

    - Kontoname
    - Adresse 1: Straße 1
    - Adresse 1: Stadt
    - Adresse 1: Postleitzahl
    - Anzahl der Mitarbeiter
    - Jahresumsatz

1. Legen Sie die **Text**-Eigenschaft der Titelleiste auf **Create/Edit** (Erstellen/Bearbeiten) fest.

    Auf dem Bildschirm werden dann die vorgenommenen Änderungen angezeigt.

    ![Festlegen der Eigenschaften „Datasource“ und „Item“ des Formulars](./media/data-platform-create-app-scratch/field-list.png)

1. Bennen Sie diese Anzeige in **FormScreen** um.

## <a name="configure-icons"></a>Konfigurieren von Symbolen

1. Klicken oder tippen Sie unter **BrowseScreen** auf den kreisförmigen Pfeil im oberen Bereich des Bildschirms, und legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    `Refresh(Accounts)`

    ![Symbol zum Aktualisieren](./media/data-platform-create-app-scratch/refresh-icon.png)

1. Klicken oder tippen Sie auf das Pluszeichen und legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    `NewForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![Symbol „Hinzufügen“](./media/data-platform-create-app-scratch/plus-icon.png)

1. Klicken oder tippen Sie auf den ersten Pfeil nach rechts, und legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    `EditForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![Symbol „Weiter“](./media/data-platform-create-app-scratch/next-icon.png)

1. Klicken oder tippen Sie unter **FormScreen** auf das Symbol „Abbrechen“, und legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    `ResetForm(EditForm1);Navigate(BrowseScreen, ScreenTransition.None)`

    ![Symbol „Abbrechen“](./media/data-platform-create-app-scratch/cancel-icon.png)

1. Klicken oder tippen Sie auf das Häkchensymbol, und legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    `SubmitForm(EditForm1); Navigate(BrowseScreen, ScreenTransition.None)`

    ![Häkchensymbol](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** erst auf **Symbole** und dann auf das **Papierkorbsymbol**.

1. Legen Sie für das **Papierkorbsymbol** die **Color**-Eigenschaft auf **Weiß** und die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    `Remove(Accounts, BrowseGallery.Selected); Navigate(BrowseScreen, ScreenTransition.None)`

    ![Papierkorbsymbol](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>Testen der App

1. Klicken oder tippen Sie im linken Navigationsbereich auf **BrowseScreen**, und öffnen Sie dann die Vorschau, indem Sie F5 drücken bzw. auf das Wiedergabesymbol in der oberen rechten Ecke klicken oder tippen.

    ![Vorschau öffnen](./media/data-platform-create-app-scratch/open-preview.png)

1. Lassen Sie die Liste abwechselnd in aufsteigender und absteigender Reihenfolge anzeigen, und filtern Sie diese nach bestimmten Zeichen in den einzelnen Kontonamen.

1. Fügen Sie ein Konto hinzu, bearbeiten Sie dieses, und beginnen Sie mit dem Update des Kontos. Verwerfen Sie jedoch Ihre Änderungen, und löschen Sie das Konto.

## <a name="next-steps"></a>Nächste Schritte

- [Verknüpfen Sie diese App mit einer Projektmappe](add-app-solution.md), damit Sie diese beispielsweise in einer anderen Umgebung bereitstellen oder sie auf AppSource veröffentlichen können.
- [Öffnen Sie mindestens eine Beispiel-App](open-and-run-a-sample-app.md), um verschiedene App-Typen zu untersuchen, die Sie erstellen können.
