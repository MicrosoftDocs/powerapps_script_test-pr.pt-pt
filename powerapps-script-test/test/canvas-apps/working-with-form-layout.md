---
title: Grundlegendes zum Layout von Datenformularen für Canvas-Apps | Microsoft-Dokumentation
description: Erstellen Sie mit PowerApps professionell aussehende Formularlayouts in Canvas-Apps mithilfe von Zeilen und Spalten.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/17/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 43d623daecb609fbe3d4e593a7e15f95051871e9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836416"
---
# <a name="understand-data-form-layout-for-canvas-apps-in-powerapps"></a>Grundlegendes zum Layout von Datenformularen für Canvas-Apps in PowerApps

Erstellen Sie mühelos ein professionell aussehendes und effizientes Formular, wenn Sie eine Canvas-App in PowerApps erstellen. Sehen Sie sich beispielsweise dieses einfache Formular zum Aufzeichnen von Verkaufsaufträgen an:

![Beispiel eines Verkaufsauftrags](./media/working-with-form-layout/sales-order.png)

In diesem Tutorial durchlaufen wir die Schritte zum Erstellen dieses Formulars. Außerdem beschäftigen wir uns mit einigen komplexeren Themen wie der dynamischen Größenänderung von Feldern zum Ausfüllen des verfügbaren Platzes.

## <a name="before-you-start"></a>Bevor Sie beginnen

Wenn Sie noch nicht mit PowerApps vertraut sind (oder Apps bisher lediglich automatisch generiert haben), empfiehlt es sich, [eine App von Grund auf neu zu erstellen](get-started-create-from-blank.md), bevor Sie in dieses Thema einsteigen. Durch Erstellen einer App von Grund auf machen Sie sich mit den grundlegenden Konzepten vertraut, beispielsweise mit dem Hinzufügen von Datenquellen und Steuerelementen, die in diesem Artikel zwar erwähnt, jedoch nicht erläutert werden.

## <a name="add-a-gallery"></a>Einen Katalog hinzufügen

1. Erstellen Sie eine Tablet-App von Grund auf neu.

    Alles in diesem Artikel Besprochene gilt auch für Smartphonelayouts, allerdings haben Smartphone-Apps oft nur eine vertikale Spalte.
2. Fügen Sie die Entität **Sales Order** (Verkaufsauftrag) in [Common Data Service](../common-data-service/data-platform-intro.md) als Datenquelle für die App hinzu.

    Außerhalb dieses Tutorials können Sie eine beliebige Datenquelle verwenden, u.a. SharePoint-Listen und Excel-Tabellen.
3. Fügen Sie ein vertikales **Katalog**-Steuerelement hinzu, und legen Sie dessen **Items**-Eigenschaft auf **'Sales order'** fest.
   
    (Optional) Um die Beispiele in diesem Tutorial anzugleichen, ändern Sie das **Layout** des Katalogs so, dass nur **Titel und Untertitel** angezeigt werden.
   
    ![Liste der Verkaufsaufträge](./media/working-with-form-layout/gallery-layout.png)
4. Klicken oder tippen Sie im Katalog auf **SO004**.
   
    ![Liste der Verkaufsaufträge](./media/working-with-form-layout/sales-order-gallery-screen.png)
   
    Dieser Eintrag wird im Formular angezeigt, das Sie anhand der folgenden Schritte in diesem Artikel erstellen.

## <a name="add-a-title-bar"></a>Hinzufügen einer Titelleiste
1. Fügen Sie einen leeren Bildschirm an der Position hinzu, an der das Formular platziert werden soll.
   
    Außerhalb dieses Tutorials können Sie die Steuerelemente **Katalog** und **[Bearbeitungsformular](controls/control-form-detail.md)** auf demselben Bildschirm platzieren. Sie haben jedoch mehr Platz zum Bearbeiten, wenn Sie sie auf separaten Bildschirmen platzieren.
