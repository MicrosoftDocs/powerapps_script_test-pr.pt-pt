---
title: Funktionen „EditForm“, „NewForm“, „SubmitForm“, „ResetForm“ und „ViewForm“ | Microsoft-Dokumentation
description: Referenzinformationen mit Syntax und Beispielen für die Funktionen „EditForm“, „NewForm“, „SubmitForm“, „ResetForm“ und „ViewForm“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 55df8d30509720478c1594406865986ddc9a95c4
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865806"
---
# <a name="editform-newform-submitform-resetform-and-viewform-functions-in-powerapps"></a>Funktionen „EditForm“, „NewForm“, „SubmitForm“, „ResetForm“ und „ViewForm“ in PowerApps
Zeigen Sie ein Element an, bearbeiten oder erstellen Sie ein Element, speichern Sie den Inhalt und setzen Sie die Steuerelemente in einem **[Bearbeitungsformular](../controls/control-form-detail.md)**-Steuerelement zurück.

## <a name="overview"></a>Übersicht
Diese Funktionen ändern den Status des **Bearbeitungsformular**-Steuerelements.  Das Formularsteuerelement kann sich in einem dieser Modi befinden:

| Modus | Beschreibung |
| --- | --- |
| **FormMode.Edit** |Das Formular wird mit einem vorhandenen Datensatz gefüllt, und der Benutzer kann die Werte der Felder ändern.  Sobald der Vorgang abgeschlossen ist, kann der Benutzer die am Datensatz vorgenommenen Änderungen speichern. |
| **FormMode.New** |Das Formular wird mit Standardwerten gefüllt, und der Benutzer kann die Werte der Felder ändern.  Anschließend kann der Benutzer den Datensatz der Datenquelle hinzufügen. |
| **FormMode.View** |Das Formular wird mit einem vorhandenen Datensatz gefüllt, der Benutzer kann die Werte der Felder jedoch nicht ändern. |

## <a name="description"></a>Beschreibung
Diese Funktionen werden häufig von der **[OnSelect](../controls/properties-core.md)**-Formel eines **[Button](../controls/control-button.md)**- oder **[Image](../controls/control-image.md)**-Steuerelements aufgerufen, sodass der Benutzer Änderungen speichern oder verwerfen oder einen Eintrag erstellen kann. Sie können [Steuerelemente und diese Funktionen zusammen verwenden](../working-with-forms.md), um eine vollständige Lösung zu erstellen.

Diese Funktionen geben keine Werte zurück.

### <a name="submitform"></a>SubmitForm
Verwenden Sie die **SubmitForm**-Funktion in der **[OnSelect](../controls/properties-core.md)**-Eigenschaft eines Button-Steuerelements, um Änderungen in einem Formularsteuerelement in die Datenquelle zu speichern.

Vor dem Übermitteln von Änderungen überprüft diese Funktion jedes Feld, das als erforderlich markiert ist oder eine oder mehrere Einschränkungen für den Wert hat, auf Validierungsprobleme. Dieses Verhalten entspricht dem der **[Validate](function-validate.md)**-Funktion.

**SubmitForm** überprüft auch die **[Valid](../controls/control-form-detail.md)**-Eigenschaft des Formulars, die eine Aggregation aller **[Valid](../controls/control-card.md)**-Eigenschaften der **[Card](../controls/control-card.md)**-Steuerelemente ist, die das Formularsteuerelement enthält. Wenn ein Problem auftritt, werden die Daten nicht übermittelt, und die Eigenschaften **[Error](../controls/control-form-detail.md)** und **[ErrorKind](../controls/control-form-detail.md)** des Formularsteuerelements werden entsprechend festgelegt.

Wenn die Validierung erfolgreich war, übermittelt **SubmitForm** die Änderung an die Datenquelle.

