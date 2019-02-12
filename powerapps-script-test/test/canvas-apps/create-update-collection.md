---
title: Erstellen und Aktualisieren einer Sammlung | Microsoft-Dokumentation
description: Erstellen von Sammlungen und Hinzufügen von Spalten zu vorhandenen Sammlungen in PowerApps
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/30/2015
ms.author: lonu
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c1043d32fc4ab4213d2ac2e690ef69e13fec8ed3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42831647"
---
# <a name="create-and-update-a-collection-in-your-app"></a>Erstellen und Aktualisieren einer Sammlung in Ihrer App
Verwenden Sie eine Sammlung zum Speichern von Daten, die in Ihrer App verwendet werden können. Eine Sammlung ist eine Gruppe von ähnlichen Elementen. Erstellen Sie beispielsweise eine MyImages-Sammlung mit den Abbildungen aller Produkte, die Ihr Unternehmen verkauft. In PowerApps können Sie Ihre MyImages-Sammlung hinzufügen und eine App erstellen, in der alle Abbildungen dieser Produkte angezeigt werden. Sie können aber z.B. auch eine PriceList-Sammlung erstellen, die die Produkte und Preise für jedes Produkt enthält.

### <a name="prerequisites"></a>Voraussetzungen
* [Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.
* Erstellen Sie eine App, oder öffnen Sie eine vorhandene App in PowerApps.
* Erfahren Sie, wie Sie [ein Steuerelement](add-configure-controls.md) in PowerApps konfigurieren.
* Bei diesem Vorgang wird die Datei [PriceList.zip](http://pwrappssamples.blob.core.windows.net/samples/PriceList.zip) als Eingabebeispiel verwendet. Die ZIP-Datei enthält eine XML-Datei, die in Excel konvertiert werden kann. Andernfalls liest PowerApps die Dateien in den ZIP-Dateien automatisch und importiert sie erfolgreich. Sie können diese Beispieldaten herunterladen und verwenden oder eigene Daten importieren.

## <a name="create-a-single-column-collection"></a>Erstellen einer Sammlung mit einer einzigen Spalte
Verwenden Sie die Funktion **Collect**, um eine Sammlung zu erstellen und ihr Elemente hinzuzufügen.

1. Wählen Sie in der App auf der Registerkarte **Einfügen** die Option **Text** und dann **Texteingabe** aus.

   ![][1]

1. Wählen Sie in der oberen linken Ecke **Text1** aus, und benennen Sie das Steuerelement in **Destination** (Ziel) um:

   ![][2]

1. Wählen Sie auf der Registerkarte**Insert** (Einfügen) die Option **Button** (Schaltfläche), um Ihrem Designer ein Schaltflächen-Steuerelement hinzuzufügen. In der Dropdown-Liste wird die Eigenschaft **[OnSelect](controls/properties-core.md)** aufgeführt. Legen Sie sie auf die folgende Funktion fest:  
   
    ```Collect(Destinations, Destination!Text)```
   
    Es sollte wie folgt aussehen:

    ![][3]

5. Wählen Sie den Text der Schaltfläche, und geben Sie **Add** (Hinzufügen) ein:

   ![][5]

1. Wählen Sie die Schaltfläche **Add** (Hinzufügen) aus, und verschieben Sie sie unter Ihr Text-Steuerelement. Sie können sie an eine beliebige Stelle verschieben:  
   ![][6]

In diesem Vorgang haben Sie die Collect-Funktion verwendet, um eine Sammlung mit dem Namen **Destinations** (Ziele) zu erstellen. Außerdem haben Sie ein Schaltflächen-Steuerelement hinzugefügt, das bei Auswahl dieser Option Ihrer Sammlung neue Elemente hinzufügt. Sehen Sie sich an, was Sie erstellt haben:

1. Wählen Sie die Vorschau:  
   ![][7]  
2. Geben Sie einen Namen für die Stadt in das Feld ein, und wählen Sie anschließend die Schaltfläche **Add** (Hinzufügen) aus.
3. Geben Sie weitere Städtenamen ein, und wählen Sie jedes Mal die Schaltfläche **Add** (Hinzufügen) aus.
4. Drücken Sie die **ESC**-Taste, um das Vorschaufenster zu schließen.
5. Sehen Sie sich jetzt die Destinations-Sammlung an und welche Textwerte Sie eingegeben haben. Wählen Sie auf der Registerkarte **File** (Datei) die Option **Collection** (Sammlung) aus. Der von Ihnen eingegebene Text wird aufgeführt:  
   ![][8]

#### <a name="extra-credit"></a>Bonus
Jetzt verbinden wir die Destinations-Sammlung mit einem Listenfeld:

1. Wechseln Sie in den Designer zurück.
2. Wählen Sie auf der Registerkarte **Insert** (Einfügen) die Option **Controls** (Steuerelemente) und anschließend **Listbox** (Listenfeld) aus:  
   ![][22]  
3. Verschieben Sie das Listenfeld so, dass es problemlos angezeigt werden kann. Legen Sie seine **[Items](controls/properties-core.md)**-Eigenschaft auf den folgenden Ausdruck fest:  
   ```Destinations!Value```  <br/>
   
    Wenn Sie dies tun, wird das Listenfeld automatisch mit den Elementen aufgefüllt, die Sie zuvor in der Destinations-Sammlung eingegeben haben:  
   ![][4]  

Zeigen Sie die Änderungen mithilfe der Vorschau an: ![][7] Im Listenfeld sehen Sie die verschiedenen Städte, die Sie eingegeben haben. Geben Sie im Texteingabe-Steuerelement eine neue Stadt ein, und wählen Sie die Schaltfläche **Add** (Hinzufügen) aus. Das Listenfeld wird automatisch mit der von Ihnen eingegebenen neuen Stadt aktualisiert.

## <a name="create-a-multi-column-collection"></a>Erstellen einer Sammlung mit mehreren Spalten
Die folgenden Schritte zeigen Ihnen, wie Sie mithilfe der Collect-Funktion in Ihrer App eine Sammlung erstellen und ihr mehrere Spalten hinzufügen.

1. Öffnen Sie auf der Registerkarte **Home** einen neuen Bildschirm.
2. Wählen Sie auf der Registerkarte **Insert** (Einfügen) die Option **Text** und anschließend **Input Text** (Texteingabe) aus.
3. Benennen Sie das Text-Steuerelement in **City** (Stadt) um:  
   ![][9]  
4. Fügen Sie ein weiteres Texteingabe-Steuerelement ein, und benennen Sie es in **States** (Bundesstaaten) um.
5. Verschieben Sie die Steuerelemente „City“ und „States“ und Bundesstaaten so, dass sie beide angezeigt werden können:  
   ![][10]  
   
    > [!NOTE]
   > Sie können „Text Input“ durch Begriffe wie „City“ oder „States“ ersetzen, wie aus der Abbildung ersichtlich.  
6. Wählen Sie auf der Registerkarte **Insert** (Einfügen) die Option **Button** (Schaltfläche) aus. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Funktion fest:  
   ```Collect(Destinations, {Cities:City!Text, States:States!Text})```  
   
    Es sollte wie folgt aussehen:  
    ![][11]  
   
    > [!NOTE]
   > Mit dieser Funktion können Sie der Sammlung auch zusätzliche Spalten hinzufügen. Beispielsweise können Sie für „Country“ (Land) ein weiteres Texteingabe-Steuerelement hinzufügen, um eine Spalte für Länder hinzuzufügen:
   
    `Collect(Destinations, {Cities:City!Text, States:States!Text}, {Countries:Country!Text})`
7. Benennen Sie das Schaltflächen-Steuerelement **AddCityStateButton** um, und legen Sie seine **[Text](controls/properties-core.md)**-Eigenschaft auf **Add City and State** (Stadt und Bundesstaat hinzufügen) fest:  
   ![][12]  

In diesem Vorgang haben Sie der Sammlung **Destinations** eine Spalte **Cities** (Städte) und eine Spalte **States** (Bundesstaaten) hinzugefügt. Das Schaltflächen-Steuerelement fügt Ihrer Sammlung diese neuen Textelemente hinzu. Sehen Sie sich an, was Sie erstellt haben:

1. Wählen Sie die Vorschau:  
   ![][7]  
2. Geben Sie in die Felder „City“ und „State“ einen beliebigen Text ein, und wählen Sie anschließend die Schaltfläche **Add City and State** (Stadt und Bundesstaat hinzufügen) aus.
3. Fügen Sie weitere Städte und Bundesstaaten hinzu.
4. Drücken Sie die **ESC**-Taste, um das Vorschaufenster zu schließen.
5. Wählen Sie zum Anzeigen der Elemente, die Sie der Destinations-Sammlung hinzugefügt haben, die Registerkarte **File** (Datei) aus und anschließend **Collections** (Sammlungen):  
   ![][13]

## <a name="add-columns-to-a-collection"></a>Hinzufügen von Spalten zu einer Sammlung
Die folgende Anleitung besteht aus mehreren Abschnitten. Wenn Sie die einzelnen Schritte abgeschlossen haben, wissen Sie, wie Sie Daten in Ihre Sammlung importieren, wie Sie einen Katalog erstellen, der Daten in einer Preisliste anzeigt, und wie Sie ein Schieberegler-Steuerelement verwenden, das die Produktmenge bestimmt.

### <a name="import-the-price-list-and-create-the-collection"></a>Importieren der Preisliste und Erstellen der Sammlung
1. Laden Sie die [PriceList](http://pwrappssamples.blob.core.windows.net/samples/PriceList.zip)-Zip-Datei herunter.
2. Fügen Sie auf der Registerkarte **Home** einen neuen Bildschirm hinzu.
3. Wählen Sie auf der Registerkarte **Einfügen** die Option **Steuerelemente** und anschließend **Importieren** aus:  
   ![][14]  
4. Wählen Sie auf der Registerkarte **Action** (Aktion) die Option **OnSelect** aus. Geben Sie die folgende Funktion ein:  
   
    ```Collect(PriceList, Import1!Data)```  
5. Zeigen Sie eine Vorschau Ihrer App an. Wählen Sie die Schaltfläche **Import Data** (Daten importieren) und die Datei „PriceList.zip“ aus, und wählen Sie anschließend **Open** (Öffnen) aus.
6. Schließen Sie das Vorschaufenster.
7. Wählen Sie die Registerkarte **File** (Datei) aus und anschließend **Collections** (Sammlungen). Die von Ihnen importierten PriceList-Elemente werden aufgeführt:  
   ![][15]

### <a name="add-the-gallery-to-show-the-collection-items"></a>Hinzufügen des Katalogs, um die Sammlungselemente anzuzeigen
1. Wechseln Sie in den Designer zurück.
2. Wählen Sie auf der Registerkarte **Insert** (Einfügen) die Option**Gallery** (Katalog) aus, führen Sie einen Bildlauf nach unten bis zum Eintrag **Custom Galleries** (Benutzerdefinierte Kataloge) durch, und wählen Sie anschließend **Portrait** (Hochformat) aus:    
   ![][16]  
3. Benennen Sie den Katalog in **PriceGallery** um, und legen Sie die **[Items](controls/properties-core.md)** -Eigenschaft auf **PriceList** fest:  
   ![][18]  
4. Verschieben Sie den PriceList-Katalog unter das Steuerelement **Import Data** (Daten importieren). Wählen Sie den Katalograhmen aus, und klicken und ziehen Sie, um die Größe des Katalogs so zu verändern, dass drei Quadrate angezeigt werden.
5. Wählen Sie das erste Quadrat im Katalog aus, und fügen Sie drei Bezeichnungen hinzu (Registerkarte **Insert** (Hinzufügen) > **Label** (Bezeichnung)).
6. Ordnen Sie die Bezeichnungen in einer Zeile im oberen Bereich des ersten Quadrats an, und ändern Sie ihre Größe entsprechend. Ihr Katalog sieht etwa wie folgt aus:  
   ![][19]
7. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft jeder Bezeichnung auf den folgenden Ausdruck fest:  
   
   | Bezeichnung | Text-Eigenschaft festgelegt auf |
   | --- | --- |
   | Label1 |``ThisItem!Name`` |
   | Label2 |``Text(ThisItem!Price, "$#")`` |
   | Label3 |``ThisItem!Maker`` |
   
    Auf diese Weise werden die Bezeichnungen automatisch mit dem Namen, dem Preis und den Erstellerwerten innerhalb der PriceList-Sammlung aktualisiert.
8. Ändern Sie die Größe der Bezeichnungen und des Katalogs, und entfernen Sie alle zusätzlichen Leerzeichen. Ihr Bildschirm sollte etwa wie folgt aussehen:  
   ![][17]

### <a name="add-the-quantity-slider-and-update-the-collection"></a>Hinzufügen des Mengen-Schiebereglers und Aktualisieren der Sammlung
1. Wählen Sie im Menü **Insert** (Einfügen) die Option **Controls** (Steuerelemente) aus und anschließend **Slider** (Schieberegler). Benennen Sie den Schieberegler in **OrderQty** um, und verschieben Sie Ihn unter den Katalog.
2. Fügen Sie eine Schaltfläche hinzu, legen Sie ihre **[Text](controls/properties-core.md)**-Eigenschaft auf **Add** (Hinzufügen) fest, und verschieben Sie sie unter den **OrderQty**-Schieberegler. Ihre App sieht etwa wie folgt aus:  
   ![][20]
3. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft der Schaltfläche **Add** (Hinzufügen) auf den folgenden Ausdruck fest:  
   
    ```Collect(OrderList, {Name:PriceGallery!Selected!Name, Qty:OrderQty!Value, Cost:OrderQty!Value*LookUp(PriceList, PriceGallery!Selected!Name in Name, Price)});SaveData(OrderList, "orderfile")```  
   
    > [!NOTE]
   > Wenn Sie diese Schaltfläche im weiteren Verlauf dieser Prozedur auswählen, erstellen und speichern Sie eine Sammlung mit dem Namen **OrderList**. Die Sammlung enthält den Namen des Produkts, das Sie im Katalog eingeben, die Menge, die Sie mit dem Schieberegler auswählen, und die Gesamtkosten, die sich durch die Multiplikation der Menge mit dem Preis des Produkts ergeben.
4. Wählen Sie die Registerkarte **Screen** (Bildschirm) aus, und legen Sie die **[OnVisible](controls/control-screen.md)**-Eigenschaft auf den folgenden Ausdruck fest:  
   
    ```If(IsEmpty(PriceList), LoadData(PriceList, "pricefile"));If(IsEmpty(OrderList), LoadData(OrderList, "orderfile"))```

Sehen Sie sich an, was Sie erstellt haben:

1. Öffnen Sie **Preview** (Vorschau).
2. Wählen Sie im Katalog ein Produkt aus, verschieben Sie den Schieberegler auf die gewünschte Menge, und wählen Sie anschließend die Schaltfläche **Add** (Hinzufügen) aus.  
   
   > [!IMPORTANT]
   > Wenn Sie ein Produkt auswählen, wird dieses Produkt nicht hervorgehoben, um sichtbar zu machen, dass Sie es ausgewählt haben. Wir haben diese Funktionalität bei der Erstellung des Katalogs nicht hinzugefügt. Denken Sie also daran, dass Sie das Produkt dennoch durch Klicken auswählen.  
   > 
   > 
3. Wiederholen Sie diese Schritte, um weitere Produkte hinzuzufügen. Drücken Sie die **ESC**-Taste, um das Vorschaufenster zu schließen.
4. Wählen Sie auf der Registerkarte **File** (Datei) die Option **Collections** (Sammlungen) aus, um eine Vorschau der von Ihnen erstellten **OrderList**-Sammlung anzuzeigen:  
   ![][21]

> [!TIP]
> Zum Entfernen aller Elemente aus der Bestellliste fügen Sie eine Schaltfläche hinzu, legen ihre **[Text](controls/properties-core.md)**-Eigenschaft auf **Clear** (Deaktivieren) fest, und legen anschließend die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf den folgenden Ausdruck fest:  
> ```Clear(OrderList);SaveData(OrderList, "orderfile")```  
> Um alle Element einzeln zu entfernen, zeigen Sie die **OrderList**-Sammlung in einem Katalog an und legen anschließend die **[OnSelect](controls/properties-core.md)**-Eigenschaft einer Bezeichnung in dieser Sammlung auf folgenden Ausdruck fest:  
> ```Remove(OrderList, ThisItem);SaveData(OrderList, "orderfile")```
> 
> 

## <a name="tips-and-tricks"></a>Tipps und Tricks
* Sie können die Schaltfläche für die Vorschau (![][7]) jederzeit auswählen, um Ihre Diagramme anzuzeigen und wie sie mit Daten angefüllt aussehen.
* Beim Entwerfen Ihrer App können Sie die Größe der Steuerelemente erneut ändern und sie durch Klicken und Ziehen verschieben.

## <a name="what-you-learned"></a>Vermittelte Inhalte
In diesem Thema haben Sie folgende Aufgaben ausgeführt:

* Verwenden der Collect()-Funktion, um eine Sammlung in Ihrer App zu erstellen
* Hinzufügen eines Schaltflächen-Steuerelements, das bei Auswahl dieser Option Ihrer Sammlung neue Elemente hinzugefügt
* Verwenden eines Listenfelds, um Ihrer Sammlung Elemente hinzuzufügen
* Hinzufügen eines Schieberegler-Steuerelements in der Sammlung

[1]: ./media/create-update-collection/insertmenu-inputtext.png
[2]: ./media/create-update-collection/renametext.png
[3]: ./media/create-update-collection/buttononselect.png
[4]: ./media/create-update-collection/listboxpreview.png
[5]: ./media/create-update-collection/buttontext.png
[6]: ./media/create-update-collection/buttonundertext.png
[7]: ./media/create-update-collection/preview.png
[8]: ./media/create-update-collection/existingcollections.png
[9]: ./media/create-update-collection/renametext-city.png
[10]: ./media/create-update-collection/citystate.png
[11]: ./media/create-update-collection/buttononselectcitystate.png
[12]: ./media/create-update-collection/buttononcitystate.png
[13]: ./media/create-update-collection/existingcollectionscitystate.png
[14]: ./media/create-update-collection/import.png
[15]: ./media/create-update-collection/pricelistcollection.png
[16]: ./media/create-update-collection/portrait.png
[17]: ./media/create-update-collection/resizedgallery.png
[18]: ./media/create-update-collection/galleryitems.png
[19]: ./media/create-update-collection/gallerylabels.png
[20]: ./media/create-update-collection/slider.png
[21]: ./media/create-update-collection/existingcollectionsorderlist.png
[22]: ./media/create-update-collection/listbox.png