2. Fügen Sie am oberen Rand des neuen Bildschirms ein **[Bezeichnungs](controls/control-text-box.md)**-Steuerelement hinzu, und legen Sie deren **Text**-Eigenschaft auf den folgenden Ausdruck fest:
   <br>**„Sales Order“ & Gallery1.Selected.SalesOrderId**
   
    Die Bezeichnung zeigt die Verkaufsauftragsnummer des Eintrags, der im Katalog ausgewählt wurde.
3. (Optional) Formatieren Sie die Bezeichnung wie folgt:
   
   1. Legen Sie die **Align**-Eigenschaft auf **Center** fest.
   
   2. Legen Sie die zugehörige **Size**-Eigenschaft auf **20** fest.
   
   3. Legen Sie die zugehörige **Fill**-Eigenschaft auf **Navy** fest.
   
   4. Legen Sie die zugehörige **Color**-Eigenschaft auf **White** fest.
   
   5. Legen Sie die zugehörige **Width**-Eigenschaft auf **Parent.Width** fest.
   
   6. Legen Sie die zugehörige **X**-Eigenschaft und **Y**-Eigenschaft auf **0** fest.
      
      ![Titelleiste](./media/working-with-form-layout/title-bar.png)

## <a name="add-a-form"></a>Ein Formular hinzufügen
1. Fügen Sie ein **Bearbeitungsformular**-Steuerelement hinzu, verschieben Sie es, und passen Sie seine Größe so an, dass es den Bildschirm unter der Bezeichnung ausfüllt.
   
    Im nächsten Schritt verbinden wir das Formular-Steuerelement mit der Datenquelle **Sales Order** (Verkaufsauftrag) im rechten Bereich und nicht über die Bearbeitungsleiste. Wenn Sie die Bearbeitungsleiste verwenden, werden im Formular standardmäßig keine Felder angezeigt. Sie können alle gewünschten Felder anzeigen lassen, indem Sie im rechten Bereich die entsprechenden Kontrollkästchen aktivieren.
2. Klicken oder tippen Sie im rechten Bereich auf den Abwärtspfeil neben **Keine Datenquelle ausgewählt**, und klicken oder tippen Sie dann auf **Sales Order** (Verkaufsauftrag).
   
    Die Standardfelder aus der Datenquelle **Sales Order** (Verkaufsauftrag) werden in einem einfachen Layout mit drei Spalten angezeigt. Viele davon sind jedoch leer, und es kann eine Weile dauern, bis sie an ihren endgültigen Positionen positioniert sind.  
3. Legen Sie die **Item**-Eigenschaft des Formulars auf **Gallery1.Selected** fest.
   
    Im Formular wird der im Katalog ausgewählte Eintrag angezeigt, möglicherweise entspricht die Standardgruppe von Feldern jedoch nicht den Feldern, die Sie im endgültigen Produkt wünschen.
4. Blenden Sie im rechten Bereich die einzelnen Felder aus, indem Sie die entsprechenden Kontrollkästchen deaktivieren:
   
   * **Sales Order ID** (Verkaufsauftrags-ID)
   * **Account** (Konto)
   * **Sales Person** (Vertriebsmitarbeiter)
   * **Account Contact** (Ansprechpartner Konto)
5. Verschieben Sie das Feld **Order Status** (Bestellstatus), indem Sie es nach links ziehen und auf der anderen Seite des Felds **Customer purchase order reference** (Kundenbestellreferenz) ablegen.
   
    Ihr Bildschirm sollte diesem Beispiel ähneln:
   
    ![Sales Order (Verkaufsauftrag) in einem einfachen Layout mit drei Spalten](./media/working-with-form-layout/sales-order-form-screen-3.png)

## <a name="select-a-data-card"></a>Auswählen einer Datenkarte
Jedes angezeigte Feld hat eine entsprechende Datenkarte auf dem Formular. Diese Karte besteht aus einer Gruppe von Steuerelementen für den Feldtitel, ein Eingabefeld, einen Stern (der angezeigt wird, wenn es sich um ein Pflichtfeld handelt) sowie eine Validierungsfehlermeldung.

