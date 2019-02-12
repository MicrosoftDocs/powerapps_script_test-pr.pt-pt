---
title: Häufige Probleme und Lösungen für PowerApps | Microsoft-Dokumentation
description: Eine Liste häufiger Probleme und Lösungen für PowerApps.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/02/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f5701f85d28d987229aa56756b5c1817892bd5c0
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42855100"
---
# <a name="common-issues-and-resolutions-for-powerapps"></a>Häufige Probleme und Lösungen für PowerApps

Dieser Artikel listet einige häufige Probleme auf, die bei der Verwendung von PowerApps auftreten können. Nach Möglichkeit werden Problemumgehungen bereitgestellt.

## <a name="added-after-february-2018"></a>Änderungen nach Februar 2018

1. **Mehrere Medien-Steuerelemente in PowerApps Mobile** (2. August 2018)

    PowerApps Mobile kann auf verschiedenen Arten von Geräten ausgeführt werden. Einige dieser Geräte weisen plattformspezifische Einschränkungen auf:

    - Mit Ausnahme von iPhone-Geräten können Sie Videos auf allen Plattformen in mehreren **Video**-Steuerelementen gleichzeitig abspielen.
    - Mit Ausnahme des Webplayers können Sie auf allen Plattformen Audio mit mehreren **Microphone**-Steuerelementen gleichzeitig aufzeichnen.

1. **Erneutes Veröffentlichen von Apps** (2. August 2018)

    Wenn Sie Ihre App über mehrere Monate hinweg nicht aktualisiert haben, können Sie sie erneut veröffentlichen, um sie mit der aktuellsten Version von PowerApps zu synchronisieren, wobei Leistungsverbesserungen und andere Fehlerbehebungen angewendet werden.

1. <a name="out-of-memory"></a>**Browser hat nicht genügend Arbeitsspeicher** (23. Juli 2018)

    Wenn Sie bei der Verwendung von PowerApps nicht mehr genügend Arbeitsspeicher haben, sollten Sie eine 64-Bit-Version von Chrome, Edge oder Internet Explorer herunterladen.

1. **Starten einer Website aus einer eingebetteten App** (10. Mai 2018)

    Internet Explorer und Microsoft Edge blockieren möglicherweise den Aufruf einer URL oder Website, die sich im geschützten Modus oder in einer niedrigeren Sicherheitszone als die Website befindet, in der die App geladen wurde. Um dieses Problem zu lösen, [ändern Sie die Sicherheits- und Datenschutzeinstellungen](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings) für Ihren Browser.

1. **Kombinationsfeld-Steuerelemente in Katalogen** (3. Mai 2018)

    Wenn Sie ein Steuerelement des Typs **Kombinationsfeld** innerhalb eines Katalogs verwenden, werden die ausgewählten Optionen nicht beibehalten, sobald der Benutzer durch den Katalog scrollt. Dies ist kein Problem, wenn Sie ein Steuerelement des Typs **Kombinationsfeld** in einem Katalog verwenden, der Scrollen nicht unterstützt. Eine Problemumgehung ist derzeit nicht verfügbar.

1. **Verwenden eines benutzerdefinierten Bilds als App-Symbol** (11. April 2018)

    In PowerApps Studio für Windows Version 3.18043 können Sie kein benutzerdefiniertes Bild zur Verwendung als App-Symbol hochladen. Wenn Sie dieses Problem umgehen wollen, verwenden Sie [PowerApps Studio für Web](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), um ein benutzerdefiniertes Bild hochzuladen. Stattdessen können Sie auch eins der Symbole verwenden, das in PowerApps Studio für Windows enthalten ist und die Hintergrundfarbe anpassen.

1. **Kopieren und Einfügen von Anzeigen über mehrere Apps hinweg** (4. April 2018)

    Das Kopieren und Einfügen von Anzeigen über mehrere Apps wird derzeit nicht unterstützt. Wenn Sie dieses Problem umgehen möchten, fügen Sie eine neue Anzeige zu Ihrer Ziel-App hinzu, kopieren Sie die Steuerelemente aus der Anzeige in die Quell-App, und fügen Sie sie in die Anzeige Ihrer Ziel-App ein.

