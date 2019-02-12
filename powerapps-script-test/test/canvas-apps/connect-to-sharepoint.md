---
title: Erstellen einer Verbindung von einer Canvas-App mit SharePoint | Microsoft-Dokumentation
description: Stellen Sie in PowerApps eine Verbindung mit SharePoint her, die Sie verwenden, wenn Sie eine Canvas-App automatisch generieren oder von Grund auf neu erstellen.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/03/2016
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 170115f07da57878c553a1776fc26a9cd27a8258
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42844153"
---
# <a name="create-a-connection-to-sharepoint-from-powerapps"></a>Herstellen einer Verbindung mit SharePoint aus PowerApps
Erstellen Sie eine Verbindung mit SharePoint Online oder lokalem SharePoint, sodass Sie eine Canvas-App automatisch generieren oder von Grund auf neu erstellen können.

Wenn Sie mit PowerApps nicht vertraut sind, finden Sie Grundlagen unter [Einführung in PowerApps](getting-started.md).

Zum Zeitpunkt dieses Artikels unterstützt PowerApps benutzerdefinierte Listen, jedoch keine Bibliotheken. Darüber hinaus können Sie Daten in verschiedenen Arten von Spalten anzeigen, z.B. **Auswahl** und **Bild**, aber Sie können diese Daten nicht aktualisieren. Weitere Informationen finden Sie unter [Known issues (Bekannte Probleme)](connections/connection-sharepoint-online.md#known-issues).

## <a name="specify-a-sharepoint-connection"></a>Angeben einer SharePoint-Verbindung
1. Wenn Sie noch nicht angemeldet sind, [melden Sie sich bei PowerApps an](../signup-for-powerapps.md).

2. Melden Sie sich unter [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.

3. Klicken oder tippen Sie in der linken Navigationsleiste auf **Verwalten**, und klicken oder tippen Sie anschließend auf **Verbindungen**.

    ![Option „New“ im Menü „File“](./media/connect-to-sharepoint/manage-connections.png)

4. Klicken oder tippen Sie in der Nähe der oberen rechten Ecke auf **Neue Verbindung**.

    ![Schaltfläche „Neue Verbindung“](./media/connect-to-sharepoint/new-connection.png)

5. Klicken oder tippen Sie In der Liste der Verbindungen auf **SharePoint**.

    ![Hinzufügen einer SharePoint-Verbindung](./media/connect-to-sharepoint/add-sp-portal.png)

6. Führen Sie die Schritte einer der folgenden Vorgehensweisen durch, die weiter unten in diesem Thema angezeigt werden:

   * [Verbinden mit einer SharePoint Online-Website](connect-to-sharepoint.md#connect-to-a-sharepoint-online-site)
   * [Verbinden mit einer lokalen SharePoint-Website](connect-to-sharepoint.md#connect-to-an-on-premises-sharepoint-site)

## <a name="connect-to-a-sharepoint-online-site"></a>Verbinden mit einer SharePoint Online-Website
1. Klicken oder tippen Sie auf **Direkt verbinden (Clouddienste)**, und klicken oder tippen Sie anschließend auf **Verbindung hinzufügen**.

    ![Auswählen von SharePoint Online](./media/connect-to-sharepoint/choose-online.png)

2. Wechseln Sie zu [Nächste Schritte](connect-to-sharepoint.md#next-steps) am Ende dieses Themas.

## <a name="connect-to-an-on-premises-sharepoint-site"></a>Verbinden mit einer lokalen SharePoint-Website
1. Klicken oder tippen Sie auf **Verbindung mit einem lokalen Datengateway herstellen**.

    ![Auswählen von lokalem SharePoint](./media/connect-to-sharepoint/choose-onprem.png)

    > [!NOTE]
   > Gateways und lokale Verbindungen können nur in der [Standardumgebung](working-with-environments.md) des Benutzers erstellt und verwendet werden.

2. Geben Sie Ihren Benutzernamen und Ihr Kennwort an.

    Wenn Ihre Anmeldeinformationen einen Domänennamen enthalten, geben Sie sie folgendermaßen an: *Domäne\Alias*.

    ![Angeben Ihrer Anmeldeinformationen](./media/connect-to-sharepoint/specify-credentials.png)

3. Wenn Sie kein lokales Datengateway installiert haben, [installieren Sie eines](gateway-reference.md), und klicken oder tippen Sie anschließend auf das Symbol zum Aktualisieren der Liste der Gateways.

    ![Gateway installieren](./media/connect-to-sharepoint/install-gateway.png)

4. Klicken oder tippen Sie unter **Gateway auswählen** auf das Gateway, das Sie verwenden möchten, und klicken oder tippen Sie auf **Verbindung hinzufügen**.

    ![Gateway auswählen](./media/connect-to-sharepoint/choose-gateway.png)

## <a name="next-steps"></a>Nächste Schritte
* [Generieren Sie eine App automatisch](app-from-sharepoint.md), basierend auf einer Liste, die Sie angeben. Die App verfügt standardmäßig über drei Bildschirme: jeweils einen zum Durchsuchen von Datensätzen, zum Anzeigen von Details zu einem einzelnen Datensatz und zum Erstellen oder Aktualisieren eines Datensatzes.
* [Neuerstellen einer App von Grund auf](get-started-create-from-blank.md). Dieses Thema wurde für Excel geschrieben, die gleichen Prinzipien gelten jedoch auch für SharePoint.
