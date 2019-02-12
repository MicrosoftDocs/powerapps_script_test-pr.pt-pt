---
title: Hinzufügen von Listenfeldern, Dropdownlisten oder Optionsfeldern zu einer Canvas-App | Microsoft-Dokumentation
description: Erstellen oder Konfigurieren von Mehrfachauswahloptionen in einer Canvas-App in PowerApps
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/24/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 293c850c5af980a480a56cb9fb3b8c7866950580
ms.sourcegitcommit: c1f58a16f8dcd309a1d5fc4658ca16d82c615994
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2018
ms.locfileid: "49991744"
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons-to-a-canvas-app"></a>Hinzufügen eines Listenfelds, einer Dropdownliste oder eines Optionsfelds zu einer Canvas-App

Zeigen Sie eine einzelne Spalte mit Daten (z.B. aus einer Tabelle mit mehreren Spalten) in einer Canvas-App an, damit Benutzer ein oder mehrere Elemente in einer Liste auswählen können.

- Fügen Sie ein Listenfeld hinzu, um Benutzern die Auswahl von mehreren Optionen zu ermöglichen.
- Fügen Sie eine Dropdownliste hinzu, um den beanspruchten Platz auf einem Bildschirm zu reduzieren.
- Fügen Sie eine Gruppe von Optionsfeldern für einen bestimmten Designeffekt hinzu.

Dieses Thema bezieht sich zwar auf Listenfelder und Optionsfelder, die Prinzipien gelten jedoch auch für Dropdownlisten.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-simple-list"></a>Erstellen einer einfachen Liste

1. Fügen Sie ein Steuerelement vom Typ **Listenfeld** mit der Bezeichnung **MyListBox** hinzu, und legen Sie seine **Items**-Eigenschaft auf folgenden Ausdruck fest:

    ```["circle","triangle","rectangle"]```  <br/>

    Der Designer sieht nun etwa wie folgt aus:

    ![][4]

4. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole** aus, wählen Sie den Kreis aus, und verschieben Sie ihn unter **MyListBox**:

    ![][5]  

5. Fügen Sie ein Dreieck und ein Rechteck hinzu, und ordnen Sie die Formen unter **MyListBox** in einer Reihe an:

    ![][6]  

6. Legen Sie die **[Visible](controls/properties-core.md)**-Eigenschaft der folgenden Formen auf die genannten Funktionen fest:  

   | Form | Wert für Visible-Funktion |
   | --- | --- |
   | circle |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | triangle |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | rectangle |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. Wählen Sie bei gedrückter ALT-Taste eine oder mehrere Formen unter **MyListBox** aus.

    Nur die ausgewählte Form bzw. die ausgewählten Formen werden angezeigt.

In diesen Schritten haben Sie mithilfe eines Ausdrucks eine Liste von Elementen erstellt. Sie können diese Vorgehensweise auf andere Elemente im Unternehmen anwenden. Sie können mit einem Steuerelement vom Typ **Dropdownliste** beispielsweise Produktabbildungen, Produktbeschreibungen usw. anzeigen.

## <a name="add-radio-buttons"></a>Hinzufügen von Optionsfeldern
1. Klicken Sie erst auf der Registerkarte **Start** auf **Neuer Bildschirm** und anschließend auf **Leer**.

2. Wählen Sie auf der Registerkarte **Einfügen** die Option **Steuerelemente** und anschließend **Radio** aus.

    ![][10]  

3. Benennen Sie das **Radio**-Steuerelement in **Choices** um, und legen Sie seine **[Items](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    Ändern Sie ggf. die Größe des Steuerelements, um alle Optionen anzuzeigen.

4. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole** aus, und wählen Sie anschließend den Kreis aus.

5. Legen Sie die **[Fill](controls/properties-color-border.md)**-Eigenschaft des Kreises auf die folgende Funktion fest:  
   ```If(Choices.Selected.Value = "red", Red, Choices.Selected.Value = "green", Green, Choices.Selected.Value = "blue", Blue)```  

    In dieser Formel ändert der Kreis je nach ausgewähltem Optionsfeld seine Farbe.

6. Verschieben Sie den Kreis wie im folgenden Beispiel veranschaulicht unter das **Radio**-Steuerelement:

    ![][14]  

7. Wählen Sie bei gedrückter ALT-Taste ein anderes Optionsfeld aus, um die Farbe des Kreises ändern.

[1]: ./media/add-list-box-drop-down-list-radio-button/preview.png
[2]: ./media/add-list-box-drop-down-list-radio-button/listbox.png
[3]: ./media/add-list-box-drop-down-list-radio-button/renamelistbox.png
[4]: ./media/add-list-box-drop-down-list-radio-button/itemslistbox.png
[5]: ./media/add-list-box-drop-down-list-radio-button/circle.png
[6]: ./media/add-list-box-drop-down-list-radio-button/allshapes.png
[10]: ./media/add-list-box-drop-down-list-radio-button/radiobutton.png
[12]: ./media/add-list-box-drop-down-list-radio-button/itemsradio.png
[14]: ./media/add-list-box-drop-down-list-radio-button/radiocircle.png
[15]: ./media/add-list-box-drop-down-list-radio-button/dropdown.png
