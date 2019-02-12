---
title: Übersicht über die Twitter-Verbindung | Microsoft-Dokumentation
description: Anleitung zum Herstellen einer Verbindung mit Twitter, einige Beispiele für die erforderlichen Schritte und Auflistung aller Funktionen
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/12/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2ab480b0bb2aa61c65e33f67cca5a3b0974ca2c8
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834524"
---
# <a name="connect-to-twitter-from-powerapps"></a>Herstellen einer Verbindung mit Twitter aus PowerApps
![Twitter](./media/connection-twitter/twittericon.png)

Über Twitter können Sie Tweets senden und Tweets, Timeline, Freunde und Follower aus Ihrem Twitter-Konto abrufen.

Sie können diese Informationen in einer Bezeichnung in Ihrer App anzeigen. Sie können z.B. ein Eingabetextfeld hinzufügen, die Benutzer auffordern, Text für einen Tweet einzugeben und dann eine Schaltfläche zum Senden des Tweets hinzufügen. Auf ähnliche Weise können Sie einen Tweet abrufen oder suchen und den Text dann in einem Bezeichnung- oder Katalog-Steuerelement in Ihrer App anzeigen.

In diesem Thema wird gezeigt, wie Sie die Twitter-Verbindung erstellen und in einer App verwenden, und es werden die verfügbaren Funktionen aufgeführt.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-twitter"></a>Herstellen einer Verbindung mit Twitter
1. Öffnen Sie PowerApps, wählen Sie **Neu** aus, und erstellen Sie eine **Leere App**. Wählen Sie das Layout für Smartphone oder Tablet aus. Das Tablet-Layout bietet Ihnen einen größeren Arbeitsbereich:  

   ![Öffnen einer leeren App](./media/connection-twitter/blank-app.png)
2. Klicken oder tippen Sie im rechten Bereich auf die Registerkarte **Daten** und dann auf **Datenquelle hinzufügen**.
3. Wählen Sie **Neue Verbindung** und anschließend **Twitter** aus:  

    ![Herstellen einer Verbindung mit Twitter](./media/connection-twitter/addconnection.png)

    ![Herstellen einer Verbindung mit Twitter](./media/connection-twitter/add-twitter.png)
4. Wählen Sie **Verbinden** aus, geben Sie Ihre Anmeldeinformationen für Twitter ein, und wählen Sie dann **App autorisieren** aus.
5. Wählen Sie **Datenquelle hinzufügen** aus. Die Verbindung wird unter **Datenquellen** angezeigt:  
    ![Bereich „Optionen“ schließen](./media/connection-twitter/twitterdatasource.png)

Die Verbindung mit Twitter wurde erstellt und Ihrer App hinzugefügt. Sie kann jetzt verwendet werden.

## <a name="use-the-twitter-connection-in-your-app"></a>Verwenden der Twitter-Verbindung in der App
### <a name="show-a-timeline"></a>Anzeigen einer Timeline
1. Wählen Sie im Menü **Einfügen** die Option **Katalog** aus, und fügen Sie einen der **Mit Text**-Kataloge hinzu.
2. So zeigen Sie Timelines an  

   * Um die Timeline des aktuellen Benutzers anzuzeigen, legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf die folgenden Formeln fest:

       `Twitter.HomeTimeline().TweetText`  
       `Twitter.HomeTimeline({maxResults:3}).TweetText`  
   * Um die Timeline eines anderen Benutzers anzuzeigen, legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf die folgende Formel fest:  

       `Twitter.UserTimeline( *TwitterHandle* ).TweetText`

       Geben Sie einen Twitter-Benutzernamen in doppelten Anführungszeichen oder einen entsprechenden Wert ein. Geben Sie z.B. `"satyanadella"` oder `"powerapps"` direkt im Formelausdruck ein.
   * Fügen Sie ein Texteingabe-Steuerelement mit dem Namen **Tweep** hinzu, und legen Sie die Default-Eigenschaft auf `Tweep.Text` fest. Geben Sie im Textfeld „Tweep“ einen Twitter-Benutzernamen wie `satyanadella` (ohne Anführungszeichen und das Symbol @) ein.

       Legen Sie im Katalog-Steuerelement die Items-Eigenschaft auf die folgende Formel fest:  

       `Twitter.UserTimeline(Tweep.Text, {maxResults:5}).TweetText`

       Im Katalog-Steuerelement werden automatisch die Tweets des eingegebenen Twitter-Benutzernamens angezeigt.

     > [!TIP]
     > In einigen dieser Formeln wird das Argument **maxResults** zum Anzeigen der letzten *x* Tweets in einer Timeline verwendet.