Sie können Karten auch direkt auf dem Formular auswählen. Bei Auswahl einer Karte wird darüber eine schwarze Beschriftung angezeigt.

![Datenkartenauswahl](./media/working-with-form-layout/sales-order-data-card-selection.png)

> [!NOTE]
> Wenn Sie eine Karte löschen (und nicht nur ausblenden) möchten, wählen Sie sie aus, und drücken Sie ENTF.

## <a name="arrange-cards-in-columns"></a>Anordnen von Karten in Spalten
In der Standardeinstellung weisen Formulare in Tablet-Apps drei Spalten auf, während Smartphone-Apps über eine Spalte verfügen. Sie können nicht nur angeben, wie viele Spalten ein Formular aufweisen soll, sondern auch, ob alle Karten in den Bereich zwischen den Spaltenrändern passen sollen.

In dieser Abbildung wurde die Anzahl der Spalten im Formular von 3 in 4 geändert. Dazu wurde das Kontrollkästchen **An Spalten ausrichten** aktiviert. Die Karten im Formular wurden automatisch so angepasst, dass sie in das neue Layout passen.

![Sales Order (Verkaufsauftrag) in einfachem Layout mit vier Spalten](./media/working-with-form-layout/sales-order-form-screen-4.png)

## <a name="resize-cards-across-multiple-columns"></a>Ändern der Größe von Karten über mehrere Spalten hinweg
Je nach den Daten in den einzelnen Karten möchten Sie u.U. einige Karten in eine einzige Spalte einpassen, während sich andere Karten über mehrere Spalten erstrecken sollen. Wenn eine Karte mehr Daten enthält, als in einer einzelnen Spalte angezeigt werden sollen, können Sie die Karte verbreitern. Wählen Sie sie dazu aus, und ziehen Sie anschließend den Ziehpunkt am linken oder rechten Rand ihres Auswahlfelds. Beim Ziehen des Ziehpunkts wird die Karte an den Spaltenbegrenzungen „eingerastet“.

Um Ihr Design flexibler zu gestalten, jedoch eine gewisse Struktur beizubehalten, können Sie die Anzahl der Spalten auf 12 erhöhen. Mit dieser Änderung können Sie jede Karte auf einfache Weise so konfigurieren, dass sie sich über das gesamte Formular, über die Hälfte, ein Drittel, ein Viertel oder ein Sechstel usw. des Formulars erstreckt. Schauen wir uns dies in der Praxis an.

1. Legen Sie im rechten Bereich die Anzahl der Spalten im Formular auf **12** fest.
   
    ![Angeben der Anzahl von Spalten](./media/working-with-form-layout/12-columns.png)
   
    Am Formular wird keine sichtbare Änderung vorgenommen, aber Sie verfügen über eine größere Anzahl von Fangpunkten, wenn Sie den rechten oder linken Ziehpunkt ziehen.
2. Vergrößern Sie die Breite der Karte **Order date** (Bestelldatum), indem Sie den Ziehpunkt rechts um einen Fangpunkt nach rechts ziehen.
   
    Die Karte erstreckt sich über vier der 12 Spalten des Formulars (bzw. 1/3 des Formulars) und nicht mehr über nur drei der 12 Spalten des Formulars (bzw. 1/4 des Formulars). Immer wenn Sie die Breite einer Karte um einen Fangpunkt vergrößern, verbreitert sich die Karte um ein weiteres 1/12 des Formulars.
   
    ![Ändern der Größe einer Karte per Ziehen und Ablegen](./media/working-with-form-layout/card-resize-1.png)
3. Wiederholen Sie den vorherigen Schritt mit den Karten **Order status** (Bestellstatus) und **Customer purchase order reference** (Kundenbestellreferenz).
   
    ![Drei Karten in der ersten Zeile](./media/working-with-form-layout/card-resize-2.png)

4. Ändern Sie die Größe der Karten **Name** und **Description** (Beschreibung), sodass sie sechs Spalten (oder 1/2) des Formulars einnehmen.

5. Richten Sie die ersten zwei Zeilen der Lieferadresse so ein, dass sie sich vollständig über das Formular erstrecken:

