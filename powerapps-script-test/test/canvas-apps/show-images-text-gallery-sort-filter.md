---
title: Anzeigen, Sortieren und Filtern von Daten in einem Katalog | Microsoft-Dokumentation
description: Verwenden Sie einen Katalog, um Bilder und Text anzuzeigen. Sortieren und filtern Sie die Bilder in PowerApps.
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/02/2015
ms.author: lonu
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e782b7082e8dbf0d4efee2060131aa620e7a4af1
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42844456"
---
# <a name="show-sort-and-filter-data-in-a-powerapps-gallery"></a>Anzeigen, Sortieren und Filtern von Daten in einem PowerApps-Katalog
Erstellen Sie einen Katalog, um Bilder und Text zu verschiedenen Produkten anzuzeigen, und sortieren und filtern Sie diese Informationen.

In PowerApps können Sie einen Katalog verwenden, um mehrere verwandte Elemente anzuzeigen. Kataloge eignen sich hervorragend zur Anzeige von Produktinformationen, z.B. Namen und Preise. In diesem Thema erstellen wir einen Katalog und sortieren und filtern die Informationen mithilfe von Excel-ähnlichen Funktionen. Außerdem wird bei Auswahl eines Elements ein Rahmen um das Element platziert.

> [!NOTE]
> In diesem Thema wird eine Tablet-App verwendet. Sie können auch eine Telefon-App verwenden, aber dann müssen einige der Steuerelemente in der Größe verändert werden.
> 
> 

### <a name="prerequisites"></a>Voraussetzungen
* [Registrieren Sie sich für PowerApps](../signup-for-powerapps.md), und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen eingeben, die Sie bei der Registrierung angegeben haben.
* Erstellen Sie aus einer [Vorlage](get-started-test-drive.md) oder mithilfe von [Daten](get-started-create-from-data.md) eine Tablet-App, oder [erstellen Sie die App von Grund auf neu](get-started-create-from-blank.md).
* Erfahren Sie, wie Sie ein [Steuerelement konfigurieren](add-configure-controls.md).
* In den hier gezeigten Schritten werden die [CreateFirstApp](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip)-Daten als Beispieleingabe verwendet, die auch JPG-Bilder umfassen. Die ZIP-Datei enthält eine XML-Datei, die in Excel konvertiert werden kann. Andernfalls liest PowerApps die Dateien in den ZIP-Dateien automatisch und importiert sie erfolgreich. Sie können diese Beispieldaten herunterladen und verwenden oder eigene Daten importieren.

## <a name="show-data-in-a-gallery"></a>Anzeigen von Daten in einem Katalog
1. Erstellen Sie unter Verwendung der Beispieldaten eine Sammlung namens **Inventory**. Führen Sie hierbei diese Schritte aus:  
   
   1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Steuerelemente** und anschließend **Importieren** aus:
      
      ![][1]  
   2. Legen Sie die Eigenschaft **[OnSelect](controls/properties-core.md)** des Importsteuerelements auf die folgende Formel fest:  
      **Collect(Inventory, Import1!Data)**
      
      ![][12]  
   3. Klicken Sie auf die Schaltfläche **Daten importieren**, um den Windows-Explorer zu öffnen. Wählen Sie *CreateFirstApp.zip* und anschließend **Öffnen** aus.
   4. Wählen Sie im Menü **Datei** die Option **Sammlungen** aus. Die Sammlung „Inventory“ wird mit den importierten Daten aufgeführt:
      
      ![][3]  
      
      Sie haben soeben die Sammlung „Inventory“ erstellt, die Informationen zu fünf Produkten enthält, darunter ein Bild des Entwurfs, den Namen des Produkts und die im Lager vorrätige Stückanzahl.
      
      > [!NOTE]
      > Das Importsteuerelement wird zum Importieren von Excel-ähnlichen Daten und zum Erstellen der Sammlung verwendet. Das Importsteuerelement importiert Daten, wenn Sie Ihre App erstellen und eine Vorschau der App anzeigen. Aktuell importiert das Importsteuerelement keine Daten, wenn Sie Ihre App veröffentlichen.
      > 
      > 
2. Wählen Sie den nach links weisenden Pfeil aus, um zum Designer zurückzukehren.
3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Katalog**, und klicken oder tippen Sie dann auf den Katalog **Horizontal**.
   
    ![][4]
4. Klicken oder tippen Sie im rechten Bereich auf die Option, in der Titel und Untertitel die Grafik überschneiden:
   
    ![][15]
5. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des Katalogs auf **Inventory** fest:
   
    ![][5]
6. Benennen Sie den Katalog in **ProductGallery** um, und verschieben Sie den Katalog, damit er nicht die anderen Steuerelemente blockiert. Ändern Sie die Größe des Katalogs, sodass drei Produkte angezeigt werden:
   
    ![][6]
7. Wählen Sie im ersten Katalogelement die unten angezeigte Bezeichnung aus:  
   
    ![][7]  
   
   > [!NOTE]
   > Wenn Sie das erste Element in einem Katalog ändern, ändern Sie automatisch auch alle weiteren Elemente im Katalog.  
   > 
   > 
8. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft der Bezeichnung auf den folgenden Ausdruck fest:  
    **ThisItem!UnitsInStock** <br/>
   
    Hierdurch zeigt die Bezeichnung die für jedes Produkt im Lager vorrätige Stückanzahl an:

![][8]  

> [!NOTE]
> Standardmäßig ist die **[Text](controls/properties-core.md)**-Eigenschaft der obersten Bezeichnung auf ```ThisItem!ProductName``` festgelegt. Sie können diese Einstellung auf ein anderes Element in Ihrer Sammlung festlegen. Wenn Ihre Sammlung beispielsweise über die Felder *ProductDescription* oder *Price* verfügt, können Sie die Bezeichnung auf ```ThisItem!ProductDescription``` oder ```ThisItem!Price``` festlegen.
> 
> 

Mithilfe der hier genannten Schritte haben Sie Daten in eine Sammlung importiert, die JPG-Bilder enthalten. Anschließend haben Sie einen Katalog hinzugefügt, der die Daten anzeigt, und Sie haben eine Bezeichnung konfiguriert, mit der die für jedes Produkt im Lager vorrätige Stückanzahl angezeigt wird.

## <a name="highlight-the-gallery-item-you-select"></a>Markieren des ausgewählten Katalogelements
1. Wählen Sie ein Element im Katalog aus, *nicht jedoch* das erste Element. Das Bearbeitungssymbol wird angezeigt (oben links). Wählen Sie das Bearbeitungssymbol aus:  
   ![][9]  
2. Wählen Sie auf der Registerkarte **Einfügen** die Option **Formen** und anschließend das Rechteck aus. Für jedes Katalogelement wird ein durchgehendes blaues Rechteck angezeigt.
3. Wählen Sie auf der Registerkarte **Start** die Option **Füllung** und anschließend **Keine Füllung** aus.
4. Wählen Sie **Rahmen** und anschließend **Rahmenart** aus, und wählen Sie dann die durchgezogene Linie aus.
5. Wählen Sie erneut **Rahmen** aus, und legen Sie die Stärke auf 3 fest. Ändern Sie die Größe des Rechtecks, sodass es das Katalogelement umschließt. Die Elemente in Ihrem Katalog weisen jetzt einen blauen Rahmen auf und sollten folgendermaßen aussehen:  
   ![][10]  
6. Wählen Sie auf der Registerkarte **Form** die Option **Sichtbar** aus, und geben Sie in der Bearbeitungsleiste die folgende Formel ein:  
   
    **If(ThisItem!IsSelected, true)**
   
    Die aktuelle Auswahl in einem Katalog ist von einem blauen Rechteck umgeben. Wählen Sie einige Katalogelemente aus, um zu bestätigen, dass das Rechteck um jedes ausgewählte Element platziert wird. Sie können auch die **Vorschau** ![][2] öffnen, um die erstellten Elemente zu testen.

> [!TIP]
> Wählen Sie das Rechteck aus, wählen Sie auf der Registerkarte **Start** die Option **Neu anordnen** und dann **In den Hintergrund** aus. Mithilfe dieser Funktion können Sie ein Katalogelement auswählen, ohne dass der Rahmen andere Elemente blockiert.
> 
> 

Mithilfe der hier genannten Schritte haben Sie einen Rahmen um die aktuelle Auswahl im Katalog einfügt.

## <a name="sort-and-filter-items-in-the-gallery"></a>Sortieren und Filtern von Elementen im Katalog
Mithilfe der nachfolgenden Schritte werden wir die Katalogelemente in aufsteigender und absteigender Reihenfolge sortieren. Darüber hinaus fügen wir einen Schieberegler hinzu, um Katalogelemente nach der im Lager vorrätigen Stückzahl zu „filtern“, die von Ihnen ausgewählt wurde.

#### <a name="sort-in-ascending-or-descending-order"></a>Sortieren in aufsteigender oder absteigender Reihenfolge
1. Wählen Sie ein Element im Katalog aus, *nicht jedoch* das erste Element.
2. Die Eigenschaft **[Items](controls/properties-core.md)** ist aktuell auf „Inventory“ festgelegt (den Namen Ihrer Sammlung). Ändern Sie die Einstellung wie folgt:  
   
    **Sort(Inventory, ProductName)**
   
    Hierdurch werden die Elemente im Katalog in aufsteigender Reihenfolge nach dem Produktnamen sortiert: ![][11]  
   
    Versuchen Sie es mit der absteigenden Reihenfolge. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des Katalogs auf die folgende Formel fest:  
   
    Sort(Inventory, ProductName, Descending)  

#### <a name="add-a-slider-control-and-filter-items-in-the-gallery"></a>Hinzufügen eines Schiebereglers und Filtern der Elemente im Katalog
1. Fügen Sie ein Steuerelement vom Typ „Schieberegler“ hinzu (Registerkarte **Einfügen** > **Steuerelemente**), benennen Sie es in **StockFilter** um, und verschieben Sie es unter den Katalog.
2. Konfigurieren Sie den Schieberegler so, dass Benutzer ihn nicht auf einen Wert außerhalb des Bereichs für die vorrätige Stückzahl festlegen können:  
   
   1. Wählen Sie auf der Registerkarte **Inhalt** die Einstellung **Min**, und geben Sie den folgenden Ausdruck ein:  
      ```Min(Inventory, UnitsInStock)```  
   2. Wählen Sie auf der Registerkarte **Inhalt** die Einstellung **Max**, und geben Sie den folgenden Ausdruck ein:  
      ```Max(Inventory, UnitsInStock)```
