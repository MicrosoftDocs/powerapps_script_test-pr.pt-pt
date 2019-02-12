---
title: '„Formular anzeigen“- und „Formular bearbeiten“-Steuerelemente: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über die „Formular anzeigen“- und „Formular bearbeiten“-Steuerelemente
author: aneesmsft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2017
ms.author: aneesa
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 91f84ebbec83c5734e910680f4ab3a79077164df
ms.sourcegitcommit: ce621966a34061dda2f75232403847e21816ffa9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/30/2018
ms.locfileid: "47459453"
---
# <a name="edit-form-and-display-form-controls-in-powerapps"></a>„Formular anzeigen“- und „Formular bearbeiten“-Steuerelemente in PowerApps
Zeigen Sie Datensätze aus einer Datenquelle an, bearbeiten Sie diese und erstellen Sie neue.

## <a name="description"></a>Beschreibung
Wenn Sie ein **Formular anzeigen**-Steuerelement hinzufügen, können Benutzer alle Felder eines Datensatzes oder von Ihnen vorher festgelegte Felder anzeigen. Wenn Sie ein **Formular bearbeiten**-Steuerelement hinzufügen, können Benutzer die Felder bearbeiten, einen Datensatz erstellen und Änderungen in einer Datenquelle speichern.

![Beispielformular und Steuerelemente für die Anzeige von Formularen](./media/control-form-detail/form-detail-intro.png)

Wenn Sie ein **[Bildkatalog](control-gallery.md)**-Steuerelement hinzufügen, können Sie es so konfigurieren, dass in einer Datenquelle eine Tabelle angezeigt wird. Dann können Sie das Formular so konfigurieren, dass von Benutzern ausgewählte Datensätze in einem Bildkatalog angezeigt werden. Sie können auch eines oder mehrere **[Schaltflächen](control-button.md)**-Steuerelemente hinzufügen, mit denen Benutzer Bearbeitungen speichern oder abbrechen oder einen Datensatz erstellen können. Durch Kombination verschiedener Steuerelemente können Sie [eine vollständige Lösung erstellen](../working-with-forms.md).

### <a name="record-selection"></a>Datensatzauswahl
Bei beiden Formulartypen können Sie die Eigenschaft **DataSource** als Datensatztabelle und die **Item**-Eigenschaft so konfigurieren, dass ein bestimmter Datensatz in der Tabelle angezeigt wird. Beispiel: Sie können die **Item**-Eigenschaft eines Formulars als **SelectedItem**-Eigenschaft eines **[Bildkatalog](control-gallery.md)**-Steuerelements konfigurieren. Wenn der Benutzer im Bildkatalog einen Datensatz auswählt, wird er im Formular angezeigt (im Formular können mehr Felder dargestellt werden). Wenn der Benutzer zum Bildkatalog zurückkehrt und einen anderen Datensatz auswählt, ändert sich der Wert der **SelectedItem**-Eigenschaft des Bildkatalogs. Dadurch wird die **Item**-Eigenschaft des Formulars aktualisiert, wodurch der nun ausgewählte Datensatz angezeigt wird.

Sie können auch die **Item**-Eigenschaft eines Formulars mithilfe eines **Dropdown**-Steuerelements wie unter [Show, edit, or add a record (Anzeigen, Bearbeiten oder Hinzufügen eines Datensatzes)](../add-form.md) beschrieben festlegen. Alternativ können Sie Funktionen wie **Lookup** oder **First** verwenden. Sie können die **Item**-Eigenschaft auf eine der folgenden Formeln festlegen, um den Eintrag „Fabrikam“ in der Entität **Accounts** in Common Data Service für Apps anzuzeigen:

```First(Accounts)```

```Lookup(Accounts, "Fabrikam" in name)```

Jedes Formular enthält eines oder mehrere **[Karten](control-card.md)**-Steuerelemente. Durch Festlegen der **[DataField](control-card.md)**-Eigenschaft einer Karte können Sie [angeben, welche Felder auf der Karte angezeigt werden (und mehr)](../add-form.md).

### <a name="create-a-record"></a>Erstellen eines Datensatzes
Wenn sich ein **Formular bearbeiten**-Steuerelement im Modus **Bearbeiten** befindet, kann der Benutzer den Datensatz aktualisieren, der in der **Item**-Eigenschaft des Formulars angegeben ist. Die **Mode**-Eigenschaft gibt in diesem Fall **Edit** zurück.

