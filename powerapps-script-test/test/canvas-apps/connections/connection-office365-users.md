---
title: Übersicht über die Verbindung mit Office 365-Benutzer| Microsoft-Dokumentation
description: Anleitung zum Herstellen einer Verbindung mit Office 365-Benutzer, einige Beispiele für die erforderlichen Schritte und Auflistung aller Funktionen
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/07/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 507bac0b57cdc1e348bd384d5544d7b664a3e0f5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42851262"
---
# <a name="connect-to-office-365-users-connection-from-powerapps"></a>Herstellen einer Verbindung mit Office 365-Benutzer aus PowerApps
![Office 365-Benutzer](./media/connection-office365-users/office365icon.png)

Office 365-Benutzer bietet Ihnen Zugriff auf Benutzerprofile in Ihrer Organisation mithilfe Ihres Office 365-Kontos. Sie können verschiedene Aktionen ausführen, z. B. Ihr Profil, das Profil eines Benutzers, den Vorgesetzten oder die direkten Mitarbeiter eines Benutzers abrufen.

Sie können diese Informationen in einer Bezeichnung in Ihrer App anzeigen. Sie können eine Funktion oder mehrere Funktionen anzeigen und sogar verschiedene Funktionen kombinieren. Beispielsweise können Sie einen Ausdruck erstellen, der den Benutzernamen und die Telefonnummer kombiniert, und dann diese Information in der App anzeigen.

In diesem Thema wird gezeigt, wie Sie Office 365-Benutzer als Verbindung hinzufügen, Office 365-Benutzer Ihrer App als Datenquelle hinzufügen und wie Sie Tabellendaten in einem Katalogsteuerelement verwenden.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="add-a-connection"></a>Eine Verbindung hinzufügen
1. [Fügen Sie eine Datenverbindung hinzu](../add-data-connection.md), und wählen Sie **Office 365-Benutzer** aus:  

    ![Herstellen einer Verbindung mit Office 365](./media/connection-office365-users/add-office.png)
2. Wählen Sie **Verbinden** aus, und wenn Sie aufgefordert werden, sich anzumelden, geben Sie Ihr Geschäftskonto ein.

Die Verbindung mit Office 365-Benutzer wurde erstellt und Ihrer App hinzugefügt. Sie kann jetzt verwendet werden.

## <a name="use-the-connection-in-your-app"></a>Verwenden der Verbindung in der App
### <a name="show-information-about-the-current-user"></a>Informationen über den aktuellen Benutzer anzeigen
1. Wählen Sie im Menü **Insert** (Einfügen) die Option **Label** (Bezeichnung) aus
2. Legen Sie in der Funktionsleiste die **[Text](../controls/properties-core.md)**-Eigenschaft auf eine der folgenden Formeln fest:

    `Office365Users.MyProfile().Department`  
    `Office365Users.MyProfile().DisplayName`  
    `Office365Users.MyProfile().GivenName`  
    `Office365Users.MyProfile().Id`  
    `Office365Users.MyProfile().JobTitle`  
    `Office365Users.MyProfile().Mail`  
    `Office365Users.MyProfile().MailNickname`  
    `Office365Users.MyProfile().Surname`  
    `Office365Users.MyProfile().TelephoneNumber`  
    `Office365Users.MyProfile().UserPrincipalName`  
    `Office365Users.MyProfile().AccountEnabled`  

In der Bezeichnung werden die Informationen über den aktuellen Benutzer angezeigt, die Sie eingegeben haben.

### <a name="show-information-about-another-user"></a>Anzeigen von Informationen zu einem anderen Benutzer
1. Klicken Sie im Menü **Insert** (Einfügen) auf **Text**, und wählen Sie dann **Texteingabe** (Texteingabe) aus. Benennen Sie das Steuerelement in **InfoAbout** um:  

    ![Umbenennen des Steuerelements](./media/connection-office365-users/renameinfoabout.png)
