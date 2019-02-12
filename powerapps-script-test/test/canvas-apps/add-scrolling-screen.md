---
title: Hinzufügen eines Scrollbildschirms zu einer Canvas-App | Microsoft-Dokumentation
description: Erstellen Sie in PowerApps einen Bildschirm, durch den Benutzer scrollen können, um mehr Inhaltstypen anzuzeigen als auf einem Bildschirm in einer Canvas-App angezeigt werden können.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7094c42c8b070095d08d33a276785cce36933407
ms.sourcegitcommit: 6851486b8a44d76b6d87837952b7a7f38a8752b6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/18/2018
ms.locfileid: "53570280"
---
# <a name="add-a-scrolling-screen-to-a-canvas-app-in-powerapps"></a>Hinzufügen eines Scrollbildschirms zu einer Canvas-App in PowerApps

Erstellen Sie in einer Canvas-App einen Bildschirm, durch den Benutzer scrollen können, um andere Elemente anzuzeigen. Erstellen Sie z.B. eine Smartphone-App, die Daten in mehreren Diagrammen anzeigt, die Benutzer durch Scrollen anzeigen können.

Wenn Sie in einem Abschnitt mehrere Steuerelemente hinzufügen, bleibt die relative Position der Steuerelemente im Abschnitt erhalten, wobei es keine Rolle spielt, ob es sich um eine Smartphone-App oder eine Tablet-App handelt. Beachten Sie, dass sich Bildschirmgröße und -ausrichtung auf die Anordnung der Abschnitte auswirken können.  

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-scrolling-screen"></a>Erstellen eines Scrollbildschirms

1. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Neuer Bildschirm**:

    ![Option zum Hinzufügen eines Bildschirms zu einer App][1]

2. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Layouts**, und klicken oder tippen Sie anschließend auf die Option zum Erstellen eines unendlichen Scrolling-Zeichenbereichs:  
   
    ![Option zum Hinzufügen eines unendlichen Scrolling-Zeichenbereichs][2]
   
    Dem Zeichenbereich wird Folgendes hinzugefügt:  
   
    ![Ein Bildschirm mit einem unendlichen Scrolling-Zeichenbereich in seiner Standarddarstellung][3]

## <a name="add-elements"></a>Hinzufügen von Elementen
Fügen wir dem Zeichenbereich nun einige Steuerelemente hinzu, um die Funktionsweise des Scrollbildschirms zu veranschaulichen.

1. Klicken oder tippen Sie im hinzugefügten Zeichenbereich auf **Ein Element von der Registerkarte „Einfügen“ hinzufügen**.
   
    ![][4]
2. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Diagramme**, und klicken oder tippen Sie anschließend auf **Säulendiagramm**.
   
    ![Option zum Hinzufügen eines Säulendiagramms][5]
   
    Ein Säulendiagramm wird in der ersten Karte auf dem Bildschirm angezeigt:  
   
    ![Standardmäßiges Säulendiagramm][7]
3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Text**, und klicken oder tippen Sie anschließend auf **Stifteingabe**:  
   
    ![Option zum Hinzufügen eines Stift-Steuerelements][8]
4. Verschieben Sie das Stift-Steuerelement unter das Diagramm, und ändern Sie die Größe des Steuerelements so, dass es den unteren Rand der Karte bedeckt:  
   
    ![Stift-Steuerelement verschieben und dessen Größe ändern][9]

## <a name="add-a-section"></a>Hinzufügen eines Abschnitts
Nun fügen wir eine weitere Karte mit einem weiteren Steuerelement hinzu.

1. Klicken oder tippen Sie am unteren Rand des Bildschirms auf **Abschnitt hinzufügen**:  
   
    ![Option zum Hinzufügen eines Abschnitts][10]
   
    Dem Bildschirm wird eine neue Karte hinzugefügt:  
   
    ![Neue Karte unter dem Standardabschnitt][11]
2. Wechseln Sie bei ausgewählter Karte zur Registerkarte **Einfügen**, klicken oder tippen Sie auf **Diagramme**, und klicken oder tippen Sie anschließend auf **Liniendiagramm**.
   
    Das neue Diagramm ist zu groß, um gemeinsam mit den anderen Steuerelementen auf dem Bildschirm angezeigt zu werden:  
   
    ![Am unteren Rand der neuen Karte hinzugefügtes Liniendiagramm][12]
3. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Klicken oder Tippen des Wiedergabe-Symbols in der Nähe der oberen rechten Ecke).
   
    ![Öffnen des Vorschaumodus](./media/add-scrolling-screen/open-preview.png)
4. Scrollen Sie nach unten, um das neue Liniendiagramm anzuzeigen.  
   
    ![Vorschau des Liniendiagramms][13]

[1]: ./media/add-scrolling-screen/add-screen.png
[2]: ./media/add-scrolling-screen/add-canvas.png
[3]: ./media/add-scrolling-screen/default-canvas.png
[4]: ./media/add-scrolling-screen/insert-visual.png
[5]: ./media/add-scrolling-screen/add-chart.png
[7]: ./media/add-scrolling-screen/default-chart.png
[8]: ./media/add-scrolling-screen/add-pen.png
[9]: ./media/add-scrolling-screen/move-resize-pen.png
[10]: ./media/add-scrolling-screen/add-section.png
[11]: ./media/add-scrolling-screen/new-card.png
[12]: ./media/add-scrolling-screen/add-line-chart.png
[13]: ./media/add-scrolling-screen/line-chart-preview.png
