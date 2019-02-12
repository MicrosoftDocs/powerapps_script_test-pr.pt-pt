---
title: Speichern von Bildern in einer Excel-Datei | Microsoft-Dokumentation
description: So speichern Sie ein Bild in einer Excel-Tabelle in einem Cloudspeicherkonto
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/15/2016
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48b8da1fbe328eb8834a58b7c052e8d4bd6a8151
ms.sourcegitcommit: c1f58a16f8dcd309a1d5fc4658ca16d82c615994
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2018
ms.locfileid: "42852365"
---
# <a name="how-to-save-images-in-an-excel-file-and-then-add-these-images-to-your-app"></a>So speichern Sie Bilder in einer Excel-Datei und fügen diese Bilder anschließend zu Ihrer App hinzu

In diesem Tutorial werden wir:

* Eine Excel-Datei erstellen und sie als Tabelle formatieren
* Eine Verbindung mit OneDrive for Business erstellen. Jedes Cloudspeicherkonto wird funktionieren. In dieser exemplarischen Vorgehensweise wird OneDrive for Business verwendet.
* Eine App mit einem Stifteingabe-Steuerelement erstellen
* Die aus dem Stifteingabe-Steuerelement erstellten Bilder in eine Excel-Datei speichern
* Bilder aus einer Excel-Datei in Ihrer App anzeigen

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]
* Erfahren Sie, wie Sie [eine Datenquelle hinzufügen](add-data-connection.md)

## <a name="create-the-excel-file-as-a-table"></a>Erstellen der Excel-Datei als Tabelle

1. Benennen Sie eine Spalte in einer leeren Excel-Datei mit **Bild [image]**.
2. Erstellen Sie eine Tabelle, indem Sie folgende Schritte durchführen:    
   
   1. Wählen Sie eine bestimmte Dateneinheit in einer Zeile und einer beliebigen Spalte. Wählen Sie beispielsweise **Bild** aus.
   2. Wählen Sie im Menüband **Einfügen** **Tabelle** aus.
   3. Wählen Sie im Dialogfenster **Meine Tabelle hat Überschriften** und **OK** aus.
      
      Die Excel-Datei liegt nun im Tabellenformat vor. Weitere Informationen über das Formatieren einer Tabelle in Excel finden Sie unter [Formatieren einer Excel-Tabelle](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370).
   4. Benennen Sie die Tabelle **Zeichnungen**:  
      
      ![Tabelle in „Zeichnungen“ umbenennen](./media/tutorial-working-with-images-in-excel/drawings-table.png)
3. Benennen Sie die Excel-Datei **SavePen.xlsx**, und speichern Sie die Datei in Ihr Cloudspeicherkonto (OneDrive for Business, Dropbox usw.).

## <a name="create-an-app-with-the-pen-control"></a>Erstellen einer App mit dem Stift-Steuerelement
1. Erstellen Sie in PowerApps eine [leere App](get-started-create-from-blank.md).
2. Fügen Sie in Ihrer App das Cloudspeicherkonto als eine [Datenquelle](add-data-connection.md) hinzu. Nachdem dies geschehen ist, fügen Sie **SavePen.xlsx** als Verbindung hinzu, und wählen Sie anschließend die Tabelle **Zeichnungen** aus:  
   ![Verbinden](./media/tutorial-working-with-images-in-excel/savepen.png)  
   
   Nun wird die Tabelle „Zeichnungen“ als Datenquelle aufgelistet.
3. Wählen Sie im Menü **Einfügen** **Text** und anschließend **Stifteingabe** aus. Benennen Sie sie in **MyPen** um:  
   
   ![Umbenennen](./media/tutorial-working-with-images-in-excel/rename-mypen.png)
4. Fügen Sie ein Steuerelement **Schaltfläche** (Menü **Einfügen**) hinzu, und legen Sie dessen Eigenschaft **OnSelect** auf die folgende Formel fest:  
   `Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})`
5. Fügen Sie ein Steuerelement **Bildkatalog** (Menü **Einfügen** > **Katalog**) hinzu, und legen Sie dessen Eigenschaft **Elemente** auf `Drawings` fest. Die Eigenschaft **Image** des Katalog-Steuerelements wird automatisch auf `ThisItem.Image` festgelegt.
   
   Ihr Bildschirm sollte etwa wie folgt aussehen:  
   
   ![Beispielbildschirm](./media/tutorial-working-with-images-in-excel/screen.png)  
