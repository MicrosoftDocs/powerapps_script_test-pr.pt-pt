---
title: Grundlegendes zur Integration von SharePoint-Formularen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie benutzerdefinierte Formulare mit SharePoint verwendet werden.
author: sarafankit
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/11/2017
ms.author: ankitsar
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 341d6973504ba50dbeeb058019a32196f72ec8c5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864927"
---
# <a name="understand-sharepoint-forms-integration"></a>Grundlegendes zur Integration von SharePoint-Formularen
Sie können jetzt in PowerApps [jedes SharePoint-Listenformular leicht anpassen](customize-list-form.md). In diesem Artikel wird die Funktionsweise dieser Formulare erläutert und beschrieben, wie Sie sie weiter anpassen können.

Wenn Sie ein Formular für eine SharePoint-Liste angepasst haben, ist Ihnen wahrscheinlich aufgefallen, dass das generierte Standardformular für alle Vorgänge, z.B. das Erstellen, Anzeigen oder Bearbeiten eines Elements, verwendet werden kann. Dies erfolgt mithilfe generierter Formeln und des **SharePointIntegration**-Steuerelements.

## <a name="understand-the-default-generated-form"></a>Grundlegendes zum generierten Standardformular

Das generierte Standardformular besteht aus den folgenden Steuerelementen und den entsprechenden Standardwerten:

* **FormScreen1** – Dies ist der [Bildschirm](controls/control-screen.md), der das Formular enthält.

* **SharePointForm1** – Dies ist das [Formular](working-with-forms.md), das zum Erstellen, Anzeigen oder Bearbeiten des Listenelements verwendet wird.

    * **Datenquelle** – Die Liste, für die das Formular angepasst wurde.

    * **Item** – Das in der Liste ausgewählte Element. Dieses wird in PowerApps Studio der Einfachheit halber auf das erste Element (First()) in der Liste festgelegt.

        **If(IsBlank(SharePointIntegration.Selected) || IsEmpty(SharePointIntegration.Selected),First('*YourListName*'),SharePointIntegration.Selected)**

    * **OnSuccess** – Sobald das Element erfolgreich erstellt oder gespeichert wurde, wird das Formular zurückgesetzt und von SharePoint ausgeblendet.

        **ResetForm(SharePointForm1); RequestHide()**

* **SharePointIntegration** – Das Steuerelement für die Übermittlung von Benutzeraktionen zwischen SharePoint und PowerApps.

    * **Datenquelle** – Die Liste, für die das Formular angepasst wurde.

        **'*YourListName*'**

    * **OnNew** – Legt **SharePointForm1** im Modus „Neu“ fest.

        **NewForm(SharePointForm1)**

    * **OnView** – Legt **SharePointForm1** im Ansichtsmodus fest.

        **ViewForm(SharePointForm1)**

    * **OnEdit** – Legt **SharePointForm1** im Bearbeitungsmodus fest.

        **EditForm(SharePointForm1)**

    * **OnSave** – Übermittelt die Änderungen an **SharePointForm1**. Bei erfolgreicher Übermittlung des Formulars wird die Formel **SharePointForm1.OnSuccess** ausgeführt.

        **SubmitForm(SharePointForm1)**

    * **OnCancel** – Macht die Änderungen an **SharePointForm1** rückgängig. Das Formular wird immer ausgeblendet, wenn der Benutzer in SharePoint auf **Abbrechen** klickt oder tippt.

        **ResetForm(SharePointForm1)**

Durch diese Standardwerte wird sichergestellt, dass das Formular bei Ausführung innerhalb von SharePoint funktioniert. Es wird der PowerApps-Formularmodus geändert, wenn der Benutzer in SharePoint mit dem Formular interagiert, und sichergestellt, dass die Änderungen an SharePoint übermittelt werden.

## <a name="understand-the-sharepointintegration-control"></a>Grundlegendes zum SharePointIntegration-Steuerelement
Das **SharePointIntegration**-Steuerelement übermittelt Benutzeraktionen zwischen SharePoint und PowerApps.

![](./media/sharepoint-form-integration/sharepointintegration-object.png)