* Bei erfolgreicher Ausführung wird das **[OnSuccess](../controls/control-form-detail.md)**-Verhalten des Formulars ausgeführt, und die Eigenschaften **[Error](../controls/control-form-detail.md)** und **[ErrorKind](../controls/control-form-detail.md)** werden gelöscht.  Wenn das Formular im **FormMode.New**-Modus war, wird es zurück in den **FormMode.Edit**-Modus gesetzt.
* Bei erfolgloser Ausführung wird das **[OnFailure](../controls/control-form-detail.md)**-Verhalten des Formulars ausgeführt, und die Eigenschaften **[Error](../controls/control-form-detail.md)** und **[ErrorKind](../controls/control-form-detail.md)** werden entsprechend festgelegt.  Der Modus des Formulars bleibt unverändert.  

### <a name="editform"></a>EditForm
Die **EditForm**-Funktion ändert den Modus des Formularsteuerelements in **FormMode.Edit**. In diesem Modus wird der Inhalt der **[Item](../controls/control-form-detail.md)**-Eigenschaft des Formularsteuerelements verwendet, um das Formular zu füllen.  Wenn die **SubmitForm**-Funktion ausgeführt wird, während sich das Formular in diesem Modus befindet, wird ein Datensatz geändert, nicht erstellt.  **FormMode.Edit** ist der Standardmodus für das Formularsteuerelement.

### <a name="newform"></a>NewForm
Die **NewForm**-Funktion ändert den Modus des Formularsteuerelements in **FormMode.New**. In diesem Modus wird der Inhalt der **[Item](../controls/control-form-detail.md)**-Eigenschaft des Formularsteuerelements ignoriert, und das Formular wird mit den Standardwerten der **[DataSource](../controls/control-form-detail.md)**-Eigenschaft des Formulars aufgefüllt. Wenn die **SubmitForm**-Funktion ausgeführt wird, während sich das Formular in diesem Modus befindet, wird ein Datensatz erstellt, nicht geändert.

### <a name="resetform"></a>ResetForm
Die **ResetForm**-Funktion setzt den Inhalt eines Formulars auf die ursprünglichen Werte zurück, bevor vom Benutzer Änderungen vorgenommen wurden. Wenn sich das Formular im **FormMode.New**-Modus befindet, wird das Formular in den **FormMode.Edit**-Modus zurückgesetzt. Das **[OnReset](../controls/control-form-detail.md)**-Verhalten der Formularsteuerelemente wird ebenfalls ausgeführt.  Sie können einzelne Steuerelemente auch mit der **[Reset](function-reset.md)**-Funktion zurücksetzen, jedoch lediglich innerhalb des Formulars.

### <a name="viewform"></a>ViewForm
Die **ViewForm**-Funktion ändert den Modus des Formularsteuerelements in **FormMode.View**. In diesem Modus wird der Inhalt der **[Item](../controls/control-form-detail.md)**-Eigenschaft des Formularsteuerelements verwendet, um das Formular zu füllen.  Die **SubmitForm**-Funktion und die **RestForm**-Funktion haben in diesem Modus keine Auswirkungen.

### <a name="displaymode-poperty"></a>DisplayMode-Eigenschaft
Der aktuelle Modus kann über die **Mode**-Eigenschaft gelesen werden.  Der Modus bestimmt zudem den Wert der **DisplayMode**-Eigenschaft, der von Datenkarten und Steuerelementen innerhalb des Formularsteuerelements verwendet werden kann.  Häufig wird die **DisplayMode**-Eigenschaft der Datenkarte auf **Parent.DisplayMode** festgelegt (womit auf das Formular verwiesen wird); dasselbe gilt für die **DisplayMode**-Eigenschaft des Steuerelements (womit auf die Datenkarte verwiesen wird): 

| Modus | DisplayMode | Beschreibung |
| --- | --- | --- |
| **FormMode.Edit** |**DisplayMode.Edit** |Datenkarten und Steuerelemente können bearbeitet werden; Änderungen an einem Datensatz können akzeptiert werden. |
| **FormMode.New** |**DisplayMode.Edit** |Datenkarten und Steuerelemente können bearbeitet werden; ein neuer Datensatz kann akzeptiert werden. |
| **FormMode.View** |**DisplayMode.View** |Datenkarten und Steuerelemente sind nicht bearbeitbar und für die Anzeige optimiert. |

