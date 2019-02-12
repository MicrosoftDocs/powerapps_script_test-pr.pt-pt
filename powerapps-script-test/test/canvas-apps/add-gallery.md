---
title: Anzeigen einer Liste von Elementen in einer Canvas-App | Microsoft-Dokumentation
description: Verwenden Sie einen Katalog, um eine Liste der Elemente in Ihrer Canvas-App anzuzeigen, und filtern Sie die Liste, indem Sie ein Kriterium angeben.
author: karthik-1
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/28/2017
ms.author: sharik
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c8498fb02182d289727385b111c564669408368
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42835096"
---
# <a name="show-a-list-of-items-in-powerapps"></a>Anzeigen einer Liste mit Elementen in PowerApps

Sie können eine Liste von Elementen aus beliebigen Datenquellen anzeigen, indem Sie Ihrer Canvas-App ein **[Katalog](controls/control-gallery.md)**-Steuerelement hinzufügen. In diesem Thema wird Excel als Datenquelle verwendet. Filtern Sie die Liste, indem Sie das **Katalog**-Steuerelement so konfigurieren, dass nur die Elemente angezeigt werden, die dem Filterkriterium in einem **[Texteingabe](controls/control-text-input.md)**-Steuerelement entsprechen.

## <a name="prerequisites"></a>Voraussetzungen

* Erfahren Sie, wie Sie in PowerApps [ein Steuerelement hinzufügen und konfigurieren](add-configure-controls.md).

* Einrichten der Beispieldaten:
    1. Laden Sie [diese Excel-Datei](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) mit Beispieldaten für dieses Lernprogramm herunter.

    2. Laden Sie die Excel-Datei in ein [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md) hoch, z.B. in OneDrive for Business.

## <a name="add-a-gallery-control"></a>Ein Katalog-Steuerelement hinzufügen
1. Öffnen Sie PowerApps, und klicken oder tippen Sie dann am linken Bildschirmrand auf **Neu**.

2. Klicken oder tippen Sie in der Kachel **Leere App** auf **Telefonlayout**.

3. Klicken oder tippen Sie im Dialogfeld **Willkommen bei PowerApps Studio** auf **Überspringen**.

4. [Fügen Sie eine Verbindung](add-data-connection.md) mit der **FlooringEstimates**-Tabelle in der Excel-Datei hinzu.

5. (Optional) Fügen Sie dem Standardbildschirm ein **Katalog**-Steuerelement hinzu, indem Sie auf die Registerkarte **Einfügen**, auf **Katalog** und dann auf ein **Katalog**-Steuerelement klicken oder tippen, das leer ist oder eine Standardauswahl von Steuerelementen enthält.

    Diese Optionen beinhalten **Katalog**-Steuerelemente, die horizontal oder vertikal scrollen. Sie können aber auch ein **Katalog**-Steuerelement hinzufügen, dessen Größe automatisch aus der Inhaltsmenge in den einzelnen Elementen abgeleitet wird.

    ![Hinzufügen des Katalogs](./media/add-gallery/gallery-dropdown.png)

6. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Neuer Bildschirm**.

    Sie können einen leeren Bildschirm, einen Scrollbildschirm, einen Bildschirm mit einem **Katalog**-Steuerelement oder einen Bildschirm mit einem Formular hinzufügen.

7. Klicken oder tippen Sie auf **Listenbildschirm**, um einen Bildschirm mit einem **Katalog**-Steuerelement und weiteren Steuerelementen (z.B. einer Suchleiste) hinzuzufügen.

    > [!NOTE]
   > Gleich, ob Sie ein **Katalog**-Steuerelement einem neuen oder einem vorhandenen Bildschirm hinzufügen, Sie können nahe dem unteren Rand des **Katalog**-Steuerelements klicken oder tippen, um es auszuwählen, dann im rechten Bereich auf **Flooring Estimates** und anschließend auf ein anderes Layout im Bereich **Daten** klicken oder tippen. Lassen Sie für dieses Tutorial das Standardlayout eingestellt.

    ![Auswählen des Kataloglayouts](./media/add-gallery/select-layout.png)

8. Klicken oder tippen Sie auf das **Katalog**-Steuerelement im soeben hinzugefügten Bildschirm.

9. Klicken oder tippen Sie auf der Registerkarte **Eigenschaften** im rechten Bereich auf **CustomGallerySample**.

10. Klicken oder tippen Sie im Bereich **Daten** auf **CustomGallerySample**, und klicken oder tippen Sie anschließend auf **FlooringEstimates**.

    ![Auswählen der Datenquelle](./media/add-gallery/choose-data.png)

    Im **Katalog**-Steuerelement werden die Beispieldaten angezeigt.

    ![Anzeigen von Daten](./media/add-gallery/show-data-default.png)

    Die Konfiguration von Suche und Sortierung erfolgt später in diesem Thema.

## <a name="add-a-control-to-the-gallery-control"></a>Hinzufügen eines Steuerelements zum Katalog-Steuerelement
Entscheiden Sie sich für ein **Katalog**-Steuerelementlayout, bevor Sie Anpassungen vornehmen. Der erste Satz von Steuerelementen in einem **Katalog**-Steuerelement ist die Vorlage, die bestimmt, wie die Daten im **Katalog**-Steuerelement dargestellt werden.

