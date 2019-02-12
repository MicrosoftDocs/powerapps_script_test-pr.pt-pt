---
title: ShowError-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die ShowError-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/05/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3ceb6e0bcac83bbd79d78dac859a7ddb7acf42a8
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864614"
---
# <a name="notify-function-in-powerapps"></a>Benachrichtigungsfunktion in PowerApps
Zeigt dem Benutzer eine Bannermeldung an.

## <a name="description"></a>Beschreibung
Über die **Benachrichtigungsfunktion** „Notify“ wird dem Benutzer im oberen Bereich des Bildschirms eine Bannermeldung über der zu diesem Zeitpunkt geöffneten Seite angezeigt.  

Abhängig vom Typ der Meldung werden eine passende Farbe und ein passendes Symbol angezeigt.   Der Typ wird vom zweiten Argument der Funktion angegeben:

| NotificationType-Argument | Beschreibung |
| --- | --- |
| **NotificationType.Error** | Zeigt eine Fehlermeldung an. |
| **NotificationType.Information** (Standard) | Zeigt eine Informationsmeldung an.  |
| **NotificationType.Success** | Zeigt eine Erfolgsmeldung an. |
| **NotificationType.Warning** | Zeigt eine Warnmeldung an. |

Die Meldungen werden beim Erstellen der App und beim Verwenden der App durch die Endbenutzer angezeigt.

**Notify** kann ausschließlich in [Verhaltensformeln eingesetzt werden](../working-with-formulas-in-depth.md).

**Notify** kann zusammen mit der [**IfError**](function-iferror.md)-Funktion verwendet werden. Dadurch können Fehler erkannt und mit einer benutzerdefinierten Fehlernachricht gemeldet werden.

PowerApps kann auch über einen anderen Mechanismus, der sich gänzlich von **Notify** unterscheidet, Pushbenachrichtigungen senden.  Weitere Informationen finden Sie unter [Senden einer Pushbenachrichtigung in PowerApps](../add-notifications.md).

**Notify** gibt immer *TRUE* zurück.

Hinweis: Diese Funktion hatte in der Vergangenheit den Namen **ShowError**, wenn nur Fehlermeldungen angezeigt werden konnten.

## <a name="syntax"></a>Syntax
**Notify**( *Message*, [ *NotificationType* ] )

* *Message* – Erforderlich.  Meldung, die dem Benutzer angezeigt wird.
* *NotificationType* – Optional.  In der obenstehenden Tabelle aufgelisteter Meldungstyp, der angezeigt werden soll.  Standardmäßig wird **NotificationType.Information** angezeigt.  

## <a name="examples"></a>Beispiele

### <a name="step-by-step"></a>Schritt für Schritt

1. Fügen Sie der Anzeige ein **Schaltflächen-Steuerelement** („Button“) hinzu.

2. Legen Sie die Eigenschaft **OnSelect** der **Schaltfläche** auf die folgende Formel fest:

    **Notify( "Hello, World" )**

3. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.  

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Information angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem blauen Banner angezeigt wird.](media/function-showerror/hello-world.png)

4. Ändern Sie den Meldungstyp, damit ein Fehler angezeigt wird.  Fügen Sie ein zweites Argument zu der Formel hinzu:

    **Notify( "Hello, World", NotificationType.Error )**

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als ein Fehler angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem roten Banner angezeigt wird.](media/function-showerror/hello-world-error.png)

4. Ändern Sie den Meldungstyp, damit eine Warnung angezeigt wird.  Ändern Sie das zweite Argument in der Formel:

    **Notify( "Hello, World", NotificationType.Warning )**

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Warnung angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem orangen Banner angezeigt wird.](media/function-showerror/hello-world-warning.png)

4. Ändern Sie den Meldungstyp, damit ein Erfolg angezeigt wird.  Ändern Sie das zweite Argument in der Formel:

    **Notify( "Hello, World", NotificationType.Success )**

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Erfolg angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem grünen Banner angezeigt wird.](media/function-showerror/hello-world-success.png)
