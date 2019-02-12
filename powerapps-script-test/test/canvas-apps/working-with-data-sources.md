---
title: Grundlegendes zu Datenquellen für Canvas-Apps | Microsoft-Dokumentation
description: Referenzinformationen zum Arbeiten mit Verbindungen und Datenquellen für Canvas-Apps.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/08/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b51b7cde36a70001ff8545c497da7c4b4d5d1fa3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833909"
---
# <a name="understand-data-sources-for-canvas-apps-in-powerapps"></a>Grundlegendes zu Datenquellen für Canvas-Apps in PowerApps

Die meisten Canvas-Apps in PowerApps nutzen externe Informationen, die als **Datenquellen** bezeichnet werden und in Clouddiensten gespeichert sind. Ein gängiges Beispiel ist eine Tabelle in einer Excel-Datei, die in OneDrive for Business gespeichert ist. Apps greifen auf diese Datenquellen mithilfe von **Verbindungen** zu.

In diesem Artikel werden die verschiedenen Arten von Datenquellen und das Arbeiten mit Datenquellen in Form von Tabellen beschrieben.

Es ist einfach, eine App zu erstellen, die grundlegende Lese- und Schreibvorgänge in Bezug auf eine Datenquelle ausführt. Es gibt aber Fälle, in denen Sie den Datenfluss in Ihre App und aus Ihrer App besser kontrollieren möchten.  In diesem Artikel wird beschrieben, wie die Funktionen **[Patch](functions/function-patch.md)**, **[DataSourceInfo](functions/function-datasourceinfo.md)**, **[Validate](functions/function-validate.md)** und **[Errors](functions/function-errors.md)** eine bessere Kontrolle ermöglichen.

## <a name="kinds-of-data-sources"></a>Arten von Datenquellen

Datenquellen können mit einem Clouddienst verbunden sein oder für eine App lokal sein.

### <a name="connected-data-sources"></a>Verbundene Datenquellen

Die geläufigsten Datenquellen sind **Tabellen**, die Sie zum Abrufen und Speichern von Informationen verwenden können. Mithilfe von **Verbindungen** mit Datenquellen können Sie Daten in Microsoft Excel-Arbeitsmappen, SharePoint-Listen, SQL-Tabellen und vielen anderen Formaten lesen und schreiben, die in Clouddiensten wie OneDrive for Business, DropBox und SQL Server gespeichert sein können.

Andere Datenquellen als Tabellen sind z.B. E-Mail, Kalender, Twitter und Benachrichtigungen, die jedoch in diesem Artikel nicht behandelt werden.

### <a name="local-data-sources"></a>Lokale Datenquellen

Mithilfe der Steuerelemente **[Katalog](controls/control-gallery.md)**, **[Formular anzeigen](controls/control-form-detail.md)** und **[Formular bearbeiten](controls/control-form-detail.md)** ist es einfach, eine App zu erstellen, die Daten aus einer Datenquelle liest und schreibt.  Lesen Sie zunächst den Artikel [Understand data forms (Grundlegendes zu Datenformularen)](working-with-forms.md).  

Wenn Sie PowerApps zum Erstellen einer App aus Daten auffordern, werden diese Steuerelemente verwendet. Im Hintergrund verwendet die App eine interne Tabelle zum Speichern und Bearbeiten der Daten, die aus der Datenquelle stammen.