2. Geben Sie in **InfoAbout** eine E-Mail-Adresse eines Benutzers in Ihrer Organisation ein, oder fügen Sie sie ein. Geben Sie z. B. *IhrName*@*IhrUnternehmen.com* ein.
3. Fügen Sie ein **Label** (Bezeichnung) hinzu (Menü **Einfügen**), und legen Sie seine **[Text](../controls/properties-core.md)**-Eigenschaft auf eine der folgenden Formeln fest:

   * So zeigen Sie Informationen zu einem anderen Benutzer an:  

       `Office365Users.UserProfile(InfoAbout.Text).Department`  
       `Office365Users.UserProfile(InfoAbout.Text).DisplayName`  
       `Office365Users.UserProfile(InfoAbout.Text).GivenName`  
       `Office365Users.UserProfile(InfoAbout.Text).Id`  
       `Office365Users.UserProfile(InfoAbout.Text).JobTitle`  
       `Office365Users.UserProfile(InfoAbout.Text).Mail`  
       `Office365Users.UserProfile(InfoAbout.Text).MailNickname`  
       `Office365Users.UserProfile(InfoAbout.Text).Surname`  
       `Office365Users.UserProfile(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.UserProfile(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.UserProfile(InfoAbout.Text).AccountEnabled`  
   * So zeigen Sie Informationen zum Vorgesetzten eines anderen Benutzers an:  

       `Office365Users.Manager(InfoAbout.Text).Department`  
       `Office365Users.Manager(InfoAbout.Text).DisplayName`  
       `Office365Users.Manager(InfoAbout.Text).GivenName`  
       `Office365Users.Manager(InfoAbout.Text).Id`  
       `Office365Users.Manager(InfoAbout.Text).JobTitle`  
       `Office365Users.Manager(InfoAbout.Text).Mail`  
       `Office365Users.Manager(InfoAbout.Text).MailNickname`  
       `Office365Users.Manager(InfoAbout.Text).Surname`  
       `Office365Users.Manager(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.Manager(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.Manager(InfoAbout.Text).AccountEnabled`  

In der Bezeichnung werden die Informationen angezeigt, die Sie über den von Ihnen angegebenen Benutzer oder den Vorgesetzten dieses Benutzers eingegeben haben.

> [!NOTE]
> Wenn Sie eine App basierend auf einer Entität im Common Data Service entwickeln, können Sie einen Benutzer anhand der ID statt anhand der E-Mail-Adresse angeben.

Beispielsweise können Sie [eine App automatisch erstellen](../data-platform-create-app.md), einen Bildschirm hinzufügen, der ein **Label**-Steuerelement (Bezeichnung) enthält, und die **Text**-Eigenschaft des Steuerelements auf diese Formel festlegen:
<br>**Office365Users.UserProfile(BrowseGallery1.Selected.CreatedByUser).DisplayName**

Wenn Sie einen Kontakt erstellen und in der App diesen Kontakt im Bildschirm zum Durchsuchen auswählen, wird im **Label**-Steuerelement (Bezeichnung) der Anzeigename angezeigt.

