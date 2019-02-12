---
title: Freigeben einer Canvas-App | Microsoft-Dokumentation
description: Geben Sie Ihre Canvas-App frei, indem Sie anderen Benutzern die Berechtigung erteilen, die App auszuführen oder zu ändern.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 07/11/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 926d2b4b0d24f07a9a4cd42216e7d737db57308c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42853840"
---
# <a name="share-a-canvas-app-in-powerapps"></a>Freigeben einer Canvas-App in PowerApps

Nachdem Sie eine Canvas-App erstellt haben, die eine geschäftliche Anforderung behandelt, geben Sie an, welche Benutzer in Ihrer Organisation die App ausführen dürfen und welche sie ändern oder sogar erneut freigeben dürfen. Geben Sie jeden Benutzer anhand seines Namens an, oder geben Sie eine Sicherheitsgruppe in Azure Active Directory an. Wenn jeder von Ihrer App profitieren würde, geben Sie an, dass Ihre gesamte Organisation diese ausführen darf.

> [!IMPORTANT]
> Damit eine freigegebene App wie erwartet funktionieren kann, müssen Sie auch die Berechtigungen für die Datenquelle oder Quellen, auf denen die App basiert, verwalten, z.B. [Common Data Service für Apps](#common-data-service-for-apps) oder [Excel](share-app-data.md). Sie müssen möglicherweise auch [andere Ressourcen freigeben](share-app-resources.md), von denen die App abhängt, z.B. Flows, Gateways oder Verbindungen.

## <a name="prerequisites"></a>Voraussetzungen

Um eine App freizugeben, müssen Sie sie in der Cloud speichern (nicht lokal) und dann veröffentlichen.

- Geben Sie Ihrer App einen aussagekräftigen Namen und eine klare Beschreibung, damit Benutzer wissen, was die App bewirkt und sie so leicht in einer Liste finden können. Wählen Sie im Menü **Datei** in PowerApps Studio die **App-Einstellungen** aus, geben Sie einen Namen an, und tippen bzw. fügen Sie eine Beschreibung ein.

- Wenn Sie Änderungen vornehmen, müssen Sie die App speichern und erneut veröffentlichen, wenn andere Personen diese Änderungen sehen sollen.

## <a name="share-an-app"></a>Eine App freigeben

1. [Melden Sie sich bei PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wählen Sie dann am linken Bildschirmrand **Apps** aus.

    ![Anzeigen der App-Liste](./media/share-app/file-apps.png)

1. Wählen Sie für die App, die Sie freigeben möchten, die Auslassungspunkte (...) und anschließend **Freigeben** aus.

    ![Geöffneter Bildschirm „Freigeben“](./media/share-app/ellipsis-share.png)

1. Geben Sie an, für welche Benutzer oder Sicherheitsgruppen in Azure Active Directory Sie die App freigeben möchten.

    > [!NOTE]
    > Sie können keine Apps mit einer Verteilergruppe in Ihrer Organisation oder mit Benutzern oder Gruppen außerhalb Ihrer Organisation teilen.

    ![Angeben von Benutzern](./media/share-app/share-list.png)

    Sie können die App ebenfalls für Ihre gesamte Organisation freigeben, sodass alle Mitglieder die App ausführen können. Diese können jedoch keine Änderungen vornehmen oder die App freigeben.

1. Optional: Damit Benutzer Ihre App leichter finden können, aktivieren Sie das Kontrollkästchen zum Senden einer Einladung per E-Mail.

    Die Einladung enthält einen Link, mit dem Benutzer die App ausführen können.

    - Wenn ein Benutzer auf einem Desktopcomputer auf den Link klickt, wird die App in [Dynamics 365](http://home.dynamics.com) veröffentlicht.
    - Wenn der Benutzer auf einem Mobilgerät auf den Link tippt, wird die App in PowerApps Mobile geöffnet.

    Wenn Sie Benutzern die Berechtigung zum Ändern der App erteilen, enthält die Benachrichtigung auch einen separaten Link, um die App zur Bearbeitung in PowerApps Studio zu öffnen.

    Unabhängig davon, ob Sie eine Einladung senden oder nicht, können Benutzer die App über AppSource auf [Dynamics 365](http://home.dynamics.com) ausführen. Benutzer, die über eine **Kann bearbeiten**-Berechtigung verfügen, können die App auch innerhalb von [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) bearbeiten.

1. Geben Sie die Berechtigung für jeden Benutzer bzw. jede Sicherheitsgruppe an, und klicken Sie dann auf **Speichern**.

    - **Verwenden**: Benutzer können die App ausführen, aber nicht freigeben.
    - **Kann bearbeiten**: Benutzer können die App ausführen, ändern, und die benutzerdefinierte Version für andere Benutzer freigeben.

        ![Berechtigungen angeben](./media/share-app/edit-use.png)

    Klicken Sie zum Ändern der Berechtigungen für einen Benutzer oder eine Sicherheitsgruppe neben der Berechtigung, über die der Benutzer oder die Gruppe bereits verfügt, auf den Pfeil nach unten, und geben Sie dann eine andere Berechtigung ein.

    Wählen Sie das Symbol **x** für einen Benutzer oder für eine Gruppe aus, um einem Benutzer oder einer Gruppe alle Berechtigungen zu entziehen.

## <a name="security-group-considerations"></a>Überlegungen zu Sicherheitsgruppen

- Wenn Sie eine App für eine Sicherheitsgruppe, bestehende Mitglieder dieser Gruppe und jeden freigeben, der dieser Gruppe beitritt, verfügen alle über die von Ihnen angegebenen Berechtigungen für diese Gruppe. Jeder, der die Gruppe verlässt, verliert diese Berechtigung, es sei denn, die Person gehört noch zu einer anderen Gruppe, die über Zugriff verfügt, oder Sie verleihen der Person die Berechtigung als Einzelperson.
- Jedes Mitglied einer Sicherheitsgruppe besitzt dieselbe Berechtigung für eine App wie die Gruppe. Sie können allerdings für ein Mitglied oder mehrere Mitglieder dieser Gruppe tiefgreifendere Berechtigungen angeben, um diesen Personen besseren Zugriff zu gewähren. Sie können beispielsweise „Sicherheitsgruppe A“ die Berechtigung **Verwenden** erteilen. Sie können jedoch auch „Benutzer B“, der zu dieser Gruppe gehört, die Berechtigung **Kann bearbeiten** erteilen. Jedes Mitglied der Sicherheitsgruppe kann die App ausführen, aber nur Benutzer B kann diese bearbeiten. Wenn Sie „Sicherheitsgruppe A“ die Berechtigung **Kann bearbeiten** erteilen, aber „Benutzer B“ nur die Berechtigung **Verwenden**, kann der Benutzer die App trotzdem bearbeiten.

## <a name="manage-entity-permissions"></a>Verwalten von Entitätsberechtigungen

### <a name="common-data-service-for-apps"></a>Common Data Service für Apps

Wenn Sie eine App auf Grundlage von Common Data Service (CDS) für Apps erstellen, müssen Sie auch sicherstellen, dass die Benutzer, die diese App ausführen werden, über die entsprechenden Berechtigungen für die Entität bzw. Entitäten verfügen, auf denen die App basiert. Konkret müssen Benutzer einer Sicherheitsrolle angehören, die Aufgaben wie Erstellen, Lesen, Schreiben und/oder Löschen relevanter Datensätze ausführen kann. In vielen Fällen werden Sie mindestens eine benutzerdefinierte Sicherheitsrolle mit genau den Berechtigungen erstellen wollen, die Benutzer für die Verwendung Ihrer Apps benötigen. Anschließend können Sie diese Rolle bzw. Rollen den Benutzern nach Bedarf zuweisen. 

#### <a name="prerequisite"></a>Voraussetzung

Für die nächsten beiden Verfahren müssen Sie über **Systemadministratorberechtigungen** für eine CDS for Apps-Datenbank verfügen.

#### <a name="create-a-security-role"></a>Sicherheitsrolle erstellen

1. [Melden Sie sich in PowerApps an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), und stellen Sie sicher, dass Sie sich in derselben Umgebung wie die App befinden, die Sie freigeben möchten.

1. Wählen Sie in der rechten oberen Ecke das Zahnradsymbol und dann **Erweiterte Anpassungen** aus.

    ![Öffnen des Bereichs „Erweiterte Anpassungen“](media/share-app/advanced-customizations.png)

1. Klicken Sie auf die Verknüpfung **Sicherheitsrollen**.

    ![Öffnen von Sicherheitsrollen](media/share-app/security-roles.png)

1. Wählen Sie unter **Alle Rollen** **Neu** aus, tippen oder geben Sie dann einen Namen für die Rolle, die Sie erstellen, ein.

    ![Sicherheitsgruppe erstellen](media/share-app/new-role.png)

1. Wählen Sie mindestens eine Registerkarte aus, um die Entität bzw. Entitäten zu suchen, die von Ihrer App verwendet werden. Wählen Sie anschließend die Berechtigungen aus, denen Sie die Sicherheitsrolle zuweisen möchten.

    Diese Grafik stellt beispielsweise dar, dass eine Sicherheitsrolle Datensätze in der Entität „Account“, die auf der Registerkarte **Core records** (Kerndatensätze) angezeigt wird, erstellen, lesen und schreiben kann.

    ![Berechtigungen angeben](media/share-app/grant-access.png)

1. Klicken Sie auf **Speichern und schließen**.

#### <a name="assign-a-user-to-a-role"></a>Benutzer einer Rolle zuweisen

1. Öffnen Sie wie im vorhergehend beschriebenen Schritt den Bereich **Erweiterte Anpassungen**, und klicken Sie dann auf die Verknüpfung **Benutzer**.

    ![Verknüpfung „Benutzer“](media/share-app/open-users.png)

1. Tippen oder geben Sie in der oberen rechten Ecke den Namen des Benutzers ein, dem die Rolle zugewiesen werden soll, und klicken Sie dann auf das Suchsymbol.

    ![Nach Benutzern suchen](media/share-app/search-users.png)

1. Zeigen Sie in den Suchergebnissen auf das gewünschte Ergebnis, und aktivieren Sie dann das Kontrollkästchen, das angezeigt wird.

1. Wählen Sie oben im Banner **Rollen verwalten** aus.

1. Aktivieren Sie im Dialogfeld, das daraufhin angezeigt wird, die Kontrollkästchen für **Common Data Service-Benutzer** sowie für die Rolle, die Benutzer für Ihre App benötigen. Klicken Sie anschließend auf **OK**.

    ![Benutzer einer Rolle zuweisen](media/share-app/assign-users.png)

### <a name="common-data-service-previous-version"></a>Common Data Service (vorherige Version)

Wenn Sie eine App freigeben, die auf einer früheren Version von Common Data Service basiert, müssen Sie die Laufzeitberechtigung für den Dienst separat erteilen. Wenn Sie hierzu nicht berechtigt sind, wenden Sie sich an Ihren Umgebungsadministrator.
