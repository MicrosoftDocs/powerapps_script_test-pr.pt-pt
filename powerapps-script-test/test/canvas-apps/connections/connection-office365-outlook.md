---
title: Übersicht über die Verbindung mit Office 365 Outlook | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Beispiele, für die Office 365 Outlook-Verbindung mit PowerApps
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/20/2017
ms.author: lanced
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4f22f55b3c64d38cc274b0b69d8e7799c1a24f60
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833492"
---
# <a name="connect-to-office-365-outlook-from-powerapps"></a>Herstellen einer Verbindung mit Office 365 Outlook aus PowerApps
![Office 365 Outlook](./media/connection-office365-outlook/office365icon.png)

Wenn Sie eine Verbindung mit Office 365 Outlook herstellen, können Sie E-Mail-Nachrichten anzeigen, senden, löschen und beantworten sowie weitere Aufgaben ausführen.

Sie können Steuerelemente hinzufügen, um diese Funktionen in Ihrer App auszuführen. Sie können beispielsweise **Texteingabe**-Steuerelemente hinzufügen, mit denen der Empfänger, der Betreff und der Text der E-Mail abgefragt werden, sowie ein **Schaltflächen**-Steuerelement, um die E-Mail zu senden.

In diesem Thema wird gezeigt, wie Sie Office 365 als Verbindung hinzufügen, Office 365 Ihrer App als Datenquelle hinzufügen und wie Sie die Daten in verschiedenen Steuerelementen verwenden.

> [!IMPORTANT]
> Zum Zeitpunkt der Veröffentlichung dieses Artikels werden für den Kalender keine wiederkehrenden Ereignisse unterstützt.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-office-365-outlook"></a>Herstellen einer Verbindung mit Office 365 Outlook
1. [Fügen Sie eine Datenverbindung hinzu](../add-data-connection.md), und wählen Sie **Office 365 Outlook** aus:  
   
    ![Herstellen einer Verbindung mit Office 365](./media/connection-office365-outlook/add-office.png)
2. Wählen Sie **Verbinden** aus, und wenn Sie aufgefordert werden, sich anzumelden, geben Sie Ihr Geschäftskonto ein.

Die Office 365 Outlook-Verbindung wurde erstellt und Ihrer App hinzugefügt. Sie kann jetzt verwendet werden.

## <a name="show-messages"></a>Anzeigen von Nachrichten
1. Wählen Sie im Menü **Einfügen** die Option **Katalog** aus, und fügen Sie einen der **Textkataloge** hinzu.
2. Legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft auf den folgenden Ausdruck fest:  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    Das Katalog-Steuerelement wird automatisch mit einigen Ihrer E-Mails aufgefüllt.
3. Legen Sie im Katalog die **Text**-Eigenschaft der ersten Bezeichnung auf `ThisItem.From` fest. Legen Sie die zweite Bezeichnung auf `ThisItem.Subject` fest. Legen Sie die dritte Bezeichnung auf `ThisItem.Body` fest. Sie können auch die Größe der Bezeichnungen ändern.
   
    Das Katalog-Steuerelement wird automatisch mit den neuen Eigenschaften aktualisiert.
4. Für diese Funktion sind verschiedene optionale Parameter verfügbar. Legen Sie die **Items**-Eigenschaft des Katalogs auf eine der folgenden Formeln fest:
   
    `Office365.GetEmails({fetchOnlyUnread:false})`  
    `Office365.GetEmails({fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2, searchQuery:"powerapps"})`  
    `Office365.GetEmails({folderPath:"Deleted Items", fetchOnlyUnread:false, top:2, skip:3})`

## <a name="send-a-message"></a>Senden einer Nachricht
1. Klicken Sie im Menü **Insert** (Einfügen) auf **Text**, und wählen Sie dann **Texteingabe** (Texteingabe) aus.
2. Wiederholen Sie den vorherigen Schritt zwei weitere Male, sodass Sie über drei Felder verfügen, und ordnen Sie diese in einer Spalte an:  
   
    ![Drei Felder in einer Spalte](./media/connection-office365-outlook/threetextinput.png)
3. Benennen Sie die Steuerelemente wie folgt um:  
   
   * **inputTo**
   * **inputSubject**
   * **inputBody**
4. Wählen Sie im Menü **Einfügen** die Option **Steuerelemente** und anschließend **Schaltfläche** aus. Legen Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:  
   
    `Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text)`
