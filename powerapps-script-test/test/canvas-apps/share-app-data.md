---
title: Freigeben von Excel-Dateien, die von einer App verwendet werden | Microsoft-Dokumentation
description: Geben Sie Excel-Dateien in Dropbox, OneDrive und Google Drive frei. Benutzer können Dateien und Ordner bearbeiten und anzeigen.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/16/2016
ms.author: jamesol
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 65a828d33add99bbee086f24c3a4892abfaae048
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42853227"
---
# <a name="share-excel-data-used-by-your-app"></a>Freigeben von Excel-Daten, die von Ihrer App verwendet werden
Sie können Excel-Daten in einem [Cloudkonto](connections/cloud-storage-blob-connections.md) wie z.B. OneDrive für Ihre App-Benutzer freigeben.

Beispielsweise können Sie eine App erstellen, die die Namen und Telefonnummern der Gruppe für den technischen Support in Ihrem Unternehmen anzeigt. Die Informationen werden in einem Excel-Arbeitsblatt gespeichert, das Sie in einem Ordner in Dropbox platzieren. Anschließend können Sie den Ordner für Ihre App-Benutzer freigeben, sodass sie die Namen und Telefonnummern anzeigen können.

Sie müssen die Daten freigeben, damit Benutzer Ihre App ausführen und sogar ändern können. Benutzer ohne Freigabeberechtigungen können die Daten in der Excel-Datei nicht anzeigen.

In diesem Thema wird gezeigt, wie Sie Daten in einem Excel-Arbeitsblatt unter Verwendung von Dropbox, OneDrive und Google Drive freigeben. Informationen zum Erstellen einer App, die Daten aus einer Excel-Datei anzeigt, finden Sie unter [Erstellen einer App aus einem Satz an Daten](get-started-create-from-data.md).

## <a name="share-data-in-dropbox"></a>Freigeben von Daten in Dropbox
1. Melden Sie sich unter Verwendung desselben Kontos bei Dropbox an, mit dem Sie eine Verbindung zwischen PowerApps und Dropbox hergestellt haben.
2. Wählen Sie den Ordner aus, der die Excel-Datei enthält, und wählen dann **Freigeben** aus:  
   
    ![Befehl zum Freigeben](./media/share-app-data/dropbox-share.png)
3. Geben Sie im Dialogfeld die E-Mail-Adressen ein, mit denen sich Ihre App-Benutzer bei Dropbox anmelden.  
   
    ![Freigabe in Dropbox](./media/share-app-data/dropbox-perms.png)
4. Wenn Ihre App-Benutzer Daten in Ihrer App hinzufügen, ändern oder löschen dürfen, wählen Sie **Kann bearbeiten** aus. Wählen Sie andernfalls **Kann anzeigen** aus.
5. Wählen Sie **Freigeben** aus.

Weitere Informationen finden Sie unter [Freigeben von Ordnern in Dropbox](https://www.dropbox.com/en/help/19).

## <a name="share-data-in-onedrive"></a>Freigeben von Daten in OneDrive
1. Melden Sie sich unter Verwendung desselben Kontos bei OneDrive an, mit dem Sie eine Verbindung zwischen PowerApps und OneDrive hergestellt haben.
2. Wählen Sie den Ordner aus, der die Datei enthält, und wählen dann **Freigeben** aus:  
   
    ![Befehl zum Freigeben](./media/share-app-data/onedrive-share.png)
   
    > [!NOTE]
   > Geben Sie in OneDrive for Business die Datei selbst und nicht den Ordner frei, der die Datei enthält.
3. Wählen Sie im Dialogfeld **E-Mail** aus.
   
    ![Freigabe per E-Mail](./media/share-app-data/onedrive-email.png)
4. Geben Sie die E-Mail-Adressen an, mit denen Ihre App-Benutzer sich bei OneDrive anmelden, und wählen Sie dann **Freigeben** aus.  
   
    ![Angeben eines Benutzers](./media/share-app-data/onedrive-perms.png)

Weitere Informationen finden Sie unter [Freigeben von OneDrive-Dateien und -Ordnern](https://support.office.com/article/Share-OneDrive-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07).

## <a name="share-data-in-google-drive"></a>Freigeben von Daten in Google Drive
1. Melden Sie sich unter Verwendung desselben Kontos bei Google Drive an, mit dem Sie eine Verbindung zwischen PowerApps und Google Drive hergestellt haben.
2. Klicken Sie mit der rechten Maustaste auf den Ordner, der Ihre Excel-Datei enthält, und wählen Sie **Freigeben** aus.  
   
    ![Befehl zum Freigeben](./media/share-app-data/googledrive-share.png)
3. Geben Sie im Dialogfeld die E-Mail-Adressen ein, mit denen sich Ihre App-Benutzer bei Google Drive anmelden:  
   
    ![Angeben eines Benutzers](./media/share-app-data/googledrive-perms.png)
4. Wenn Ihre App-Benutzer Daten in Ihrer App hinzufügen, ändern oder löschen dürfen, wählen Sie **Kann bearbeiten** in der Liste der Berechtigungen aus. Wählen Sie andernfalls **Kann anzeigen** aus.
5. Wählen Sie **Fertig** aus.

Weitere Informationen finden Sie unter [Freigeben von Google Drive-Dateien und -Ordnern](https://support.google.com/drive/answer/2494822).

### <a name="known-limitations"></a>Bekannte Einschränkungen
Weitere Informationen zum Freigeben von Excel-Daten in Ihrer Organisation erhalten Sie in diesen [Ausführungen zu Einschränkungen](connections/cloud-storage-blob-connections.md#known-limitations).