3. Legen Sie die **Items**-Eigenschaft des Katalogs auf `Twitter.HomeTimeline()` fest.

    Wenn der Katalog ausgewählt ist, werden im rechten Bereich Optionen für diesen Katalog angezeigt.
4. Wählen Sie **TweetText** in der ersten Liste, **TweetedBy** in der zweiten Liste und **CreatedAt** in der dritten Liste aus.

    Im Katalog werden nun die Werte der ausgewählten Eigenschaften angezeigt.

### <a name="show-followers"></a>Anzeigen von Followern
1. So zeigen Sie mit einem **Mit Text**-Katalog Follower an  

   * Um die Follower des aktuellen Benutzers anzuzeigen, legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf die folgende Formel fest:  

       `Twitter.MyFollowers()`  
       `Twitter.MyFollowers({maxResults:3})`
   * Um die Follower eines anderen Benutzers anzuzeigen, legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf die folgende Formel fest:  

       `Twitter.Followers( *TwitterHandle* )`

       Geben Sie einen Twitter-Benutzernamen in doppelten Anführungszeichen oder einen entsprechenden Wert ein. Geben Sie z.B. `"satyanadella"` oder `"powerapps"` direkt im Formelausdruck ein.
   * Fügen Sie ein Texteingabe-Steuerelement mit dem Namen **Tweep** hinzu, und legen Sie die Default-Eigenschaft auf `Tweep.Text` fest. Geben Sie im Textfeld „Tweep“ einen Twitter-Benutzernamen wie `satyanadella` (ohne Anführungszeichen und das Symbol @) ein.

       Legen Sie im Katalog-Steuerelement die Items-Eigenschaft auf die folgende Formel fest:  

       `Twitter.Followers(Tweep.Text, {maxResults:5})`

       Im Katalog-Steuerelement wird automatisch angezeigt, wer dem eingegebenen Twitter-Benutzernamen folgt.

     > [!TIP]
     > In einigen dieser Formeln wird das Argument **maxResults** zum Anzeigen der letzten *x* Tweets in einer Timeline verwendet.
2. Legen Sie die **Items**-Eigenschaft des Katalogs auf `Twitter.MyFollowers()` fest.

    Wenn der Katalog ausgewählt ist, werden im rechten Bereich Optionen für diesen Katalog angezeigt.
3. Wählen Sie **UserName** in der zweiten Liste aus, und wählen Sie **FullName** in der dritten Liste aus.

    Im Katalog werden nun die Werte der ausgewählten Eigenschaften angezeigt.

### <a name="show-followed-users"></a>Anzeigen der Benutzer, denen gefolgt wird
1. So zeigen Sie mit einem **Mit Text**-Katalog an, welchen Benutzern gefolgt wird  

   * Um anzuzeigen, welchen Benutzern der aktuelle Benutzer folgt, legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf die folgende Formel fest:  

       `Twitter.MyFollowing()`  
       `Twitter.MyFollowing({maxResults:3})`
   * Um anzuzeigen, welchen Benutzern ein anderer Benutzer folgt, legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf die folgende Formel fest:

       `Twitter.Following( *TwitterHandle* )`

       Geben Sie einen Twitter-Benutzernamen in doppelten Anführungszeichen oder einen entsprechenden Wert ein. Geben Sie z.B. `"satyanadella"` oder `"powerapps"` direkt im Formelausdruck ein.
   * Fügen Sie ein Texteingabe-Steuerelement mit dem Namen **Tweep** hinzu, und legen Sie die Default-Eigenschaft auf `Tweep.Text` fest. Geben Sie im Textfeld „Tweep“ einen Twitter-Benutzernamen wie `satyanadella` (ohne Anführungszeichen und das Symbol @) ein.

       Legen Sie im Katalog-Steuerelement die Items-Eigenschaft auf die folgende Formel fest:  

       `Twitter.Following(Tweep.Text, {maxResults:5})`

       Im Katalog-Steuerelement werden automatisch die anderen Benutzernamen angezeigt, denen Sie folgen.

     Wenn der Katalog ausgewählt ist, werden im rechten Bereich Optionen für diesen Katalog angezeigt.