Wenn sich ein **Formular bearbeiten**-Steuerelement im Modus **Neu** befindet, wird die **Item**-Eigenschaft allerdings ignoriert. Das Formular zeigt dann keinen bestehenden Datensatz an. Stattdessen entsprechen die Werte in allen Feldern den Standardwerten der Datenquelle, die zur Konfiguration des Formulars verwendet wurde. Mit der **[NewForm](../functions/function-form.md)**-Funktion wird ein Formular auf diesen Modus festgelegt.

Beispiel: Sie können mithilfe der **[Text](properties-core.md)**-Eigenschaft einer Schaltfläche deren Anzeigetext auf **Neu** festlegen und deren **[OnSelect](properties-core.md)**-Eigenschaft mit einem Formular verknüpfen, das die **[NewForm](../functions/function-form.md)**-Funktion enthält. Wenn ein Benutzer diese Schaltfläche verwendet, wechselt das Formular in den **New**-Modus. Der Benutzer kann dann einen Datensatz mit bekannten Werten erstellen.

Ein Formular wechselt zurück in den **Edit**-Modus, wenn die **[ResetForm](../functions/function-form.md)**-Funktion ausgeführt oder die **[SubmitForm](../functions/function-form.md)**-Funktion erfolgreich ausgeführt wird.

* Sie können mithilfe der **[Text](properties-core.md)**-Eigenschaft einer Schaltfläche deren Anzeigetext auf **Abbrechen** festlegen und deren **[OnSelect](properties-core.md)**-Eigenschaft mit einem Formular verknüpfen, das die **[ResetForm](../functions/function-form.md)**-Funktion enthält. Wenn der Benutzer diese Schaltfläche verwendet, werden jegliche Änderungen verworfen, und die Werte im Formular werden auf die Standardwerte aus der Datenquelle zurückgesetzt.
* Sie können mithilfe der **[Text](properties-core.md)**-Eigenschaft einer Schaltfläche deren Anzeigetext auf **Änderungen speichern** festlegen und deren **[OnSelect](properties-core.md)**-Eigenschaft mit einem Formular verknüpfen, das die **[SubmitForm](../functions/function-form.md)**-Funktion enthält. Wenn der Benutzer diese Schaltfläche verwendet, wird die Datenquelle aktualisiert, und die Werte im Formular werden auf die Standardwerte aus der Datenquelle zurückgesetzt.

### <a name="save-changes"></a>Änderungen speichern
Wenn Sie eine **Änderungen speichern**-Schaltfläche erstellen, wie im vorigen Abschnitt beschrieben, kann der Benutzer einen Datensatz erstellen oder aktualisieren und mit der Schaltfläche dann die Änderungen in der Datenquelle speichern. Sie können alternativ ein **[Bild](control-image.md)**-Steuerelement oder ein anderes Steuerelement verwenden, um die gleiche Aufgabe auszuführen, solange die **[SubmitForm](../functions/function-form.md)**-Funktion enthalten ist. In jedem Fall enthalten die Eigenschaften **Error**, **ErrorKind**, **OnSuccess** und **OnFailure** Informationen zum Ergebnis des Vorgangs.

Wenn die **[SubmitForm](../functions/function-form.md)**-Funktion ausgeführt wird, werden die Daten, die der Benutzer übermitteln möchte, zunächst überprüft. Wenn ein erforderliches Feld keinen Wert enthält oder ein Wert nicht den Anforderungen entspricht, wird die **ErrorKind**-Eigenschaft festgelegt und die **OnFailure**-Formel ausgeführt. Sie können die **Änderungen speichern**-Schaltfläche oder ein anderes Steuerelement so konfigurieren, dass der Benutzer sie bzw. es nur dann auswählen kann, wenn die Daten gültig sind (also die **Valid**-Eigenschaft des Formulars den Wert **true** hat). Beachten Sie, dass der Benutzer nicht nur das Problem beheben, sondern auch die **Änderungen speichern**-Schaltfläche erneut auswählen (oder, wie oben beschrieben, die Änderungen mithilfe der **Abbrechen**-Schaltfläche verwerfen) muss, damit die Eigenschaften **Error** und **ErrorKind** zurückgesetzt werden.