>[!NOTE]
>Sie können nur auf die Eigenschaften des **SharePointIntegration**-Steuerelements zugreifen, wenn das Formular in SharePoint ausgeführt wird. Beim Anpassen des Formulars in PowerApps Studio ist dies nicht möglich. Diese Eigenschaften sind in **OnStart** oder **OnVisible** möglicherweise nicht verfügbar. 

Das **SharePointIntegration**-Steuerelement verfügt über die folgenden Eigenschaften:

**Selected** – Das in der SharePoint-Liste ausgewählte Element.

**OnNew** – Legt fest, wie eine App reagiert, wenn ein Benutzer auf die Schaltfläche **Neu** klickt oder tippt oder in SharePoint das Formular **Element erstellen** öffnet.

**OnView** – Legt fest, wie eine App reagiert, wenn ein Benutzer auf ein **Element** klickt oder tippt oder in SharePoint das Formular **Elementdetail** öffnet.

**OnEdit** – Legt fest, wie eine App reagiert, wenn ein Benutzer auf die Schaltfläche **Alle bearbeiten** klickt oder tippt oder in SharePoint das Formular **Element bearbeiten** öffnet.

**OnSave** – Legt fest, wie eine App reagiert, wenn ein Benutzer in SharePoint auf die Schaltfläche **Speichern** klickt oder tippt.

**OnCancel** – Legt fest, wie eine App reagiert, wenn ein Benutzer in SharePoint auf die Schaltfläche **Abbrechen** klickt oder tippt.

**SelectedListItemID** – Die Element-ID des ausgewählten Elements in einer SharePoint-Liste.

**Datenquelle** – Die Liste, die den Datensatz enthält, der im Formular angezeigt, bearbeitet oder erstellt wird. Beachten Sie, dass nach dem Ändern dieser Eigenschaft die Eigenschaften **Selected** und **SelectedItemID** möglicherweise nicht mehr ordnungsgemäß angewendet werden.

## <a name="customize-the-default-form"></a>Anpassen des Standardformulars
Nachdem Sie einen Einblick in die Funktionsweise des generierten Standardformulars und des **SharePointIntegration**-Steuerelements erhalten haben, können Sie die Formeln ändern, um die Formulare weiter anzupassen. Beachten Sie beim Anpassen von Formularen folgende Punkte:

* Um für das Erstellen, Anzeigen oder Bearbeiten eines Elements jeweils eigene benutzerdefinierte Erfahrungen zu erstellen, legen Sie die Formel **OnNew**, **OnView** bzw. **OnEdit** des **SharePointIntegration**-Steuerelements auf das Festlegen von Variablen oder das Navigieren zu unterschiedlichen Bildschirmen fest.

* Passen Sie mit der Formel **OnSave** des **SharePointIntegration**-Steuerelements an, was geschieht, wenn ein Benutzer in SharePoint auf **Speichern** klickt oder tippt. Wenn Sie über mehrere Formulare verfügen, stellen Sie sicher, dass nur die Änderungen für das derzeit verwendete Formular übermittelt werden.

  > [!TIP]
  >    Legen Sie in den Formeln **OnNew**, **OnView** und **OnEdit** unterschiedliche Werte für eine Variable fest. Sie können mit dieser Variablen in der Formel **OnSave** bestimmen, welches Formular verwendet wird.

* Schließen Sie in die Formel **OnSuccess** aller Formulare **RequestHide()** ein. Wenn Sie dies vergessen, weiß SharePoint nicht, wann das Formular ausgeblendet werden soll.

* Sie können nicht steuern, dass ein Formular ausgeblendet wird, wenn ein Benutzer in SharePoint auf **Abbrechen** tippt oder klickt. Stellen Sie deshalb in der Formel **OnCancel** des **SharePointIntegration**-Steuerelements sicher, dass die Formulare zurückgesetzt werden.

* Die Eigenschaften des **SharePointIntegration**-Steuerelements sind in **OnStart** oder **OnVisible** möglicherweise nicht verfügbar, und diese Ereignisse werden nur einmal ausgeführt, während die Liste geladen wird. Logik lässt sich mithilfe der Formeln **OnNew**, **OnView** oder **OnEdit** ausführen, bevor das Formular dem Benutzer angezeigt wird. 