Fertig! Wir verfügen nun über das gewünschte Formular, in dem Zeilen unterschiedlich viele Spalten aufweisen:

![Verkaufsauftrag in 12-Spalten-Layout mit Größenänderung](./media/working-with-form-layout/card-resize-done.png)

## <a name="manipulate-controls-in-a-card"></a>Bearbeiten von Steuerelementen in einer Karte
Die Lieferadresse besteht aus verschiedenen Informationsbestandteilen, die wir für den Benutzer visuell gruppieren möchten. Jedes Feld verbleibt auf seiner eigenen Datenkarte. Doch wir können die Steuerelemente innerhalb der Karte ändern, damit sie besser zusammenpassen.

1. Wählen Sie die Karte **First line of Delivery address** (Erste Zeile der Lieferadresse) aus, wählen Sie die Bezeichnung auf der Karte aus, und löschen Sie anschließend die ersten drei Wörter im Text.
   
    ![Umbenennen der Bezeichnung der ersten Zeile der Lieferadresse des Verkaufsauftrags](./media/working-with-form-layout/delivery-address-rename.png)
2. Wählen Sie die Karte **Second line of Delivery address** (Zweite Zeile der Lieferadresse) aus, wählen Sie die Bezeichnung auf der Karte aus, und löschen Sie anschließend den gesamten Text.
   
    Oft können Sie das Bezeichnungssteuerelement einfach entfernen. Möglicherweise gibt es jedoch Formeln, die davon abhängen, dass dieses Steuerelement vorhanden ist. Ein sicherer Weg ist das Entfernen des Texts oder Festlegen der **Visible**-Eigenschaft des Steuerelements auf **FALSE**.
   
    ![Umbenennen der Bezeichnung der zweiten Zeile der Lieferadresse des Verkaufsauftrags](./media/working-with-form-layout/delivery-address-rename-2.png)
3. Verschieben Sie nun auf derselben Karte das Eingabetextfeld über die Bezeichnung, um den Platz zwischen der ersten und der zweiten Zeile der Adresse zu verkleinern.
   
    Die Höhe der Karte wird reduziert, wenn dessen Inhalt weniger Raum einnimmt.
   
    ![Umbenennen der Bezeichnung der zweiten Zeile der Lieferadresse des Verkaufsauftrags](./media/working-with-form-layout/delivery-address-move-input.png)

Jetzt wollen wir uns der dritten Zeile der Adresse widmen. Wie in den vorherigen Schritten kürzen wir jetzt den Text jeder Bezeichnung dieser Karten und ordnen das Texteingabefeld rechts neben den jeweiligen Bezeichnungen an. Es folgen die Schritte für die Karte **State** (US-Bundesstaat):

| Schritt | Beschreibung | Ergebnis |
| --- | --- | --- |
| 1 |Wählen Sie die Karte **State** (US-Bundesstaat) aus, sodass Ziehpunkte an ihrem Rand angezeigt werden. |![Auswählen einer Karte](./media/working-with-form-layout/state-morph-2.png) |
| 2 |Wählen Sie die Bezeichnung auf dieser Karte aus, sodass Ziehpunkte an ihrem Rand angezeigt werden. |![Auswählen eines Steuerelements in einer Karte](./media/working-with-form-layout/state-morph-3.png) |
| 3 |Platzieren Sie den Cursor rechts neben dem Text, und löschen Sie den nicht benötigten Teil. |![Ändern des Text innerhalb eines Steuerelements in einer Karte](./media/working-with-form-layout/state-morph-3b.png) |
| 4 |Ändern Sie mithilfe der Ziehpunkte an den Seiten die Größe des Bezeichnungssteuerelements entsprechend der neuen Textgröße. |![Ändern der Größe eines Steuerelements in einer Karte](./media/working-with-form-layout/state-morph-4b.png) |
| 5 |Wählen Sie das Texteingabe-Steuerelement innerhalb dieser Karte aus. |![Auswählen eines anderen Steuerelements in der Karte](./media/working-with-form-layout/state-morph-6.png) |
| 6 |Ändern Sie mithilfe der Ziehpunkte an den Seiten die Größe des Texteingabe-Steuerelements in die gewünschte Größe. |![Ändern der Größe eines Steuerelements in einer Karte](./media/working-with-form-layout/state-morph-6b.png) |
| 7 |Ziehen Sie das Texteingabefeld nach rechts oben neben das Bezeichnungssteuerelement, und legen Sie es dort ab. |![Verschieben eines Steuerelements innerhalb einer Karte](./media/working-with-form-layout/state-morph-7b.png) |
| Unsere Änderungen an der Karte **State** (US-Bundesstaat) sind damit abgeschlossen. |![Änderungen an der Karte sind abgeschlossen](./media/working-with-form-layout/state-morph-8.png) | |