Wenn die Daten die Überprüfung durchlaufen haben, übermittelt die **[SubmitForm](../functions/function-form.md)**-Funktion sie an die Datenquelle, was abhängig von der Netzwerklatenz einige Zeit dauern kann.

* Wenn die Übermittlung erfolgreich ist, wird der Wert der **Error**-Eigenschaft gelöscht, die **ErrorKind**-Eigenschaft wird auf **ErrorKind.None** festgelegt, und die **OnSuccess**-Formel wird ausgeführt. Wenn der Benutzer einen Datensatz erstellt hat (wenn sich das Formular also im **New**-Modus befindet), wechselt das Formular in den **Edit**-Modus, sodass der Benutzer einen neu erstellten oder einen anderen Datensatz bearbeiten kann.
* Wenn bei der Übermittlung ein Fehler auftritt, enthält die **Error**-Eigenschaft eine benutzerfreundliche Fehlermeldung aus der Datenquelle, in der das Problem beschrieben wird. Die **ErrorKind**-Eigenschaft wird entsprechend (abhängig vom Problem) festgelegt, und die **OnFailure**-Formel wird ausgeführt.

Einige Datenquellen erkennen, wenn zwei Personen den gleichen Datensatz gleichzeitig zu aktualisieren versuchen. In diesem Fall wird **ErrorKind** auf **ErrorKind.Conflict** festgelegt. Das Problem wird gelöst, indem die Datenquelle mit den Änderungen des anderen Benutzers aktualisiert wird und dann die Änderungen des ersten Benutzers erneut angewandt werden.

> [!TIP]
> Wenn Sie eine **Abbrechen**-Schaltfläche in einem Formular verwenden, sodass Benutzer Änderungen verwerfen können, fügen Sie die **[ResetForm](../functions/function-form.md)**-Eigenschaft zur **[OnSelect](properties-core.md)**-Eigenschaft der Schaltfläche hinzu, auch wenn die Eigenschaft die **[Navigate](../functions/function-navigate.md)**-Funktion zum Wechseln zwischen Bildschirmen enthält. Andernfalls werden die Änderungen des Benutzers nicht verworfen.

### <a name="layout"></a>Layout
Karten werden standardmäßig bei Smartphone-Apps in einer Spalte und bei Tablet-Apps in drei Spalten platziert. Sie können beim Konfigurieren des Formulars angeben, wie viele Spalten ein Formular haben soll und ob Karten an diesen ausgerichtet werden sollen. Diese Einstellungen werden nicht als Eigenschaften verfügbar gemacht, da sie nur verwendet werden, um die Eigenschaften **X**, **Y** und **Width** der Karten festzulegen.

Weitere Informationen finden Sie unter [Grundlegendes zum Layout von Datenformularen](../working-with-form-layout.md).

## <a name="key-properties"></a>Haupteigenschaften
**DataSource** – Die Datenquelle mit dem Datensatz, der vom Benutzer angezeigt, bearbeitet oder erstellt wird.

* Wenn Sie diese Eigenschaft nicht festlegen, kann der Benutzer keine Datensätze anzeigen, bearbeiten oder erstellen, und weder weitere Metadaten noch die Überprüfung sind verfügbar.

**DefaultMode**: Der Ausgangsmodus des Formularsteuerelements.  In der Beschreibung zu **Modus** weiter unten sind die zulässigen Werte und deren jeweilige Bedeutung angegeben. 

**DisplayMode**: Der zu verwendende Modus für Datenkarten und Steuerelemente im Formularsteuerelement.  

Ist abgeleitet von der zugrunde liegenden **Mode**-Eigenschaft und kann nicht unabhängig festgelegt werden:

| Modus | DisplayMode | Beschreibung |
| --- | --- | --- |
| **FormMode.Edit** |**DisplayMode.Edit** |Datenkarten und Steuerelemente können bearbeitet werden; Änderungen an einem Datensatz können akzeptiert werden. |
| **FormMode.New** |**DisplayMode.Edit** |Datenkarten und Steuerelemente können bearbeitet werden; ein neuer Datensatz kann akzeptiert werden. |
| **FormMode.View** |**DisplayMode.View** |Datenkarten und Steuerelemente sind nicht bearbeitbar und für die Anzeige optimiert. |