3. Wählen Sie ein Element im Katalog aus, *nicht jedoch* das erste Element. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des Katalogs auf den folgenden Ausdruck fest:  
   ```Filter(Inventory, UnitsInStock<=StockFilter!Value)```
4. Stellen Sie den Schieberegler in der **Vorschau** auf einen Wert zwischen der höchsten und der niedrigsten Menge im Katalog ein. Wenn Sie den Wert über den Schieberegler ändern, werden nur die Produkte angezeigt, deren Stückzahl unter dem ausgewählten Wert liegt:  
   ![][13]  

Fügen wir jetzt unseren Filter hinzu:

1. Kehren Sie zum Designer zurück.
2. Wählen Sie auf der Registerkarte **Einfügen** die Einstellung **Text** aus, wählen Sie **Eingabetext** aus, und benennen Sie das neue Steuerelement in **NameFilter** um. Verschieben Sie das Textsteuerelement unter den Schieberegler.
3. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des Katalogs auf den folgenden Ausdruck fest:  
   ```Filter(Inventory, UnitsInStock<=StockFilter!Value && NameFilter!Text in ProductName)```
4. Stellen Sie den Schieberegler in der **Vorschau** auf den Wert *30* ein, und geben Sie im Texteingabe-Steuerelement den Buchstaben *g* ein. Der Katalog zeigt nur Produkte an, bei denen die vorrätige Stückzahl unter 30 liegt *und* deren Name mit dem Buchstaben „g“ beginnt:  
   ![][14]  

## <a name="tips-and-tricks"></a>Tipps und Tricks
* Sie können jederzeit die Schaltfläche für die Vorschau (![][2]) auswählen, um die erstellten Elemente anzuzeigen und zu testen.
* Beim Entwurf Ihrer App können Sie die Größe der Steuerelemente ändern und sie verschieben, indem Sie darauf klicken und das Steuerelement an eine andere Position ziehen.
* Drücken Sie **ESC**, oder klicken Sie auf **X**, um das Vorschaufenster zu schließen.
* Wenn Sie einen Katalog verwenden, wählen Sie das erste Element im Katalog aus, um alle Elemente im Katalog zu ändern. Wählen Sie beispielsweise das erste Element aus, um allen Elementen im Katalog einen Rahmen hinzuzufügen.
* Um die Eigenschaften des Katalogs zu aktualisieren, wählen Sie ein beliebiges Element im Katalog aus, *nicht jedoch* das erste Element. Wählen Sie beispielsweise das zweite Element aus, um die Eigenschaften *Items*, *ShowScrollbar* und weitere Eigenschaften zu aktualisieren, die auf den Katalog angewendet werden (nicht auf die Elemente im Katalog).  

## <a name="what-you-learned"></a>Vermittelte Inhalte
In diesem Thema haben Sie folgende Aufgaben ausgeführt:

* Sie haben eine Sammlung erstellt, Daten mit JPG-Bildern in diese Sammlung importiert und die Daten in einem Katalog angezeigt.
* Sie haben unter jedem Bild im Katalog eine Bezeichnung konfiguriert, um die im Lager vorrätige Stückzahl anzugeben.
* Sie haben einen Rahmen um das ausgewählte Element hinzugefügt.
* Sie haben die Elemente nach Produktnamen in aufsteigender und absteigender Reihenfolge sortiert.
* Sie haben einen Schieberegler und ein Eingabetextfeld hinzugefügt, um die Produkte nach vorrätiger Stückzahl und nach dem Produktnamen zu filtern.

[1]: ./media/show-images-text-gallery-sort-filter/import.png
[2]: ./media/show-images-text-gallery-sort-filter/preview.png
[3]: ./media/show-images-text-gallery-sort-filter/inventorycollection.png
[4]: ./media/show-images-text-gallery-sort-filter/insert-vertical.png
[5]: ./media/show-images-text-gallery-sort-filter/itemsinventory.png
[6]: ./media/show-images-text-gallery-sort-filter/threeimages.png
[7]: ./media/show-images-text-gallery-sort-filter/firstitem.png
[8]: ./media/show-images-text-gallery-sort-filter/bottomlabel.png
[9]: ./media/show-images-text-gallery-sort-filter/editgallery.png
[10]: ./media/show-images-text-gallery-sort-filter/border.png
[11]: ./media/show-images-text-gallery-sort-filter/sort.png
[12]: ./media/show-images-text-gallery-sort-filter/onselect.png
[13]: ./media/show-images-text-gallery-sort-filter/slider.png
[14]: ./media/show-images-text-gallery-sort-filter/inputandslider.png
[15]: ./media/show-images-text-gallery-sort-filter/select-overlay.png