6. Drücken Sie F5, oder wählen Sie die Vorschau (![](./media/tutorial-working-with-images-in-excel/preview.png)) aus. Zeichnen Sie ein Element im MyPen, und wählen Sie anschließend die Schaltfläche aus. Das erste Bild im Katalog-Steuerelement enthält Ihre soeben erstellte Zeichnung. Bearbeiten Sie die Zeichnung weiter, und wählen Sie die Schaltfläche aus. Das zweite Bild im Katalog-Steuerelement enthält die soeben erstellte Zeichnung.
   
   Schließen Sie das Vorschaufenster.
7. Navigieren Sie zu Ihrem Cloudspeicherkonto. Es gibt einen neuen Order **SavePen_images**, der automatisch erstellt wird. Sie müssen möglicherweise aktualisieren, um den neuen Ordner zu sehen. Dieser Ordner enthält die gespeicherten Bilder sowie die IDs für deren Dateinamen.
   
    Öffnen Sie „SavePen.xlsx“. Die Bilderspalte enthält den Pfad zu diesen neuen Bilder.

## <a name="add-the-image-in-an-excel-file-to-your-app"></a>Fügen Sie das Bild in einer Excel-Datei Ihrer App hinzu.
Sie können z.B. Bilder in einem Cloudspeicherkonto speichern und anschließend eine Excel-Tabelle zum Anzeigen der Bilder in Ihrer App verwenden.

In diesem Beispiel wird die Datei [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) verwendet, die einige JPEG-Dateien enthält.

> [!NOTE]
> Zum Anzeigen von Bildern aus einer Excel-Datei muss der Pfad zu diesen Bilder Schrägstriche verwenden. Wenn (wie bei den vorherigen Schritten) PowerApps Bilder für eine Excel-Tabelle speichert, verwendet der Pfad umgekehrte Schrägstriche. Daher können Sie auch **SavePen_images** aus dem vorherigen Beispiel verwenden. Wenn Sie dies tun, ändern Sie die Pfade in der Excel-Tabelle so, dass anstelle der umgekehrten Schrägstriche normale Schrägstriche verwendet werden. Andernfalls werden die Bilder nicht angezeigt werden.  

1. Laden Sie die Datei [CreateFirstApp.zip](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) herunter, und extrahieren Sie den Ordner **Ressourcen** in Ihr Cloudspeicherkonto.
2. Erstellen Sie in einem Excel-Arbeitsblatt eine Tabelle, die in etwa wie folgt aussieht:
   
    ![Tabelle „Jackets“](./media/tutorial-working-with-images-in-excel/jackets.png)
3. Benennen Sie die Tabelle **Jacken**. Benennen Sie die Excel-Datei **Assets.xlsx**. Sie können den Ordner **Ressourcen** auch in **Assets_images** umbenennen.
4. Fügen Sie in der App die Tabelle **Jacken** als Datenquelle hinzu.  
5. Fügen Sie ein Steuerelement **Image only**(Nur Image) hinzu (Menü **Einfügen** > **Katalog**), und legen Sie dessen Eigenschaft **Elemente** auf `Jackets` fest:  
   
    ![Items-Eigenschaft](./media/tutorial-working-with-images-in-excel/items-jackets.png)
   
    Der Katalog wird automatisch mit den Bildern aktualisiert:  
   
    ![Bilder „Jacken“](./media/tutorial-working-with-images-in-excel/images.png)

Wenn Sie die Eigenschaft Items festlegen, wird die Excel-Tabelle automatisch mit der neuen Spalte **PowerAppsId** aktualisiert.

In der Excel-Tabelle kann der Pfad zu den Bildern ebenfalls eine Bild-URL sein. Laden Sie die Beispieldatei [Flooring Estimates](http://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx)(Flooring Estimates) in Ihr Cloudspeicherkonto herunter, fügen Sie die Tabelle `FlooringEstimates` als Datenquelle in der App hinzu und legen Sie anschließend das Katalog-Steuerelement auf `FlooringEstimates` fest. Der Katalog wird automatisch mit den Bildern aktualisiert.

## <a name="learn-more"></a>Weitere Informationen
[Add an image, a video, or a sound (Fügen Sie ein Bild, ein Video oder einen Sound hinzu)](add-images-pictures-audio-video.md)  
[Show data in a line, pie, or bar chart in your app (Anzeigen von Daten in einem Linien-, Kreis- oder Balkendiagramm in Ihrer App)](use-line-pie-bar-chart.md)  
[Understand tables and records in PowerApps (Grundlegendes zu Tabellen und Datensätzen in PowerApps)](working-with-tables.md)