**Error** – Eine benutzerfreundliche Fehlermeldung, die für das Formular angezeigt wird, wenn bei der **[SubmitForm](../functions/function-form.md)**-Funktion ein Fehler auftritt.

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.
* Die Eigenschaft ändert sich nur, wenn die Funktion **[SubmitForm](../functions/function-form.md)**, **EditForm** oder **[ResetForm](../functions/function-form.md)** ausgeführt wird.
* Wenn kein Fehler auftritt, ist diese Eigenschaft *leer*, und **ErrorKind** wird auf **ErrorKind.None** festgelegt.
* Wenn möglich, wird die Fehlermeldung in der Sprache des Benutzers angezeigt. Einige Fehlermeldungen stammen direkt aus der Datenquelle. Sie sind möglicherweise nicht in der Sprache des Benutzers verfasst.

**ErrorKind** – Gibt die Art des aufgetretenen Fehlers an, wenn beim Ausführen von **SubmitForm** ein Fehler auftritt.

* Gilt nur für das **Formular bearbeiten**-Steuerelement.
* Diese Eigenschaft verfügt über die gleiche Enumeration wie die **[Errors](../functions/function-errors.md)**-Funktion. Ein **Formular bearbeiten**-Steuerelement kann diese Werte zurückgeben:

| ErrorKind | Beschreibung |
| --- | --- |
| **ErrorKind.Conflict** |Ein anderer Benutzer hat den gleichen Datensatz geändert, wodurch ein Konflikt aufgetreten ist. Führen Sie die **[Refresh](../functions/function-refresh.md)**-Funktion aus, um den Datensatz erneut zu laden, und versuchen Sie noch einmal, die Änderung vorzunehmen. |
| **ErrorKind.None** |Die Fehlerart ist nicht bekannt. |
| **ErrorKind.Sync** |Die Datenquelle hat einen Fehler gemeldet. Überprüfen Sie die **Error**-Eigenschaft, um weitere Informationen zu erhalten. |
| **ErrorKind.Validation** |Ein allgemeines Überprüfungsproblem wurde festgestellt. |

**Item** – Der Datensatz in dem **DataSource**-Element, das vom Benutzer angezeigt oder bearbeitet wird.

**LastSubmit** – Der letzte erfolgreich übermittelte Datensatz, einschließlich der vom Server generierten Felder.

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.
* Wenn die Datenquelle Felder automatisch generiert oder berechnet (wie das **ID**-Feld mit einer eindeutigen Zahl), wird der neue Wert der **LastSubmit**-Eigenschaft zugewiesen, wenn die **SubmitForm**-Funktion erfolgreich ausgeführt wird.
* Der Wert dieser Eigenschaft ist in der **OnSuccess**-Formel verfügbar.

**Mode** – Das Steuerelement befindet sich im Modus **Edit** oder **New**.

| Modus | Beschreibung |
| --- | --- |
| **FormMode.Edit** |Der Benutzer kann einen Datensatz mithilfe des Formulars bearbeiten. Die Werte auf den Karten des Formulars werden mithilfe des vorhandenen Datensatzes aufgefüllt. Der Benutzer kann sie dann ändern. Wenn die **[SubmitForm](../functions/function-form.md)**-Funktion erfolgreich ausgeführt wird, wird ein vorhandener Datensatz geändert. |
| **FormMode.New** |Der Benutzer kann einen Datensatz mithilfe des Formulars erstellen. Die Werte in den Steuerelementen des Formulars werden mithilfe der Datensatz-Standardwerte der Datenquelle aufgefüllt. Wenn die **[SubmitForm](../functions/function-form.md)**-Funktion erfolgreich ausgeführt wird, wird ein Datensatz erstellt. |
| **FormMode.View** |Der Benutzer kann einen Datensatz mithilfe des Formulars anzeigen. Die Werte in den Steuerelementen des Formulars werden mithilfe der Datensatz-Standardwerte der Datenquelle aufgefüllt. |

Das Formular wechselt vom **New**-Modus in den **Edit**-Modus, wenn eine dieser Änderungen auftritt:

