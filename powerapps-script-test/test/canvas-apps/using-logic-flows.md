---
title: Starten eines Flows in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen Sie einen Flow, der mindestens eine Aufgabe ausführt, wenn ein Ereignis in einer Canvas-App auftritt, z.B. wenn ein Benutzer eine Schaltfläche auswählt.
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/05/2017
ms.author: sharik
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 05d633b20038ad61215a8e898b1ec7afa044b574
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42840767"
---
# <a name="start-a-flow-in-a-canvas-app"></a>Starten eines Flows in einer Canvas-App

Mit Microsoft Flow können Sie eine Logik erstellen, die mindestens eine Aufgabe ausführt, wenn ein Ereignis in einer Canvas-App auftritt. Sie können zum Beispiel eine Schaltfläche so konfigurieren, dass bei Auswahl durch den Benutzer ein Element in einer SharePoint-Liste erstellt wird, eine E-Mail oder eine Besprechungsanfrage gesendet wird, eine Datei der Cloud hinzugefügt wird oder all dies ausgeführt wird. Sie können jedes Steuerelement in der App für das Starten des Flows konfigurieren, der auch weiterhin ausgeführt wird, wenn Sie PowerApps schließen.

## <a name="prerequisites"></a>Voraussetzungen

* [Registrieren Sie sich](../signup-for-powerapps.md) bei PowerApps.
* Erfahren Sie, wie Sie ein [Steuerelement konfigurieren](add-configure-controls.md).

## <a name="create-a-flow"></a>Erstellen eines Flows

1. Melden Sie sich auf [powerapps.com](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wählen Sie dann auf der linken Navigationsleiste **Flows** aus.

2. Wählen Sie auf der **Meine Flows**-Seite **Ohne Vorlage neu erstellen** aus.

    ![Option, um einen Flow ohne Vorlage zu erstellen](./media/using-logic-flows/create-from-blank.png)

    **PowerApps** wird als Standardtrigger hinzugefügt.

    ![PowerApps als Trigger, der den Flow auslöst](./media/using-logic-flows/set-trigger.png)

3. Wählen Sie **Neuer Schritt** und dann **Aktion hinzufügen** aus.

    ![Option zum Hinzufügen einer Aktion](./media/using-logic-flows/add-action.png)

4. Geben Sie im Feld **Alle Dienste und Aktionen durchsuchen** eine Aktion für den Flow an (siehe das folgende Beispiel):

   1. Geben Sie in das Feld **SharePoint** ein, und wählen Sie dann in der Liste **SharePoint – Element erstellen** unter **Aktionen** aus.

       ![Option zum Erstellen eines SharePoint-Elements](./media/using-logic-flows/create-sharepoint-item.png)

   2. Geben Sie, wenn Sie dazu aufgefordert werden, die Anmeldeinformationen für die Verbindung mit SharePoint an.

   3. Geben oder fügen Sie in das Feld **Websiteadresse** die URL einer SharePoint Online-Website ein, die eine Liste enthält.

       > [!NOTE]
      > Geben Sie die URL für die Website ohne die Liste an.

   4. Wählen Sie im Feld **Listenname** die Liste aus, die Sie verwenden möchten.

   5. Klicken oder tippen Sie auf das Feld **Titel**, und wählen Sie dann **Dynamischen Inhalt hinzufügen** aus.

       ![Hinzufügen von „In PowerApps fragen“ zum Feld „Titel“](./media/using-logic-flows/ask-in-powerapps.png)

   6. Wählen Sie in der Liste der Parameter **In PowerApps fragen** aus.

       ![Hinzufügen eines Parameters](./media/using-logic-flows/add-parameter.png)

5. (Optional) Geben Sie eine oder mehrere weitere Aktionen an, z.B. Senden einer Genehmigungs-E-Mail an eine Adresse, die Sie angeben, oder Erstellen eines zugehörigen Eintrags in einer anderen Datenquelle.

6. Geben oder fügen Sie oben auf dem Bildschirm einen Namen für den Flow ein, und wählen Sie dann **Flow erstellen** aus.

    ![Benennen und Speichern des Flows](./media/using-logic-flows/name-flow.png)

## <a name="add-a-flow-to-an-app"></a>Hinzufügen eines Flows zu einer App
1. Wählen Sie in PowerApps **Neu** im Menü **Datei** aus.

2. Wählen Sie auf der Kachel **Leere App** **Telefonlayout** aus.

3. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement hinzu, und nennen Sie es **RecordTitle**.

4. Fügen Sie ein **[Schaltflächen](controls/control-button.md)**-Steuerelement hinzu, und verschieben Sie es unter **RecordTitle**.

5. Wählen Sie bei ausgewähltem **[Schaltflächen](controls/control-button.md)**-Steuerelement **Flows** auf der Registerkarte **Aktion** aus.

    ![Option „Flows“ auf der Registerkarte „Aktion“](./media/using-logic-flows/action-tab.png)

6. Wählen Sie im Bereich, der angezeigt wird, den Flow aus, den Sie im vorherigen Verfahren erstellt haben.

    > [!NOTE]
   > Wenn der von Ihnen erstellte Flow nicht verfügbar ist, vergewissern Sie sich, dass PowerApps auf die Umgebung festgelegt ist, in der Sie den Flow erstellt haben.

    ![Hinzufügen eines Flows aus dem Bereich „Anpassung“](./media/using-logic-flows/add-flow-from-pane.png)

7. Geben oder fügen Sie in der Bearbeitungsleiste **RecordTitle.Text)** am Ende der Formel ein, die automatisch hinzugefügt wurde.

    ![OnSelect-Eigenschaft, die den Flow enthält](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>Testen des Flows
1. Öffnen Sie die Vorschau durch Drücken von F5 (oder durch Auswählen des Pfeils in der Nähe der oberen rechten Ecke).

    ![OnSelect-Eigenschaft, die den Flow enthält](./media/using-logic-flows/open-preview.png)

2. Geben oder fügen Sie Text in **RecordTitle** ein, und klicken oder tippen Sie dann auf das **[Schaltflächen](controls/control-button.md)**-Steuerelement.

    Ein SharePoint-Element wird in der angegebenen Liste mit dem angegebenen Text als Titel erstellt. Wenn die Liste bei Ausführung des Flows geöffnet war, müssen Sie ggf. Ihr Browserfenster aktualisieren, um die Änderungen anzuzeigen.
