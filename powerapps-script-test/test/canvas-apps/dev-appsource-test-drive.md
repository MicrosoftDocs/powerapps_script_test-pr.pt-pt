---
title: Testen Ihrer Canvas-App durch Kunden auf AppSource | Microsoft-Dokumentation
description: Verwenden Sie AppSource, um eine Canvas-App mit Kunden zu teilen und Leads für Ihr Unternehmen zu generieren.
author: linhtranms
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/08/2017
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5920c40396ab3ff8c1691b5d683615f41f6a7509
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863735"
---
# <a name="let-customers-test-drive-your-canvas-app-on-appsource"></a>Testen Ihrer Canvas-App durch Kunden auf AppSource

Erstellen Sie Ihre Canvas-Apps in PowerApps mit Leidenschaft? Möchten Sie eine Canvas-App für Kunden freigeben? [AppSource.com](https://appsource.microsoft.com) unterstützt Lösungen für PowerApps-Testversionen, um Ihnen eine Möglichkeit zu geben, Apps für Kunden freizugeben und Leads für Ihr Unternehmen zu generieren.

## <a name="what-is-a-test-drive-solution"></a>Was ist eine Test Drive-Projektmappe?

Eine Test Drive-Projektmappe ermöglicht es Ihren Kunden, eine echte App auszuprobieren, ohne sich für einen PowerApps-Plan zu registrieren oder Anwendungen zu installieren. Kunden melden sich einfach mithilfe ihres AAD-Kontos (Azure Active Directory) bei AppSource.com an und führen die App in einem Webbrowser aus. Ohne Test Drive können Ihre Kunden nur von Ihrer App lesen oder ein Video anschauen, das sie beschreibt. Mit Test Drive erhalten Kunden eine bessere Vorstellung davon, was Ihre Lösung ist und über welche Funktionalität Ihre App verfügt. Und sie machen die Erfahrung, die App tatsächlich zu verwenden. Kunden können dabei nicht „unter die Haube sehen“, um herauszufinden, wir Ihre App erstellt wurde, daher ist Ihr geistiges Eigentum geschützt. Wir sammeln und teilen Leadinformationen für Benutzer, die Ihre Test Drive-App starten, um Sie beim Ausbau Ihres Geschäfts zu unterstützen.

Hier ist ein Beispiel für eine [App-Auflistung](https://go.microsoft.com/fwlink/?linkid=848867) auf AppSource.com:

![AppSource-Beispielauflistung ](./media/dev-appsource-test-drive/sample-app-source-listing.png)

Durch Auswählen des Links **Kostenlose Testversion** (Free Trial) aus der App-Auflistung oben wird die zugeordnete PowerApps Test Drive-App direkt im Browser des Benutzers gestartet:

![Webplayer für Beispiel-App](./media/dev-appsource-test-drive/sample-app-web-player.png)

## <a name="how-do-i-build-a-test-drive-solution"></a>Wie wird eine Test Drive-Projektmappe erstellt?
Das Erstellen einer App für eine Test Drive-Projektmappe unterscheidet sich nicht vom Erstellen anderer Apps in PowerApps, Sie verwenden lediglich eingebettete Daten anstelle von externen Datenverbindungen. Die Verwendung von eingebetteten Daten setzt die Schwelle für die Bereitstellung der App beim Kunden herab, sodass sich für den Kunden ein reibungsloser Testablauf ergibt. Die vollständige Lösung, die schließlich an Kunden verteilt wird, beinhaltet normalerweise Datenverbindungen, aber für eine Test Drive-Projektmappe funktionieren eingebettete Daten wirklich gut.

PowerApps unterstützt von Haus aus das Erstellen von Apps mit eingebetteten Daten, sodass Sie lediglich Beispieldaten benötigen, die Ihre App verwenden kann. Diese Daten sollten in einer Excel-Datei in Form einer oder mehrerer Tabellen vorliegen. Sie ziehen die Daten dann in PowerApps aus den Excel-Tabellen in die App und arbeiten dort mit ihnen statt mit einer externen Verbindung. Der aus drei Schritten bestehende Prozess unten zeigt Ihnen, wie Daten in die App importiert und darin verwendet werden.

### <a name="step-1-import-data-into-the-app"></a>Schritt 1: Importieren von Daten in die App
Angenommen, Sie besitzen eine Excel-Datei mit zwei Tabellen: **SiteInspector** und **SitePhotos**.

![Zu importierende Excel-Tabellen](./media/dev-appsource-test-drive/excel-file.png)

Importieren Sie diese zwei Tabellen mithilfe der Option **Der App statische Daten hinzufügen** in PowerApps.

![Hinzufügen von statischen Daten zur App](./media/dev-appsource-test-drive/static-data.png)

Die Tabellen sind jetzt als Datenquellen in Ihrer App verfügbar.

![Excel-Tabellen als importierte Datenquellen](./media/dev-appsource-test-drive/data-sources.png)

### <a name="step-2-handling-read-only-and-read-write-scenarios"></a>Schritt 2: Behandlung von Szenarien mit Schreibschutz und mit Lese-/Schreibzugriff
Die importierten Daten sind *statisch* und daher schreibgeschützt. Wenn Ihre App schreibgeschützt ist (sie dem Benutzer also Daten nur anzeigt), verweisen Sie direkt in der App auf die Tabellen. Wenn Sie beispielsweise auf das Feld **Title** in der Tabelle **SiteInspector** zugreifen möchten, verwenden Sie **SiteInspector.Title** in Ihrer Formel.

Wenn für Ihre Daten Lese-/Schreibzugriff besteht, ziehen Sie die Daten aus den einzelnen Tabellen zuerst in eine *Sammlung*, die eine Tabellendatenstruktur in PowerApps darstellt. Arbeiten Sie dann mit der Sammlung anstelle der Tabelle. So ziehen Sie Daten aus den Tabellen **SiteInspector** und **SitePhotos** in die Sammlungen **SiteInspectorCollect** und **SitePhotosCollect**:

```
ClearCollect(SiteInspectorCollect,SiteInspector); ClearCollect(SitePhotosCollect,SitePhotos)
```

Die Formel leert beide Sammlungen und sammelt anschließend die Daten aus den einzelnen Tabellen in der entsprechenden Sammlung:

* Rufen Sie diese Formel an beliebiger Stelle in Ihrer App auf, um die Daten zu laden.
* Sie können alle Sammlungen in Ihrer App anzeigen, indem Sie zu **Datei** > **Sammlungen** navigieren.
* Weitere Informationen finden Sie unter [Erstellen und Aktualisieren einer Sammlung in Ihrer App](../canvas-apps/create-update-collection.md).

Wenn Sie jetzt auf das Feld **Title** zugreifen möchten, verwenden Sie in Ihrer Formel **SiteInspectorCollect.Title**.

### <a name="step-3-add-update-and-delete-data-in-your-app"></a>Schritt 3: Hinzufügen, Aktualisieren und Löschen von Daten in Ihrer App
Sie haben gesehen, wie Daten direkt und aus einer Sammlung gelesen werden; jetzt möchten wir Ihnen zeigen, wie Sie Daten in einer Sammlung hinzufügen, aktualisieren und löschen:

**Um einer Sammlung eine Zeile hinzuzufügen**, verwenden Sie [Collect( DataSource, Item, ... )](../canvas-apps/functions/function-clear-collect-clearcollect.md):

```
Collect(SiteInspectorCollect,{ID:Value(Max(SiteInspectorCollect, ID)+1),
    Title:TitleText.Text,SubTitle:SubTitleText.Text,Description:DescriptionText.Text)
```

**Um eine Zeile in einer Sammlung zu aktualisieren** , verwenden Sie [UpdateIf( DataSource, Condition1, ChangeRecord1 [, Condition2, ChangeRecord2, ...] )](../canvas-apps/functions/function-update-updateif.md):

```
UpdateIf(SiteInspectorCollect,ID=record.ID,
    {Title:TitleEditText.Text,SubTitle:SubTitleEditText.Text,Description:DescriptionEditText.Text)
```

**Um eine Zeile aus einer Sammlung zu löschen**, verwenden Sie [RemoveIf( DataSource, Condition [, ...] )](../canvas-apps/functions/function-remove-removeif.md):

```
RemoveIf(SiteInspectorCollect,ID=record.ID)
```

> [!NOTE]
> Sammlungen enthalten nur Daten, während die App ausgeführt wird; beim Schließen der App werden sämtliche Änderungen verworfen.

Zusammengefasst lässt sich sagen, dass Sie eine Version Ihrer App mit eingebetteten Daten erstellen können, die die Erfahrung der App bei bestehender Verbindung mit externen Daten simuliert. Nach dem Einbetten der Daten sind Sie bereit, diese App auf AppSource.com als Test Drive-Projektmappe zu veröffentlichen.

## <a name="how-do-i-list-my-test-drive-solution-on-appsourcecom"></a>Wie liste ich meine Test Drive-Projektmappe auf AppSource.com auf?
Jetzt, da Ihre App fertig ist, ist es an der Zeit, sie auf AppSource.com zu veröffentlichen. Um diesen Prozess einzuleiten, füllen Sie das [Bewerbungsformular](https://powerapps.microsoft.com/partners/get-listed/) auf PowerApps.com aus.

Nachdem Sie sich beworben haben, erhalten Sie eine E-Mail mit Anweisungen zum Einreichen Ihrer App für die Veröffentlichung auf AppSource.com. Die Dokumentation zum Onboarding, die den vollständigen Prozess lückenlos beschreibt, kann [hier](https://go.microsoft.com/fwlink/?linkid=851031) heruntergeladen werden.