1. **Ändern des Layouts von SharePoint-Formularen** (7. März 2018)

    Wenn Sie in bestimmten Sprachen ein Formular in einer SharePoint-Liste anpassen und versuchen, das Layout vom Hochformat (Standard) in das Querformat zu ändern, werden in der App möglicherweise mehrere Fehler angezeigt (gelbe Dreiecke in Steuerelementen). Um diese Fehler zu beheben und das Layout mit Querformat zu erhalten, klicken Sie auf **Rückgängig**.

## <a name="added-in-or-before-february-2018"></a>Änderungen im oder vor dem Februar 2018

1. **Data Table-Steuerelement**

    Wenn Sie ein **Data Table**-Steuerelement kopieren und einfügen, für das die **Items**-Eigenschaft auf eine Formel mit einer **Filter**-Funktion festgelegt wurde, enthalten die Feldnamen in der Formel für die **Items**-Eigenschaft im neuen **Data Table**-Steuerelement das Suffix **_1**. Hierdurch werden die Feldnamen ungültig, und es werden keine Daten in der Datentabelle angezeigt. Um dieses Problem zu umgehen, überprüfen Sie vor dem Kopieren des Steuerelements, dass die **Filter**-Funktion nicht auf ein Feld in der Datenquelle verweist, dessen Name dem Namen einer Spalte im **Data Table**-Steuerelement entspricht. Wenn es der Fall ist, benennen Sie die Spalte im **Data Table**-Steuerelement um. Alternativ können Sie das Suffix **_1** aus den ungültigen Feldnamen entfernen, damit sie den Namen in der Entität entsprechen.

1. **Kamerasteuerelemente in PowerApps Studio für Windows**

    PowerApps Studio für Windows stürzt möglicherweise ab, wenn Sie ein Kamerasteuerelement hinzufügen oder eine App öffnen, die ein Kamerasteuerelement verwendet. Um dieses Problem zu vermeiden, verwenden Sie [PowerApps Studio for Web](create-app-browser.md), wenn Sie ein Kamerasteuerelement hinzufügen oder nutzen.

1. **Version 2.0.700 auf Android-Geräten**

    Wenn Sie Version 2.0.700 auf einem Android-Gerät installieren und Apps nicht geöffnet werden können (oder eine App nicht mehr reagiert), deinstallieren Sie PowerApps, starten Sie das Gerät neu, und installieren Sie dann PowerApps erneut.

1. **„Leerer“ Katalog beim Öffnen einer App**

    Wenn Sie automatisch eine App auf der Grundlage von Daten erstellen, die App speichern und anschließend wieder öffnen, werden im durchsuchbaren Katalog möglicherweise nicht sofort Daten angezeigt. Geben Sie zum Beheben dieses Problems mindestens ein Zeichen im Suchfeld ein, und löschen Sie dann den eingegebenen Text. Im Katalog werden nun ordnungsgemäß die Daten angezeigt.

1. **Aktualisieren von PowerApps unter Windows 8.1**

    Wenn Sie PowerApps auf einem Computer installieren, auf dem Windows 8 oder Windows 8.1 ausgeführt wird, lassen Sie die Windows Store-App geöffnet und aktiv, suchen Sie über den Charm „Einstellungen“ nach Updates, und installieren Sie diese.

1. **Benutzerdefinierte Connectors und der Common Data Service**

    Wenn eine mithilfe von PowerApps Build 2.0.540 oder früher erstellte App auf einer Datenbank im Common Data Service und wenigstens einem benutzerdefinierten Connector in einer anderen Umgebung basiert, müssen Sie den Connector in der gleichen Umgebung wie die Datenbank bereitstellen und die App so aktualisieren, dass sie den neuen Connector verwendet. Andernfalls teilt ein Dialogfeld Benutzern mit, dass die API nicht gefunden wurde. Weitere Informationen finden Sie in der [Übersicht zu Umgebungen](../../administrator/environments-overview.md).

