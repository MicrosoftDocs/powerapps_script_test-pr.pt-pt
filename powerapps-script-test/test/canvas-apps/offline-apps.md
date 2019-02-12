---
title: Entwickeln von offlinefähigen Canvas-Apps | Microsoft-Dokumentation
description: Entwickeln Sie offlinefähige Canvas-Apps, damit Ihre Benutzer online und offline stets produktiv sein können.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/09/2017
ms.author: mblythe
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f081369d75ec6f8fc29e6177b8173734d2462e03
ms.sourcegitcommit: 097ddfb25eb0f09f0229b866668c2b02fa57df55
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49991767"
---
# <a name="develop-offline-capable-canvas-apps"></a>Entwickeln von offlinefähigen Canvas-Apps

Eins der häufigsten Szenarios, denen Sie als Entwickler von mobilen Apps begegnen, besteht darin, Ihren Benutzern produktives Arbeiten in Umgebungen mit eingeschränkter Konnektivität oder ohne Konnektivität zu ermöglichen. PowerApps weist eine Reihe von Features und Verhaltensweisen auf, die Sie bei der Entwicklung von Canvas-Apps mit Offlinefähigkeit unterstützen. Sie haben folgende Möglichkeiten:

* Starten von PowerApps Mobile ohne Onlineverbindung.
* Ausführen von Apps, die offline entwickelt wurden.
* Mithilfe des Signalobjekts [Connection](../canvas-apps/functions/signals.md#connection) bestimmen, ob eine App offline, online oder in einer getakteten Verbindung ist.
* Verwenden von [Sammlungen](../canvas-apps/create-update-collection.md) und Nutzung von Funktionen wie [LoadData und SaveData](../canvas-apps/functions/function-savedata-loaddata.md), um offline grundlegende Datenspeicherung zur Verfügung zu machen.

> [!NOTE]
> Diese Funktion wird noch entwickelt und ist zum aktuellen Zeitpunkt noch nicht für jedes Szenario optimiert. Die Funktionen SaveData() zum Speichern von Daten auf und LoadData() zum Laden von Daten von einem lokalen Gerät arbeiten am besten in ihrer aktuellen Implementierung bei relativ kleinen Datenmengen (z.B. einige Dutzend Textdatensätze in einer Tabelle), die normalerweise 2 MB nicht überschreiten. Nützlich ist dies für einige einfache „Offlineszenarios“ oder für die Erhöhung der Startleistung von Canvas-Apps durch lokales Zwischenspeichern von Daten. Wenn Sie diese Funktion jedoch zum Speichern großer Datenmengen (z.B. Speichern von Tausenden Zeilen in einer Tabelle oder Zwischenspeicherung großer Bilder oder Videos) verwenden, sind Fehler oder ein unerwartetes Verhalten mit der aktuellen Implementierung möglich, was vermieden werden sollte. Die Funktionen lösen zudem Mergingkonflikte nicht automatisch, wenn ein Gerät, das offline war, wieder die Konnektivität herstellt. Die Konfiguration für die zu speichernden Daten und die Art und Weise, wie Daten gespeichert und die Neuverbindung hergestellt werden, richten sich nach dem Ersteller der Ausdrücke.
>
> Wir arbeiten gerade an der Erweiterung der Funktionen von Offline-Apps, der Verbesserung der Stabilität und Größenbegrenzungen und (zukünftig) an der automatischen Verarbeitung von Entscheidungen, welche Daten gespeichert und wie Konflikte gehandhabt werden sollen. Halten Sie sich hier und im [PowerApps-Blog](https://powerapps.microsoft.com/blog/) auf dem Laufenden über neue verfügbare Aktualisierungen.

## <a name="how-to-build-offline-capable-apps"></a>Erstellen von offlinefähigen Apps

Das Erste, was Sie bei Offlineszenarien bedenken müssen, ist die Weise, in der Ihre Apps mit Daten umgehen. Apps in PowerApps greifen auf Daten hauptsächlich mithilfe einer Sammlung von [Connectors](../canvas-apps/connections-list.md) zu, die von der Plattform bereitgestellt werden, wie etwa SharePoint, Office 365 und Common Data Service. Darüber hinaus können Sie benutzerdefinierte Connectors erstellen, die Apps den Zugriff auf jeden Dienst ermöglichen, der einen RESTful-Endpunkt bereitstellt. Dabei kann es sich um eine Web-API oder um einen Dienst handeln, wie etwa Azure Functions. Alle diese Connectors verwenden HTTPS im Internet, was bedeutet, dass Ihre Benutzer online sein müssen, damit sie auf Daten und andere Funktionen zugreifen können, die von einem Dienst bereitgestellt werden.

![PowerApps-App mit Connectors](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>Verarbeitung von Offlinedaten
Einer der interessantesten Aspekte von PowerApps ist die Sammlung von Funktionen und Formeln, mit deren Hilfe Sie Daten unabhängig von der Datenquelle auf konsistente Weise filtern, durchsuchen, aggregieren und bearbeiten können. Die Quellen reichen von im Arbeitsspeicher vorhandenen App-internen Sammlungen über SharePoint-Listen bis hin zu SQL-Datenbanken und dem Common Data Service. Diese Konsistenz ermöglicht es Ihnen, eine App auf einfache Weise für die Verwendung eines anderen Back-Ends als Ziel zu ändern. Wichtiger noch ist in diesem Zusammenhang, dass Sie dadurch fast ohne Änderungen an der Logik einer App lokale Sammlungen für die Datenverwaltung verwenden können. Tatsächlich stellen lokale Sammlungen den wichtigsten Mechanismus in der Verarbeitung von Offlinedaten dar.

## <a name="building-an-offline-twitter-app"></a>Erstellen einer Twitter-Offline-App
Um den Schwerpunkt bei den Offlineaspekten der App-Entwicklung zu belassen, zeigen wir Ihnen ein einfaches Szenario, das sich auf Twitter konzentriert. Wir erstellen eine App, mit der Sie Twitter-Beiträge lesen und Tweets absenden können, während Sie offline sind. Wenn die App Zugang zu einer Onlineverbindung erhält, veröffentlicht sie die Tweets und lädt die lokalen Daten erneut.

Allgemein betrachtet, führt die App die folgenden Funktionen aus:

1. Beim Starten der App (basierend auf der Eigenschaft **OnVisible** des ersten Bildschirms):

   * Wenn das Gerät über Onlinezugriff verfügt, erfolgt der Zugriff auf den Twitter-Connector direkt, um Daten abzurufen und eine Sammlung mit diesen Daten aufzufüllen.
   * Wenn das Gerät offline ist, laden wir die Daten mithilfe von [LoadData](../canvas-apps/functions/function-savedata-loaddata.md) aus einer lokalen Cachedatei.
   * Wir ermöglichen dem Benutzer das Übermitteln von Tweets – wenn die App online ist, erfolgt sofort die Veröffentlichung auf Twitter, und der lokale Cache wird aktualisiert.
2. Im Onlinemodus geschieht alle 5 Minuten Folgendes:

   * Wir veröffentlichen alle Tweets, die sich im lokalen Cache befinden.
   * Wir aktualisieren den lokalen Cache und speichern ihn mithilfe von [SaveData](../canvas-apps/functions/function-savedata-loaddata.md).

### <a name="step-1-create-a-new-phone-app"></a>Schritt 1: Erstellen einer neuen Smartphone-App
1. Öffnen Sie PowerApps Studio.
2. Klicken oder tippen Sie auf **Neu** > **Leere App** > **Smartphonelayout**.

    ![Leere App, Smartphonelayout](./media/offline-apps/blank-app.png)

### <a name="step-2-add-a-twitter-connection"></a>Schritt 2: Hinzufügen einer Twitter-Verbindung

1. Klicken oder tippen Sie auf **Inhalt** > **Datenquellen**, und wählen Sie dann im Bereich **Datenquellen** **Datenquelle hinzufügen** aus.

2. Klicken oder tippen Sie auf **Neue Verbindung**, wählen Sie **Twitter** aus, und klicken oder tippen Sie dann auf **Erstellen**.

3. Geben Sie Ihre Anmeldeinformationen ein, und erstellen Sie die Verbindung.

    ![Hinzufügen einer Twitter-Verbindung](./media/offline-apps/twitter-connection.png)

### <a name="step-3-load-tweets-into-a-localtweets-collection-on-app-startup"></a>Schritt 3: Laden von Tweets in eine LocalTweets-Sammlung beim Start
Wählen Sie in der App die **OnVisible**-Eigenschaft für **Screen1** aus, und kopieren Sie die folgende Formel:

```
If(Connection.Connected,

    ClearCollect(LocalTweets, Twitter.SearchTweet("PowerApps", {maxResults: 100}));

    UpdateContext({statusText: "Online data"})

    ,

    LoadData(LocalTweets, "Tweets", true);

    UpdateContext({statusText: "Local data"})

);

LoadData(LocalTweetsToPost, "LocalTweets", true);

SaveData(LocalTweets, "Tweets")
```

![Formel zum Laden von Tweets](./media/offline-apps/load-tweets.png)

Diese Formel überprüft, ob das Gerät online ist:

* Wenn das Gerät online ist, lädt es mit dem Suchausdruck „PowerApps“ bis zu 100 Tweets in eine **LocalTweets**-Sammlung.
* Wenn das Gerät offline ist, lädt es den lokalen Cache aus einer Datei mit dem Namen „Tweets“, sofern diese verfügbar ist.

### <a name="step-4-add-a-gallery-and-bind-it-to-the-localtweets-collection"></a>Schritt 4: Hinzufügen eines Katalogs und Anbindung des Katalogs an die LocalTweets-Sammlung

1. Fügen Sie einen neuen Katalog mit flexibler Höhe hinzu: **Einfügen** > **Katalog** > **Leer flexible Höhe**.

2. Legen Sie die Eigenschaft **Items** auf **LocalTweets** fest.

3. Fügen Sie vier **Label**-Steuerelemente hinzu, um Daten aus den einzelnen Tweets anzuzeigen, und legen Sie die Eigenschaft **Text** wie folgt fest:
   * **ThisItem.TweetText**
   * **ThisItem.UserDetails.FullName & " \@" & ThisItem.UserDetails.UserName**
   * **"RT: " & ThisItem.RetweetCount**
   * **Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)**
4. Fügen Sie ein **Image**-Steuerelement hinzu, und legen Sie die **Image**-Eigenschaft auf **ThisItem.UserDetails.ProfileImageUrl** fest.

### <a name="step-5-add-a-connection-status-label"></a>Schritt 5: Hinzufügen einer Verbindungsstatusbezeichnung
Fügen Sie ein neues **Label**-Steuerelement hinzu, und legen Sie dessen Eigenschaft **Text** auf die folgende Formel fest:

```
If (Connection.Connected, "Connected", "Offline")
```

Diese Formel überprüft, ob das Gerät online ist. Wenn dies der Fall ist, lautet der Text der Bezeichnung „Verbunden“, andernfalls „Offline“.

### <a name="step-6-add-a-text-input-to-compose-new-tweets"></a>Schritt 6: Hinzufügen einer Texteingabe zum Verfassen neuer Tweets

1. Fügen Sie ein neues **Text input**-Steuerelement mit dem Namen „NewTweetTextInput“ hinzu.

2. Legen Sie die **Reset**-Eigenschaft der Texteingabe auf **resetNewTweet** fest.

### <a name="step-7-add-a-button-to-post-the-tweet"></a>Schritt 7: Hinzufügen einer Schaltfläche zum Veröffentlichen des Tweets
1. Fügen Sie ein **Button**-Steuerelement hinzu, und legen Sie die Eigenschaft **Text** auf „Tweet“ fest.
2. Legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    ```
    If (Connection.Connected,

        Twitter.Tweet("", {tweetText: NewTweetTextInput.Text}),

        Collect(LocalTweetsToPost, {tweetText: NewTweetTextInput.Text});

        SaveData(LocalTweetsToPost, "LocalTweetsToPost")

    );

    UpdateContext({resetNewTweet: true});

    UpdateContext({resetNewTweet: false})
    ```  

Diese Formel überprüft, ob das Gerät online ist:

* Wenn das Gerät online ist, veröffentlicht es den Text sofort als Tweet.
* Wenn das Gerät offline ist, erfasst es den Tweet in einer Sammlung **LocalTweetsToPost** und speichert ihn in der App.

Anschließend setzt die Formel den Text im Textfeld zurück.

### <a name="step-8-add-a-timer-to-check-for-tweets-every-five-minutes"></a>Schritt 8: Hinzufügen eines Timers zum Abrufen von Tweets alle fünf Minuten
Fügen Sie ein neues **Timer**-Steuerelement hinzu:

* Legen Sie die **Duration**-Eigenschaft auf 300000 fest.

* Legen Sie die **AutoStart**-Eigenschaft auf „true“ fest.

* Legen Sie **OnTimerEnd** auf die folgende Formel fest:

    ```
    If(Connection.Connected,

        ForAll(LocalTweetsToPost, Twitter.Tweet("", {tweetText: tweetText}));

        Clear(LocalTweetsToPost);

        Collect(LocalTweetsToPost, {tweetText: NewTweetTextInput.Text});

        SaveData(LocalTweetsToPost, "LocalTweetsToPost");

        UpdateContext({statusText: "Online data"})
    )
    ```

Diese Formel überprüft, ob das Gerät online ist. Wenn das der Fall ist, veröffentlicht die App alle Elemente in der Sammlung **LocalTweetsToPost** als Tweets. Anschließend wird die Auflistung gelöscht.

Da die App jetzt fertiggestellt ist, sehen wir sie uns einmal an, bevor wir mit Tests fortfahren. Auf der linken Seite verfügt die App über eine Verbindung; auf der rechten Seite ist sie offline und verfügt über einen Tweet, der sofort beim Wechsel in den Onlinezustand veröffentlicht wird.

![Fertiggestellte App mit Online- und Offlinemodi](./media/offline-apps/finished-app.png)

## <a name="testing-the-app"></a>Testen der App
Gehen Sie folgendermaßen vor, um die App zu testen:

1. Führen Sie PowerApps bei bestehender Onlineverbindung auf einem mobilen Gerät aus. Sie müssen eine App zumindest einmal online ausführen, damit Sie die App auf das Gerät herunterladen können.
2. Starten Sie die Twitter-App.
3. Beachten Sie, dass die Tweets geladen werden und der Status **Verbunden** anzeigt.
4. Schließen Sie PowerApps vollständig.
5. Legen Sie den Flugmodus für das Gerät fest, um sicherzustellen, dass es offline arbeitet.
6. Führen Sie PowerApps aus. Sie können die Twitter-App jetzt offline ausführen und besitzen Zugriff auf alle anderen Apps, die Sie zuvor online auf dem betreffenden Gerät ausgeführt haben (d.h., PowerApps blendet alle Apps aus, die nicht auf Ihr Gerät heruntergeladen wurden).
7. Führen Sie die App erneut aus.
8. Beachten Sie ,dass sie den Verbindungsstatus ordnungsgemäß als **Offline** angibt.
9. Schreiben Sie einen neuen Tweet. Er wird lokal in der Sammlung **LocalTweetsToPost** gespeichert.
10. Beenden Sie den Flugmodus. Nach dem Auslösen des Timers veröffentlicht die App den Tweet.

Wir hoffen, dass dieser Artikel Ihnen eine Vorstellung von den Möglichkeiten gegeben hat, die PowerApps für das Erstellen von Offline-Apps bietet. Wie immer freuen wir uns über Ihr Feedback in unserem [Forum](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) und über Ihre Beispiele für Offline-Apps im [PowerApps Community-Blog](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog).

