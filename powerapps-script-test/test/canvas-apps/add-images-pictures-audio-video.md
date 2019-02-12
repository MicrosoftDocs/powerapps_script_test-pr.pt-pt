---
title: Einbetten von Multimediadateien in einer Canvas-App und Hochladen der App | Microsoft-Dokumentation
description: Anzeigen von Multimediadateien in einer Canvas-App und Hochladen in eine Datenquelle
author: karthik-1
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/12/2017
ms.author: sharik
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 99bdf6f3a71fe9a7f5003449017c70c1f5a73d09
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42857703"
---
# <a name="using-multimedia-files-in-powerapps"></a>Verwenden von Multimediadateien in PowerApps

In diesem Artikel wird erläutert, wie Sie Multimediadateien in Ihre Canvas-App einbetten, Stiftzeichnungen in eine Datenquelle hochladen und Bilder aus einer Datenquelle in der Canvas-App anzeigen. Die in diesem Artikel verwendete Datenquelle ist eine Excel-Datei in OneDrive for Business.

## <a name="prerequisites"></a>Voraussetzungen

[Registrieren Sie sich für PowerApps](../signup-for-powerapps.md), und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen eingeben, die Sie bei der Registrierung angegeben haben.

## <a name="add-media-from-a-file-or-the-cloud"></a>Hinzufügen von Medien aus einer Datei oder aus der Cloud

Zum Hochladen können Sie eine beliebige Art von Mediendatei auswählen (z.B. Bilder, Video oder Audio).

1. Wählen Sie auf der Registerkarte **Inhalt** die Option **Medien** aus.

2. Wählen Sie unter **Medien** **Bilder**, **Videos** oder **Audio** aus, und wählen Sie anschließend **Durchsuchen** aus:

    ![Durchsuchen von Medien][1]

3. Wählen Sie die hinzuzufügende Datei aus, und wählen Sie dann **Öffnen** aus.

    Der Ordner **Bilder** auf dem Computer wird geöffnet, und Sie können dort ein Bild auswählen oder zu einem anderen Ordner navigieren.

4. Wenn Sie die gewünschten Dateien hinzugefügt haben, drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.

5. Wählen Sie auf der Registerkarte **Einfügen** **Medien** aus, und wählen Sie anschließend **Bild**, **Video** oder **Audio** aus:

    ![Auswählen des Medientyps][8]

6. Wenn Sie ein Bild-Steuerelement hinzugefügt haben, legen Sie dessen **[Image](controls/properties-visual.md)**-Eigenschaft auf die hinzugefügte Datei fest:  

    ![Festlegen der Image-Eigenschaft](./media/add-images-pictures-audio-video/imageproperty.png)

    > [!NOTE]
   > Geben Sie nur den Dateinamen ohne Erweiterung an, und schließen Sie diesen in einfache Anführungszeichen ein.

7. Wenn Sie ein Video- oder Audio-Steuerelement hinzugefügt haben, legen Sie dessen **Media**-Eigenschaft auf die hinzugefügte Datei fest:  

    ![Festlegen der Media-Eigenschaft](./media/add-images-pictures-audio-video/mediaproperty.png)

    > [!NOTE]
   > Geben Sie ein YouTube-Video wieder, indem Sie die **Media**-Eigenschaft eines Videosteuerelements auf die entsprechende URL festlegen, die in doppelte Anführungszeichen eingeschlossen werden muss.

## <a name="add-media-from-azure-media-services"></a>Hinzufügen von Medien aus Azure Media Services
1. Laden Sie in Ihrem Azure Media Services-Konto über **AMS > Einstellungen > Medienobjekte** Ihr Videomedienobjekt hoch, und veröffentlichen Sie es.

2. Nachdem das Video veröffentlicht wurde, kopieren Sie seine URL.

3. Fügen Sie in PowerApps über **Einfügen > Medien** das **Video**-Steuerelement hinzu.

4. Legen Sie die **Media**-Eigenschaft der URL fest, die Sie kopiert haben.

    Wie in dieser Abbildung gezeigt, können Sie jede Streaming-URL auswählen, die von Azure Media Services unterstützt wird:

    ![Festlegen der Media-Eigenschaft](./media/add-images-pictures-audio-video/ams-with-powerapps.png)

## <a name="add-images-from-the-cloud-to-your-app"></a>Hinzufügen von Bildern aus der Cloud zur App
In diesem Szenario speichern Sie Bilder in einem Cloudspeicherkonto (OneDrive for Business). Sie verwenden eine Excel-Tabelle, in der der Pfad zu den Bildern enthalten ist, und Sie zeigen die Bilder in einem Katalog-Steuerelement in der App an.

