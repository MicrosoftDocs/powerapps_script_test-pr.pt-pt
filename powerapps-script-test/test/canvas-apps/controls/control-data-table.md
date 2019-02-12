---
title: 'Datentabellen-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Datentabellen-Steuerelement
author: jasongre
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/05/2017
ms.author: jasongre
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fb7c2ac88c24197d014ebdc1b2b6a50e4802e0bf
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42846772"
---
# <a name="data-table-control-in-powerapps"></a>Datentabellen-Steuerelement in PowerApps
Dient zum Anzeigen eines Satzes von Daten im Tabellenformat.

## <a name="description"></a>Beschreibung
Das **Datentabellen**-Steuerelement zeigt ein Dataset in einem Format an, das Spaltenheader für jedes vom Steuerelement dargestellte Feld enthält. Als Ersteller einer App haben Sie die volle Kontrolle darüber, welche Felder in welcher Reihenfolge angezeigt werden. Wie das **Katalog**-Steuerelement weist das **Datentabellen**-Steuerelement die Eigenschaft **Selected** auf, die auf die ausgewählte Zeile zeigt. Daher kann das **Datentabelle**-Steuerelement mit anderen Steuerelementen verknüpft werden.

## <a name="capabilities"></a>Funktionen
Das **Datentabellen**-Steuerelement wurde am 5. Mai 2017 in PowerApps eingeführt. Dieser Abschnitt bietet Informationen zu unterstützten und nicht unterstützten Funktionen.

### <a name="now-available"></a>Jetzt verfügbar
* Daten in einem **Datentabellen**-Steuerelement sind schreibgeschützt.
* In einem **Datentabellen**-Steuerelement wird stets eine einzelne Zeile ausgewählt.
* Verknüpfen Sie ein **Datentabellen**-Steuerelement mit einer verbundenen oder lokalen Datenquelle.
* Passen Sie Spaltenbreiten in einem **Datentabellen**-Steuerelement an, während Sie die App ausführen. Allerdings werden Ihre Änderungen nicht gespeichert.
* In einem **Datentabellen**-Steuerelement wird eine Gruppe von Standardfeldern angezeigt, wenn Sie es mit einem Connector verknüpfen, in den diese Funktion implementiert ist, wie z.B. Common Data Service. Sie können dann diese und andere Felder nach Bedarf ein- und ausblenden.
* Anpassen von Spaltenbreite und Überschriftentext.
* Anzeigen von Links in einem **Datentabellen**-Steuerelement.
* Kopieren und Einfügen eines **Datentabellen**-Steuerelements.

### <a name="not-yet-available"></a>Noch nicht verfügbar
* Anpassen des Formats einzelner Spalten.
* Hinzufügen eines **Datentabellen**-Steuerelements in einem Formularsteuerelement.
* Ändern der Höhe aller Zeilen.
* Anzeigen von Bildern in einem **Datentabellen**-Steuerelement.
* Anzeigen von Feldern aus verwandten Entitäten.
* Verwenden integrierter Funktionen zum Filtern und Sortieren von Daten nach Spaltenüberschrift.
* Hinzufügen eines **Datentabellen**-Steuerelements zu einem **Katalog**-Steuerelement.
* Bearbeiten von Daten im **Datentabellen**-Steuerelement.
* Auswählen mehrerer Zeilen.

### <a name="known-issues"></a>Bekannte Probleme
* Es werden keine Daten angezeigt, wenn Sie die **FirstN**-Funktion in der **Items**-Eigenschaft verwenden.

## <a name="key-properties"></a>Haupteigenschaften
* [**Items**](properties-core.md): Quelle der Daten, die im **Datentabellen**-Steuerelement angezeigt werden.
* **Selected**: die im **Datentabellen**-Steuerelement ausgewählte Zeile.