## <a name="syntax"></a>Syntax
**SubmitForm**( *FormularName* )

* *FormularName*: Erforderlich. Formularsteuerelement zum Übermitteln an die Datenquelle.

**EditForm**( *FormularName* )

* *FormularName*: Erforderlich.  Formularsteuerelement zum Wechseln in den **FormMode.Edit**-Modus.

**NewForm**( *FormularName* )

* *FormularName*: Erforderlich. Formularsteuerelement zum Wechseln in den **FormMode.New**-Modus.

**ResetForm**( *FormularName* )

* *FormularName*: Erforderlich. Formularsteuerelement zum Zurücksetzen auf die ursprünglichen Werte. Ändert zudem den Modus des Formulars von **FormMode.New** in **FormMode.Edit**.

**ViewForm**( *Formularname* )

* *FormularName*: Erforderlich.  Formularsteuerelement zum Wechseln in den **FormMode.View**-Modus.

## <a name="examples"></a>Beispiele
Ausführliche Beispiele finden Sie unter [Understand data forms (Grundlegendes zu Datenformularen)](../working-with-forms.md).

1. Fügen Sie ein Button-Steuerelement hinzu, legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf **Save** (Speichern) und dessen **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **SubmitForm( EditForm )**
2. Legen Sie die **[OnFailure](../controls/control-form-detail.md)**-Eigenschaft eines Formularsteuerelements auf leer und die **[OnSuccess](../controls/control-form-detail.md)**-Eigenschaft auf diese Formel fest:
   
    **Back()**
3. Nennen Sie ein **[Label](../controls/control-text-box.md)**-Steuerelement **ErrorText**, und legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **EditForm.Error**
   
    Wenn der Benutzer die Schaltfläche **Save** (Speichern) auswählt, werden alle am Formularsteuerelement vorgenommenen Änderungen an die zugrunde liegende Datenquelle übermittelt.
   
   * Wenn die Übermittlung erfolgreich ist, werden alle Änderungen gespeichert. Wenn sich das Formularsteuerelement im **New**-Modus (Neu) befindet, wird stattdessen ein Datensatz erstellt. **ErrorText** ist *leer* und die vorherige Ansicht wird erneut angezeigt.
   * Wenn die Übermittlung fehlschlägt, zeigt **ErrorText** eine benutzerfreundliche Fehlermeldung an, und die aktuelle Ansicht bleibt sichtbar, sodass der Benutzer das Problem beheben und den Vorgang wiederholen kann.
4. Fügen Sie ein Button-Steuerelement hinzu, legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf **Cancel** (Abbrechen) und dessen **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **ResetForm( EditForm ); Back()**
   
    Wenn der Benutzer die Schaltfläche **Cancel** (Abbrechen) auswählt, werden die Werte im Formularsteuerelement in den Zustand vor der Bearbeitung durch den Benutzer zurückgesetzt, die vorherige Ansicht wird erneut angezeigt, und das Formularsteuerelement wird in den **Edit**-Modus (Bearbeiten) zurückgesetzt, wenn es sich im **New**-Modus (Neu) befand.
5. Fügen Sie ein Button-Steuerelement hinzu, legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf **New** (Neu) und dessen **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **NewForm( EditForm ); Navigate( EditScreen, None )**
   
    Wenn der Benutzer die Schaltfläche **New** (Neu) auswählt, wechselt das Formularsteuerelement in den **New**-Modus (Neu), das Steuerelement wird mit den Standardwerten für die Datenquelle des Formularsteuerelements aufgefüllt, und das Formular mit dem Formularsteuerelement wird angezeigt. Wenn die **SubmitForm**-Funktion ausgeführt wird, wird ein Datensatz erstellt anstatt aktualisiert.