Eine besondere Art von Datenquelle ist die [Sammlung](working-with-data-sources.md#collections), die für die App lokal ist und nicht über eine Verbindung mit einem Dienst in der Cloud gesichert ist, sodass die Informationen nicht auf Geräten für den gleichen oder andere Benutzer freigegeben werden können. Sammlungen können geladen und lokal gespeichert werden.

### <a name="kinds-of-tables"></a>Arten von Tabellen

Bei Tabellen, die für eine App in PowerApps intern sind, handelt es sich wie bei einer Zahl oder einer Zeichenfolge um feste Werte. Interne Tabellen sind nur im Arbeitsspeicher der App vorhanden und werden an keiner anderen Stelle gespeichert. Sie können die Struktur und die Daten einer Tabelle nicht direkt ändern. Sie können stattdessen eine neue Tabelle mithilfe einer Formel erstellen, indem Sie mit dieser Formel eine geänderte Kopie der ursprünglichen Tabelle erstellen.

Externe Tabellen werden in einer Datenquelle für späteren Abruf und Freigabe gespeichert.  PowerApps bietet „Verbindungen“ zum Lesen und Schreiben von gespeicherten Daten.  Innerhalb einer Verbindung können Sie auf mehrere Tabellen mit Informationen zugreifen.  Sie wählen aus, welche Tabellen in der App verwendet werden sollen, und aus jeder wird eine separate *Datenquelle*.  

Wenn Sie mehr erfahren möchten, wird unter [Arbeiten mit Tabellen](working-with-tables.md) ausführlicher auf interne Tabellen eingegangen, aber auch auf externe Tabellen, die sich in einem Clouddienst befinden.

## <a name="working-with-tables"></a>Arbeiten mit Tabellen
Sie können Datenquellen in Form von Tabellen wie eine interne PowerApps-Tabelle verwenden.  Wie eine interne Tabelle weist auch jede Datenquelle [Datensätze](working-with-tables.md#records), [Spalten](working-with-tables.md#columns) und Eigenschaften auf, die Sie in Formeln verwenden können. Weitere Anforderungen:

* Die Datenquelle weist die gleichen Spaltennamen und Datentypen auf wie die zugrunde liegende Tabelle in der Verbindung.
  
    > [!NOTE]
  > Bei Excel- oder SharePoint-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, ersetzt PowerApps die Leerzeichen durch **"\_X0020\_"**. **"Name der Spalte"** in SharePoint oder Excel wird beispielsweise in PowerApps bei Anzeige im Datenlayout oder Verwendung in einer Formel als **"Name_x0020_der_x0020_Spalte"** angezeigt.
* Die Datenquelle wird automatisch vom Dienst geladen, wenn die App geladen wird.  Sie können erzwingen, dass die Daten aktualisiert werden, indem Sie die **[Refresh](functions/function-refresh.md)**-Funktion verwenden.
* Wenn Benutzer eine App ausführen, können sie Datensätze erstellen, ändern und löschen und diese Änderungen mithilfe von Push an die zugrunde liegende Tabelle im Dienst zurückleiten.
  * Datensätze können mithilfe der Funktionen **[Patch](functions/function-patch.md)** und **[Collect](functions/function-clear-collect-clearcollect.md)** erstellt werden.  
  * Datensätze können mithilfe der Funktionen **[Patch](functions/function-patch.md)**, **[Update](functions/function-update-updateif.md)** und **[UpdateIf](functions/function-update-updateif.md)** geändert werden.
  * Datensätze können mithilfe der Funktionen **[Remove](functions/function-remove-removeif.md)** und **[RemoveIf](functions/function-remove-removeif.md)** entfernt werden.
  * Fehler, die bei der Arbeit mit einer Datenquelle auftreten, sind über die **[Errors](functions/function-errors.md)**-Funktion verfügbar.
* Die Funktionen **[DataSourceInfo](functions/function-datasourceinfo.md)**, **[Defaults](functions/function-defaults.md)** und **[Validate](functions/function-validate.md)** bieten Informationen über die Datenquelle, mit denen Sie die Benutzerfreundlichkeit optimieren können.

### <a name="creating-data-sources"></a>Erstellen von Datenquellen
PowerApps kann nicht zum Erstellen einer verbundenen Datenquelle oder zum Ändern deren Struktur verwendet werden; die Datenquelle muss bereits in einem Dienst vorhanden sein. Beispielsweise verwenden Sie zum Erstellen einer Tabelle in einer auf OneDrive gespeicherten Excel-Arbeitsmappe zunächst Excel Online auf OneDrive, um eine Arbeitsmappe zu erstellen. Als Nächstes erstellen Sie eine Verbindung zu Ihrer App.  

Datenquellen einer Sammlung *können* innerhalb einer App erstellt und geändert werden, sind jedoch nur temporär.

### <a name="display-one-or-more-records"></a>Anzeigen eines oder mehrerer Datensätze
![](media/working-with-data-sources/reading-from-a-datasource.png) Das obige Diagramm veranschaulicht den Informationsfluss, wenn eine App die Informationen in einer Datenquelle liest:

* Die Informationen werden gespeichert und über einen Speicherdienst geteilt (in diesem Fall eine SharePoint-Liste einer Office 365-Website).
* Eine Verbindung stellt diese Informationen der App zur Verfügung.  Die Verbindung übernimmt die Authentifizierung des Benutzers, der auf die Informationen zugreift.
* Wenn die App gestartet wird oder die **[Refresh](functions/function-refresh.md)**-Funktion gedrückt wird, werden Informationen zur lokalen Verwendung aus der Verbindung in eine Datenquelle in der App geholt.
* Formeln werden verwendet, um die Informationen zu lesen und sie in Steuerelementen verfügbar zu machen, die der Benutzer sehen kann. Sie können die Datensätze einer Datenquelle anzeigen, indem Sie einen Katalog auf einem Formular verwenden und die **[Items](controls/properties-core.md)**-Eigenschaft mit der Datenquelle verknüpfen: **Gallery.Items = DataSource**.  Sie verknüpfen Steuerelemente innerhalb des Katalogs mit dem Katalog, indem Sie die **[Default](controls/properties-core.md)**-Eigenschaft der Steuerelemente verwenden.  
* Die Datenquelle ist auch eine Tabelle.  Sie können also **[Filter](functions/function-filter-lookup.md)**, **[Sort](functions/function-sort.md)**, **[AddColumns](functions/function-table-shaping.md)** und andere Funktionen verwenden, um die Datenquelle zu optimieren und zu erweitern, bevor Sie sie als Ganzes verwenden.  Sie können auch **[Lookup](functions/function-filter-lookup.md)**, **[First](functions/function-first-last.md)**, **[Last](functions/function-first-last.md)** und andere Funktionen zur Arbeit mit einzelnen Datensätzen verwenden.

### <a name="modify-a-record"></a>Ändern eines Datensatzes
Im vorherigen Abschnitt haben Sie gesehen, wie eine Datenquelle gelesen wird.  Beachten Sie, dass die Pfeile in der Abbildung oben unidirektional sind.  Änderungen an einer Datenquelle werden nicht mithilfe von Push über die gleichen Formeln zurückgeleitet, über die die Daten abgerufen wurden.  Stattdessen werden neue Formeln verwendet.  Häufig wird zum Bearbeiten eines Datensatzes ein anderes Formular als zum Durchsuchen von Datensätzen verwendet, vor allem auf einem mobilen Gerät.

Beachten Sie, dass zum Ändern eines vorhandenen Datensatzes einer Datenquelle der Datensatz ursprünglich aus der Datenquelle stammen muss.  Der Datensatz kann durch einen Katalog, eine [Kontextvariable](working-with-variables.md#create-a-context-variable) und eine beliebige Anzahl von Formeln gegangen sein, aber sein Ursprung sollte zur Datenquelle zurückverfolgt werden können.  Dies ist wichtig, da zusätzliche Informationen mit dem Datensatz übertragen werden, durch die er eindeutig identifiziert werden kann, um sicherzustellen, dass Sie den richtigen Datensatz ändern.    

![](media/working-with-data-sources/writing-to-a-datasource.png) Das obige Diagramm zeigt den Informationsfluss zum Aktualisieren einer Datenquelle:

* Ein **[Bearbeitungsformular](controls/control-form-detail.md)**-Steuerelement stellt einen Container für Eingabekarten zur Verfügung, die aus Benutzereingabesteuerelementen wie einem Texteingabefeld oder einem Schieberegler bestehen.  Die Eigenschaften **[DataSource](controls/control-form-detail.md)** und **[Item](controls/control-form-detail.md)** werden verwendet, um den zu bearbeitenden Datensatz zu identifizieren.
* Jede Eingabekarte verfügt über eine **[Default](controls/properties-core.md)**-Eigenschaft, die in der Regel auf das Feld des **ThisItem**-Datensatzes des Formulars festgelegt wird.  Die Steuerelemente in der Eingabekarte nehmen dann ihre Eingabewerte von **[Default](controls/properties-core.md)**.  Normalerweise müssen Sie diese Option nicht ändern.
* Jede Eingabekarte macht eine **[Update](controls/control-card.md)**-Eigenschaft verfügbar.  Diese Eigenschaft entspricht der Eingabe des Benutzers in ein bestimmtes Feld des Datensatzes für das Zurückschreiben an die Datenquelle.  Normalerweise müssen Sie diese Option nicht ändern.
* Eine Schaltfläche oder ein Bildsteuerelement auf dem Formular ermöglichen dem Benutzer, Änderungen am Datensatz zu speichern.  Die **[OnSelect](controls/properties-core.md)**-Formel des Steuerelements ruft die **[SubmitForm](functions/function-form.md)**-Funktion für diese Aufgabe auf.  **[SubmitForm](functions/function-form.md)** liest alle **[Update](controls/control-card.md)**-Eigenschaften der Karten und verwendet diese zum Zurückschreiben an die Datenquelle.
* In einigen Fällen werden Probleme auftreten.  Eine Netzwerkverbindung ist möglicherweise offline, oder eine Validierungsüberprüfung erfolgt durch einen Dienst, der App nicht bekannt war.  Die Eigenschaften **Error** und **[ErrorKind](controls/control-form-detail.md)** des Formularsteuerelements stellen diese Informationen zur Verfügung, damit Sie dem Benutzer angezeigt werden können.  

Für eine differenziertere Kontrolle über diesen Prozess können Sie auch die Funktionen **[Patch](functions/function-patch.md)** und **[Errors](functions/function-errors.md)** verwenden.  Das **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement stellt eine **[Updates](controls/control-form-detail.md)**-Eigenschaft zur Verfügung, damit Sie die Werte der Felder innerhalb des Formulars lesen können.  Sie können diese Eigenschaft auch verwenden, um einen benutzerdefinierten Connector für eine Verbindung aufzurufen, und die Funktionen **Patch** und **SubmitForm** vollständig umgehen.

### <a name="validation"></a>Validierung
Vor einer Änderung an einem Datensatz sollte die App so gut es geht sicherstellen, dass die Änderung akzeptiert wird.  Es gibt zwei Gründe dafür:

* *Unmittelbares Feedback für den Benutzer*.  Am besten wird ein Problem behoben, wenn es gerade aufgetreten und dem Benutzer noch besonders bewusst ist.  Im Prinzip kann mit jedem Touch oder Tastaturanschlag roter Text angezeigt werden, der ein Problem mit dem Eintrag angibt.
* *Weniger Netzwerkverkehr und geringere Wartezeit für den Benutzer*.  Je mehr Probleme in der App erkannt werden, desto weniger Konversationen über das Netzwerk sind nötig, um Fehler zu erkennen und zu beheben.  Jede Konversation nimmt Zeit in Anspruch, während der Benutzer warten muss, bevor er den Vorgang fortsetzen kann.

PowerApps bietet zwei Tools zur Validierung:

* Die Datenquelle kann Informationen darüber geben, was gültig ist und was nicht.  Zum Beispiel können Zahlen über Mindest- und Höchstwerte verfügen, und ein oder mehrere Einträge können erforderlich sein.  Sie können auf diese Informationen mit der **[DataSourceInfo](functions/function-datasourceinfo.md)**-Funktion zugreifen.  
* Die **[Validate](functions/function-validate.md)**-Funktion verwendet dieselben Informationen, um den Wert einer einzelnen Spalte oder eines vollständigen Datensatzes zu überprüfen.

### <a name="error-handling"></a>Fehlerbehandlung
Hervorragend, Sie haben den Datensatz validiert.  Nun ist es an der Zeit, diesen Datensatz mit **[Patch](functions/function-patch.md)** zu aktualisieren!

Aber leider gibt es möglicherweise noch immer ein Problem.  Das Netzwerk ist ausgefallen, die Validierung am Dienst ist fehlgeschlagen, oder der Benutzer verfügt nicht über die nötigen Berechtigungen, um nur einige der möglichen Fehler zu nennen, die bei Ihrer App auftreten können.  Sie muss angemessen auf Fehlersituationen reagieren und dem Benutzer Feedback und eine Möglichkeit bieten, den Fehler zu beheben.  

Wenn Fehler mit einer Datenquelle auftreten, zeichnet die App die Fehlerinformationen automatisch auf und stellt sie über die **[Errors](functions/function-errors.md)**-Funktion zur Verfügung.  Fehler werden den Datensätzen zugeordnet, bei denen die Probleme aufgetreten sind.  Wenn der Benutzer ein Problem selbst beheben kann wie z.B. ein Validierungsproblem, kann er den Datensatz erneut übermitteln, und die Fehler werden gelöscht.

Wenn ein Fehler bei der Erstellung eines Datensatzes mit **[Patch](functions/function-patch.md)** oder **[Collect](functions/function-clear-collect-clearcollect.md)** auftritt, gibt es keinen Datensatz, dem Fehler zugeordnet werden können.  In diesem Fall wird von **[Patch](functions/function-patch.md)** *leer* zurückgegeben, das als Datensatzargument für **[Errors](functions/function-errors.md)** verwendet werden kann.  Erstellungsfehler werden mit dem nächsten Vorgang gelöscht.

Die **[Errors](functions/function-errors.md)**-Funktion gibt eine Tabelle mit Fehlerinformationen zurück.  Diese Informationen können die Spalteninformationen enthalten, wenn der Fehler einer bestimmten Spalte zugeordnet werden kann.  Verwenden Sie Fehlermeldungen auf Spaltenebene in Bezeichnungssteuerelementen, die sich in der Nähe der Spalte auf der Bearbeitungsansicht befinden.  Verwenden Sie Fehlermeldungen auf Datensatzebene, bei denen die **Spalte** in der Fehlertabelle *leer* ist, in der Nähe der Schaltfläche **Save** (Speichern) für den gesamten Datensatz.  

### <a name="working-with-large-data-sources"></a>Arbeiten mit großen Datenquellen
Beim Erstellen von Berichten aus großen Datenquellen (z.B. Millionen von Datensätzen) möchten Sie den Netzwerkverkehr minimieren. Nehmen wir an, dass Sie über alle Kunden mit StatusCode „Platinum“ (Platin) in New York City Berichte erstellen möchten und dass die Customers-Tabelle (Kunden) Millionen von Datensätzen enthält.

Sie möchten **nicht** diese Millionen von Kunden in Ihre App überführen, sondern die gewünschten auswählen. Sie möchten, dass diese Auswahl in Ihrem Clouddienst erfolgt, in dem die Tabelle gespeichert ist, und Sie nur die ausgewählten Datensätze über das Netzwerk senden.

Viele, aber nicht alle Funktionen, die Sie zur Auswahl der Datensätze verwenden können, können *delegiert* werden, d.h. dass sie im Clouddienst ausgeführt werden. Wie Sie dies tun können, erfahren Sie unter [Delegation (Delegierung)](delegation-overview.md).

## <a name="collections"></a>Sammlungen
Sammlungen sind eine besondere Art von Datenquelle.  Sie sind für die App lokal und werden nicht über eine Verbindung mit einem Dienst in der Cloud gesichert, sodass die Informationen nicht auf Geräten für den gleichen oder andere Benutzer freigegeben werden können.  Sie funktionieren mit wenigen Ausnahmen wie jede andere Datenquelle:

* Sammlungen können mit der **[Collect](functions/function-clear-collect-clearcollect.md)**-Funktion dynamisch erstellt werden.  Sie müssen im Gegensatz zu verbindungsbasierten Datenquellen nicht im Voraus erstellt werden.
* Die Spalten einer Sammlung können jederzeit mit der **[Collect](functions/function-clear-collect-clearcollect.md)**-Funktion geändert werden.
* Sammlungen lassen doppelte Datensätze zu.  Mehr als eine Kopie desselben Datensatzes kann in einer Sammlung vorhanden sein.  Funktionen wie **[Remove](functions/function-remove-removeif.md)** verarbeiten die erste Übereinstimmung, die sie finden, es sei denn, das **All**-Argument wird angegeben.
* Sie können die Funktionen **[SaveData](functions/function-savedata-loaddata.md)** und **[LoadData](functions/function-savedata-loaddata.md)** zum Speichern und erneuten Laden einer Kopie der Sammlung verwenden.  Die Informationen werden an einem privaten Speicherort gespeichert, auf den andere Benutzer, Apps oder Geräte nicht zugreifen können.
* Sie können die Steuerelemente **[Export](controls/control-export-import.md)** und **[Import](controls/control-export-import.md)** zum Speichern und erneuten Laden eine Kopie der Sammlung in eine Datei verwenden, mit der der Benutzer interagieren kann.  

Weitere Informationen zum Arbeiten mit einer Sammlung als Datenquelle finden Sie unter [Create and update a collection (Erstellen und Aktualisieren einer Sammlung)](create-update-collection.md).

Sammlungen werden häufig verwendet, um den globalen Zustand für die App zu speichern.  Weitere Informationen zu den verfügbaren Optionen zum Verwalten des Zustands finden Sie unter [Working with variables (Arbeiten mit Variablen)](working-with-variables.md).