### <a name="show-the-direct-reports-of-another-user"></a>Anzeigen der direkt unterstellten Mitarbeiter eines anderen Benutzers
1. Fügen Sie ein Texteingabe-Steuerelement hinzu (Menü **Insert** (Einfügen) > **Text** > **Text input**  (Texteingabe)), und benennen Sie es in **InfoAbout** um.
2. Geben Sie in **InfoAbout** die E-Mail-Adresse eines Benutzers in Ihrer Organisation ein. Geben Sie z. B. *NameIhresVorgesetzten*@*IhrUnternehmen.com* ein.
3. Fügen Sie einen Katalog **mit Text** hinzu (Menü **Insert** (Einfügen) > **Gallery** (Katalog)), und legen Sie dessen **[Items](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:

    `Office365Users.DirectReports(InfoAbout.Text)`

    Im Katalog werden Informationen zu den direkt unterstellten Mitarbeitern des von Ihnen eingegebenen Benutzers angezeigt.

    Wenn der Katalog ausgewählt ist, werden im rechten Bereich Optionen für diesen Katalog angezeigt.
4. Wählen Sie in der zweiten Liste **JobTitle** aus. Wählen Sie in der dritten Liste **DisplayName** aus. Der Katalog wird mit diesen Werten aktualisiert.  

> [!NOTE]
> Das erste Feld ist eigentlich eine Bildsteuerung. Wenn Sie über kein Bild verfügen, können Sie die Bildsteuerung löschen und stattdessen eine Bezeichnung hinzufügen. Unter [Hinzufügen und Konfigurieren von Steuerelementen](../add-configure-controls.md) finden Sie viele hilfreiche Informationen.

### <a name="search-for-users"></a>Nach Benutzern suchen
1. Fügen Sie ein Texteingabe-Steuerelement hinzu (Menü **Insert** (Einfügen) > **Text** > **Text input** (Texteingabe)), und benennen Sie es in **SearchTerm** um. Geben Sie einen zu suchenden Namen ein. Geben Sie beispielsweise Ihren Vornamen ein.
2. Fügen Sie einen Katalog **mit Text** hinzu (Menü **Insert** (Einfügen) > **Gallery** (Katalog)), und legen Sie dessen **[Items](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:

    `Office365Users.SearchUser({searchTerm: SearchTerm.Text})`

    Im Katalog werden Benutzer angezeigt, deren Name den von Ihnen eingegebenen Suchtext enthält.

    Wenn der Katalog ausgewählt ist, werden im rechten Bereich Optionen für diesen Katalog angezeigt.
3. Wählen Sie in der zweiten Liste **Mail** aus. Wählen Sie in der dritten Liste **DisplayName** aus.

    Die zweite und dritte Bezeichnung im Katalog werden aktualisiert.

## <a name="view-the-available-functions"></a>Anzeigen der verfügbaren Funktionen
Diese Verbindung umfasst die folgenden Funktionen:

| Funktionsname | Beschreibung |
| --- | --- |
| [MyProfile](connection-office365-users.md#myprofile) |Ruft das Profil für den aktuellen Benutzer ab. |
| [UserProfile](connection-office365-users.md#userprofile) |Ruft ein bestimmtes Benutzerprofil ab. |
| [Manager](connection-office365-users.md#manager) |Ruft das Benutzerprofil für den Vorgesetzten des angegebenen Benutzers ab. |
| [DirectReports](connection-office365-users.md#directreports) |Gibt die direkt unterstellten Mitarbeiter für den angegebenen Benutzer zurück. |
| [SearchUser](connection-office365-users.md#searchuser) |Ruft die Suchergebnisse von Benutzerprofilen ab. |

### <a name="myprofile"></a>MyProfile
Mein Profil abrufen: Ruft das Profil für den aktuellen Benutzer ab.

#### <a name="input-properties"></a>Eingabeeigenschaften
Keine

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Typ | Beschreibung |
| --- | --- | --- |
| Department |Zeichenfolge |Die Abteilung des Benutzers |
| DisplayName |Zeichenfolge |Der Anzeigename des Benutzers |
| GivenName |Zeichenfolge |Der Vorname des Benutzers |
| Id |Zeichenfolge |Die Benutzer-ID |
| JobTitle |Zeichenfolge |Die Position des Benutzers |
| Mail |Zeichenfolge |Die E-Mail-ID des Benutzers |
| MailNickname |Zeichenfolge |Der Spitzname des Benutzers |
| Surname |Zeichenfolge |Der Nachname des Benutzers |
| TelephoneNumber |Zeichenfolge |Die Telefonnummer des Benutzers |
| UserPrincipalName |Zeichenfolge |Der Benutzerprinzipalname |
| AccountEnabled |Boolesch |Flag für aktiviertes Konto |

### <a name="userprofile"></a>UserProfile
Benutzerprofil abrufen: Ruft ein bestimmtes Benutzerprofil ab.

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Id |Zeichenfolge |ja |Der Prinzipalname oder die E-Mail-ID des Benutzers |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Typ | Beschreibung |
| --- | --- | --- |
| Department |Zeichenfolge |Die Abteilung des Benutzers |
| DisplayName |Zeichenfolge |Der Anzeigename des Benutzers |
| GivenName |Zeichenfolge |Der Vorname des Benutzers |
| Id |Zeichenfolge |Die Benutzer-ID |
| JobTitle |Zeichenfolge |Die Position des Benutzers |
| Mail |Zeichenfolge |Die E-Mail-ID des Benutzers |
| MailNickname |Zeichenfolge |Der Spitzname des Benutzers |
| Surname |Zeichenfolge |Der Nachname des Benutzers |
| TelephoneNumber |Zeichenfolge |Die Telefonnummer des Benutzers |
| UserPrincipalName |Zeichenfolge |Der Benutzerprinzipalname |
| AccountEnabled |Boolesch |Flag für aktiviertes Konto |

### <a name="manager"></a>Manager
Vorgesetzten abrufen: Ruft das Benutzerprofil für den Vorgesetzten des angegebenen Benutzers ab.

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Id |Zeichenfolge |ja |Der Prinzipalname oder die E-Mail-ID des Benutzers |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Typ | Beschreibung |
| --- | --- | --- |
| Department |Zeichenfolge |Die Abteilung des Benutzers |
| DisplayName |Zeichenfolge |Der Anzeigename des Benutzers |
| GivenName |Zeichenfolge |Der Vorname des Benutzers |
| Id |Zeichenfolge |Die Benutzer-ID |
| JobTitle |Zeichenfolge |Die Position des Benutzers |
| Mail |Zeichenfolge |Die E-Mail-ID des Benutzers |
| MailNickname |Zeichenfolge |Der Spitzname des Benutzers |
| Surname |Zeichenfolge |Der Nachname des Benutzers |
| TelephoneNumber |Zeichenfolge |Die Telefonnummer des Benutzers |
| UserPrincipalName |Zeichenfolge |Der Benutzerprinzipalname |
| AccountEnabled |Boolesch |Flag für aktiviertes Konto |

### <a name="directreports"></a>DirectReports
Get direct reports (Direkt unterstellte Mitarbeiter abrufen): Ruft die direkt unterstellten Mitarbeiter ab.

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Id |Zeichenfolge |ja |Der Prinzipalname oder die E-Mail-ID des Benutzers |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Typ | Beschreibung |
| --- | --- | --- |
| Department |Zeichenfolge |Die Abteilung des Benutzers |
| DisplayName |Zeichenfolge |Der Anzeigename des Benutzers |
| GivenName |Zeichenfolge |Der Vorname des Benutzers |
| Id |Zeichenfolge |Die Benutzer-ID |
| JobTitle |Zeichenfolge |Die Position des Benutzers |
| Mail |Zeichenfolge |Die E-Mail-ID des Benutzers |
| MailNickname |Zeichenfolge |Der Spitzname des Benutzers |
| Surname |Zeichenfolge |Der Nachname des Benutzers |
| TelephoneNumber |Zeichenfolge |Die Telefonnummer des Benutzers |
| UserPrincipalName |Zeichenfolge |Der Benutzerprinzipalname |
| AccountEnabled |Boolesch |Flag für aktiviertes Konto |

### <a name="searchuser"></a>SearchUser
Search for users (Benutzer suchen): Ruft die Suchergebnisse von Benutzerprofilen ab.

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| searchTerm |Zeichenfolge |Nein |Suchzeichenfolge Gilt für: Anzeigename, Vorname, Nachname, E-Mail-ID, E-Mail Spitzname und Benutzerprinzipalname |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Typ | Beschreibung |
| --- | --- | --- |
| Department |Zeichenfolge |Die Abteilung des Benutzers |
| DisplayName |Zeichenfolge |Der Anzeigename des Benutzers |
| GivenName |Zeichenfolge |Der Vorname des Benutzers |
| Id |Zeichenfolge |Die Benutzer-ID |
| JobTitle |Zeichenfolge |Die Position des Benutzers |
| Mail |Zeichenfolge |Die E-Mail-ID des Benutzers |
| MailNickname |Zeichenfolge |Der Spitzname des Benutzers |
| Surname |Zeichenfolge |Der Nachname des Benutzers |
| TelephoneNumber |Zeichenfolge |Die Telefonnummer des Benutzers |
| UserPrincipalName |Zeichenfolge |Der Benutzerprinzipalname |
| AccountEnabled |Boolesch |Flag für aktiviertes Konto |

## <a name="helpful-links"></a>Nützliche Links
* Alle [verfügbaren Verbindungen](../connections-list.md).
* Erfahren Sie, wie Sie Ihren Apps [Verbindungen hinzufügen](../add-manage-connections.md).

