---
title: Übersicht über die SharePoint-Verbindung | Microsoft-Dokumentation
description: Hier finden Sie die verfügbaren Funktionen, Antworten und Beispiele für SharePoint.
author: sarafankit
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/12/2017
ms.author: ankitsar
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a13d2602f06f436d4b805669b004f1ee63daeb9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836733"
---
# <a name="connect-to-sharepoint-from-powerapps"></a>Verbinden mit SharePoint aus PowerApps
![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

Stellen Sie eine Verbindung mit einer SharePoint-Website her, um automatisch eine App aus einer Liste zu generieren, eine App neu zu erstellen oder eine vorhandene App zu aktualisieren.

## <a name="known-issues"></a>Bekannte Probleme
Sie können Daten aus einer benutzerdefinierten Liste, nicht jedoch aus einer Bibliothek hinzufügen. Darüber hinaus werden nicht alle Typen von Spalten unterstützt, und nicht alle Spaltentypen unterstützen alle Typen von Karten.

| Spaltentyp | Support | Standardkarten |
| --- | --- | --- |
| Eine Textzeile |Ja |Text anzeigen |
| Mehrere Textzeilen |Ja |Text anzeigen |
| Auswahl |Ja |Suche anzeigen<br>Suche bearbeiten<br>Mehrfachauswahl anzeigen<br>Mehrfachauswahl bearbeiten |
| Number |Ja |Prozentsatz anzeigen<br>Bewertung anzeigen<br>Text anzeigen |
| Währung |Ja |Prozentsatz anzeigen<br>Bewertung anzeigen<br>Text anzeigen |
| Datum und Uhrzeit |Ja |Text anzeigen |
| Nachschlagen |Ja |Suche anzeigen<br>Suche bearbeiten<br>Mehrfachauswahl anzeigen<br>Mehrfachauswahl bearbeiten |
| Boolesch (Ja/Nein) |Ja |Text anzeigen<br>Ansicht umschalten |
| Person oder Gruppe |Ja |Suche anzeigen<br>Suche bearbeiten<br>Mehrfachauswahl anzeigen<br>Mehrfachauswahl bearbeiten |
| Hyperlink |Ja |URL anzeigen<br>Text anzeigen |
| Bild |Ja (schreibgeschützt) |Bild anzeigen<br>Text anzeigen |
| Anlage |Ja (schreibgeschützt) |Anlagen anzeigen|
| Berechnet |Ja (schreibgeschützt) | |
| Ergebnis der Aufgabe |Nein | |
| Externe Daten |Nein | |
| Verwaltete Metadaten |Ja (schreibgeschützt) | |
| Bewertung |Nein | |

PowerApps kann Spalten mit Leerzeichen lesen, aber die Leerzeichen werden durch den hexadezimalen Escapecode **"\_X0020\_"** ersetzt. **"Name der Spalte"** in SharePoint wird beispielsweise in PowerApps bei Anzeige im Datenlayout oder Verwendung in einer Formel als **"Name_x0020_der_x0020_Spalte"** angezeigt.

## <a name="prerequisites"></a>Voraussetzungen
1. [Registrieren Sie sich](../../signup-for-powerapps.md) bei PowerApps.

1. [Melden Sie sich bei PowerApps an](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen eingeben, die Sie bei der Registrierung verwendet haben.

1. Klicken Sie am linken Rand auf **Apps** und dann auf dem Banner auf **App erstellen**.

## <a name="create-an-app"></a>Erstellen einer App
* [Generieren Sie eine App automatisch](../app-from-sharepoint.md) auf Grundlage der Daten in einer SharePoint-Liste.

    Die App verfügt standardmäßig über drei Bildschirme: jeweils einen zum Durchsuchen von Datensätzen, zum Anzeigen von Details zu einem Datensatz und zum Erstellen oder Aktualisieren eines Datensatzes. Nach dem Generieren der App können Sie [den Bildschirm zum Durchsuchen](../customize-layout-sharepoint.md) und [den Bearbeitungs- und Detailbildschirm](../customize-forms-sharepoint.md) an Ihre Anforderungen anpassen.

    **Hinweis:** Wenn Ihre SharePoint-Liste eine Spalte vom Typ **Auswahl**, **Nachschlagen**, oder **Person oder Gruppe** enthält, finden Sie weitere Informationen unter [Anzeigen von Daten in einem Katalog](connection-sharepoint-online.md#show-data-in-a-gallery) weiter unten in diesem Thema.

* Erstellen Sie eine eigene Anwendung von Grund auf neu, indem Sie [eine Verbindung mit SharePoint herstellen](../connect-to-sharepoint.md), sich mit den Konzepten in [App von Grund auf neu erstellen](../get-started-create-from-blank.md) vertraut machen und sie in SharePoint anstelle von Excel anwenden.

## <a name="add-a-sharepoint-list-to-an-existing-app"></a>Hinzufügen einer SharePoint-Liste zu einer vorhandenen App
1. Öffnen Sie in PowerApps Studio die App, die Sie aktualisieren möchten.

2. Klicken oder tippen Sie im Menüband auf der Registerkarte **Ansicht** auf **Datenquellen**

3. Klicken oder tippen Sie im rechten Bereich auf **Datenquelle hinzufügen**.

    ![Datenquelle hinzufügen](./media/connection-sharepoint-online/add-data-source.png)

4. Klicken oder tippen Sie auf **Neue Verbindung**, anschließend auf **SharePoint** und dann auf **Verbinden**.

    ![Hinzufügen einer SharePoint-Verbindung](./media/connection-sharepoint-online/add-sharepoint.png)

5. Geben Sie den Typ der SharePoint-Website ein, mit dem Sie eine Verbindung herstellen möchten:

    ![Angeben des Verbindungstyps](./media/connection-sharepoint-online/choose-type.png)

   * Klicken oder tippen Sie auf **Direkte Verbindung (Clouddienste)**, um eine Verbindung mit SharePoint Online herzustellen.

   * Klicken oder tippen Sie auf **Verbindung mit einem lokalen Datengateway herstellen**, um eine Verbindung mit einer lokalen SharePoint-Website herzustellen.

       Geben Sie **Windows** als Authentifizierungstyp an, und geben Sie dann Ihre Anmeldeinformationen ein. (Wenn Ihre Anmeldeinformationen einen Domänennamen enthalten, geben Sie sie folgendermaßen an: *Domäne\Alias*.)

       ![Eingeben der Anmeldeinformationen](./media/connection-sharepoint-online/specify-creds.png)

       **Hinweis:** Wenn Sie kein lokales Datengateway installiert haben, [installieren Sie eines](../gateway-reference.md), und klicken oder tippen Sie anschließend auf das Symbol zum Aktualisieren der Liste der Gateways.

       Klicken oder tippen Sie unter **Gateway auswählen** auf das Gateway, das Sie verwenden möchten.

       ![Auswählen des Gateways](./media/connection-sharepoint-online/choose-gateway.png)

6. Klicken oder tippen Sie auf **Verbinden**.

7. Unter **Verbindung mit einer SharePoint-Website herstellen** klicken oder tippen Sie auf einen Eintrag in der Liste **Zuletzt geöffnete Websites** (oder geben Sie die URL der Website ein, die Sie verwenden möchten, bzw. fügen Sie sie ein). Klicken oder tippen Sie auf dann auf **Los**.

    ![Auswählen der SharePoint-Website](./media/connection-sharepoint-online/select-sp-site.png)

8. Aktivieren Sie unter **Liste auswählen** das Kontrollkästchen für eine oder mehrere Listen, die Sie verwenden möchten, und klicken oder tippen Sie dann auf **Verbinden**:  

    ![Auswählen der Tabellen in SharePoint](./media/connection-sharepoint-online/select-sp-tables.png)

    Nicht alle Typen von Listen werden standardmäßig angezeigt. PowerApps unterstützt benutzerdefinierte Liste, aber keine vorlagenbasierten Listen.  Wenn der Name der Liste, die Sie verwenden möchten, nicht angezeigt wird, scrollen Sie nach unten, und geben Sie dann den Namen der Liste in das Feld **Benutzerdefinierten Listennamen eingeben** ein.

    ![Benutzerdefinierte Liste in SharePoint](./media/connection-sharepoint-online/custom-list.png)

    Die Datenquellen werden Ihrer App hinzugefügt.

    ![Liste der der App hinzugefügten Datenquellen](./media/connection-sharepoint-online/data-sources-list.png)

## <a name="show-data-in-a-gallery"></a>Anzeigen von Daten in einem Katalog
Wenn Sie Daten aus einem dieser Spaltentypen in einem Katalog anzeigen möchten, legen Sie über die Formelleiste die **Text**-Eigenschaft für eines oder mehrere **Label**-Steuerelemente (Bezeichnung) in diesem Katalog fest:

* Geben Sie für eine Spalte vom Typ **Auswahl** oder **Nachschlagen** **ThisItem.[Spaltenname].Value** an, um Daten in dieser Spalte anzuzeigen.

    Geben Sie z.B. **ThisItem.Standort.Value** an, wenn Sie eine **Auswahl**-Spalte mit dem Namen **Standort** haben. Geben Sie **ThisItem.PostalCode.Value** für eine **Nachschlage**-Spalte namens **PostalCode** ein.

* Geben Sie bei einer Spalte vom Typ **Person oder Gruppe** **ThisItem.[Spaltenname].DisplayName** an, um den Anzeigenamen des Benutzers oder der Gruppe anzuzeigen.

    Geben Sie z.B. **ThisItem.Manager.DisplayName** an, um die Anzeigenamen aus einer **Person oder Gruppe**-Spalte mit dem Namen **Manager** anzuzeigen.

    Sie können auch andere Informationen zu Benutzern anzeigen, z.B. E-Mail-Adressen oder Positionsbeschreibungen. Um eine vollständige Liste der Optionen anzuzeigen, geben Sie **ThisItem.[Spaltenname].** (mit dem abschließenden Punkt) ein.

    **Hinweis:** Für eine **CreatedBy**-Spalte geben Sie **ThisItem.Author.DisplayName** ein, um die Anzeigenamen von Benutzern anzuzeigen, die die Elemente in der Liste erstellt haben. Für eine **ModifiedBy**-Spalte geben Sie **ThisItem.Editor.DisplayName** ein, um die Anzeigenamen von Benutzern anzuzeigen, die die Elemente in der Liste geändert haben.

* Geben Sie für eine Spalte vom Typ **Verwaltete Metadaten** **ThisItem.[Spaltenname].Label** an, um Daten in dieser Spalte anzuzeigen.

    Geben Sie z.B. **ThisItem.Sprachen.Label** ein, wenn Sie mit einer **Verwaltete Metadaten**-Spalte mit dem Namen **Sprachen** arbeiten.

## <a name="next-steps"></a>Nächste Schritte
* Erfahren Sie, wie Sie [Daten aus einer Datenquelle anzeigen](../add-gallery.md).
* Erfahren Sie, wie Sie [Details anzeigen und Datensätze erstellen oder aktualisieren](../add-form.md).
* Hier erhalten Sie Informationen zu anderen Arten von [Datenquellen](../connections-list.md), mit denen Sie eine Verbindung herstellen können.