5. Verschieben Sie die Schaltfläche, sodass sie unter den anderen Steuerelementen angezeigt wird, und legen Sie ihre **[Text](../controls/properties-core.md)**-Eigenschaft auf **"Send email"** fest.
6. Drücken Sie F5, oder wählen Sie die Vorschauschaltfläche (![Vorschauschaltfläche](./media/connection-office365-outlook/preview.png)) aus. Geben Sie eine gültige E-Mail-Adresse in **inputTo** ein, und geben Sie in den anderen beiden **Texteingabe**-Steuerelementen beliebigen Text ein.
7. Wählen Sie **end email** aus, um die Nachricht zu senden. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.

## <a name="send-a-message-with-an-attachment"></a>Senden einer Nachricht mit einem Anhang
Sie können beispielsweise eine App erstellen, in der der Benutzer Bilder mit der Kamera des Geräts aufzeichnet und diese als Anhänge sendet. Benutzer können zudem viele weitere Dateitypen an eine E-Mail-App anhängen.

Führen Sie die Schritte im vorhergehenden Abschnitt aus, um einer Nachricht einen Anhang hinzuzufügen. Fügen Sie dabei jedoch einen Parameter hinzu, um einen Anhang anzugeben (beim Festlegen der **OnSelect**-Eigenschaft der Schaltfläche). Dieser Parameter ist als Tabelle strukturiert, in der Sie für jeden Anhang bis zu drei Eigenschaften angeben können:

* Name
* ContentBytes
* @odata.type

> [!NOTE]
> Sie können die @odata.type-Eigenschaft nur für einen Anhang angeben, und Sie können sie auf eine leere Zeichenfolge festlegen.

In diesem Beispiel wird ein Foto als **file1.jpg** gesendet:

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""})})`

In diesem Beispiel wird zusätzlich zum Foto eine Audiodatei gesendet:

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""}, {Name:"AudioFile", ContentBytes:microphone1.audio })})`

## <a name="delete-a-message"></a>Löschen einer Nachricht
1. Wählen Sie im Menü **Einfügen** die Option **Katalog** aus, und fügen Sie einen der **Textkataloge** hinzu.
2. Legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft auf den folgenden Ausdruck fest:  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    Das Katalog-Steuerelement wird automatisch mit einigen Ihrer E-Mails aufgefüllt.
3. Legen Sie im Katalog die **Text**-Eigenschaft der ersten Bezeichnung auf `ThisItem.Id` fest. Legen Sie die zweite Bezeichnung auf `ThisItem.Subject` fest. Legen Sie die dritte Bezeichnung auf `ThisItem.Body` fest.
4. Wählen Sie die erste Bezeichnung im Katalog aus, und benennen Sie sie in **EmailID** um:
   
    ![Erste Bezeichnung umbenennen](./media/connection-office365-outlook/renameheading.png)
5. Wählen Sie die dritte Bezeichnung im Katalog aus, und fügen Sie eine **Schaltfläche** hinzu (Menü **Einfügen**). Legen Sie die **OnSelect**-Eigenschaft der Schaltfläche auf die folgende Formel fest:  
   
    `Office365.DeleteEmail(EmailID.Text)`
6. Drücken Sie F5, oder wählen Sie die Vorschauschaltfläche aus (![Vorschauschaltfläche](./media/connection-office365-outlook/preview.png)). Wählen Sie eine der E-Mails in Ihrem Katalog aus, und klicken Sie auf die Schaltfläche. 
    
    > [!NOTE]
    > Hierdurch werden die ausgewählten E-Mails aus dem Posteingang gelöscht. Vergewissern Sie sich daher, dass Sie die richtigen E-Mails auswählen.
7. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.

## <a name="mark-a-message-as-read"></a>Markieren einer Nachricht als gelesen
In diesem Abschnitt werden die gleichen Steuerelemente verwendet wie unter [Löschen einer Nachricht](connection-office365-outlook.md#delete-a-message).

1. Legen Sie die **OnSelect**-Eigenschaft der Schaltfläche auf die folgende Formel fest:  
   
    `Office365.MarkAsRead(EmailID.Text)`
2. Drücken Sie F5, oder wählen Sie die Vorschauschaltfläche aus (![Vorschauschaltfläche](./media/connection-office365-outlook/preview.png)). Wählen Sie eine ungelesene E-Mail aus, und klicken Sie auf die Schaltfläche.
3. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.

## <a name="helpful-links"></a>Nützliche Links
* Eine Liste aller Funktionen und der zugehörigen Parameter finden Sie in der [Referenz zu Office 365 Outlook](https://docs.microsoft.com/connectors/office365connector/).
* Alle [verfügbaren Verbindungen](../connections-list.md).  
* Informieren Sie sich über das [Verwalten von Verbindungen](../add-manage-connections.md).