Das Ergebnis für die vollständige dritte Adresszeile:

![Lieferadresse des Verkaufsauftrags mit präziserer dritter Zeile](./media/working-with-form-layout/delivery-address-resize-city-1.png)

Beachten Sie, dass viele Karten mit dynamischen Formeln für ihre Eigenschaften anfangen. Das Texteingabe-Steuerelement, dessen Größe wir geändert und das wir nach oben verschoben haben, hat z.B. eine **Width**-Eigenschaft, die auf der Breite seines übergeordneten Elements basiert. Beim Verschieben und Ändern der Größe eines Steuerelements werden diese dynamischen Formeln durch statische Werte ersetzt. Falls gewünscht, können Sie dynamische Formeln mithilfe der Bearbeitungsleiste wiederherstellen.

## <a name="turning-off-snap-to-columns"></a>Deaktivieren von „An Spalten ausrichten“
Gelegentlich benötigen Sie eine präzisere Steuerung, als sie mit den standardmäßigen 12 Spalten möglich ist. In diesen Fällen können Sie **An Spalten ausrichten** deaktivieren und Karten manuell positionieren. Das Formular wird weiterhin an 12 Spalten ausgerichtet, Sie können jedoch auch die ALT-TASTE gedrückt halten, um eine Karte nach Wunsch manuell zu positionieren und ihre Größe festzulegen.

In unserem Beispiel haben die vier Komponenten, aus denen die dritte Zeile der Adresse besteht, alle genau die gleiche Breite. Dieses Layout ist möglicherweise nicht optimal, da Namen von Städten häufig länger als Namen von US-Bundesstaaten sind. Das Texteingabefeld für Länder/Regionen ist aufgrund der Länge seiner Bezeichnung kurz.

Deaktivieren Sie zum Optimieren dieses Raums die Option **An Spalten ausrichten** im rechten Bereich, und halten Sie die ALT-TASTE gedrückt, während Sie Größe und die Position dieser Karten anpassen. Wenn Sie die ALT-TASTE gedrückt halten, weisen alle Steuerelemente schwarze Beschriftungen auf. Dieses Verhalten ist beabsichtigt, damit die Steuerelementnamen lesbar sind.

![Positionieren und Ändern der Größe bei gedrückter ALT-TASTE](./media/working-with-form-layout/delivery-address-alt-resize.png)

Nach sorgfältiger Positionierung weist das Ergebnis entsprechende Größen für jedes Feld und einen gleichmäßigen horizontalen Abstand zwischen Feldern auf:

![Dritte Zeile der Lieferadresse des Verkaufsauftrags präzise positioniert](./media/working-with-form-layout/delivery-address-resize-city-2.png)

Was sind zusammengefasst die Unterschiede zwischen der Aktivierung und Deaktivierung von **An Spalten ausrichten**?

| Verhalten | „An Spalten ausrichten“ ein | „An Spalten ausrichten“ aus |
| --- | --- | --- |
| Bei Größenänderung erfolgt eine Ausrichtung an |Anzahl der von Ihnen gewählten Spalten:<br>1, 2, 3, 4, 6 oder 12 |12 Spalten |
| Ausrichten bei Größenänderung kann außer Kraft gesetzt werden |Nein |Ja, mit der ALT-TASTE |
| Das Layout von Karten wird zwischen Zeilen neu angeordnet (mehr dazu später) |Ja |Nein |