In diesem Szenario wird die Datei [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) verwendet, die einige JPEG-Dateien enthält.

> [!NOTE]
> Im Pfad zu diesen Bildern in der Excel-Datei müssen Schrägstriche verwendet werden. Werden Pfade zu Bildern von PowerApps in einer Excel-Tabelle gespeichert, werden im Pfad umgekehrte Schrägstriche verwendet. Wenn Sie Pfade zu Bildern aus einer solchen Tabelle verwenden, ändern Sie die Pfade in der Excel-Tabelle so, dass anstelle der umgekehrten Schrägstriche normale Schrägstriche verwendet werden. Andernfalls werden die Bilder nicht angezeigt.  

1. Laden Sie die Datei [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) herunter, und extrahieren Sie den Ordner **Assets** in Ihr Cloud-Speicherkonto.

2. Benennen Sie den Ordner **Assets** in **Assets_images** um.

3. Erstellen Sie in einem Excel-Arbeitsblatt eine Tabelle mit einer Spalte, und füllen Sie diese mit den folgenden Daten:

    ![Tabelle „Jackets“](./media/add-images-pictures-audio-video/jackets.png)

4. Benennen Sie die Tabelle **Jackets**, und benennen Sie die Excel-Datei **Assets.xlsx**.

5. Fügen Sie in der App die Tabelle **Jackets** als Datenquelle hinzu.  

6. Fügen Sie ein **Nur-Bild**-Steuerelement hinzu (**Einfügen** Registerkarte > **Katalog**), und legen Sie dessen **Items**-Eigenschaft auf `Jackets` fest:  

    ![Items-Eigenschaft](./media/add-images-pictures-audio-video/items-jackets.png)

    Der Katalog wird automatisch mit den Bildern aktualisiert:  

    ![Bilder aus „Jackets“](./media/add-images-pictures-audio-video/images.png)

    Wenn Sie die **Items**-Eigenschaft festlegen, wird der Excel-Tabelle automatisch die Spalte **PowerAppsId** hinzugefügt.

    In der Excel-Tabelle kann der Pfad zu den Bildern ebenfalls eine Bild-URL sein. Ein Beispiel ist die Beispieldatei [Flooring Estimates](http://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx). Sie können sie in Ihr Cloud-Speicherkonto herunterladen, die Tabelle `FlooringEstimates` als Datenquelle in der App hinzufügen und anschließend das Katalog-Steuerelement auf `FlooringEstimates` festlegen. Der Katalog wird automatisch mit den Bildern aktualisiert.

## <a name="upload-pen-drawings-to-the-cloud"></a>Hochladen von Stiftzeichnungen in die Cloud
In diesem Szenario erfahren Sie, wie Sie Stiftzeichnungen in Ihre Datenquelle (OneDrive for Business) hochladen und wie die Zeichnungen dort gespeichert werden.

1. Fügen Sie in Excel Zelle A1 **Image [Bild]** hinzu.

2. Erstellen Sie eine Tabelle, indem Sie folgende Schritte durchführen:    

   1. Wählen Sie Zelle A1 aus.

   2. Wählen Sie im Menüband **Einfügen** **Tabelle** aus.

   3. Aktivieren Sie im Dialogfeld das Kontrollkästchen **Meine Tabelle hat Überschriften**, und wählen Sie anschließend **OK** aus.

       ![Erstellen einer Tabelle](./media/add-images-pictures-audio-video/create-table.png)

       Die Excel-Datei liegt nun im Tabellenformat vor. Weitere Informationen zum Formatieren von Tabellen im Excel-Format finden Sie unter [Daten als Tabelle formatieren](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370).

   4. Benennen Sie die Tabelle **Drawings**:

       ![Umbenennen der Tabelle in „Drawings“](./media/add-images-pictures-audio-video/name-media-table.png)

3. Speichern Sie die Excel-Datei in OneDrive for Business unter dem Namen **SavePen.xlsx**.

4. Erstellen Sie in PowerApps eine [leere App](get-started-create-from-blank.md).

5. Fügen Sie in der App das OneDrive for Business-Konto als [Datenquelle](add-data-connection.md) hinzu:

   1. Klicken oder tippen Sie auf die Registerkarte **Ansicht**, und klicken oder tippen Sie anschließend auf **Datenquellen**.

       ![](./media/add-images-pictures-audio-video/choose-data-sources.png)

   2. Klicken oder tippen Sie auf **Datenquelle hinzufügen**, und tippen oder klicken Sie auf **OneDrive for Business**.

       ![](./media/add-images-pictures-audio-video/select-source.png)

   3. Klicken oder tippen Sie auf **SavePen.xlsx**.

   4. Wählen Sie die Tabelle **Drawings** aus, und klicken oder tippen Sie auf **Verbinden**.

       ![Verbinden](./media/add-images-pictures-audio-video/savepen.png)  

       Nun wird die Tabelle „Drawings“ als Datenquelle aufgelistet.

6. Wählen Sie auf der Registerkarte **Einfügen** die Option **Text** aus, und wählen Sie anschließend **Stifteingabe** aus.

7. Benennen Sie das neue Steuerelement **MyPen**:  

    ![Umbenennen](./media/add-images-pictures-audio-video/rename-mypen.png)

8. Fügen Sie auf der Registerkarte **Einfügen** ein **Schaltflächen**-Steuerelement hinzu, und legen Sie dessen **OnSelect**-Eigenschaft auf diese Formel fest:

    **Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})**

