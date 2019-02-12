---
title: Anzeigen, Bearbeiten und Hinzufügen eines Datensatzes aus einer Tabelle in eine Canvas-App | Microsoft-Dokumentation
description: Mithilfe eines Canvas-App-Formulars können Sie einen Datensatz aus einer Tabelle in der Datenquelle anzeigen, bearbeiten oder hinzufügen.
author: karthik-1
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/06/2017
ms.author: sharik
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 853f54448b3cf29ebd108299ca69cc96ce51be19
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42854811"
---
# <a name="show-edit-or-add-a-record-from-a-table-in-powerapps"></a>Datensatz aus einer Tabelle in PowerApps anzeigen, bearbeiten oder hinzufügen

Wenn alle Felder in einem Datensatz angezeigt werden sollen, müssen Sie ein **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement in eine Canvas-App hinzufügen und es konfigurieren. Wenn Sie ein Feld in einem Datensatz bearbeiten (bzw. einen Datensatz hinzufügen) und die Änderungen in einer Datenquelle speichern möchten, fügen Sie ein **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement zu einer Canvas-App hinzu, und konfigurieren Sie dieses.

## <a name="prerequisites"></a>Voraussetzungen

* Erfahren Sie, wie Sie in PowerApps [ein Steuerelement hinzufügen und konfigurieren](add-configure-controls.md).
* Laden Sie [diese Excel-Datei](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) mit Beispieldaten für dieses Lernprogramm herunter.
* Laden Sie die Excel-Datei in ein [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md) hoch, z.B. in OneDrive for Business.
* [Fügen Sie eine Verbindung](add-data-connection.md) in einer neuen oder vorhandenen App zur **FlooringEstimates**-Tabelle in der Excel-Datei hinzu.
* Bei Verwendung einer vorhandenen App müssen Sie dieser [einen Bildschirm hinzufügen](add-screen-context-variables.md).

## <a name="add-a-form-and-show-data"></a>Hinzufügen eines Formulars und Anzeigen von Daten
1. Fügen Sie ein **[Dropdown](controls/control-drop-down.md)**-Steuerelement hinzu, weisen Sie ihm den Namen **ChooseProduct** hinzu, und legen Sie seine **[Items](controls/properties-core.md)**-Eigenschaft auf diesen Wert fest:

    **FlooringEstimates.Name**

    > [!NOTE]
   > Weitere Informationen zum Hinzufügen und Umbenennen eines Steuerelements sowie zum Festlegen einer Eigenschaft finden Sie unter [Hinzufügen und Konfigurieren eines Steuerelements](add-configure-controls.md).

    In der Liste werden Namen von Bodenbelägen aus der Datenquelle aufgeführt.

2. Fügen Sie ein **Formular bearbeiten**-Steuerelement hinzu, verschieben Sie es unter **ChooseProduct**, und ändern Sie dann die Größe des Formulars, sodass es den größten Teil des Bildschirms einnimmt.

    ![Ein Formular hinzufügen](./media/add-form/add-a-form.png)

    > [!NOTE]
   > In diesem Artikel wird das **Formular bearbeiten**-Steuerelement beschrieben, gleiche Prinzipien gelten jedoch auch für das **Formular anzeigen**-Steuerelement.

3. Legen Sie die **[DataSource](controls/control-form-detail.md)**-Eigenschaft des Formulars auf **FlooringEstimates** und die **[Item](controls/control-form-detail.md)**-Eigenschaft des Formulars auf diese Formel fest:

   **First(Filter(FlooringEstimates, Name=ChooseProduct.Selected.Value))**

   Mit dieser Formel wird angegeben, dass im Formular nach abgeschlossener Konfiguration der Datensatz angezeigt wird, den der Benutzer in **ChooseProduct** auswählt.

4. Klicken oder tippen Sie im Bereich **Daten** auf das Kontrollkästchen jedes Felds, um es anzuzeigen.

    > [!NOTE]
   > Wenn der Bereich **Daten** geschlossen ist, öffnen Sie ihn, indem Sie links das Formular auswählen und anschließend rechts auf **Daten** klicken oder tippen.

    ![Anzeigen der Felder im Formular](./media/add-form/checkbox.png)

5. Ziehen Sie im Bereich **Daten** den Eintrag **Name** in der Liste an die oberste Stelle.

    ![Karte verschieben](./media/add-form/drag-field.png)

    Das **Formular bearbeiten**-Steuerelement spiegelt die vorgenommene Änderung wider.

    ![„Name“ an oberster Position](./media/add-form/move-card-form.png)

## <a name="set-the-card-type-for-a-field"></a>Festlegen des Kartentyps für ein Feld
1. Klicken oder tippen Sie bei ausgewähltem Formular auf die Kartenauswahl für **Price** im Bereich **Daten**.

    ![Kartenauswahl](./media/add-form/price-card2.png)

2. Scrollen Sie nach unten, und klicken oder tippen Sie auf die Option **Text anzeigen**, um das Feld als schreibgeschützt festzulegen.

    ![Text anzeigen](./media/add-form/view-text.png)

    Das Formular spiegelt die vorgenommene Änderung wider.

    ![Schreibgeschützte Zahl](./media/add-form/read-only.png)  

## <a name="edit-form-only-save-changes"></a>(Nur „Formular bearbeiten“) Speichern der Änderungen
1. Wählen Sie im linken Bereich das Formular aus, und klicken oder tippen Sie auf die Auslassungspunkte (...).

   ![Formular auswählen](./media/add-form/select-form.png)

2. Klicken oder tippen Sie auf **Umbenennen**, und benennen Sie das Formular in **EditForm** um.

3. Fügen Sie ein **[Button](controls/control-button.md)**-Steuerelement hinzu, und legen Sie seine **[Text](controls/properties-core.md)**-Eigenschaft auf **Save** fest.

    ![Hinzufügen einer Schaltfläche „Save“](./media/add-form/save-button.png)  

4. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft der Schaltfläche **Save** auf diese Formel fest:

   **SubmitForm(EditForm)**

5. Öffnen Sie den Vorschaumodus, indem Sie auf die Wiedergabeschaltfläche in der oberen rechten Ecke klicken oder tippen (oder indem Sie F5 drücken).

    ![Öffnen des Vorschaumodus](./media/add-form/open-preview.png)

6. Ändern Sie den Namen eines Produkts, und klicken oder tippen Sie anschließend auf die soeben erstellte Schaltfläche **Save**.

    Die **[SubmitForm](functions/function-form.md)**-Funktion speichert die Änderungen an der Datenquelle, mit der das Formular konfiguriert wurde.

7. (optional) Wählen Sie das Schließen-Symbol aus, um die Vorschau zu schließen (Sie können auch ESC drücken).

    ![Schließen der Vorschau](./media/add-form/close-preview.png)

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie mehr über das Arbeiten mit [Formularen](working-with-forms.md) und [Formeln](working-with-formulas.md).