1. **Ausführen einer App unter Windows 8.1**

    Wenn Sie [dieses Update für Windows 8.1](https://technet.microsoft.com/library/security/ms16-118) installieren, können Sie Apps, die Sie in PowerApps Studio öffnen, nicht unter diesem Betriebssystem ausführen. Sie können Apps jedoch weiterhin ausführen, die Sie in [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) oder mithilfe von PowerApps Mobile öffnen.

1. **Spaltennamen mit Leerzeichen**

    Bei Verwendung einer SharePoint-Liste oder Excel-Tabelle, in denen ein Spaltenname ein Leerzeichen enthält, wird dieses von PowerApps durch **"\_X0020\_"** ersetzt. **"Name der Spalte"** in SharePoint oder Excel wird beispielsweise in PowerApps bei Anzeige im Datenlayout oder Verwendung in einer Formel als **"Name_x0020_der_x0020_Spalte"** angezeigt.

1. **Ändern eines Flows in einer freigegebenen Anwendung**

    Wenn Sie einer App einen Flow hinzufügen, sie freigeben und dann einen Dienst hinzufügen oder eine Verbindung im Flow ändern, müssen Sie den Flow aus der freigegebenen App entfernen, den Flow erneut hinzufügen und die App erneut freigeben. Andernfalls empfangen Benutzer, die den Flow auslösen, einen Authentifizierungsfehler.

1. **Verwenden einer lokalisierten Version**.

    Wenn Sie Version 2.0.531 unter Windows 8.1 ausführen, können Sie in einem **Texteingabe**-Steuerelement keine Eingaben vornehmen, wenn das Gerät auf eine Sprache eingestellt ist, für die ein IME-Fenster erforderlich ist.

1. **Kamerasteuerelement eines Windows Phones**

    Eine Anwendung, die ein Kamerasteuerelement enthält, stürzt möglicherweise ab, wenn Sie die App auf einem Windows Phone öffnen, das Build 10.0.10586.107 ausführt. Führen Sie zur Vermeidung dieses Problems ein Upgrade auf den aktuellen Build aus (etwa, indem Sie den [Aktualisierungsratgeber](https://www.microsoft.com/store/p/upgrade-advisor/9nblggh0f5g4) ausführen).

1. **Öffnen einer App aus einer Vorlage**

    Wenn Sie das Release 2.0.500 oder ein früheres ausführen, wird eine Fehlermeldung angezeigt, wenn Sie versuchen, eine App aus einer Vorlage zu erstellen. Sie müssen ein Upgrade durchführen, um diese Funktion verwenden zu können.

    Wenn Sie das Release 2.0.510 oder ein späteres ausführen, wird möglicherweise eine Warnung angezeigt, wenn Sie versuchen, eine App aus einer Vorlage zu erstellen. Sie können die Meldung jedoch schließen und die App erstellen.

1. **Scannen eines Barcodes**

    Informationen zu Beschränkungen und bewährten Methoden beim Verwenden eines **Barcode**-Steuerelements finden Sie unter [Scan a barcode (Scannen eines Barcodes)](scan-barcode.md).

1. **Erstellen und Bearbeiten von Apps in einem Browser**

    Viele (jedoch nicht alle) Vorgänge, die Sie in PowerApps Studio für Windows ausführen können, können Sie auch in PowerApps Studio für das Web ausführen. Weitere Informationen finden Sie unter [Create or edit apps in a browser (Erstellen oder Bearbeiten von Apps in einem Browser)](create-app-browser.md).

1. **Ändern eines Titelfelds in einer Entität**

    Wenn Sie das Titelfeld für eine Entität ändern, auf die andere Entitäten über mindestens ein Nachschlagefeld verweisen, tritt ein Fehler auf, wenn Sie versuchen, die Änderung zu speichern. Um dieses Problem zu umgehen, entfernen Sie alle Nachschlagefelder für die Entität, bei der Sie das Titelfeld ändern möchten, nehmen Sie die Änderung vor, und erstellen Sie die Nachschlagefelder erneut. Weitere Informationen zu Nachschlagefeldern finden Sie unter [Erstellen einer Beziehung zwischen Entitäten](../common-data-service/data-platform-entity-lookup.md).

1. **Apps, die eine Verbindung mit lokalem SharePoint herstellen**

    Wenn Sie eine App freigeben, die auf Verbindungen beruht, die nicht automatisch freigegeben werden (z.B. eine lokale SharePoint-Website), wird Benutzern, die die App in einem Browser öffnen, ein Dialogfeld ohne Text angezeigt, wenn Sie auf **Anmelden** klicken oder tippen. Klicken oder tippen Sie auf das „Schließen“-Symbol (X) in der rechten oberen Ecke, um das Dialogfeld zu schließen. Das Dialogfeld wird nicht angezeigt, wenn Sie die App in PowerApps Studio oder PowerApps Mobile öffnen. Weitere Informationen zu freigegebenen Verbindungen finden Sie unter [Share app resources (Freigeben von App-Ressourcen)](share-app-resources.md).

1. **Wenn PowerApps aus Daten eine App generiert, wird das Feld zum Sortieren und Durchsuchen nicht automatisch konfiguriert**.

   Um dieses Feld zu konfigurieren, bearbeiten Sie die **[Elemente](controls/properties-core.md)**-Formel für den Katalog, wie in den Abschnitten zum Filtern und Sortieren unter [Add a gallery (Hinzufügen eines Katalogs)](add-gallery.md) beschrieben.

1. **Bei Apps, die aus Daten erstellt werden, kann nur auf die ersten 500 Datensätze einer Datenquelle zugegriffen werden**.

     Im Allgemeinen arbeitet PowerApps mit Datenquellen jeder Größe, indem Vorgänge an die Datenquelle delegiert werden. Bei Vorgängen, die nicht delegiert werden können, gibt PowerApps beim Erstellen eine Warnung aus und führt den Vorgang nur für die ersten 500 Datensätze der Datenquelle aus.  Weitere Informationen zur Delegierung finden Sie im Artikel zur [Filterfunktion](functions/function-filter-lookup.md).

1. **Excel-Daten müssen als Tabelle formatiert sein**.

     Weitere Informationen zu Einschränkungen bei der Verwendung von Excel als Datenquelle finden Sie unter [Cloudspeicherverbindungen](connections/cloud-storage-blob-connections.md#known-limitations).

1. **Benutzerdefinierte SharePoint-Listen werden unterstützt, Bibliotheken jedoch nicht, bestimmte Typen von Listenspalten oder Spalten, die mehrere Werte oder Auswahlen unterstützen**.

     Weitere Informationen finden Sie unter [SharePoint Online](connections/connection-sharepoint-online.md#known-issues).

1. **Die gemeinsame Erstellung wird nicht unterstützt. Bitte immer nur ein Autor zur gleichen Zeit**.

     Wenn mehr als eine Person zur gleichen Zeit die gleiche App bearbeitet, kann eine App beschädigt oder die Änderungen von Anderen überschrieben werden. Schließen Sie die App, bevor sie von einer anderen Person bearbeitet wird.

1. **Manchmal kann es einen Moment dauern, bis eine neu freigegebene App verwendet werden kann**.

     In einigen Fällen ist eine neu freigegebene App nicht sofort verfügbar. Warten Sie einige Minuten, und sie sollte verfügbar sein.

1. **Im [Formularsteuerelement](controls/control-form-detail.md), können Sie Daten nicht mithilfe einer benutzerdefinierten Karte ändern**.

     Der bestehenden benutzerdefinierten Karte fehlt die **[Update](controls/control-card.md)**-Eigenschaft, die für das Zurückschreiben von Änderungen benötigt wird. Dieses Problem können Sie folgendermaßen umgehen:

    * Wählen Sie das Formularsteuerelement aus, und fügen Sie eine Karte mithilfe des rechten Bereichs basierend auf dem Feld ein, das mit der Karte angezeigt werden soll.  
    * Entsperren Sie die Karte, wie unter [Understand data cards (Grundlegendes zu Datenkarten)](working-with-cards.md#unlock-a-card) beschrieben.
    * Entfernen Sie Steuerelemente, oder ordnen Sie diese passend neu an, so wie Sie es mit der benutzerdefinierten Karte machen würden.

1. **Eine App, die auf Android 5.0, Nexus 6 mit den WebView-Versionen 48 oder 49 ausgeführt wird, kann abstürzen**.

     Benutzer können dieses Problem beheben, indem Sie auf eine niedrigere Version von WebView (3x) oder auf Android 6.0 aktualisieren.

1. **Die Kameraverwendung kann vorübergehend deaktiviert sein, wenn der Speicherplatz gering ist**.

     Wenn der Speicherplatz Ihres mobilen Geräts gering ist, wird die Kamera vorübergehend deaktiviert, um zu verhindern, dass das Gerät abstürzt.

1. **Der Office 365-Video-Connector wird nicht unterstützt**.

1. **Der Kartenkatalog wird nicht mehr unterstützt**.

     Vorhandene Apps, die diese Funktion verwenden, werden vorerst weiter ausgeführt, Sie können jedoch keinen Kartenkatalog hinzufügen. Ersetzen Sie Kartenkataloge mit den neuen Steuerelementen **[Edit form](controls/control-form-detail.md)** (Formular bearbeiten) und **[Display form](controls/control-form-detail.md)** (Formular anzeigen).
