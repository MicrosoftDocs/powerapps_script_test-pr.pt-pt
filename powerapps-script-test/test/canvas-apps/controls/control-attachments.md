---
title: 'Attachments-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen zum Attachment-Steuerelement, einschließlich Eigenschaften und Beispielen
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/23/2018
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: da9c8f85844e37d6af8e1063b36496c820fbfa07
ms.sourcegitcommit: e2a9d1a6090cdd8aa78515b49f38ed2365217ea6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/17/2018
ms.locfileid: "49384246"
---
# <a name="attachments-control-in-powerapps"></a>Attachments-Steuerelement in PowerApps
Ein Steuerelement, mit dem Benutzer Dateien auf Ihr Gerät herunterladen sowie Dateien in einer SharePoint-Liste oder einer Common Data Service für Apps-Entität hochladen und löschen können.

## <a name="limitations"></a>Beschränkungen
Für das Steuerelement für Anlagen gelten folgende Einschränkungen:
1. Anlagen werden für SharePoint-Listen und Common Data Service für Apps-Entitäten unterstützt.

1. Die Funktionen zum Hochladen und Löschen funktionieren nur in Formularen.  Das Steuerelement für Anlagen wird im Bearbeitungsmodus deaktiviert angezeigt, wenn es sich nicht in einem Formular befindet. Beachten Sie, dass der Endbenutzer das Formular speichern muss, um hinzugefügte und gelöschte Dateien im Back-End zu speichern.

1. Sie können nur Dateien bis maximal 10 MB hochladen.  

## <a name="description"></a>Beschreibung
Mit dem **Attachments**-Steuerelement können Sie Dateien aus einer SharePoint-Liste öffnen, hinzufügen und löschen.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)** – Die Quelle mit Beschreibungen der Dateien, die heruntergeladen werden können.

**MaxAttachments** – Die maximale Anzahl von Dateien, die vom Steuerelement akzeptiert wird.

**MaxAttachmentSize** – die maximal zulässige Dateigröße für jede neue Anlage in MB.  Zurzeit besteht eine Beschränkung von 10 MB.

**OnAttach** – Legt fest, wie die App reagiert, wenn der Benutzer eine neue Dateianlage hinzufügt.

**OnRemove** – Legt fest, wie die App reagiert, wenn der Benutzer eine vorhandene Anlage löscht.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf eine Anlage klickt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben Sollte den Zweck dieser Anlagen beschreiben.

**AddAttachmentText** – Der Beschriftungstext des Links, mit dem eine neue Anlage hinzugefügt wird.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement das Hinzufügen und Löschen von Dateien zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**MaxAttachmentsText** – Der Text, der den Link „Datei anfügen“ ersetzt, wenn das Steuerelement die maximal zulässige Anzahl von Dateien enthält.

**NoAttachmentsText** – Hinweistext, der für den Benutzer, der angezeigt wird, wenn keine Anlagen vorhanden sind.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).


## <a name="example"></a>Beispiel
1. Erstellen Sie eine App aus Daten, wobei eine SharePoint-Liste als Datenquelle verwendet wird. Alternativ können Sie der App ein Formular hinzufügen und eine SharePoint-Liste als Datenquelle festlegen.

2. Wählen Sie in der Strukturansicht auf der linken Seite das **Form**-Steuerelement aus.

3. Klicken Sie im Optionsbereich auf der rechten Seite auf der Registerkarte „Eigenschaften“ auf **Daten**.

4. Aktivieren Sie unter **Felder**, das Feld **Anlagen**.

    Im Formular wird das der SharePoint-Liste zugeordnete Feld „Anlagen“ angezeigt.

[Erfahren Sie, wie Sie ein Steuerelement hinzufügen und konfigurieren].(../add-configure-controls.md)


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **ItemColor** und **ItemFill**
* **ItemHoverColor** und **ItemHoverFill**
* **ItemPressedColor** und **ItemPressedFill**
* **AddedItemColor** und **AddedItemFill**
* **RemovedItemColor** und **RemovedItemFill**
* **ItemErrorColor** und **ItemErrorFill**
* **AddAttachmentColor** und **Fill**
* **MaxAttachmentsColor** und **Fill**
* **NoAttachmentsColor** und **Fill**

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
Die folgenden Eigenschaften müssen vorhanden sein:
* **[AccessibleLabel](properties-accessibility.md)**
* **AddAttachmentsText**
* **MaxAttachmentsText**
* **NoAttachmentsText**

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Ihnen dabei helfen.