## <a name="set-width-and-height"></a>Breite und Höhe festlegen
Wie immer in PowerApps wird das Layout des Formulars von Eigenschaften für die Kartensteuerelemente bestimmt. Wie bereits beschrieben, können Sie die Werte dieser Eigenschaften ändern, indem Sie Steuerelemente an andere Positionen ziehen oder die Größe von Steuerelementen durch Ziehen der Ziehpunkte ändern. Allerdings kann es Situationen geben, in denen Sie diese Eigenschaften selbst verstehen und bearbeiten möchten, insbesondere wenn Sie Ihre Formulare mithilfe von Formeln dynamisch gestalten.

### <a name="basic-layout-x-y-and-width"></a>Standardlayout: X, Y und Breite
Mit der **X**-Eigenschaft und der **Y**-Eigenschaft wird die Position von Karten gesteuert. Wenn wir mit Steuerelementen im unformatierten Zeichenbereich arbeiten, geben diese Eigenschaften eine absolute Position an. In einem Formular hingegen haben diese Eigenschaften eine andere Bedeutung:

* **X**: Reihenfolge innerhalb einer Zeile.
* **Y**: Zeilennummer.

Vergleichbar mit Steuerelementen im Zeichenbereich gibt die Eigenschaft **Width** die Mindestbreite der Karte an (mehr zu diesem Aspekt später).

Werfen wir einen Blick auf die Eigenschaften **X**, **Y** und **Width** auf unserem Formular:

![X- und Y-Koordinaten des Verkaufsauftragsformulars](./media/working-with-form-layout/sales-order-xy.png)

### <a name="overflowing-rows"></a>Überlaufende Zeilen
Was geschieht, wenn die Karten in einer Zeile zu breit für diese Zeile sind? Normalerweise muss Sie dies nicht kümmern. Bei aktivierter Option **An Spalten ausrichten** werden diese drei Eigenschaften automatisch so angepasst, dass alle Inhalte perfekt ohne Überlauf in die Zeilen passen.

Bei deaktiviertem **An Spalten ausrichten** oder einer formelbasierten **Width**-Eigenschaft auf einer oder mehreren Ihrer Karten kann es hingegen zu einem Zeilenüberlauf kommen. In diesem Fall erfolgt ein automatischer Umbruch der Zeilen, wobei effektiv eine neue Zeile erstellt wird. Ändern wir beispielsweise die **Width**-Eigenschaft der Karte **Customer purchase order reference** (Kundenbestellreferenz, erste Zeile, dritte Karte) manuell in **500**:

![Bei manueller Größenänderung erfolgt ein Umbruch in eine neue Zeile](./media/working-with-form-layout/manual-size-500.png)

Die drei Karten in der obersten Zeile passen horizontal nicht mehr hinein, und durch den Umbruch beim Überlauf wurde eine weitere Zeile erstellt. Die **Y**-Koordinate aller dieser Koordinaten ist immer noch 0, und die Karten **Name** und **Description** (Beschreibung) weisen immer noch den **Y**-Wert 1 auf. Karten mit unterschiedlichen **Y**-Werten werden nicht zeilenübergreifend zusammengeführt.

Mithilfe dieses Verhaltens können Sie ein vollständig dynamisches Layout erstellen, bei dem Karten basierend auf einer Z-Reihenfolge platziert werden, wobei waagerecht so viel Platz wie möglich eingenommen wird, ehe der Wechsel in die nächste Zeile erfolgt. Weisen Sie zu diesem Zweck allen Karten denselben **Y**-Wert zu, und verwenden Sie **X** für die Reihenfolge der Karten.

### <a name="filling-spaces-widthfit"></a>Füllen von Leerbereichen: WidthFit
Durch den Überlauf im letzten Beispiel wurde ein Leerbereich hinter der Karte **Order status** (Bestellstatus) erzeugt, die die zweite Karte in der ersten Zeile darstellte. Wir könnten die **Width**-Eigenschaft der beiden restlichen Karten manuell anpassen, um diesen Leerbereich zu füllen. Eine solche Vorgehensweise wäre aber mühsam.

