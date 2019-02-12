---
title: Scannen eines Barcodes in einer Canvas-App | Microsoft-Dokumentation
description: Scannen Sie eine Vielzahl von Barcodetypen, z.B. UPC und Codabar.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2016
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9b826b66dd1d7d5cb51d464070e087c94dd189b6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849541"
---
# <a name="scan-a-barcode-in-powerapps"></a>Scannen eines Barcodes in PowerApps

Scannen Sie verschiedene Arten von Barcodes, indem Sie eine Canvas-App erstellen und auf einem Gerät ausführen, z.B. auf einem Mobiltelefon, das über eine Kamera verfügt. Die numerische Darstellung des Barcodes wird in einem **Label** (Bezeichnung) angezeigt, und Sie können diese Daten in eine Vielzahl von [Datenquellen](connections-list.md) hochladen.

Wenn Sie mit PowerApps nicht vertraut sind, sehen Sie sich den Abschnitt [Erste Schritte](getting-started.md) an.

## <a name="known-limitations"></a>Bekannte Einschränkungen

* Barcodes müssen mindestens 2,5 cm hoch und 4 cm breit sein.
* Um Barcodes mit einem Telefon zu scannen, halten Sie es hochkant, und bewegen Sie es langsam zwischen 18 cm bis 25 cm vom Barcode entfernt.
* Lange Barcodetypen, (z.B. I2of5-Barcodes, die 15 Zeichen oder mehr umfassen können), können zu abgeschnittenen oder anderweitig fehlerhaften Ergebnissen führen – insbesondere dann, wenn der Barcode nicht deutlich gedruckt ist.
* Für iPhones und Android-Geräte können Sie die Eigenschaft **Höhe** für das Steuerelement **Barcode** angeben, aber die Breite wird durch ein festgelegtes Seitenverhältnis bestimmt.
* Sie müssen außerdem möglicherweise die Eigenschaft **Scanrate** des Steuerelements **Barcode** auf **35** oder einen niedrigeren Wert festlegen.
* Um auf iOS-Geräten zu verhindern, dass zu schnell kein Arbeitsspeicher mehr verfügbar ist, legen Sie die Eigenschaft für die **Höhe** des Steuerelements **Barcode** auf **700** (oder niedriger) und die Eigenschaft **Scanrate** auf **30** fest.
* Wenn das Gerät nicht mehr genügend Arbeitsspeicher aufweist und die App nicht mehr reagiert, starten Sie die App neu.

## <a name="create-a-blank-app"></a>Erstellen einer leeren App
1. [Registrieren](../signup-for-powerapps.md) Sie sich für PowerApps, und führen Sie anschließend *eine* der folgenden Aktionen aus:

