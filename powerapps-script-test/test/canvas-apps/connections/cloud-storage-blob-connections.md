---
title: Übersicht über die Cloudspeicherverbindung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit einem Cloudspeicherkonto herstellen und Excel-Daten in Ihrer App anzeigen können
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 10a6178c63495b929eb6e5885ded9394b31a11ef
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42850164"
---
# <a name="connect-to-cloud-storage-from-powerapps"></a>Herstellen einer Verbindung mit Cloudspeicher aus PowerApps
PowerApps bietet mehrere Cloudspeicherverbindungen. Bei Verwendung einer dieser Verbindungen können Sie eine Excel-Datei speichern und die darin enthaltenen Informationen in Ihrer gesamten App nutzen. Hierzu zählen folgende Verbindungen:  

| **Azure Blob** | **Box** | **Dropbox** | **Google Drive** | **OneDrive** | **OneDrive<br> for Business** |
| --- | --- | --- | --- | --- | --- |
| ![Symbol](./media/cloud-storage-blob-connections/blobicon.png) |![API-Symbol][boxicon] |![API-Symbol][dropboxicon] |![API-Symbol][googledriveicon] |![API-Symbol][onedriveicon] |![API-Symbol][onedriveforbusinessicon] |

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

* Eine Excel-Datei, deren Daten [als Tabelle formatiert](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664) sind:
  
  1. Öffnen Sie die Excel-Datei, und wählen Sie eine beliebige Zelle in den zu verwendenden Daten aus.
  2. Wählen Sie auf der Registerkarte **Einfügen** die Option **Tabelle** aus.
  3. Aktivieren Sie im Dialogfeld **Speichern als Tabelle** das Kontrollkästchen **Tabelle hat Kopfzeilen**, und wählen Sie anschließend **OK** aus.
  4. Speichern Sie die Änderungen.

## <a name="connect-to-the-cloud-storage-connection"></a>Verbindung mit der Cloudspeicherverbindung herstellen
1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) den Knoten **Verwalten**, und wählen Sie **Verbindungen** aus:  
   
    ![Auswählen der Verbindungen](./media/cloud-storage-blob-connections/connections.png)
2. Wählen Sie **Neue Verbindung** aus, und wählen Sie Ihre Cloudspeicherverbindung aus. Wählen Sie beispielsweise **OneDrive** aus.
3. Sie werden aufgefordert, Benutzername und Kennwort für Ihr Cloudspeicherkonto anzugeben. Geben Sie diese ein, und wählen Sie anschließend **Anmelden** aus:  
    ![Benutzername und Kennwort eingeben](./media/cloud-storage-blob-connections/signin.png)
   
    Sobald Sie angemeldet sind, kann diese Verbindung in Ihren Apps verwendet werden.
4. Klicken oder tippen Sie in der App im Menüband auf der Registerkarte **Ansicht** auf **Datenquellen**. Klicken oder tippen Sie im rechten Bereich auf **Datenquelle hinzufügen**, klicken oder tippen Sie auf Ihre Cloudspeicherverbindung, und wählen Sie anschließend die Excel-Tabelle aus.
5. Wählen Sie **Verbinden** aus.
   
    Die Tabelle wird als Datenquelle aufgelistet:
   
    ![Auswählen der Excel-Tabelle](./media/cloud-storage-blob-connections/selecttable.png)
   
    > [!NOTE]
   > Beachten Sie, dass die Excel-Daten als Tabelle formatiert sein müssen.

## <a name="using-the-excel-data-in-your-app"></a>Verwenden von Excel-Daten in der App
1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Katalog** aus, und wählen Sie anschließend ein Katalogsteuerelement **Mit Text** aus.
2. Legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf Ihre Excel-Tabelle fest. Wenn die Excel-Tabelle beispielsweise **Table1** heißt, legen Sie sie auf „Table1“ fest:  
   
    ![Items-Eigenschaft](./media/cloud-storage-blob-connections/itemsproperty.png)  
   
    Der Katalog wird automatisch mit Informationen aus der Excel-Tabelle aktualisiert.
