---
title: Anzeigen von Elementen unterschiedlicher Höhe in einem Katalog | Microsoft-Dokumentation
description: Sie können einen Katalog mit flexibler Höhe hinzufügen und konfigurieren, damit er automatisch an die Größe des Inhalts in jedem Element des Katalogs angepasst wird.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/01/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b724bff09e02a3f69166b3c3357833804c8172b6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834840"
---
# <a name="show-items-of-different-heights-in-a-powerapps-gallery"></a>Anzeigen von Elementen unterschiedlicher Höhe in einem PowerApps-Katalog
Wenn verschiedene Elemente in einem Dataset unterschiedliche Mengen von Daten in demselben Feld enthalten, können Sie Elemente, die mehr Daten enthalten, vollständig anzeigen, ohne nach Elementen, die weniger Daten enthalten, einen leeren Bereich hinzuzufügen. Fügen Sie einen Katalog mit **flexibler Höhe** hinzu, und konfigurieren Sie ihn. Dies bietet Ihnen folgende Möglichkeiten:

* Konfigurieren von **Label**-Steuerelementen (Bezeichnung), um eine Anpassung an die Größe des Inhalts zu ermöglichen.
* Positionieren der einzelnen Steuerelemente, sodass sie automatisch untereinander angezeigt werden.

In diesem Tutorial zeigen Sie Daten zu Bodenbelägen in einem Katalogsteuerelement vom Typ **Flexible Höhe** an. Das Bild jedes Produkts wird 5 Pixel unterhalb der Übersicht angezeigt, unabhängig davon, ob die Übersicht fünf Textzeilen oder zwei Textzeilen enthält.

![Fertiggestellte App](./media/gallery-dynamic-sizing/dynamic-app.png)

**Empfohlene Lektüre**

Wenn Sie noch niemals einem Katalog Steuerelemente hinzugefügt haben, führen Sie die Schritte in [Anzeigen einer Liste mit Elementen](add-gallery.md) aus, bevor Sie mit diesem Thema fortfahren.

## <a name="add-data-to-a-blank-app"></a>Hinzufügen von Daten zu einer leeren App
1. Laden Sie [diese Excel-Datei](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) herunter, die Namen, Übersichten und Links zu Bildern von Bodenbelägen enthält.

    ![Bodenbeläge](./media/gallery-dynamic-sizing/flooring-products.png)

2. Laden Sie die Excel-Datei in ein Cloudspeicherkonto hoch, z.B. in OneDrive, Dropbox oder Google Drive.

3. Klicken oder tippen Sie in PowerApps Studio im Menü **Datei** auf **Neu**.

4. Klicken oder tippen Sie in der Kachel **Leere App** auf **Telefonlayout**.

    ![Option „New“ im Menü „File“](./media/gallery-dynamic-sizing/blank-app.png)

5. Fügen Sie eine Verbindung mit der **FlooringEstimates**-Tabelle in der Excel-Datei hinzu.

    Weitere Informationen finden Sie unter [Hinzufügen einer Datenverbindung](add-data-connection.md).

## <a name="add-data-to-a-gallery"></a>Hinzufügen von Daten zu einem Katalog
1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Katalog**, und klicken oder tippen Sie dann auf **Flexible Höhe**.

    ![Hinzufügen des Katalogs](./media/gallery-dynamic-sizing/add-flexible.png)
2. Ändern Sie die Größe des Katalogs, sodass er den gesamten Bildschirm ausfüllt.

3. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des Katalogs auf **FlooringEstimates** fest.

## <a name="show-the-product-names"></a>Anzeigen der Produktnamen
1. Klicken oder tippen Sie in der oberen linken Ecke des Katalogs auf das Stiftsymbol, um die Katalogvorlage auszuwählen.

    ![Stiftsymbol](./media/gallery-dynamic-sizing/edit-template.png)

2. Fügen Sie der ausgewählten Katalogvorlage ein **[Label](controls/control-text-box.md)** -Steuerelement hinzu.

3. Legen Sie die **Text**-Eigenschaft des **Label**-Steuerelements auf den folgenden Ausdruck fest:<br>
   **ThisItem.Name**

    ![Bezeichnung hinzufügen](./media/gallery-dynamic-sizing/add-text-box.png)

## <a name="show-the-product-overviews"></a>Anzeigen der Produktübersichten
1. Fügen Sie der ausgewählten Katalogvorlage ein weiteres **Label**-Steuerelement hinzu, und verschieben Sie es unter das erste **Label**-Steuerelement.  

2. Legen Sie die **Text**-Eigenschaft des zweiten **Label**-Steuerelements auf den folgenden Ausdruck fest:<br> **ThisItem.Overview**

3. Wählen Sie das zweite **Label**-Steuerelement aus, klicken oder tippen Sie auf das Namensschildsymbol auf der Registerkarte **Inhalt**, und benennen Sie das Steuerelement in **OverviewText** um.

    ![Umbenennen der Bezeichnung](./media/gallery-dynamic-sizing/rename-text-box.png)

4. Legen Sie die **AutoHeight**-Eigenschaft des **OverviewText**-Felds auf **true** fest.

    Dadurch wird sichergestellt, dass die Größe des Felds an seinen Inhalt angepasst wird.

      ![Automatische Texthöhe](./media/gallery-dynamic-sizing/autoheight-text.png)

## <a name="show-the-product-images"></a>Anzeigen der Produktbilder
1. Verdoppeln Sie die Größe der Vorlage.

    Sie können der Vorlage beim Erstellen der App leichter Steuerelemente hinzufügen, und diese Änderung hat keine Auswirkung auf das Aussehen der App während ihrer Ausführung.

2. Fügen Sie der ausgewählten Katalogvorlage ein **[Bild](controls/control-image.md)**-Steuerelement hinzu, und verschieben Sie es unter das Feld **OverviewText**.

3. Stellen Sie sicher, dass die **Image**-Eigenschaft des **Bild**-Steuerelements auf den folgenden Ausdruck festgelegt ist:<br>
    **ThisItem.Image**

4. Legen Sie die **[Y](controls/properties-core.md)**-Eigenschaft des **Bild**-Steuerelements entsprechend der Position und Größe des Felds **OverviewText** fest, wie in dem folgenden Ausdruck:
   <br>**OverviewText.Y + OverviewText.Height + 5**

    ![Fertiggestellte App](./media/gallery-dynamic-sizing/final-app.png)

Wenden Sie das gleiche Konzept an, wenn Sie weitere Steuerelemente hinzufügen möchten: Legen Sie die **Y**-Eigenschaft jedes Steuerelements auf Grundlage der **Y**-Eigenschaft und **Height**-Eigenschaft des über ihm angeordneten Steuerelements fest.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zum Arbeiten mit einem [Katalog](working-with-forms.md)-Steuerelement und [Formeln](working-with-formulas.md).
