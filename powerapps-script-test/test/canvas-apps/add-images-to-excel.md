---
title: Hinzufügen von Bildern zu Excel | Microsoft-Dokumentation
description: Schrittweise Anleitung zum Hinzufügen von Bilddateien und Stiftzeichnungen zu Excel in einem Cloudspeicherkonto
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/25/2016
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 89b05b5e1e8073b082e73564f744b7b85fc70426
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863940"
---
# <a name="add-images-to-excel-from-powerapps"></a>Hinzufügen von Bildern aus PowerApps zu Excel
Erstellen Sie automatisch eine App, in der Benutzer Bilder aus Dateien oder Zeichnungen mit einem **Stift**-Steuerelement anzeigen, hinzufügen oder löschen können. Die App basiert auf einer Excel-Datei, die Sie erstellen und in ein Cloudspeicherkonto hochladen.

## <a name="prerequisites"></a>Voraussetzungen

* Sie müssen mit dem [Hinzufügen und Konfigurieren von Steuerelementen](add-configure-controls.md) vertraut sein.
* Sie müssen mit dem [Konfigurieren von Excel-Daten als Tabelle](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370?ui=en-US&rs=en-US&ad=US) vertraut sein.
* Eine [PowerApps-Verbindung](add-data-connection.md) mit einem Cloudspeicherkonto (wie Dropbox, OneDrive oder Google Drive), in dem eine Excel-Datei gespeichert werden kann.

## <a name="create-the-data-source-and-the-app"></a>Erstellen der Datenquelle und der App
1. Fügen Sie in Excel in zwei beliebigen nebeneinanderliegenden Zellen (z.B. A1 und B1) **Caption** und **Image [image]** hinzu, die sich direkt über zwei leeren Zellen befinden.
2. Formatieren Sie die aktualisierten Zellen und die direkt darunter liegenden Zellen als Tabelle, und benennen Sie die Tabelle (z.B. **Images**).
   
    ![Erstellen einer Tabelle](./media/add-images-to-excel/create-table.png)
3. Speichern Sie die Datei (z.B. unter dem Namen **ImageDemo**), und laden Sie sie in Ihr Cloudspeicherkonto hoch.
4. Klicken oder tippen Sie in PowerApps im Menü **Datei** auf die Option **Neu** (am linken Rand, wenn Sie noch keine App geöffnet haben), und klicken oder tippen Sie anschließend auf **Telefonlayout** in der Kachel für Ihr Cloudspeicherkonto.
   
    ![Auswählen des Cloudspeicherkontos](./media/add-images-to-excel/select-account.png)
5. Klicken oder tippen Sie unter **Excel-Datei auswählen** auf die erstellte Datei.
   
    ![Auswählen der Arbeitsmappe](./media/add-images-to-excel/select-workbook.png)
6. Klicken oder tippen Sie unter **Tabelle auswählen** auf die erstellte Tabelle und anschließend auf **Verbinden**.
   
    ![Auswählen der Tabelle](./media/add-images-to-excel/select-table.png)
7. Wenn die Schnelleinführung angezeigt wird, sehen Sie sich diese an, oder klicken oder tippen Sie auf **Überspringen**.
   
    ![Erster Bildschirm der Schnelleinführung](./media/add-images-to-excel/quick-tour.png)

## <a name="add-an-image-from-a-file"></a>Hinzufügen eines Bilds aus einer Datei
1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Klicken oder Tippen der Schaltfläche „Wiedergabe“ rechts oben). Klicken oder tippen Sie anschließend auf das Pluszeichen rechts oben.
   
    ![Pluszeichen](./media/add-images-to-excel/plus-icon.png)
2. Geben oder fügen Sie im Feld **Caption** eine kurze Beschreibung der hinzuzufügenden Bilddatei ein, und klicken oder tippen Sie darunter, um die Datei anzugeben.
3. Navigieren Sie im Dialogfeld **Öffnen** zu der Datei, die hinzugefügt werden soll, klicken oder tippen Sie darauf, und klicken oder tippen Sie anschließend auf **Öffnen**.
   
    ![Hinzufügen der Beschriftung und des Bilds](./media/add-images-to-excel/add-image.png)
4. Klicken oder tippen Sie auf das Häkchen in der oberen rechten Ecke, um die vorgenommenen Änderungen zu speichern.
   
    ![Änderungen speichern](./media/add-images-to-excel/checkmark-icon.png)
5. Sie können beliebig viele Bilder hinzufügen, indem Sie die letzten drei Schritte erneut ausführen; drücken Sie anschließend ESC, um zum Standardarbeitsbereich zurückzukehren.
6. (Optional) Löschen Sie die **Label**-Steuerelemente (Bezeichnung) mit der Beschriftung für die einzelnen Bilder.

## <a name="add-a-drawing"></a>Hinzufügen einer Zeichnung
1. Zeigen Sie **EditScreen1** an, indem Sie in der linken Navigationsleiste darauf klicken oder tippen. Klicken oder tippen Sie anschließend auf die Bildkarte, um sie auszuwählen.
   
    ![Auswählen der Bildkarte](./media/add-images-to-excel/select-card.png)
2. Klicken oder tippen Sie im rechten Bereich auf die Kartenauswahl für das Bild, und klicken oder tippen Sie anschließend auf **Notizen hinzufügen**.
   
    ![Hinzufügen von Notizen](./media/add-images-to-excel/add-notes.png)
3. Zeigen Sie **BrowseScreen1** an, indem Sie in der linken Navigationsleiste darauf klicken oder tippen, und öffnen Sie anschließend den Vorschaumodus.
4. Klicken oder tippen Sie auf das Pluszeichen in der oberen rechten Ecke, fügen Sie eine Beschriftung hinzu, und zeichnen Sie im **Stift**-Steuerelement ein Bild.
   
    ![Zeichnen eines Bilds](./media/add-images-to-excel/draw-picture.png)
5. Klicken oder tippen Sie auf das Häkchen in der oberen rechten Ecke, um die vorgenommenen Änderungen zu speichern.
   
    ![Änderungen speichern](./media/add-images-to-excel/checkmark-icon.png)
6. Sie können beliebig viele Zeichnungen hinzufügen, indem Sie die letzten zwei Schritte erneut ausführen; drücken Sie anschließend ESC, um zum Standardarbeitsbereich zurückzukehren.