Verwenden Sie alternativ die **WidthFit**-Eigenschaft. Wenn diese Eigenschaft bei einer oder mehreren Karten in einer Zeile auf **TRUE** festgelegt ist, wird der verbleibende Platz in der Zeile gleichmäßig zwischen ihnen aufgeteilt. Aufgrund dieses Verhaltens haben wir zuvor darauf hingewiesen, dass die **Width**-Eigenschaft einer Karte ein *Mindestwert* ist und die tatsächliche Anzeige breiter sein kann. Diese Eigenschaft bewirkt nie, dass eine Karte schmaler wird, sondern stets nur ihre Verbreiterung.

Wenn wir **WidthFit** auf der Karte **Order status** (Bestellstatus) auf **TRUE** festlegen, füllt sie den gesamten verfügbaren Platz aus, während sich die erste Karte nicht ändert:

![Auf der zweiten Karte auf TRUE festgelegte „WidthFit“-Eigenschaft](./media/working-with-form-layout/manual-widthfit-1.png)

Wenn wir **WidthFit** auf der Karte **Order date** (Bestelldatum) auf **TRUE** festlegen, wird der verfügbare Platz gleichmäßig auf die beiden Karten aufgeteilt:

![Auf der ersten und zweiten Karte auf TRUE festgelegte „WidthFit“-Eigenschaft](./media/working-with-form-layout/manual-widthfit-2.png)

Beachten Sie, dass Ziehpunkte auf diesen Karten die von **WidthFit** bereitgestellte zusätzliche Breite und nicht die von der **Width**-Eigenschaft bereitgestellte Mindestbreite berücksichtigen. Es kann unübersichtlich werden, wenn Sie die **Width**-Eigenschaft bei aktivierter **WidthFit**-Eigenschaft bearbeiten. Deaktivieren Sie also besser diese Eigenschaft, nehmen Sie Änderungen an der **Width**-Eigenschaft vor, und aktivieren Sie sie anschließend wieder.

Wann ist **WidthFit** hilfreich? Wenn es ein Feld gibt, das nur in bestimmten Situationen verwendet wird, können Sie dessen **Visible**-Eigenschaft auf **FALSE** festlegen, woraufhin die anderen Karten in der Zeile den Platz um es herum automatisch einnehmen. Sie möchten ggf. eine Formel verwenden, die ein Feld nur dann anzeigt, wenn ein anderes Feld einen bestimmten Wert aufweist.

Hier legen wir die **Visible**-Eigenschaft des Felds **Order status** (Bestellstatus) auf ein statisches **FALSE** fest:

![Auf der ersten Karte auf TRUE festgelegtes „WidthFit“ mit nicht sichtbarem Auftragsstatus](./media/working-with-form-layout/manual-widthfit-3.png)

Bei quasi entfernter zweiter Karte kann die dritte Karte nun in dieselbe Zeile wie die erste Karte zurückkehren. Da für die erste Karte **WidthFit** weiter auf **TRUE** festgelegt ist, wird nur sie erweitert, um den verfügbaren Platz auszufüllen.

Da das Feld **Order status** (Bestellstatus) nicht sichtbar ist, kann es im Zeichenbereich nicht ohne Weiteres ausgewählt werden. Sie können jedoch jedes Steuerelement – gleich, ob sichtbar oder nicht – in der hierarchischen Liste der Steuerelemente links im Bildschirm auswählen.

### <a name="height"></a>Höhe
Die **Height**-Eigenschaft steuert die Höhe jeder Karte. Bei Karten ist für **Height** die entsprechende **WidthFit**-Eigenschaft vorhanden, und diese ist stets auf **TRUE** festgelegt. Sie können davon ausgehen, dass eine **HeightFit**-Eigenschaft vorhanden ist. Suchen Sie jedoch nicht danach im Produkt, da eine derartige Eigenschaft noch nicht offengelegt ist.

