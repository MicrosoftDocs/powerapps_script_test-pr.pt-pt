---
title: Verwalten eines lokalen Datengateways für Canvas-Apps | Microsoft-Dokumentation
description: Ein lokales Datengateway und seine Verbindungen verwalten
author: archnair
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/30/2016
ms.author: archanan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 85806799a5f5ea91a4671a27e71cf95daabcd01a
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863847"
---
# <a name="manage-an-on-premises-data-gateway-in-powerapps"></a>Verwalten eines lokalen Datengateways in PowerApps
Installieren Sie ein lokales Datengateway zur schnellen und sicheren Datenübertragung zwischen einer in PowerApps erstellten Canvas-App und einer Datenquelle, die sich nicht in der Cloud befindet, z.B. eine lokale SQL Server-Datenbank oder eine lokale SharePoint-Website. Zeigen Sie alle Gateways an, für die Sie Administratorberechtigungen haben, und verwalten Sie Berechtigungen und Verbindungen für diese Gateways.

Ein Gateway ermöglicht Ihnen die folgenden Verbindungen mit lokalen Daten:

* SharePoint
* SQL Server
* Oracle
* Informix
* FileSystem
* DB2

## <a name="prerequisites"></a>Voraussetzungen
* Benutzername und Kennwort, mit dem Sie sich für PowerApps [registriert](../signup-for-powerapps.md) haben
* Administrative Berechtigungen für ein Gateway (Sie verfügen über diese Berechtigungen standardmäßig für jedes Gateway, das Sie installieren, und ein Administrator eines anderen Gateways kann Ihnen diese Berechtigungen für jenes Gateway erteilen.)
* Eine Lizenz, die Zugriff auf lokale Daten über ein lokales Gateway unterstützt. Weitere Informationen finden Sie im Abschnitt "Verbindungen" auf der Seite mit den [Preisinformationen](https://powerapps.microsoft.com/pricing/).
* Gateways und lokale Verbindungen können nur in der [Standardumgebung](working-with-environments.md) des Benutzers erstellt und verwendet werden.

## <a name="install-a-gateway"></a>Gateway installieren
1. Klicken oder tippen Sie in der linken Navigationsleiste von [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) auf **Gateways**.

    ![„Gateways“ in der linken Navigationsleiste](./media/gateway-management/manage-gateway.png)

2. Wenn Sie nicht über Administratorberechtigungen für das Gateway verfügen, klicken oder tippen Sie auf [Gateway installieren](http://go.microsoft.com/fwlink/?LinkID=820931) (oder **Neues Gateway** in der oberen rechten Ecke), und befolgen Sie anschließend die Anweisungen im Assistenten, der angezeigt wird.

    ![Gateways installieren](./media/gateway-management/no-gateway-installed.png)

    Weitere Informationen dazu, wie Sie ein Gateway installieren, finden Sie unter [Grundlegendes zu lokalen Datengateways](gateway-reference.md).

## <a name="view-and-manage-gateway-permissions"></a>Anzeigen und Verwalten von Gatewayberechtigungen
1. Klicken oder tippen Sie unter [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) im linken Navigationsbereich auf **Gateways** und anschließend auf ein Gateway.

2. Fügen Sie einen Benutzer zu einem Gateway hinzu, indem Sie auf **Benutzer** klicken oder tippen, einen Benutzer oder eine Gruppe und anschließend eine Berechtigungsstufe angeben:

   * **Verwenden**: Benutzer, die Verbindungen im Gateway erstellen dürfen, die für Apps und Flows verwendet werden, aber das Gateway nicht freigeben dürfen. Wählen Sie diese Berechtigung für Benutzer, die Apps ausführen, aber nicht freigeben.
   * **Verwenden + freigeben**: Benutzer, die Verbindungen im Gateway erstellen dürfen, die für Apps und Flows verwendet werden, und das Gateway automatisch freigeben, wenn eine App freigegeben wird. Wählen Sie diese Berechtigung für Benutzer, die Apps für andere Benutzer oder die Organisation freigeben.
   * **Administrator**: Administratoren mit Vollzugriff auf das Gateway dürfen u. a. Benutzer hinzufügen, Berechtigungen festlegen, Verbindungen mit allen verfügbaren Datenquellen erstellen und das Gateway löschen.

Für die Berechtigungsstufen **Verwenden** und **Verwenden + freigeben** wählen Sie die Datenquellen, mit denen der Benutzer über das Gateway eine Verbindung herstellen kann.

## <a name="view-and-manage-gateway-connections"></a>Anzeigen und Verwalten von Gatewayverbindungen
1. Klicken oder tippen Sie unter [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) im linken Navigationsbereich auf **Gateways** und anschließend auf ein Gateway.

2. Klicken oder tippen Sie auf **Verbindungen** und anschließend auf eine Verbindung, um ihre Details anzuzeigen, die Einstellungen zu bearbeiten oder sie zu löschen.

3. Um eine Verbindung freizugeben, klicken oder tippen Sie auf **Freigeben**, und fügen Sie anschließend Benutzer hinzu oder entfernen Sie Benutzer.

    > [!NOTE]
   > Sie können nur einige Arten von Verbindungen freigeben, z.B. SQL Server. Weitere Informationen finden Sie unter [Freigeben von App-Ressourcen](share-app-resources.md).

Weitere Informationen zum Verwalten einer Verbindung finden Sie unter [Verwalten von Verbindungen](add-manage-connections.md).

## <a name="troubleshooting-and-advanced-configuration"></a>Problembehandlung und erweiterte Konfiguration
Weitere Informationen zur Behandlung von Problemen mit Gateways und Konfiguration des Gatewaydiensts für Ihr Netzwerk finden Sie unter [Grundlegendes zu lokalen Datengateways](gateway-reference.md).

## <a name="next-steps"></a>Nächste Schritte
* Erstellen Sie eine App, die eine Verbindung mit einer lokalen Datenquelle herstellt, z.B. [SQL Server](connections/connection-azure-sqldatabase.md) oder [SharePoint](connections/connection-sharepoint-online.md).
* [Geben Sie eine App frei](share-app.md), die eine Verbindung mit einer lokalen Datenquelle herstellt.
