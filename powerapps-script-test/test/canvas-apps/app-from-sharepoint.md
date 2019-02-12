---
title: Generieren einer Canvas-App aus einer SharePoint-Liste | Microsoft-Dokumentation
description: Automatisches Generieren einer Canvas-App in PowerApps, um Daten in einer SharePoint-Liste zu verwalten
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/09/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 15aa49787d6b2c3d3981e374aeb43c54a2d7a7ec
ms.sourcegitcommit: 02d0234bd84352bf1c43d0fc9225ab60947a0add
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/15/2018
ms.locfileid: "49317089"
---
# <a name="generate-a-canvas-app-in-powerapps-from-a-sharepoint-list"></a>Generieren einer Canvas-App in PowerApps aus einer SharePoint-Liste

In diesem Artikel verwenden Sie PowerApps, um automatisch eine Canvas-App basierend auf Elementen einer SharePoint-Liste zu generieren. Sie können die App aus PowerApps oder SharePoint Online generieren. In PowerApps können Sie die App basierend auf einer Liste auf einer lokalen SharePoint-Website generieren, wenn Sie über ein Datengateway [eine Verbindung herstellen](connect-to-sharepoint.md).

Die Apps, die Sie generieren, enthält drei Bildschirme:

- Im Bildschirm zum Durchsuchen können Sie durch alle Elemente der Liste scrollen.
- Im Bildschirm mit den Details können Sie alle Informationen zu einem einzelnen Element der Liste anzeigen.
- Im Bildschirm zum Bearbeiten können Sie ein Element erstellen oder Informationen zu einem vorhandenen Element aktualisieren.

Sie können die Konzepte und Techniken in diesem Thema auf jede Liste in SharePoint anwenden. Um die Schritte genau befolgen zu können, bereiten Sie Folgendes vor:

1. Erstellen Sie auf einer SharePoint Online-Website eine Liste namens **SimpleApp**.
2. Erstellen Sie in einer Spalte namens **Title** Einträge für **Vanilla**, **Chocolate** und **Strawberry**.

Das Grundprinzip beim Erstellen einer App ändert sich nicht, auch wenn Sie eine viel komplexere Liste mit mehreren Spalten und verschiedenen Typen (z.B. Text, Datumsangaben, Zahlen und Währungen) erstellen.

> [!IMPORTANT]
> PowerApps unterstützt nicht alle Typen von SharePoint-Daten. Weitere Informationen finden Sie unter [Known issues (Bekannte Probleme)](connections/connection-sharepoint-online.md#known-issues).

## <a name="generate-an-app-from-within-powerapps"></a>Generieren einer App aus PowerApps

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

1. Zeigen Sie unter **Eigene App erstellen** auf **Mit Daten beginnen**, und wählen Sie dann **Diese App erstellen** aus.

    ![Option zum Erstellen einer App](./media/app-from-sharepoint/start-from-data.png)

1. Klicken Sie auf der SharePoint-Kachel auf **Smartphonelayout**.

    ![Option zum Erstellen einer App](./media/app-from-sharepoint/sharepoint-tile.png)

1. Wenn Sie die Option **Direkt verbinden** aktiviert haben, können Sie auf **Erstellen** klicken.

    ![Erstellen der Verbindung](./media/app-from-sharepoint/create-connection.png)

1. Geben Sie unter **Verbindung mit einer SharePoint-Website herstellen** die URL ihrer SharePoint Online-Website ein, und klicken Sie anschließend auf **Gehe zu**.

    Geben Sie wie im folgenden Beispiel nur die Website-URL und nicht den Namen der Liste ein:<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. Klicken Sie unter **Liste auswählen** erst auf **SimpleApp** und dann auf **Verbinden**.

    Nach wenigen Minuten wird Ihre App auf dem Bildschirm zum Durchsuchen geöffnet, auf dem eine Liste der Elemente anzeigt wird, die Sie in Ihrer Liste erstellt haben. Wenn Ihre Liste auch Daten in anderen Spalten als nur der Spalte **Titel** enthält, zeigt die App diese Daten an. Im oberen Bereich des Bildschirms werden in einer Titelleiste Symbole zum Aktualisieren und Sortieren der Liste sowie zum Erstellen eines Elements in einer Liste angezeigt. Unterhalb der Titelleiste können Sie über ein Suchfeld die Liste basierend auf dem Text filtern, den Sie darin eingeben bzw. einfügen. 

    ![Bildschirm zum Durchsuchen](./media/app-from-sharepoint/browse-screen.png)

    Sie sollten möglicherweise Änderungen vornehmen, bevor Sie diese App verwenden oder für andere freigeben. Es wird empfohlen, dass Sie Ihre bisherige Arbeit speichern, bevor Sie fortfahren, indem Sie STRG+S drücken. Geben Sie Ihrer App einen Namen, und klicken Sie dann auf **Speichern**.

## <a name="generate-an-app-from-within-sharepoint-online"></a>Generieren einer App aus SharePoint Online

Wenn Sie eine App über die SharePoint Online-Befehlszeile aus einer benutzerdefinierten Liste erstellen, ist die App eine Ansicht dieser Liste. Sie können die App außer im Webbrowser auch auf einem iOS- oder Android-Gerät ausführen.

1. Öffnen Sie in SharePoint Online eine benutzerdefinierte Liste, klicken Sie in der Befehlsleiste auf **PowerApps**, und klicken Sie anschließend auf **App erstellen**.

    ![Erstellen einer App](./media/app-from-sharepoint/generate-new-app.png)

2. Geben Sie im angezeigten Bereich einen Namen für Ihre App ein, und klicken Sie auf **Erstellen**.

    ![Benennen der App](./media/app-from-sharepoint/app-name.png)

    Eine neue Registerkarte wird im Webbrowser angezeigt und zeigt die App, die Sie basierend auf Ihrer SharePoint-Liste automatisch generiert haben. Die App wird in PowerApps Studio angezeigt. Dort können Sie sie anpassen.

    ![Standard-App](./media/app-from-sharepoint/default-app.png)

3. (Optional) Aktualisieren Sie die Browserregisterkarte für Ihre SharePoint-Liste (indem Sie die Registerkarte auswählen und F5 drücken), und führen Sie dann die folgenden Schritte aus, um Ihre App auszuführen oder zu verwalten:

    - Um die App auszuführen (in einer separaten Browserregisterkarte), wählen Sie **Öffnen** aus.
    - Um anderen Personen in Ihrer Organisation die Ausführung der App zu ermöglichen, wählen Sie **Diese Ansicht öffentlich machen** aus.

        Um anderen Personen die Bearbeitung Ihrer App zu ermöglichen, [geben Sie sie frei](share-app.md), und legen Sie die Berechtigung **Kann bearbeiten** fest.

    - Um die Ansicht aus SharePoint zu entfernen, klicken Sie auf **Diese Ansicht entfernen**.

        Um die App aus PowerApps zu entfernen, [löschen Sie die App](delete-app.md).

## <a name="next-steps"></a>Nächste Schritte
In diesem Thema haben Sie eine App erstellt, mit der Daten in einer SharePoint-Liste verwaltet werden können. Generieren Sie als Nächstes eine App über eine komplexere Liste, und passen Sie diese App anschließend angefangen bei dem Bildschirm zum Durchsuchen an Ihre Bedürfnisse an.

> [!div class="nextstepaction"]
> [Anpassen des Standardbildschirms zum Durchsuchen](customize-layout-sharepoint.md)