Sie können dieses Verhalten nicht deaktivieren, weshalb das Ändern der Höhe von Karten schwierig sein kann. Alle Karten innerhalb einer Zeile werden mit derselben Höhe wie die höchste Karte angezeigt. Betrachten Sie eine Zeile wie diese:

![„WidthFit“ ist auf der ersten Karte auf TRUE festgelegt, und „Status order“ (Bestellstatus) ist nicht sichtbar.](./media/working-with-form-layout/height-3.png)

Welche Karte bestimmt die Höhe der Zeile? In der vorherigen Abbildung ist die Karte **Total amount** (Gesamtbetrag) ausgewählt, die hoch erscheint, aber ihre **Height**-Eigenschaft ist auf **80** festgelegt (was identisch mit der Höhe der ersten Zeile ist). Um die Höhe einer Zeile zu verringern, müssen Sie die **Height**-Eigenschaft der höchsten Zeile in der betreffenden Zeile verringern, und Sie können die höchste Karte nicht ermitteln, ohne die **Height**-Eigenschaft jeder Karte zu überprüfen.

### <a name="autoheight"></a>AutoHeight
Eine Karte kann auch höher als erwartet sein, wenn sie ein Steuerelement enthält, dessen **AutoHeight**-Eigenschaft auf **TRUE** festgelegt ist. Viele Karten enthalten z.B. ein Bezeichnungssteuerelement zum Anzeigen einer Fehlermeldung, wenn der Wert des Felds ein Problem mit der Überprüfung verursacht.

Wenn kein Fehler vorliegt, also kein Text anzuzeigen ist, wird die Höhe der Bezeichnung auf 0 verkleinert. Wenn Sie es nicht besser wüssten und nicht wüssten, dass es da wäre, sollte alles so aussehen:

![Karten mit Steuerelementen mit auf TRUE festgelegter „AutoHeight“-Eigenschaft ohne angezeigte Höhe](./media/working-with-form-layout/autoheight-0.png)

Auf der linken Seite des Bildschirms wird in der Liste der Steuerelemente **ErrorMessage1** angezeigt. Dies ist unser Bezeichnungssteuerelement. Beim Aktualisieren einer App können Sie dieses Steuerelement auswählen, um eine gewisse Höhe festzulegen und Ziehpunkte anzuzeigen, mit denen Sie das Steuerelement positionieren und seine Größe anpassen können. Das „A“ im blauen Feld gibt an, dass für das Steuerelement **AutoHeight** auf **TRUE** festgelegt ist:

![Zum Zeitpunkt der Erstellung zeigen „AutoHeight“-Steuerelemente die Höhe ein wenig an, was das Ziehen und Ablegen vereinfacht.](./media/working-with-form-layout/autoheight-1.png)

Die **Text**-Eigenschaft dieses Steuerelements ist auf **Parent.Error** festgelegt, was dazu dient, auf Validierungsregeln basierende dynamische Fehlerinformationen abzurufen. Lassen Sie uns zur Veranschaulichung die **Text**-Eigenschaft dieses Steuerelements statisch festlegen, wodurch seine Höhe (und durch Erweiterung die Höhe der Karte) vergrößert wird, um die Länge des Texts aufzunehmen:

![Mit einer Fehlermeldung können das Steuerelement und die Karte automatisch vergrößert werden](./media/working-with-form-layout/autoheight-2.png)

Lassen Sie uns die Fehlermeldung ein wenig verlängern. Wiederum werden das Steuerelement und die Karte vergrößert, um den Text aufzunehmen. Beachten Sie, dass die gesamte Zeile an Höhe zunimmt, wobei die vertikale Ausrichtung zwischen den Karten erhalten bleibt:

![Bei einer längeren Fehlermeldung werden das Steuerelement und die Karte noch weiter vergrößert, und beachten Sie, dass die Karten in derselben Zeile alle gemeinsam vergrößert werden](./media/working-with-form-layout/autoheight-3.png)