2. Wählen Sie **Beschreibung** in der Liste **Body1**, **UserName** in der Liste **Heading1** und **FullName** in der Liste **Subtitle1** aus.

    Im Katalog werden nun die Werte der ausgewählten Eigenschaften angezeigt.

### <a name="show-information-about-a-user"></a>Anzeigen von Informationen zu einem Benutzer
Fügen Sie eine Bezeichnung hinzu, und legen Sie deren **[Text](../controls/properties-core.md)**-Eigenschaft auf eine der folgenden Formeln fest:  

* `twitter.User( *TwitterHandle* ).Description`
* `twitter.User( *TwitterHandle* ).FullName`
* `twitter.User( *TwitterHandle* ).Location`
* `twitter.User( *TwitterHandle* ).UserName`
* `twitter.User( *TwitterHandle* ).FollowersCount`
* `twitter.User( *TwitterHandle* ).FriendsCount`
* `twitter.User( *TwitterHandle* ).Id`
* `twitter.User( *TwitterHandle* ).StatusesCount`

Geben Sie einen Twitter-Benutzernamen in doppelten Anführungszeichen oder einen entsprechenden Wert ein. Geben Sie z.B. `"satyanadella"` oder `"powerapps"` direkt im Formelausdruck ein.

Sie können ein auch Texteingabe-Steuerelement verwenden, um einen Twitter-Benutzernamen einzugeben, so wie in den anderen Abschnitten dieses Themas.

