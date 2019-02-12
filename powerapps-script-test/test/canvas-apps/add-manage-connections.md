---
title: Hinzufügen und Verwalten von Verbindungen über Canvas-Apps | Microsoft-Dokumentation
description: Über Canvas-Apps können Sie Verbindungen mit Datenquellen wie SharePoint, SQL Server und OneDrive for Business hinzufügen, löschen und aktualisieren.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/09/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d2a7da93835e5fbe588a8683bbdb0393d5b76ee5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834041"
---
# <a name="manage-canvas-app-connections-in-powerapps"></a>Verwalten von Canvas-App-Verbindungen in PowerApps
Stellen Sie in [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) eine Verbindung mit einer oder mehreren Datenquellen her, löschen Sie eine Verbindung, oder aktualisieren Sie ihre Anmeldeinformationen.

Über die Datenverbindung der Canvas-App können Verbindungen mit SharePoint, SQL Server, Office 365, OneDrive for Business, Salesforce, Excel und vielen anderen [Datenquellen](connections-list.md) hergestellt werden.

Ihr nächster Schritt nach diesem Artikel besteht darin, Daten aus der Datenquelle in der App anzuzeigen und zu verwalten; siehe folgende Beispiele:

* Herstellen einer Verbindung mit OneDrive for Business und Verwalten von Daten in einer Excel-Arbeitsmappe in der App.
* Aktualisieren einer Liste auf einer SharePoint-Website.
* Herstellen einer Verbindung mit SQL Server und Aktualisieren einer Tabelle aus Ihrer App.
* Senden von E-Mail in Office 365.
* Senden eines Tweets.
* Verbinden mit Twilio und senden einer SMS-Nachricht von Ihrer App.

## <a name="prerequisites"></a>Voraussetzungen
1. [Registrieren Sie sich](../signup-for-powerapps.md) bei PowerApps.
2. Melden Sie sich unter [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.

## <a name="background-on-data-connections"></a>Hintergrundinformationen zu Datenverbindungen
Die meisten Apps in PowerApps nutzen externe Informationen, die als **Datenquellen** bezeichnet werden und in Clouddiensten gespeichert sind. Ein gängiges Beispiel ist eine Tabelle in einer Excel-Datei, die in OneDrive for Business gespeichert ist. Apps können über **Verbindungen** auf diese Datenquellen zugreifen.

Der verbreitetste Typ von Datenquelle ist die Tabelle, aus der Informationen abgerufen und in der Informationen gespeichert werden können. Über Verbindungen mit Datenquellen können Sie Daten in Microsoft Excel-Arbeitsmappen, SharePoint-Listen, SQL-Tabellen und vielen anderen Formaten lesen und schreiben; diese können in Clouddiensten wie OneDrive for Business, DropBox, SQL Server usw. gespeichert sein.

Es gibt andere Arten von Datenquellen, die keine Tabellen sind, z.B. E-Mails, Kalender, Twitter und Benachrichtigungen (demnächst verfügbar).

Mithilfe von **[Katalog](controls/control-gallery.md)**-, **[Formular anzeigen](controls/control-form-detail.md)**- und **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelementen können Sie auf einfache Weise eine App erstellen, die Daten aus einer Datenquelle liest und schreibt. Lesen Sie für den Einstieg den Artikel [Grundlegendes zu Datenformularen](working-with-forms.md).

Zusätzlich zum Erstellen und Verwalten von Verbindungen in [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) können Sie auch Verbindungen erstellen, wenn Sie die folgenden Aufgaben ausführen:

* Automatisches Generieren einer [App aus Daten](app-from-sharepoint.md), z. B. aus einer benutzerdefinierten SharePoint-Liste.
* Aktualisieren Sie eine vorhandene App, oder erstellen Sie eine wie in [Eine Verbindung hinzufügen](add-data-connection.md) beschrieben neu.
* Öffnen einer App, die ein anderer Benutzer erstellt und [für Sie freigegeben](share-app.md) hat.

> [!NOTE]
> Wenn Sie stattdessen PowerApps Studio verwenden möchten, öffnen Sie das Menü **Datei**, und klicken oder tippen Sie auf **Verbindungen**; [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) wird geöffnet, sodass Sie dort Verbindungen herstellen und verwalten können.

## <a name="create-a-new-connection"></a>Erstellen einer neuen Verbindung
1. Sofern noch nicht erfolgt, melden Sie sich bei [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
2. Klicken oder tippen Sie in der linken Navigationsleiste auf **Verbindungen**.
   
    ![Verbindungen verwalten](./media/add-manage-connections/open-connections.png)
3. Klicken oder tippen Sie in der oberen rechten Ecke auf **Neue Verbindung**.
   
    ![Hinzufügen von Verbindungen](./media/add-manage-connections/add-connection.png)
4. Klicken oder tippen Sie in der angezeigten Liste auf einen Connector, und befolgen Sie dann die Eingabeaufforderungen.
   
   ![Hinzufügen von Verbindungen](./media/add-manage-connections/choose-connection.png)
5. Klicken oder tippen Sie auf die Schaltfläche **Erstellen**.
   
   ![Hinzufügen von Verbindungen](./media/add-manage-connections/create-connection.png)
6. Befolgen Sie die Eingabeaufforderungen. Bei einigen Connectors werden Sie aufgefordert, Anmeldeinformationen einzugeben, einen bestimmten Datensatz anzugeben oder andere Schritte auszuführen. Bei anderen (z.B. **Microsoft Translator**) ist dies nicht der Fall.
   
   Diese Connectors erfordern möglicherweise zusätzliche Informationen, bevor Sie sie verwenden können.
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

Der neue Connector wird unter **Verbindungen** angezeigt, und Sie können ihn [zu einer App hinzufügen](add-data-connection.md).

## <a name="update-or-delete-a-connection"></a>Eine Verbindung aktualisieren oder löschen
Suchen Sie in der Liste der Verbindungen nach der zu aktualisierenden oder zu löschenden Verbindung, und klicken oder tippen Sie anschließend auf die Auslassungszeichen (Symbol mit drei Punkten) rechts neben der Verbindung.

![Aktualisieren der Verbindung](./media/add-manage-connections/auth-or-delete.png)

* Klicken oder tippen Sie zum Aktualisieren der Anmeldeinformationen auf das Schlüsselsymbol, und geben Sie dann Anmeldeinformationen für die betreffende Verbindung an.
* Um die Verbindung zu löschen, klicken oder tippen Sie auf das Papierkorbsymbol.