3. Wählen Sie im Katalog das zweite oder dritte **Label**-Steuerelement (Bezeichnung) aus. Sie stellen fest, dass die **Text**-Eigenschaft der zweiten und der dritten Bezeichnung in der Standardeinstellung automatisch auf `ThisItem.something` festgelegt ist. Die können diese Bezeichnungen auf jede Spalte in Ihrer Tabelle festlegen.
   
    Im folgenden Beispiel ist die zweite Bezeichnung auf `ThisItem.Name` und die dritte Bezeichnung auf `ThisItem.Notes` festgelegt:  
   
    ![Zweite Bezeichnung](./media/cloud-storage-blob-connections/items-secondtextbox.png)  
   
    ![Dritte Bezeichnung](./media/cloud-storage-blob-connections/items-thirdtextbox.png)  
   
    Beispielausgabe:  
    ![Zweite und dritte Bezeichnung](./media/cloud-storage-blob-connections/secondthirdtextboxes.png)
   
> [!NOTE]
> Das erste Feld ist eigentlich eine Bildsteuerung. Wenn Sie über kein Bild in der Excel-Tabelle verfügen, können Sie das Bildsteuerelement löschen und an dessen Stelle eine Bezeichnung hinzufügen. Unter [Hinzufügen und Konfigurieren von Steuerelementen](../add-configure-controls.md) finden Sie viele hilfreiche Informationen.

In [Grundlegendes zu Tabellen und Datensätzen](../working-with-tables.md) finden Sie weitere Einzelheiten und einige Beispiele.  

## <a name="sharing-your-app"></a>Freigeben der App
Sie können [Ihre App](../share-app.md), [Ihre Ressourcen](../share-app-resources.md) (z.B. Connectors) und [Ihre Daten](../share-app-data.md) für andere Personen in der Organisation freigeben.

Wenn Sie einen Ordner in Dropbox freigeben, muss der freigegebene Ordner dem Dropbox-Konto des Benutzers zugeordnet sein.

Es gibt [bestimmte Einschränkungen](#sharing-excel-tables) für Connectors im Zusammenhang mit Excel-Dateien.

## <a name="known-limitations"></a>Bekannte Einschränkungen
Wenn Sie versuchen, eine Excel-Verbindung in der App zu verwenden und die Meldung **Datentyp nicht unterstützt** oder **Nicht als Tabelle formatiert** angezeigt wird, [formatieren Sie die Daten als Tabelle](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).

Wenn die Excel-Daten eine berechnete Spalte enthalten, können Sie anhand der Daten keine App erstellen, und die Daten können keiner vorhandenen App hinzugefügt werden.

### <a name="sharing-excel-tables"></a>Freigeben von Excel-Tabellen
So geben Sie Daten in einer Excel-Datei frei

* Geben Sie in OneDrive for Business die Datei selbst frei.
* Geben Sie in OneDrive den Ordner frei, der die Datei enthält, und geben Sie für Medien Dateipfade und keine URLs an.
* Geben Sie in Dropbox oder Google Drive entweder die Datei oder den Ordner frei.

## <a name="helpful-links"></a>Nützliche Links
Alle [verfügbaren Verbindungen](../connections-list.md).  
Erfahren Sie, wie Sie Ihren Apps [Verbindungen hinzufügen](../add-manage-connections.md) und [eine Datenquelle hinzufügen](../add-data-connection.md).  
Informieren Sie sich in [Grundlegendes zu Tabellen und Datensätzen](../working-with-tables.md) über tabellarische Datenquellen.  
Weitere Ressourcen zu Katalogen sind u.a. [Eine Liste mit Elementen anzeigen](../add-gallery.md) und [Bilder und Text in einem Katalog anzeigen](../show-images-text-gallery-sort-filter.md).

<!--Icon references-->
[boxicon]: ./media/cloud-storage-blob-connections/boxicon.png
[dropboxicon]: ./media/cloud-storage-blob-connections/dropboxicon.png
[googledriveicon]: ./media/cloud-storage-blob-connections/googledriveicon.png
[onedriveicon]: ./media/cloud-storage-blob-connections/onedriveicon.png
[onedriveforbusinessicon]: ./media/cloud-storage-blob-connections/onedriveforbusinessicon.png