## <a name="other-properties"></a>Weitere Eigenschaften
* [**BorderColor**](properties-color-border.md): die Farbe des Rahmens des **Datentabellen**-Steuerelements.
* [**BorderStyle**](properties-color-border.md): der Stil des Rahmen des **Datentabellen**-Steuerelements. Die verfügbaren Optionen sind **Solid (Gefüllt)**, **Dashed (Gestrichelt)**, **Dotted (Gepunktet)** und **None (Ohne)**.
* [**BorderThickness**](properties-color-border.md): die Stärke des Rahmens des **Datentabellen**-Steuerelements.
* [**Color**](properties-color-border.md): die Standardtextfarbe für alle Datenzeilen.
* [**Fill**](properties-color-border.md): die Standardhintergrundfarbe für alle Datenzeilen.
* [**Font**](properties-text.md): die Standardschriftart aller Datenzeilen.
* [**FontWeight**](properties-text.md): die Standardschriftbreite für alle Datenzeilen.
* **HeadingColor**: die Textfarbe der Spaltenüberschriften.
* **HeadingFill**: die Hintergrundfarbe der Spaltenüberschriften.
* **HeadingFont**: die Schriftart der Spaltenüberschriften.
* **HeadingFontWeight**: die Schriftbreite der Spaltenüberschriften.
* **HeadingSize**: der Schriftgrad der Spaltenüberschriften.
* [**Height**](properties-size-location.md): der Abstand zwischen dem oberen und unteren Rand des **Datentabellen**-Steuerelements.
* [**HoverColor** ](properties-color-border.md): die Textfarbe der Zeile, auf die der Mauszeiger zeigt.
* [**HoverFill**](properties-color-border.md): die Hintergrundfarbe der Zeile, auf die der Mauszeiger zeigt.
* **NoDataText**: die Meldung, die der Benutzer erhält, wenn es im **Datentabellen**-Steuerelement keine anzuzeigenden Datensätze gibt.
* **SelectedColor**: die Farbe des Texts in der ausgewählten Zeile.
* **SelectedFill**: die Hintergrundfarbe der ausgewählten Zeile.
* [**Size**](properties-text.md): der Standardschriftgrad für alle Datenzeilen.
* [**Visible**](properties-core.md): ein Wert, der bestimmt, ob das **Datentabellen**-Steuerelement angezeigt wird oder ausgeblendet ist.
* [**Width**](properties-size-location.md): der Abstand zwischen dem linken und rechten Rand des **Datentabellen**-Steuerelements.
* [**X**](properties-size-location.md): der Abstand zwischen dem linken Rand des **Datentabellen**-Steuerelements und dem linken Rand seines übergeordneten Containers (oder des linken Bildschirmrands, wenn es keinen übergeordneten Container gibt).
* [**Y**](properties-size-location.md): der Abstand zwischen dem oberen Rand des **Datentabellen**-Steuerelements und dem oberen Rand seines übergeordneten Containers (oder dem oberen Bildschirmrand, wenn es keinen übergeordneten Container gibt).

## <a name="related-functions"></a>Verwandte Funktionen
* [**Filter(Datenquelle, Formel)**](../functions/function-filter-lookup.md)(*Datenquelle*, *Formel*)
* [**Search(Datenquelle, Suchzeichenfolge, Spalte)**](../functions/function-filter-lookup.md)(*Datenquelle*, *Suchzeichenfolge*, *Spalte*)

## <a name="examples"></a>Beispiele
### <a name="basic-usage"></a>Grundlegende Nutzung
1. Erstellen Sie eine leere Tablet-App.
2. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Datentabelle**.
   
    ![Hinzufügen eines Datentabellen-Steuerelements zu einem Bildschirm](./media/control-data-table/insert-data-table.png)
   
    Dem Bildschirm wird ein **Datentabelle**-Steuerelement hinzugefügt.
3. Benennen Sie das neue **Datentabellen**-Steuerelement in **SalesOrderTable** um, und ändern Sie seine Größe, sodass es den gesamten Bildschirm einnimmt.
4. Klicken oder tippen Sie im rechten Bereich auf den Abwärtspfeil neben dem Text **Keine Datenquelle ausgewählt**, und klicken oder tippen Sie dann auf **Datenquelle hinzufügen**.
   
    ![Datenquelle hinzufügen](./media/control-data-table/add-data-to-data-table.png)
5. Klicken oder tippen Sie in der Liste der Verbindungen auf die Verbindung für Ihre Common Data Service-Datenbank.
   
    ![Auswählen der Verbindung für Ihre Datenquelle](./media/control-data-table/choose-cds-data-table.png)