2. [Öffnen Sie PowerApps](https://create.powerapps.com) in einem Browser auf einem Gerät, das über eine Kamera verfügt.

3. Klicken oder tippen Sie auf der Kachel **Leere App** unter **Starten Sie mit einem leeren Zeichenbereich oder einer Vorlage** auf **Telefonlayout**.

    ![App von Grund auf neu erstellen](./media/scan-barcode/create-from-blank.png)

4. Wenn Sie mit PowerApps nicht vertraut sind, schauen Sie sich die Einführung an (oder klicken oder tippen Sie auf **Überspringen**).

    ![Begrüßungsbildschirm der Schnelleinführung](./media/scan-barcode/quick-tour.png)

    > [!NOTE]
   > Sie können sich die Einführung jederzeit später anschauen. Klicken oder tippen Sie hierzu auf das Fragezeichen-Symbol in der Nähe der oberen rechten Ecke, und klicken oder tippen Sie anschließend auf **Take the intro tour**.

## <a name="add-a-barcode-control"></a>Hinzufügen eines Barcodesteuerelements
1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Medien** und anschließend auf **Barcode**.

    ![Hinzufügen eines Barcodescanners](./media/scan-barcode/add-scanner.png)

2. Stellen Sie sicher, dass das Steuerelement **Barcode** ausgewählt ist. Es sollte von einem Auswahlfeld (mit Handles zum Ändern der Steuerelementgröße) umgeben sein.

    ![Auswahlfeld](./media/scan-barcode/selection-box.png)

3. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Barcode1**, und fügen oder geben Sie unter **Umbenennen** den Namen **MyScanner** ein.

    > [!TIP]
   > Das erste **Barcode**-Steuerelement, das Sie hinzufügen, erhält standardmäßig den Namen **Barcode1**. Wenn Sie dieses Steuerelement löschen und ein weiteres Steuerelement **Barcode** hinzufügen, erhält dieses standardmäßig den Namen **Barcode2**. Durch das manuelle Umbenennen eines Steuerelements stellen Sie sicher, dass Formeln mit dem richtigen Namen auf das Steuerelement verweisen.

    ![Umbenennen des Barcodesteuerelements](./media/scan-barcode/rename-barcode.png)

## <a name="add-a-text-input-control"></a>Hinzufügen eines Steuerelements für die Texteingabe
1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Text** und anschließend auf **Texteingabe**.

    Wenn die Registerkarte **Einfügen** nicht angezeigt wird, maximieren Sie Ihr PowerApps-Fenster.

    ![Hinzufügen eines Steuerelements für die Texteingabe](./media/scan-barcode/add-text-input.png)

2. Ziehen Sie das Auswahlfeld (nicht die Handles zur Größenänderung) um das Steuerelement **Texteingabe** nach unten, bis **MyScanner** angezeigt wird.

    ![Bezeichnung mit Auswahlfeld](./media/scan-barcode/move-input-text.png)

3. Stellen Sie bei weiterhin ausgewähltem Steuerelement **Texteingabe** sicher, dass in der Eigenschaftenliste **Standard** angezeigt wird, und fügen oder geben Sie dann in der Bearbeitungsleiste **MyScanner.Text** ein.

    ![Texteigenschaft des Label-Steuerelements](./media/scan-barcode/default-text.png)

## <a name="change-the-barcode-type"></a>Ändern des Barcodetyps
1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Steuerelemente**, und klicken oder tippen Sie anschließend auf **Dropdown**.

    ![Hinzufügen einer Dropdownliste](./media/scan-barcode/insert-dropdown.png)

2. Verschieben Sie das Steuerelement **Dropdown** so, dass es unterhalb der weiteren Steuerelemente auf dem Bildschirm angezeigt wird.

    ![Verschieben der Dropdownliste](./media/scan-barcode/move-dropdown.png)

3. Stellen Sie bei weiterhin ausgewähltem Steuerelement **Dropdown** sicher, dass in der Eigenschaftenliste **Items** angezeigt wird, und fügen oder geben Sie dann in der Bearbeitungsleiste die folgende Textzeichenfolge ein:<br>
    **[Codabar, Code128, Code39, Ean, I2of5, Upc]**

    ![Festlegen der Items-Eigenschaft der Dropdownliste](./media/scan-barcode/items-property.png)

4. Benennen Sie auf der Registerkarte **Start** das Steuerelement **Dropdown** in **ChooseType** um.

    ![Umbenennen der Dropdownliste](./media/scan-barcode/rename-dropdown.png)

5. Klicken oder tippen Sie auf **MyScanner**, um das Element auszuwählen. Stellen Sie sicher, dass in der Eigenschaftenliste **BarcodeType** angezeigt wird, und fügen oder geben Sie dann in der Bearbeitungsleiste die folgende Textzeichenfolge ein:<br>
    **ChooseType.Selected.Value**

## <a name="test-the-app"></a>Testen der App
1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Klicken oder Tippen der Schaltfläche zu Wiedergabe in der Nähe der oberen rechten Ecke).

    ![Öffnen des Vorschaumodus](./media/scan-barcode/open-preview.png)

2. Halten Sie einen Barcode an die Kamera auf dem Gerät, bis der numerische Anteil des Barcodes im Steuerelement **Bezeichnung** angezeigt wird.

    Wenn der numerische Anteil nicht angezeigt wird, versuchen Sie es mit einer anderen Option in der Liste **BarcodeType**. Wenn weiterhin nicht die richtigen Daten angezeigt werden, geben Sie die richtige Nummer im Steuerelement **Texteingabe** ein.

## <a name="next-steps"></a>Nächste Schritte
* [Verbinden Sie die App mit einer Datenquelle](add-data-connection.md), und konfigurieren Sie die Funktion **[Patch](functions/function-patch.md)**, damit die Benutzer Ergebnisse speichern können.
* Fügen Sie ein Steuerelement **[Dropdown](controls/control-drop-down.md)** hinzu, und konfigurieren Sie es so, dass der Benutzer auswählen kann, welche Art von Barcode gescannt werden soll.
* Fügen Sie ein Steuerelement **[Schieberegler](controls/control-slider.md)** hinzu, und konfigurieren Sie es so, dass der Benutzer die Scanrate oder die Höhe des Steuerelements **Barcode** anpassen kann.