9. Fügen Sie ein **Bildkatalog**-Steuerelement hinzu (Registerkarte **Einfügen** > **Katalog**), und legen Sie dessen **Items**-Eigenschaft auf `Drawings` fest. Die **Image**-Eigenschaft des Katalog-Steuerelements wird automatisch auf `ThisItem.Image` festgelegt.

    Ordnen Sie die Steuerelemente so an, dass Ihr Bildschirm dem Folgenden ähnelt:  

    ![Beispielbildschirm](./media/add-images-pictures-audio-video/screen.png)

10. Drücken Sie F5, oder wählen Sie die Vorschau ( ![Vorschauschaltfläche](./media/add-images-pictures-audio-video/preview.png) ).

11. Zeichnen Sie ein Element im MyPen, und wählen Sie dann die Schaltfläche aus.

    Das erste Bild im Katalog-Steuerelement enthält Ihre soeben erstellte Zeichnung.

12. Bearbeiten Sie die Zeichnung weiter, und wählen Sie die Schaltfläche aus.

    Das zweite Bild im Katalog-Steuerelement enthält die soeben erstellte Zeichnung.

13. Schließen Sie das Vorschaufenster, indem Sie ESC drücken.

    In Ihrem Cloud-Speicherkonto wurde automatisch der Ordner **SavePen_images** erstellt. Dieser Ordner enthält die gespeicherten Bilder sowie die IDs für deren Dateinamen. Zum Anzeigen des Ordners müssen Sie u.U. das Browserfenster aktualisieren, indem Sie beispielsweise F5 drücken.

    In der Datei **SavePen.xlsx** wird in der Spalte **Image** der Pfad zu den neuen Bildern angegeben.

### <a name="known-limitations"></a>Bekannte Einschränkungen
Weitere Informationen zum Freigeben von Excel-Daten in Ihrer Organisation erhalten Sie in diesen [Ausführungen zu Einschränkungen](connections/cloud-storage-blob-connections.md#known-limitations).

## <a name="for-more-information"></a>Weitere Informationen
Testen Sie Ihre App unbedingt auf verschiedenen Plattformen, u.a. in einem [Browserfenster](https://home.dynamics.com/) und auf einem Smartphone.

Informationen zu komplexeren Szenarien, bei denen Multimediadaten direkt in eine andere Datenquelle hochgeladen werden, finden Sie unter [Profi-Tipps für die Bilderfassung](https://powerapps.microsoft.com/blog/image-capture-pro-tips/) und [Benutzerdefinierte Connectors für das Hochladen von Bildern](https://powerapps.microsoft.com/blog/custom-api-for-image-upload/).

Eine weitere Möglichkeit zum Hochladen von Dateien in eine Datenquelle besteht darin, die [Patch](functions/function-patch.md)-Funktion zu verwenden.

[1]: ./media/add-images-pictures-audio-video/add-image-video-audio-file.png
[3]: ./media/add-images-pictures-audio-video/add-intro-sound.png
[4]: ./media/add-images-pictures-audio-video/add-picture.png
[5]: ./media/add-images-pictures-audio-video/camera-gallery.png
[6]: ./media/add-images-pictures-audio-video/audio-gallery.png
[7]: ./media/add-images-pictures-audio-video/pen-gallery.png
[8]: ./media/add-images-pictures-audio-video/mediaoptions.png
[9]: ./media/add-images-pictures-audio-video/imageproperty.png
[10]: ./media/add-images-pictures-audio-video/mediaproperty.png
[11]: ./media/add-images-pictures-audio-video/renamecamera.png
