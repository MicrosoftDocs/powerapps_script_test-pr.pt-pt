---
title: Erstellen eines Diagramms in einer Canvas-App | Microsoft-Dokumentation
description: Anzeigen von Datenkategorien als Linien-, Kreis- oder Balkendiagramme in einer Canvas-App in PowerApps
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/23/2016
ms.author: lonu
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 142bb0e19fb8b9647c1808dcca10e781c4f69d4a
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862033"
---
# <a name="show-data-in-a-line-pie-or-bar-chart-in-powerapps"></a>Anzeigen von Daten in einem Linien-, Kreis- oder Balkendiagramm in PowerApps

Verwenden Sie Linien-, Kreis- und Balkendiagramme, um Ihre Daten in einer Canvas-App anzuzeigen. Beim Arbeiten mit Diagrammen sollten die Daten, die Sie importieren, nach folgenden Kriterien gegliedert sein:

* Jede Reihe sollte in der ersten Zeile stehen.
* Bezeichnungen sollten in der am weitesten links stehenden Spalte zu finden sein.

Ihre Daten sollten z.B. wie folgt aussehen:

![][9]

Sie können diese Diagramme in PowerApps erstellen und verwenden. Lassen Sie uns loslegen!

## <a name="prerequisites"></a>Voraussetzungen

* [Registrieren Sie sich für PowerApps](../signup-for-powerapps.md), und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen eingeben, die Sie bei der Registrierung angegeben haben.
* Erstellen Sie eine App aus einer [Vorlage](get-started-test-drive.md), aus [Daten](get-started-create-from-data.md) oder [von Grund auf neu](get-started-create-from-blank.md).
* Erfahren Sie, wie Sie [ein Steuerelement](add-configure-controls.md) in PowerApps konfigurieren.
* Laden Sie [ChartData.zip](http://pwrappssamples.blob.core.windows.net/samples/ChartData.zip) herunter, die Beispieldaten als XML-Datei enthält. Führen Sie die Schritte in diesem Thema aus, um sie direkt in Ihre App zu importieren. Dekomprimieren Sie alternativ die ZIP-Datei, öffnen Sie die XML-Datei in Excel, und speichern Sie es in ein [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md).

## <a name="import-the-sample-data"></a>Importieren der Beispieldaten
In den folgenden Schritten importieren wir die Beispieldaten in eine Sammlung mit dem Namen **ProductRevenue**.

1. Wählen Sie auf der Registerkarte **Insert** (Einfügen) die Option **Controls** (Steuerelemente) und anschließend **Import** (Importieren) aus.  

    ![][11]  

2. Legen Sie die Eigenschaft **[OnSelect](controls/properties-core.md)** des Steuerelements auf die folgende Funktion fest:  

   ```Collect(ProductRevenue, Import1.Data)```

3. Drücken Sie F5 zum Öffnen des Vorschaumodus, und wählen Sie anschließend die Schaltfläche **Daten importieren** aus.

4. Wählen Sie im Dialogfeld **Öffnen** „ChartData.zip“ und **Öffnen** aus. Drücken Sie anschließend ESC.

5. Wählen Sie im Menü **Datei** **Sammlungen** aus.

    Die Sammlung „ProductRevenue“ wird zusammen mit den Diagrammdaten aufgeführt, die Sie importiert haben:

    ![][1]  

   > [!NOTE]
   > Das Import-Steuerelement wird zum Importieren von Excel-ähnlichen Daten und zum Erstellen der Sammlung verwendet. Das Importsteuerelement importiert Daten, wenn Sie Ihre App erstellen und eine Vorschau der App anzeigen. Das Import-Steuerelement importiert derzeit keine Daten, wenn Sie Ihre App veröffentlichen.
   >

6. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.

## <a name="add-a-pie-chart"></a>Hinzufügen eines Kreisdiagramms
1. Wählen Sie auf der Registerkarte **Einfügen** **Diagramme** und anschließend **Kreisdiagramm** aus.

2. Verschieben Sie das Kreisdiagramm unter die Schaltfläche **Daten importieren**.

3. Wählen Sie im Kreisdiagramm-Steuerelement die Mitte des Kreisdiagramms aus:   

    ![][10]

4. Legen Sie die Eigenschaft **[Elemente](controls/properties-core.md)** des Kreisdiagramms auf diesen Ausdruck fest: `ProductRevenue.Revenue2014`

    ![][2]  

    Das Kreisdiagramm zeigt die Umsatzdaten von 2014.

    ![][3]  

## <a name="add-a-bar-chart-to-display-your-data"></a>Hinzufügen eines Balkendiagramms zum Anzeigen Ihrer Daten
Jetzt nutzen wir die Sammlung „ProductRevenue“ in einem Balkendiagramm:

1. Fügen Sie auf der Registerkarte **Startseite** einen Bildschirm hinzu.

2. Wählen Sie auf der Registerkarte **Einfügen** **Diagramme** und anschließend **Säulendiagramm** aus.

3. Wählen Sie die Mitte des Säulendiagramms aus. Legen Sie die Eigenschaft **[Elemente](controls/properties-core.md)** des Säulendiagramms auf ```ProductRevenue``` fest:

    ![][12]  

    Das Säulendiagramm zeigt die Umsatzdaten von 2012:

    ![][4]  

4. Wählen Sie im Säulendiagramm das Quadrat in der Mitte aus:

    ![][5]

5. Wählen Sie auf der Registerkarte **Diagramm** die **Anzahl der Reihen** aus, und geben Sie anschließend **3** in die Bearbeitungsleiste ein:

    ![][6]  

    Das Säulendiagramm zeigt die Umsatzdaten jedes Produkts aus drei Jahren an:

    ![][7]  

[1]: ./media/use-line-pie-bar-chart/productrevenuecollection.png
[2]: ./media/use-line-pie-bar-chart/itemsexpression.png
[3]: ./media/use-line-pie-bar-chart/piechart.png
[4]: ./media/use-line-pie-bar-chart/columnchart.png
[5]: ./media/use-line-pie-bar-chart/columnchartseries.png
[6]: ./media/use-line-pie-bar-chart/columnchartseriesfunction.png
[7]: ./media/use-line-pie-bar-chart/columnchartthreeyears.png
[8]: ./media/use-line-pie-bar-chart/preview.png
[9]: ./media/use-line-pie-bar-chart/tableformat.png
[10]: ./media/use-line-pie-bar-chart/middlepiechart.png
[11]: ./media/use-line-pie-bar-chart/import.png
[12]: ./media/use-line-pie-bar-chart/itemscolumnchart.png