### <a name="search-tweets"></a>Suchen von Tweets
1. Legen Sie bei einem **Mit Text**-Katalog die **[Items](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:  

    `Twitter.SearchTweet( *SearchTerm* ).TweetText`

    Geben Sie einen *SearchTerm* in doppelten Anführungszeichen oder durch einen Verweis auf einen entsprechenden Wert ein. Geben Sie z.B. `"PowerApps"` oder `"microsoft"` direkt in der Formel ein.

    Sie können ein auch ein **Eingabetext**-Steuerelement verwenden, um einen Suchbegriff anzugeben, so wie in den anderen Abschnitten dieses Themas.

    > [!TIP]
   > Mit „maxResults“ werden die ersten fünf Ergebnisse angezeigt:  

    `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5}).TweetText`
2. Legen Sie die **Items**-Eigenschaft des Katalogs auf `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5})` fest.

    Wenn der Katalog ausgewählt ist, werden im rechten Bereich Optionen für diesen Katalog angezeigt.
3. Wählen Sie **TweetText** in der ersten Liste, **TweetedBy** in der zweiten Liste und **CreatedAt** in der dritten Liste aus.

    Im Katalog werden nun die Werte der ausgewählten Eigenschaften angezeigt.

### <a name="send-a-tweet"></a>Senden eines Tweets
1. Fügen Sie ein Texteingabe-Steuerelement hinzu, und benennen Sie es in **MyTweet** um.
2. Fügen Sie eine Schaltfläche hinzu, und legen Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:  
    `Twitter.Tweet({tweetText: MyTweet.Text})`
3. Drücken Sie F5, oder wählen Sie die Vorschauschaltfläche aus (![](./media/connection-twitter/preview.png)). Geben Sie Text in **MyTweet** ein, und wählen Sie dann die Schaltfläche aus, um den eingegebenen Text zu twittern.
4. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.

## <a name="view-the-available-functions"></a>Anzeigen der verfügbaren Funktionen
Diese Verbindung umfasst die folgenden Funktionen:

| Funktionsname | Beschreibung |
| --- | --- |
| [UserTimeline](connection-twitter.md#usertimeline) |Ruft eine Sammlung der letzten Tweets ab, die vom angegebenen Benutzer gesendet wurden |
| [HomeTimeline](connection-twitter.md#hometimeline) |Ruft die letzten Tweets und Re-Tweets von mir und meinen Followern ab |
| [SearchTweet](connection-twitter.md#searchtweet) |Ruft eine Sammlung von relevanten Tweets ab, die mit einer angegebenen Abfrage übereinstimmen |
| [Followers](connection-twitter.md#followers) |Ruft die Benutzer ab, die dem angegebenen Benutzer folgen |
| [MyFollowers](connection-twitter.md#myfollowers) |Ruft die Benutzer ab, die mir folgen |
| [Following](connection-twitter.md#following) |Ruft die Benutzer, denen der angegebene Benutzer folgt |
| [MyFollowing](connection-twitter.md#myfollowing) |Ruft die Benutzer ab, denen ich folge |
| [User](connection-twitter.md#user) |Ruft Details zum angegebenen Benutzer ab (Beispiel: Benutzername, Beschreibung, Anzahl der folgenden Benutzer usw.) |
| [Tweet](connection-twitter.md#tweet) |Tweet |
| [OnNewTweet](connection-twitter.md#onnewtweet) |Löst einen Workflow aus, wenn ein neuer Tweet gesendet wird, der mit Ihrer Suchabfrage übereinstimmt |

### <a name="usertimeline"></a>UserTimeline
Timeline des Benutzers abrufen: Ruft eine Sammlung der letzten Tweets ab, die vom angegebenen Benutzer gesendet wurden

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| userName |Zeichenfolge |ja |Twitter-Benutzername |
| maxResults |Ganze Zahl |Nein |Maximale Anzahl von abzurufenden Tweets, z.B. {maxResults:5} |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| TweetText |Zeichenfolge |Ja | |
| TweetId |Zeichenfolge |Nein | |
| CreatedAt |Zeichenfolge |Nein | |
| RetweetCount |Ganze Zahl |Ja | |
| TweetedBy |Zeichenfolge |Ja | |
| MediaUrls |Array |Nein | |

### <a name="hometimeline"></a>HomeTimeline
Home-Timeline: Ruft die letzten Tweets und Re-Tweets von mir und meinen Followern ab

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| maxResults |Ganze Zahl |Nein |Maximale Anzahl von abzurufenden Tweets, z.B. {maxResults:5} |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| TweetText |Zeichenfolge |Ja | |
| TweetId |Zeichenfolge |Nein | |
| CreatedAt |Zeichenfolge |Nein | |
| RetweetCount |Ganze Zahl |Ja | |
| TweetedBy |Zeichenfolge |Ja | |
| MediaUrls |Array |Nein | |

### <a name="searchtweet"></a>SearchTweet
Tweet suchen: Ruft eine Sammlung von relevanten Tweets ab, die mit einer angegebenen Abfrage übereinstimmen

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| searchQuery |Zeichenfolge |ja |Abfragetext (Sie können alle von Twitter unterstützten Abfrageoperatoren verwenden: http://www.twitter.com/search)) |
| maxResults |Ganze Zahl |Nein |Maximale Anzahl von abzurufenden Tweets, z.B. {maxResults:5} |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| TweetText |Zeichenfolge |Ja | |
| TweetId |Zeichenfolge |Nein | |
| CreatedAt |Zeichenfolge |Nein | |
| RetweetCount |Ganze Zahl |Ja | |
| TweetedBy |Zeichenfolge |Ja | |
| MediaUrls |Array |Nein | |

### <a name="followers"></a>Followers
Follower abrufen: Ruft die Benutzer ab, die dem angegebenen Benutzer folgen

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| userName |Zeichenfolge |ja |Twitter-Name des Benutzers |
| maxResults |Ganze Zahl |Nein |Maximale Anzahl von abzurufenden Benutzern, z.B. {maxResults:5} |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| FullName |Zeichenfolge |Ja | |
| Ort |Zeichenfolge |Ja | |
| Id |Ganze Zahl |Nein | |
| UserName |Zeichenfolge |Ja | |
| FollowersCount |Ganze Zahl |Nein | |
| Beschreibung |Zeichenfolge |Ja | |
| StatusesCount |Ganze Zahl |Nein | |
| FriendsCount |Ganze Zahl |Nein | |

### <a name="myfollowers"></a>MyFollowers
Meine Follower abrufen: Ruft die Benutzer ab, die mir folgen

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| maxResults |Ganze Zahl |Nein |Maximale Anzahl von abzurufenden Benutzern, z.B. {maxResults:5} |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| FullName |Zeichenfolge |Ja | |
| Ort |Zeichenfolge |Ja | |
| Id |Ganze Zahl |Nein | |
| UserName |Zeichenfolge |Ja | |
| FollowersCount |Ganze Zahl |Nein | |
| Beschreibung |Zeichenfolge |Ja | |
| StatusesCount |Ganze Zahl |Nein | |
| FriendsCount |Ganze Zahl |Nein | |

### <a name="following"></a>Following
Gefolgte Benutzer abrufen: Ruft die Benutzer ab, denen der angegebene Benutzer folgt

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| userName |Zeichenfolge |ja |Twitter-Name des Benutzers |
| maxResults |Ganze Zahl |Nein |Maximale Anzahl von abzurufenden Benutzern, z.B. {maxResults:5} |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| FullName |Zeichenfolge |Ja | |
| Ort |Zeichenfolge |Ja | |
| Id |Ganze Zahl |Nein | |
| UserName |Zeichenfolge |Ja | |
| FollowersCount |Ganze Zahl |Nein | |
| Beschreibung |Zeichenfolge |Ja | |
| StatusesCount |Ganze Zahl |Nein | |
| FriendsCount |Ganze Zahl |Nein | |

### <a name="myfollowing"></a>MyFollowing
Meine gefolgten Benutzer: Ruft die Benutzer ab, denen ich folge

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| maxResults |Ganze Zahl |Nein |Maximale Anzahl von abzurufenden Benutzern, z.B. {maxResults:5} |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| FullName |Zeichenfolge |Ja | |
| Ort |Zeichenfolge |Ja | |
| Id |Ganze Zahl |Nein | |
| UserName |Zeichenfolge |Ja | |
| FollowersCount |Ganze Zahl |Nein | |
| Beschreibung |Zeichenfolge |Ja | |
| StatusesCount |Ganze Zahl |Nein | |
| FriendsCount |Ganze Zahl |Nein | |

### <a name="user"></a>User
Benutzer abrufen: Ruft Details zum angegebenen Benutzer ab (Beispiel: Benutzername, Beschreibung, Anzahl der Follower usw.)

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| userName |Zeichenfolge |ja |Twitter-Name des Benutzers |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| FullName |Zeichenfolge |Ja | |
| Ort |Zeichenfolge |Ja | |
| Id |Ganze Zahl |Nein | |
| UserName |Zeichenfolge |Ja | |
| FollowersCount |Ganze Zahl |Nein | |
| Beschreibung |Zeichenfolge |Ja | |
| StatusesCount |Ganze Zahl |Nein | |
| FriendsCount |Ganze Zahl |Nein | |

### <a name="tweet"></a>Tweet
Neuen Tweet senden: Tweet

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| tweetText |Zeichenfolge |Nein |Zu twitternder Text, z.B. {tweetText: "hello"} |
| body |Zeichenfolge |Nein |Zu sendende Medien |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| TweetId |Zeichenfolge |Ja | |

### <a name="onnewtweet"></a>OnNewTweet
Wenn ein neuer Tweet eingeht: Löst einen Workflow aus, wenn ein neuer Tweet gesendet wird, der mit Ihrer Suchabfrage übereinstimmt

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| searchQuery |Zeichenfolge |ja |Abfragetext (Sie können alle von Twitter unterstützten Abfrageoperatoren verwenden: http://www.twitter.com/search)) |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| value |Array |Nein | |

## <a name="helpful-links"></a>Nützliche Links
Alle [verfügbaren Verbindungen](../connections-list.md).  
Erfahren Sie, wie Sie Ihren Apps [Verbindungen hinzufügen](../add-manage-connections.md).