* Das Formular wird erfolgreich übermittelt, und ein Datensatz wird erstellt. Wenn der Katalog so konfiguriert ist, dass die Auswahl in den neuen Datensatz verschoben wird, befindet sich das Formular für den erstellten Datensatz im **Edit**-Modus, sodass der Benutzer weitere Änderungen vornehmen kann.
* Die **[EditForm](../functions/function-form.md)**-Funktion wird ausgeführt.
* Die **[ResetForm](../functions/function-form.md)**-Funktion wird ausgeführt. Beispiel: Der Benutzer kann eine **Abbrechen**-Schaltfläche verwenden, die mit dieser Funktion konfiguriert wurde.

**OnFailure** – Gibt an, wie eine App reagiert, wenn ein Datenvorgang nicht erfolgreich ist.

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.

**OnReset** – Gibt an, wie eine App reagiert, wenn ein Steuerelement vom Typ **Formular bearbeiten** zurückgesetzt wird.

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.

**OnSuccess** – Gibt an, wie eine App reagiert, wenn ein Datenvorgang erfolgreich ausgeführt wurde.

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.

**Unsaved** – „true“, wenn das Steuerelement vom Typ **Formular bearbeiten** nicht gespeicherte Änderungen des Benutzers enthält.

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.
* Verwenden Sie diese Eigenschaft, um den Benutzer zu warnen, bevor alle nicht gespeicherten Änderungen verloren gehen.  Um zu verhindern, dass ein Benutzer einen anderen Datensatz in einem **[Katalog](control-gallery.md)**-Steuerelement aufruft, bevor die Änderungen am aktuellen Datensatz gespeichert wurden, können Sie die **[Disabled](properties-core.md)**-Eigenschaft des Katalogs auf **Form.Unsaved** festlegen und Aktualisierungsvorgänge deaktiveren.

**Updates** – Die Werte, die für einen Datensatz, der in ein Formular-Steuerelement geladen wurde, zurück in die Datenquelle geschrieben werden sollen.  

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.
* Verwenden Sie diese Eigenschaft, um die Feldwerte aus den Karten im Steuerelement zu extrahieren.  Sie können diese Werte verwenden, um die Datenquelle manuell zu aktualisieren, indem Sie die **[Patch](../functions/function-patch.md)**-Funktion oder eine andere verfügbare Methode aufrufen.  Sie müssen diese Eigenschaft nicht verwenden, wenn Sie die **[SubmitForm](../functions/function-form.md)**-Funktion ausführen.
* Diese Eigenschaft gibt einen Datensatz von Werten zurück.  Beispiel: Wenn das Formularsteuerelement Kartensteuerelemente für die Felder **Name** und **Quantity** enthält und die Werte der **[Update](control-card.md)**-Eigenschaften für diese Karten „Widget“ und „10“ zurückgeben, würde die **Updates**-Eigenschaft für das Formularsteuerelement **{ Name: "Widget", Quantity: 10 }** zurückgeben.

**Valid** – Gibt an, ob ein Steuerelement vom Typ **[Karte](control-card.md)** oder **Formular bearbeiten** gültige Einträge enthält, die für die Übermittlung an die Datenquelle bereit sind.

* Diese Eigenschaft ist nur im **Formular bearbeiten**-Steuerelement verfügbar.
* Im **Formular**-Steuerelement aggregiert die **Valid**-Eigenschaft die **Valid**-Eigenschaften aller **[Karten](control-card.md)**-Steuerelemente in dem Formular. Die **Valid**-Eigenschaft ist nur dann **true**, wenn die Daten auf allen Karten im Formular gültig sind. Ist das nicht der Fall, hat die **Valid**-Eigenschaft den Wert **false**.
* Damit eine Schaltfläche Änderungen nur dann speichert, wenn die Daten im Formular gültig sind, aber noch nicht übermittelt wurden, geben Sie für die Schaltfläche unter **DisplayMode** folgende Formel an:
  
    **SubmitButton.DisplayMode = If(IsBlank( Form.Error ) || Form.Valid, DisplayMode.Edit, DisplayMode.Disabled)**

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="more-information"></a>Weitere Informationen
Eine umfassende Übersicht über die Funktionsweise von Formularen finden Sie unter [Grundlegendes zu Datenformularen](../working-with-forms.md).

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Fügen Sie ggf. dem Formular mithilfe einer **[Bezeichnung](control-text-box.md)** einen Titel hinzu.
