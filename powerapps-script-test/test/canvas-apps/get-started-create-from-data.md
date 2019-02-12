---
title: Generieren einer Canvas-App aus Excel | Microsoft-Dokumentation
description: Verwenden von PowerApps zum automatischen Generieren einer Canvas-App mithilfe einer Excel-Datei, die in einem Cloudspeicherkonto gespeichert ist
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3d29387c907808f90225f1ff67257d289de2b0a9
ms.sourcegitcommit: 2300de0a0486187762f830068c872116d5b04c32
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806131"
---
# <a name="generate-a-canvas-app-from-excel-in-powerapps"></a>Generieren einer Canvas-App aus Excel in PowerApps

In diesem Artikel generieren Sie Ihre erste Canvas-App automatisch in PowerApps, indem Sie Daten aus einer Excel-Tabelle verwenden. Sie wählen eine Excel-Datei aus, generieren eine App und führen die generierte App dann aus. Jede generierte App enthält Bildschirme zum Durchsuchen von Datensätzen, Anzeigen von Details der Datensätze sowie zum Erstellen oder Aktualisieren von Datensätzen. Indem Sie eine App generieren, können Sie mithilfe von Excel-Daten schnell eine funktionierende App erstellen. Diese können Sie anschließend an Ihre Anforderungen anpassen. 

Die Excel-Datei muss sich in einem Cloudspeicherkonto (z.B. OneDrive, Google Drive oder Dropbox) befinden. In diesem Artikel wird „OneDrive for Business“ verwendet.

Wenn Sie nicht eine Lizenz für PowerApps verfügen, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Voraussetzungen

Laden Sie die Datei [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) in Excel herunter, und speichern Sie diese in Ihrem [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md), um diesem Artikel genau zu folgen.

> [!IMPORTANT]
> Sie können eine eigene Excel-Datei verwenden, dafür müssen die Daten jedoch als Tabelle formatiert sein. Weitere Informationen finden Sie unter [Format a table (Formatieren einer Tabelle)](how-to-excel-tips.md). 

## <a name="generate-the-app"></a>Generieren der App

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

1. Zeigen Sie unter **Eigene App erstellen** auf **Mit Daten beginnen**, und wählen Sie dann **Diese App erstellen** aus.

    ![Option zum Erstellen einer App](./media/get-started-create-from-data/start-from-data.png)

1. Klicken oder tippen Sie auf der Kachel für Ihr Cloudspeicherkonto unter **Von Ihren Daten ausgehen** auf **Smartphonelayout**.

    ![Option zum Erstellen einer App](./media/get-started-create-from-data/odfb-tile.png)

1. Wenn Sie dazu aufgefordert werden, klicken Sie auf **Verbinden**, und geben Sie Ihre Anmeldeinformationen für dieses Konto ein.

1. Navigieren Sie unter **Choose an Excel file** zu **FlooringEstimates.xlsx**, und klicken oder tippen Sie darauf. 

1. Klicken oder tippen Sie unter **Choose a table** auf **FlooringEstimates**, und klicken oder tippen Sie anschließend auf **Connect**.

    ![Option zum Erstellen einer App](./media/get-started-create-from-data/choose-table.png)

## <a name="run-the-app"></a>Ausführen der App

1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Klicken oder Tippen auf das Wiedergabe-Symbol in der Nähe der oberen rechten Ecke).

    ![Vorschau öffnen](./media/get-started-create-from-data/open-preview.png)

1. Ändern Sie die Sortierreihenfolge, indem Sie auf das Sortieren-Symbol in der oberen rechten Ecke klicken oder tippen.

    ![Sortieren-Symbol](./media/get-started-create-from-data/sort-icon.png)

1. Filtern Sie die Liste, indem Sie Zeichen in das Suchfeld eingeben und einfügen.

1. Klicken oder tippen Sie auf das Plussymbol, um einen Datensatz hinzuzufügen, fügen Sie beliebige Daten hinzu, und klicken oder tippen Sie dann auf das Häkchen, um die Änderungen zu speichern.

1. Klicken oder tippen Sie auf den Pfeil „Weiter“ des hinzugefügten Datensatzes. Klicken oder tippen Sie dann auf das Stiftsymbol, um den Datensatz zu bearbeiten. Aktualisieren Sie mindestens ein Feld, und klicken oder tippen Sie auf das Häkchen, um die Änderungen zu speichern.

1. Klicken oder tippen Sie auf den Pfeil „Weiter“ des hinzugefügten Datensatzes. Klicken oder tippen Sie dann auf das Stiftsymbol, um den Datensatz zu bearbeiten. Aktualisieren Sie mindestens ein Feld, und klicken oder tippen Sie auf das Symbol „Abbrechen“, um die Änderungen zu verwerfen.

1. Klicken oder tippen Sie auf den Pfeil „Weiter“ des hinzugefügten Datensatzes, und klicken oder tippen Sie dann auf das Papierkorbsymbol, um diesen Datensatz zu löschen.

## <a name="next-steps"></a>Nächste Schritte

Passen Sie den Standardbildschirm zum Durchsuchen an Ihre Anforderungen an. Sie können beispielsweise die Liste nach Produktname statt nach Kategorie sortieren und filtern.

> [!div class="nextstepaction"]
> [Anpassen des Standardbildschirms zum Durchsuchen](customize-layout-sharepoint.md)