1. Wählen Sie die Vorlage aus, indem Sie nahe dem unteren Rand des **Katalog**-Steuerelements klicken oder tippen und dann in der oberen linken Ecke auf das Bleistiftsymbol klicken oder tippen.

    ![Bearbeiten der Katalogvorlage](./media/add-gallery/edit-item.png)

2. Fügen Sie bei ausgewählter Vorlage ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, verschieben Sie es, und ändern Sie seine Größe, sodass es sich nicht mit anderen Steuerelementen in der Vorlage überschneidet.

    ![Bezeichnung hinzufügen](./media/add-gallery/add-text-box.png)
3. Öffnen Sie den Bereich **Daten**, indem Sie die Vorlage auswählen und im rechten Bereich auf **Flooring Estimates** klicken oder tippen.

4. Wählen Sie die soeben in diesem Verfahren hinzugefügte Bezeichnung aus, und öffnen Sie die hervorgehobene Liste im Bereich **Daten**.

    ![Dropdownliste öffnen](./media/add-gallery/open-dropdown.png)

5. Klicken oder tippen Sie in dieser Liste auf **Price** (Preis).

    ![Ändern der Bezeichnungsbindung](./media/add-gallery/change-binding.png)

    Im **Katalog**-Steuerelement werden die neuen Werte angezeigt.

    ![Endgültiger Katalog](./media/add-gallery/final-gallery.png)

## <a name="filter-the-gallery-control"></a>Filtern des Katalog-Steuerelements
Die **[Items](controls/properties-core.md)**-Eigenschaft eines **Katalog**-Steuerelements bestimmt, welche Elemente angezeigt werden. In diesem Verfahren konfigurieren Sie diese Eigenschaft, sodass im **Katalog**-Steuerelement nur die Elemente angezeigt werden, deren Produktname den Text in **TextSearchBox1** enthält.

![Textsuchfeld](./media/add-gallery/text-search-box.png)

1. Wählen Sie das **Katalog**-Steuerelement aus, indem Sie unten im Steuerelement klicken oder tippen.

2. Legen Sie auf der Registerkarte **Erweitert** die **[Items](controls/properties-core.md)**-Eigenschaft des **Katalog**-Steuerelements auf diese Formel fest:

    **If(IsBlank(TextSearchBox1.Text), FlooringEstimates, Filter(FlooringEstimates, TextSearchBox1.Text in Text(Name)))**

    Weitere Informationen zu den Funktionen in dieser Formel finden Sie unter [formula reference (Formelreferenz)](formula-reference.md).

3. Geben Sie einen Produktnamen ganz oder teilweise im Suchfeld ein.

    Im **Katalog**-Steuerelement werden nur die Elemente angezeigt, die das Filterkriterium erfüllen.

## <a name="sort-the-gallery-control"></a>Sortieren des Katalog-Steuerelements
Die **[Items](controls/properties-core.md)**-Eigenschaft eines **Katalog**-Steuerelements bestimmt die Anzeigereihenfolge der Elemente. In diesem Verfahren konfigurieren Sie diese Eigenschaft so, dass im **Katalog**-Steuerelement die Elemente in der Reihenfolge angezeigt werden, die von **ImageSortUpDown1** festgelegt wird.

![Bild für Sortierung](./media/add-gallery/image-sorting.png)

1. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des **Katalog**-Steuerelements auf diese Formel fest:

    **Sort(If(IsBlank(TextSearchBox1.Text), FlooringEstimates, Filter(FlooringEstimates, TextSearchBox1.Text in Text(Name))), Name, If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))**

2. Wählen Sie das Sortieren-Symbol aus, um die Sortierreihenfolge des **Katalog**-Steuerelements in Bezug auf die Namen der Produkte zu ändern.

So sortieren *und* filtern Sie das **Katalog**-Steuerelement:

* Ersetzen Sie in dieser Formel beide Instanzen von *DataSource* durch den Namen der Datenquelle.

* Ersetzen Sie beide Instanzen von *ColumnName* durch den Namen der Spalte, nach der Sie sortieren und filtern möchten.

**Sort(If(IsBlank(TextSearchBox1.Text),** *DataSource*, **Filter(** *DataSource*, **TextSearchBox1.Text in Text(** *ColumnName* **))),** *ColumnName*, **If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))**

## <a name="highlight-the-selected-item"></a>Hervorheben des ausgewählten Elements
Legen Sie die **TemplateFill**-Eigenschaft des **Katalog**-Steuerelements auf eine Formel fest, die der in diesem Beispiel ähnelt:

**If(ThisItem.IsSelected, LightCyan, White)**

## <a name="change-the-default-selection"></a>Ändern der Standardauswahl
Legen Sie die **Default**-Eigenschaft des **Katalog**-Steuerelements auf den Datensatz fest, der standardmäßig ausgewählt sein soll. Geben Sie beispielsweise das fünfte Element in der Datenquelle **FlooringEstimates** an:

**Last(FirstN(FlooringEstimates, 5))**

In diesem Beispiel geben Sie das erste Element in der Kategorie **Hardwood** der Datenquelle **FlooringEstimates** an:

**First(Filter(FlooringEstimates, Category = "Hardwood"))**

## <a name="next-steps"></a>Nächste Schritte
Informationen zum Arbeiten mit [Formularen](working-with-forms.md) und [Formeln](working-with-formulas.md).