6. Klicken oder tippen Sie in der Liste der Entitäten auf **Sales order** (Verkaufsauftrag) und dann auf **Connect** (Verbinden).
   
    ![Auswählen der Entität „Sales order“ (Verkaufsauftrag)](./media/control-data-table/choose-so-data-table.png)
   
    Das **Datentabellen**-Steuerelement ist jetzt an die Datenquelle **Sales order** angefügt. Im **Datentabellen**-Steuerelement werden mehrere anfängliche Felder angezeigt, da wir einen Connector verwenden, dieser diese Funktionalität unterstützt.
   
    ![Datentabelle](./media/control-data-table/pre-order-data-table.png)
7. Aktivieren Sie im rechten Bereich ein oder mehrere Kontrollkästchen, um einzelne Felder ein- oder auszublenden.
   
    Aktivieren Sie beispielsweise das Kontrollkästchen neben **CustomerPurchaseOrderReference**, um dieses Feld auszublenden.
8. Ordnen Sie die Felder im rechten Bereich neu an, indem Sie sie nach oben oder unten ziehen.
   
    ![Ordnen Sie die Felder nach Belieben neu an](./media/control-data-table/field-re-order-data-table.png)
   
    Das **SalesOrderTable**-Steuerelement zeigt die Felder in der von Ihnen angegebenen Reihenfolge an.
   
    ![Aktualisierte Datentabelle](./media/control-data-table/post-order-data-table.png)

### <a name="restyle-the-header-for-the-data-table-control"></a>Neuformatieren der Überschriften des „Datentabellen“-Steuerelements
1. Klicken oder tippen Sie bei ausgewähltem **Datentabellen**-Steuerelement im rechten Bereich auf die Registerkarte **Erweitert**.
2. Klicken oder tippen Sie auf das Feld für die Eigenschaft **HeadingFill**, und ändern Sie dann den Wert in **RGBA(62,96,170,1)**.
3. Klicken oder tippen Sie auf das Feld für die Eigenschaft **HeadingColor**, und ändern Sie dann den Wert in **White**.
4. Klicken oder tippen Sie auf das Feld für **HeadingSize**, und ändern Sie dann den Wert in **14**.
   
    ![Datentabelle](./media/control-data-table/restyled-data-table.png)

### <a name="connect-a-data-table-control-to-another-control"></a>Verbinden eines Datentabellen-Steuerelements mit einem anderen Steuerelement
1. Fügen Sie dem Bildschirm ein **Bearbeitungsformular**-Steuerelement hinzu.
2. Ändern Sie die Größe der Steuerelemente **Datentabelle** und **Bearbeitungsformular** so, dass das **Datentabellen**-Steuerelement links auf dem Bildschirm und das **Bearbeitungsformular**-Steuerelement rechts auf dem Bildschirm angezeigt wird.
   
    ![Datentabelle und Bearbeitungsformular auf dem gleichen Bildschirm](./media/control-data-table/data-table-empty-form.png)
3. Ändern Sie bei im rechten Bereich ausgewähltem **Form1** die Anzahl der Spalten in **1**.
4. Verbinden Sie **Form1** mit der Datenquelle **Sales Order**.
   
    Mehrere anfängliche Felder werden in **Form1** angezeigt.
   
    ![Form1 mit anfänglichen Feldern](./media/control-data-table/data-table-disconnected-form.png)
5. Klicken oder tippen Sie im rechten Bereich auf die Registerkarte **Erweitert**.
6. Legen Sie die **Item**-Eigenschaft für **Form1** auf **SalesOrderTable.Selected** fest.
   
    **Form1** zeigt Informationen aus der Zeile an, die im **Datentabellen**-Steuerelement ausgewählt ist.
   
    ![Mit der Datentabelle verbundenes Bearbeitungsformular](./media/control-data-table/connected-form-data-table.png)


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* [**Color**](properties-color-border.md) und [**Fill**](properties-color-border.md)
* **HeadingColor** und **HeadingFill**
* **SelectedColor** und **SelectedFill**
* [**HoverColor**](properties-color-border.md) und [**HoverFill**](properties-color-border.md)

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Die **NoDataText**-Eigenschaft muss vorhanden sein.
