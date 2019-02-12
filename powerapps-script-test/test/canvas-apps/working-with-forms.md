---
title: Grundlegendes zu Canvas-App-Formularen | Microsoft-Dokumentation
description: Fügen Sie in PowerApps einer Canvas-App ein Formular hinzu, damit Sie Informationen aus einer Datenquelle erfassen und anzeigen können.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/27/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 661f6710c8cec55868ccc9d67d0f83dd230f89c1
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42851735"
---
# <a name="understand-canvas-app-forms-in-microsoft-powerapps"></a>Grundlegendes zu Canvas-App-Formularen in Microsoft PowerApps

Fügen Sie einer Canvas-App drei Arten von Steuerelementen hinzu, damit Benutzer nach einem Datensatz suchen, Einzelheiten zu dem Datensatz anzeigen oder einen Eintrag dazu bearbeiten oder erstellen können:

| Aktivität | Steuerelement | Beschreibung |
| --- | --- | --- |
| **Nach einem Datensatz suchen** |**[Katalog](controls/control-gallery.md)**-Steuerelement |Filtern, sortieren, suchen Sie nach und scrollen Sie durch Datensätze in einer Datenquelle, und wählen Sie einen bestimmten Datensatz aus. Zeigen Sie nur ein paar Felder aus jedem Datensatz an, um mehrere Einträge gleichzeitig anzuzeigen, sogar auf einem kleinen Bildschirm. |
| **Details eines Datensatzes anzeigen** |**[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement |Zeigen Sie für einen einzelnen Datensatz viele oder alle Felder in diesem Datensatz an. |
| **Einen Datensatz erstellen oder bearbeiten** |**[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement |Aktualisieren Sie mindestens ein Feld in einem einzelnen Datensatz (oder erstellen Sie einen Datensatz, der mit Standardwerten beginnt), und speichern Sie diese Änderungen in der zugrunde liegenden Datenquelle. |

Platzieren Sie jedes Steuerelement auf einem anderen Bildschirm, um die Unterscheidung zu erleichtern:

![Durchsuchen, Anzeigen und Bearbeiten von Datensätzen auf drei Bildschirmen](./media/working-with-forms/three-screens.png)

Kombinieren Sie diese Steuerelemente mit Formeln, wie in diesem Thema beschrieben, um die allgemeine Benutzeroberfläche zu erstellen.

## <a name="prerequisites"></a>Voraussetzungen

* [Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.
* Erfahren Sie, wie Sie [ein Steuerelement](add-configure-controls.md) in PowerApps konfigurieren.

## <a name="explore-a-generated-app"></a>Kennenlernen einer generierten App
Mit PowerApps können Sie automatisch basierend auf einer von Ihnen ausgesuchten Datenquelle eine App generieren. Jede App enthält drei Bildschirme mit den zuvor beschriebenen Steuerelementen und Formeln, die diese verbinden. Diese Apps lassen sich ohne vorherige Installation ausführen, an Ihre bestimmten Ziele anpassen oder in ihrer Funktionsweise untersuchen, damit Sie nützliche Konzepte erfahren und auf Ihre eigenen Apps anwenden können. Überprüfen Sie in den folgenden Abschnitten die Bildschirme, Steuerelemente und Formeln, die eine generierte App steuern.  

### <a name="browse-screen"></a>Bildschirm zum Durchsuchen
![Steuerelemente auf dem Bildschirm zum Durchsuchen](./media/working-with-forms/afd-browse-screen-basic.png)

Dieser Bildschirm bietet folgende Schlüsselformeln:

| Steuerelement | Unterstütztes Verhalten | Formel |
| --- | --- | --- |
| **BrowseGallery1** |Zeigen Sie Datensätzen aus der **Assets**-Datenquelle (verfügbare Objekte) an. |Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des Katalogs auf eine Formel fest, die auf der Datenquelle **Bestand** basiert. |
| **ImageNewItem1** |Zeigen Sie den Bildschirm **Bearbeiten und Erstellen** an, wobei jedes Feld auf einen Standardwert festlegen, sodass der Benutzer einen Datensatz leicht erstellen kann. |Die **[OnSelect](controls/properties-core.md)**-Eigenschaft des Bilds ist auf die folgende Formel festgelegt:<br> **NewForm( EditForm1 );<br>Navigate( EditScreen1, None )** |
| **NextArrow1** (im Katalog) |Zeigen Sie den Bildschirm **Details** an, um den aktuell ausgewählten Datensatz viele oder alle Felder anzeigen. |Die **[OnSelect](controls/properties-core.md)**-Eigenschaft des Pfeils ist auf die folgende Formel festgelegt:<br>**Navigate( DetailScreen1, None )** |

Das primäre Steuerelement auf diesem Bildschirm, **BrowseGallery1**, deckt die meisten der Bildschirmbereiche ab. Der Benutzer kann durch den Katalog scrollen, um einen bestimmten Datensatz zu suchen und weitere Felder anzuzeigen oder um zu aktualisieren.

Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft einer Katalogeigenschaft fest, um Datensätze auf Adoptionsheimen aus einer Datenquelle darin angezeigt. Legen Sie diese Eigenschaft beispielsweise auf **Bestand** fest, um Datensätze aus einer gleichnamigen Datenquelle anzuzeigen.

> [!NOTE]
> In einer generierten App wird **[Items](controls/properties-core.md)** standardmäßig auf eine wesentlich schwierigere Formel festgelegt, damit der Nutzer Daten sortieren und nach Datensätzen suchen kann. Sie erfahren später in diesem Thema, wie Sie die Formel erstellen. Die einfachere Version ist genug für heute.

Anstatt einen Datensatz zum Anzeigen oder Bearbeiten zu suchen, kann der Benutzer einen Datensatz erstellen, indem er auf das Symbol „+“ über dem Katalog klickt. Erzeugen Sie diesen Effekt , indem Sie ein **[Image](controls/control-image.md)**-Steuerelement mit einem „+“ darin hinzufügen und seine Eigenschaft **[OnSelect](controls/properties-core.md)** auf diese Formel festlegen:
<br>**NewForm( EditForm1 ); Navigate( EditScreen1, None )**

Mit dieser Formel wird der Bildschirm **Bearbeiten und Erstellen** geöffnet, der ein Steuerelement **[Formular bearbeiten](controls/control-form-detail.md)** namens **EditForm1** enthält. Die Formel ändert dieses Formular auch in den Modus **Neu**, in dem das Formular Standardwerte aus der Datenquelle zeigt, damit der Benutzer einen Datensatz leicht neu erstellen kann.

Um alle Steuerelemente in **BrowseGallery1** zu untersuchen, wählen Sie das Steuerelement im ersten Abschnitt des Katalogs aus, das als Vorlage für alle weiteren Abschnitte dient. Wählen Sie beispielsweise das mittlere **[Label](controls/control-text-box.md)**-Steuerelement am linken Rand aus:

![Steuerelemente auf dem Bildschirm zum Durchsuchen](./media/working-with-forms/afd-browse-gallery-controls.png)

In diesem Beispiel wird die **[Text](controls/properties-core.md)**-Eigenschaft des Steuerelements auf **ThisItem.AssignedTo** festgelegt, wobei es sich um ein Feld in der Datenquelle **Bestand** handelt. Die **[Text](controls/properties-core.md)**-Eigenschaft der anderen drei **[Label](controls/control-text-box.md)**-Steuerelemente im Katalog sind auf ähnliche Formeln festgelegt, und jedes Steuerelement zeigt ein anderes Feld in der Datenquelle.  

Wählen Sie das Steuerelement **[Symbole](controls/control-shapes-icons.md)** (Pfeil) aus, und überprüfen Sie, ob die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf diese Formel festgelegt wurde:
<br>**Navigate( DetailScreen1, None )**

Wenn der Benutzer in **BrowseGallery1** einen Datensatz findet, kann der Benutzer auf den Pfeil für den entsprechenden Datensatz klicken, um weitere Informationen in **DetailScreen1** anzuzeigen. Durch einen Klick auf den Pfeil ändert der Benutzer den Wert der Eigenschaft **Selected** von **BrowseGallery1**. In dieser App bestimmt diese Eigenschaft, welcher Datensatz nicht nur auf dem Bildschirm **DetailScreen1** erscheint, sondern – falls der Benutzer den Datensatz aktualisieren möchte – auch auf dem Bildschirm **Bearbeiten und Erstellen**.

### <a name="detail-screen"></a>Details-Bildschirm
![Steuerelemente auf dem Details-Bildschirm](./media/working-with-forms/afd-detail-screen-basic.png)

Dieser Bildschirm bietet folgende Schlüsselformeln:

| Steuerelement | Unterstütztes Verhalten | Formel |
| --- | --- | --- |
| **DetailForm1** |Zeigt einen Datensatz in der Datenquelle **Bestand** |Legen Sie die **[DataSource](controls/control-form-detail.md)**-Eigenschaft auf **Assets** fest. |
| **DetailForm1** |Bestimmt, welcher Datensatz angezeigt wird. In einer generierten App wird der Datensatz angezeigt, den der Benutzer im Katalog ausgewählt hat. |Legen Sie die **[Item](controls/control-form-detail.md)**-Eigenschaft dieses Steuerelements auf diesen Wert fest:<br>**BrowseGallery1.Selected** |
| **[Karten](controls/control-card.md)**-Steuerelemente |In einem Steuerelement **[Formular anzeigen](controls/control-form-detail.md)** wird ein einzelnes Feld in einem Datensatz angezeigt. |Legen Sie die **[DataField](controls/control-card.md)**-Eigenschaft auf den Namen eines Felds in doppelten Anführungszeichen (z.B. **"Name"**) fest. |
| **ImageBackArrow1** |Wenn der Benutzer dieses Steuerelement auswählt, öffnet sich **BrowseScreen1**. |Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>**Back()** |
| **ImageDelete1** |Wenn der Benutzer dieses Steuerelement auswählt, wird ein Datensatz gelöscht. |Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>**Remove( Assets, BrowseGallery1.Selected )** |
| **ImageEdit1** |Wenn der Benutzer dieses Steuerelement auswählt, öffnet sich der Bildschirm **Bearbeiten und Erstellen** des aktuellen Datensatzes. |Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>**Navigate( EditScreen1, None )** |

Am oberen Bildschirmrand befinden sich drei Bilder außerhalb von **DetailForm1** und fungieren als Schaltflächen, die zwischen den drei Bildschirmen der App orchestriert.

**DetailForm1** überwiegt auf diesem Bildschirm und zeigt den Datensatz an, den der Benutzer im Katalog ausgewählt hat (weil die **[Item](controls/control-form-detail.md)**-Eigenschaft des Formulars auf **BrowseGallery1.Selected** festgelegt ist). Die **[DataSource](controls/control-form-detail.md)**-Eigenschaft des Formulars stellt auch Metadaten über die Datenquelle bereit, z.B. einen benutzerfreundlichen Anzeigenamen für jedes Feld.

**DetailForm1** enthält mehrere **[Karten](controls/control-card.md)**-Steuerelemente. Sie können entweder das **[Karten](controls/control-card.md)**-Steuerelement selbst oder das Steuerelement auswählen, das es enthält, um zusätzliche Informationen abzurufen.

![Details zu „Karten“ und ausgewählte Karten-Steuerelemente in der Autoren-Benutzeroberfläche](./media/working-with-forms/afd-detail-card-controls.png)

Die **[DataField](controls/control-card.md)**-Eigenschaft eines **[Karten](controls/control-card.md)**-Steuerelements bestimmt, welches Feld die Karte anzeigt. In diesem Fall wird diese Eigenschaft auf **AssetID** festgelegt. Die Karte enthält ein **[Label](controls/control-text-box.md)**-Steuerelement, für das die **[Text](controls/properties-core.md)**-Eigenschaft auf **Parent.Default** festgelegt wird. Dieses Steuerelement zeigt den **Standardwert** für die Karte an, der über die **[DataField](controls/control-card.md)**-Eigenschaft festgelegt wird.

In einer generierten App sind **[Karten](controls/control-card.md)**-Steuerelemente standardmäßig gesperrt. Wenn eine Karte gesperrt ist, können Sie einige Eigenschaften wie **[DataField](controls/control-card.md)** nicht ändern, und die Bearbeitungsleiste ist für diese Eigenschaften nicht verfügbar. Diese Einschränkung trägt dazu bei, dass Ihre Anpassungen die grundlegende Funktionalität der generierten App nicht unterbrechen. Sie können allerdings einige Eigenschaften einer Karte und ihrer Steuerelemente im rechten Bereich ändern:

![Details-Bildschirm mit geöffnetem Optionsbereich](./media/working-with-forms/detail-screen-new.png)

Sie können im rechten Bereich auswählen, welche Felder angezeigt werden sollen und welche Art von Steuerelement jedes Feld anzeigen soll.

### <a name="editcreate-screen"></a>Bildschirm zum Erstellen/Bearbeiten
![Steuerelemente zum Erstellen/Bearbeiten](./media/working-with-forms/afd-edit-screen-basic.png)

Dieser Bildschirm bietet folgende Schlüsselformeln:

| Steuerelement | Unterstütztes Verhalten | Formel |
| --- | --- | --- |
| **EditForm1** |Zeigt einen Datensatz in der **Assets**-Datenquelle |Legen Sie die **[DataSource](controls/control-form-detail.md)**-Eigenschaft auf **Assets** fest. |
| **EditForm1** |Bestimmt, welcher Datensatz angezeigt wird. In einer generierten App wird der Datensatz angezeigt, den der Benutzer in **BrowseScreen1** ausgewählt hat. |Legen Sie die **[Item](controls/control-form-detail.md)**-Eigenschaft auf diesen Wert fest:<br>**BrowseGallery1.Selected** |
| **[Karten](controls/control-card.md)**-Steuerelemente |In einem Steuerelement **[Formular bearbeiten](controls/control-form-detail.md)** werden Steuerelemente bereitgestellt, damit der Benutzer mindestens ein Feld in einem Datensatz bearbeiten kann. |Legen Sie die **[DataField](controls/control-card.md)**-Eigenschaft auf den Namen eines Felds in doppelten Anführungszeichen (z.B. **"Name"**) fest. |
| **ImageCancel1** |Wenn der Benutzer dieses Steuerelement auswählt, werden alle aktuellen Änderungen verworfen, und es öffnet sich der Bildschirm **Details**. |Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>**ResetForm( EditForm1 ); Back()** |
| **ImageAccept1** |Wenn der Benutzer dieses Steuerelement auswählt, werden Änderungen an die Datenquelle gesendet. |Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>**SubmitForm( EditForm1 )** |
| **EditForm1** |Wenn Änderungen akzeptiert werden, gelangen Sie zurück zum vorherigen Bildschirm. |Legen Sie die **[OnSuccess](controls/control-form-detail.md)**-Eigenschaft auf die folgende Formel fest:<br>**Back()** |
| **EditForm1** |Wenn die Änderungen nicht akzeptiert werden, bleiben Sie auf dem aktuellen Bildschirm, damit der Benutzer Sie jegliche Probleme beseitigen und versuchen kann, die Änderungen erneut zu senden. |Lassen Sie die **[OnFailure](controls/control-form-detail.md)**-Eigenschaft leer. |
| **LblFormError1** |Wenn die Änderungen nicht akzeptiert werden, wird eine Fehlermeldung angezeigt. |Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft auf diesen Wert fest:<br>**EditForm1.Error** |

Wie auf dem Bildschirm **Details** überwiegt auf dem Bildschirm **Bearbeiten und Erstellen** ein Formularsteuerelement namens **EditForm1**. Darüber hinaus wird die **[Item](controls/control-form-detail.md)**-Eigenschaft von **EditForm1** auf **BrowseGallery1.Selected** festgelegt, sodass das Formular den Datensatz anzeigt, den der Benutzer in **BrowseScreen1** ausgewählt hat. Während der Bildschirm **Details** jedes Feld als schreibgeschützt anzeigt, kann der Benutzer den Wert von mindestens einem Feld mithilfe der Steuerelemente in **EditForm1** aktualisieren. Darüber hinaus wird die **[DataSource](controls/control-form-detail.md)**-Eigenschaft verwendet, um auf Metadaten zu dieser Datenquelle wie den benutzerfreundlichen Anzeigenamen für jedes Feld und den Speicherort für Änderungen zuzugreifen.

Klickt der Benutzer das Symbol "X" klickt, um ein Update abzubrechen, verwirft die Funktion **[ResetForm](functions/function-form.md)** alle nicht gespeicherten Änderungen, und die Funktion **[Back](functions/function-navigate.md)** öffnet den Bildschirm **Details**. Sowohl der Bildschirm **Details** als auch der Bildschirm **Bearbeiten und Erstellen** zeigen den gleichen Datensatz an, bis der Benutzer einen anderen in **BrowseScreen1** auswählt. Die Felder in diesem Datensatz bleiben auf die zuletzt gespeicherten Werte festgelegt, nicht auf die vorgenommenen und dann verworfenen Änderungen.

Wenn der Benutzer einen oder mehrere Werte im Formular ändert und dann das Häkchensymbol anklickt, sendet die Funktion **[SubmitForm](functions/function-form.md)** die Änderungen des Benutzers an die Datenquelle.

* Wenn die Änderungen erfolgreich gespeichert wurden, wird **[OnSuccess](controls/control-form-detail.md)**-Formel des Formulars ausgeführt, und die **Back()**-Funktion öffnet den Detailbildschirm, um den aktualisierten Datensatz anzuzeigen.
* Wenn die Änderungen nicht erfolgreich gespeichert wurden, wird die **[OnFailure](controls/control-form-detail.md)**-Formel des Formulars ausgeführt, was nichts ändert, da sie *leer* ist. Der Bildschirm **Bearbeiten und Erstellen** bleibt geöffnet, damit der Benutzer die Änderungen verwerfen oder den Fehler beheben kann. **LblFormError1** zeigt eine benutzerfreundliche Fehlermeldung an, auf die die **Error**-Eigenschaft des Formulars festgelegt ist.

Wie bei einem **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement enthält ein **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement **[Karten](controls/control-card.md)**-Steuerelemente, die andere Steuerelemente enthalten, die verschiedenen Felder in einem Datensatz anzeigen:

![Karten bearbeiten und ausgewählte Karten-Steuerelemente in der Autoren-Benutzeroberfläche](./media/working-with-forms/afd-edit-card-controls.png)

In der vorherigen Abbildung zeigt die ausgewählte Karte das **AssetID**-Feld und enthält ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement, sodass der Benutzer den Wert dieses Felds bearbeiten kann. (Der Detailbildschirm zeigt das gleiche Feld im Gegensatz dazu in einem **[Label](controls/control-text-box.md)**-Steuerelement an, das schreibgeschützt ist.) Das **[Texteingabe](controls/control-text-input.md)**-Steuerelement verfügt über eine **[Default](controls/properties-core.md)**-Eigenschaft, die auf **Parent.Default** festgelegt wird. Würde der Benutzer einen Datensatz erstellen anstatt ihn zu bearbeiten, würde dieses Steuerelement einen Anfangswert anzeigen, den der Benutzer durch den neuen Eintrag austauschen kann.

Im rechten Bereich können Sie alle Karten ein- oder ausblenden, sie anordnen oder sie so konfigurieren, dass sie Felder in verschiedenen Arten von Steuerelementen anzeigen.

![Bearbeitungsbildschirm mit geöffnetem Optionsbereich](./media/working-with-forms/edit-screen.png)

## <a name="build-an-app-from-scratch"></a>Eine App von Grund auf neu erstellen
Wenn Sie verstehen, wie PowerApps eine App generiert, können Sie selbst eine erstellen, die dieselben Bausteine und Formeln verwendet, die weiter oben in diesem Thema erläutert wurden.

## <a name="identify-test-data"></a>Ermitteln von Testdaten
Um so viel wie möglich aus diesem Thema zu lernen, sollten Sie eine Datenquelle suchen, mit der Sie experimentieren können. Sie sollte Testdaten enthalten, die Sie ohne Bedenken lesen und aktualisieren können.

> [!NOTE]
> Bei Verwendung einer SharePoint-Liste oder Excel-Tabelle als Datenquelle, die Spaltennamen mit Leerzeichen enthält, ersetzt PowerApps die Leerzeichen durch **"\_X0020\_"**. **"Name der Spalte"** in SharePoint oder Excel wird beispielsweise in PowerApps bei Anzeige im Datenlayout oder Verwendung in einer Formel als **"Name_x0020_der_x0020_Spalte"** angezeigt.

Um die restlichen Schritte in diesem Thema genau befolgen zu können, erstellen Sie eine SharePoint-Liste namens „Ice Cream“ (Eiscreme), die folgende Daten enthält:

![Eiscreme-SharePoint-Liste](./media/working-with-forms/sharepointlist-icecream.png)

* Erstellen Sie eine Telefon-App von Grund auf, und [verbinden Sie sie mit Ihrer Datenquelle](add-data-connection.md).
  
    > [!NOTE]
  > Tablet-Apps sind Telefon-Apps sehr ähnlich. Sie können sich aber für ein anderes [Bildschirmlayout](#screen-design) entscheiden, um den zusätzlichen Platz auf dem Bildschirm optimal auszunutzen.
  
    Die Beispiele im Rest des Themas basieren auf einer Datenquelle namens **Ice Cream**.

## <a name="browse-records"></a>Durchsuchen von Datensätzen
Rufen Sie schnelle Informationen aus einem Datensatz ab, indem Sie sie in einem Katalog auf einem Bildschirm zum Durchsuchen suchen.

1. Fügen Sie den Katalog **Vertical** hinzu, und ändern Sie nur das Layout in **Titel**.
   
    ![Mit der Eiscreme-Datenquelle verbundener Katalog](./media/working-with-forms/new-gallery.png)
2. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des Katalogs auf **Ice Cream** fest.
3. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft der ersten Bezeichnung im Katalog auf **ThisItem.Title** fest, falls diese auf etwas anderes festgelegt ist.
   
    Die Bezeichnung zeigt jetzt im Feld **Titel** den Wert für jeden Datensatz.
   
    ![Mit der Eiscreme-Datenquelle verbundener Katalog](./media/working-with-forms/new-gallery-2.png)
4. Ändern Sie die Größe des Katalogs so, dass der Bildschirm eingenommen wird, und legen Sie die **[TemplateSize](controls/control-gallery.md)**-Eigenschaft auf **60** fest.
   
    Der Bildschirm ähnelt diesem Beispiel, das alle Datensätze in der Datenquelle zeigt:
   
    ![Mit der Eiscreme-Datenquelle verbundener Katalog](./media/working-with-forms/new-gallery-icecream.png)

## <a name="view-details"></a>Details anzeigen
Wenn der Katalog die gewünschten Informationen nicht angezeigt, klicken Sie auf den Pfeil für einen Datensatz, um den Bildschirm „Details“ zu öffnen. Ein **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement auf diesem Bildschirm zeigt mehrere, möglicherweise alle Felder für den Datensatz an, den Sie ausgewählt haben.

Das **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement verwendet zwei Eigenschaften, um den Datensatz anzuzeigen:

* **[DataSource](controls/control-form-detail.md)**-Eigenschaft.  Der Name der Datenquelle, die den Datensatz enthält. Diese Eigenschaft füllt den rechten Bereich mit Feldern auf und bestimmt den Anzeigenamen und Datentyp (Zeichenfolge, Zahl, Datum usw.) eines jeden Felds.  
* **[Item](controls/control-form-detail.md)**-Eigenschaft  Der anzuzeigende Datensatz.  Diese Eigenschaft ist häufig mit der **Selected**-Eigenschaft des **[Katalog](controls/control-gallery.md)**-Steuerelements verbunden, sodass der Benutzer einen Datensatz im **[Katalog](controls/control-gallery.md)**-Steuerelement auswählen und diesen Datensatz dann tiefgreifender analysieren kann.

Wenn die **[DataSource](controls/control-form-detail.md)**-Eigenschaft festgelegt ist, können Sie Felder über den rechten Bereich hinzufügen und entfernen sowie ändern, wie die Felder angezeigt werden.

Auf diesem Bildschirm können Benutzer weder absichtlich noch versehentlich Werte des Datensatzes ändern. Das **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement ist ein schreibgeschütztes Steuerelement, das einen Datensatz nicht ändert.

So fügen Sie ein **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement hinzu:

1. Fügen Sie einen Bildschirm hinzu, und fügen Sie dann ein **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement hinzu.
2. Legen Sie die **[DataSource](controls/control-form-detail.md)**-Eigenschaft des Formularsteuerelements auf **Ice Cream** fest.

Im rechten Bereich können Sie auswählen, welche Felder auf dem Bildschirm angezeigt werden sollen und welcher Kartentyp für jedes Feld angezeigt werden soll. Wenn Sie Änderungen im rechten Bereich vornehmen, wird die **[DataField](controls/control-card.md)**-Eigenschaft auf jedem **[Karten](controls/control-card.md)**-Steuerelement auf das Feld festgelegt, mit dem der Benutzer interagieren wird. Ihr Bildschirm sollte diesem Beispiel ähneln:

![„Formular anzeigen“ für die Eiscreme-Datenquelle](./media/working-with-forms/ice-cream-new.png)

Schließlich muss das **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement mit dem **[Katalog](controls/control-gallery.md)**-Steuerelement verbunden werden, sodass ein bestimmter Datensatz detaillierter betrachtet werden kann.  Sobald die **[Item](controls/control-form-detail.md)**-Eigenschaft festgelegt ist, wird der erste Datensatz aus dem Katalog im Formular angezeigt.

* Legen Sie die **[Item](controls/control-form-detail.md)**-Eigenschaft des **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelements auf **Gallery1.Selected** fest.
   
    Die Details zum ausgewählten Element werden im Formular angezeigt.
   
    ![„Formular anzeigen“ für die Eiscreme-Datenquelle, verbunden mit dem Katalog-Steuerelement](./media/working-with-forms/view-form-select-coconut.png)

Super!  Widmen wir uns jetzt der Navigation: wie ein Benutzer den Detailbildschirm vom Katalogbildschirm und den Katalogbildschirm vom Bildschirm „Details“ aus öffnet.

* Fügen Sie eine **[Schaltflächen](controls/control-button.md)**-Steuerelement auf dem Bildschirm hinzu, legen Sie seine **[Text](controls/properties-core.md)**-Eigenschaft auf das Anzeigen von **[Back](functions/function-navigate.md)** fest, und legen Sie seine **[OnSelect](controls/properties-core.md)**-Eigenschaft auf **Back()** fest.
   
    Mit dieser Formel gelangt der Benutzer zurück zum Katalog, wenn er die Details angesehen hat.

    ![„Formular anzeigen“ für die Eiscreme-Datenquelle mit der Schaltfläche „Zurück“](./media/working-with-forms/viewform-icecream-back.png)

Kehren wir jetzt zum **[Katalog](controls/control-gallery.md)**-Steuerelement zurück und fügen einige Navigationselemente zu unserem Detailbildschirm hinzu.

1. Wechseln Sie zum ersten Bildschirm, auf dem sich das **[Katalog](controls/control-gallery.md)**-Steuerelement befindet, und wählen Sie den Pfeil im ersten Element im Katalog aus.

2. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft des Symbols auf die folgende Formel fest:
   <br>**Navigate( Screen2, None )**
   
    ![„Formular anzeigen“ für die Eiscreme-Datenquelle mit der Schaltfläche „Zurück“](./media/working-with-forms/gallery-icecream-nav-new.png)

3. Drücken Sie F5, und wählen Sie dann einen Pfeil im Katalog aus, um die Details eines Elements anzuzeigen.

4. Wählen Sie die **[Zurück](functions/function-navigate.md)**-Schaltfläche an aus, um zum Produktkatalog zurückzukehren, und drücken Sie die ESC-TASTE.

## <a name="editing-details"></a>Bearbeiten von Details
Die letzte Kernaktivität besteht im Ändern des Inhalts eines Datensatzes, was Benutzer mithilfe eines **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelements erreichen.

Das **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement verwendet zwei Eigenschaften, um den Datensatz anzuzeigen zu bearbeiten:

* **[DataSource](controls/control-form-detail.md)**-Eigenschaft.  Der Name der Datenquelle, die den Datensatz enthält.  Wie bei dem **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement füllt diese Eigenschaft den rechten Bereich mit Feldern auf und bestimmt den Anzeigenamen und Datentyp (Zeichenfolge, Zahl, Datum usw.) eines jeden Felds. Diese Eigenschaft bestimmt auch, ob der Wert jedes Felds gültig ist, bevor er an die zugrunde liegende Datenquelle gesendet wird.
* **[Item](controls/control-form-detail.md)**-Eigenschaft  Der zu bearbeitende Datensatz, der häufig mit der **Selected**-Eigenschaft des **[Katalog](controls/control-gallery.md)**-Steuerelements verbunden ist. Auf diese Weise können Sie einen Datensatz im **[Katalog](controls/control-gallery.md)**-Steuerelement auswählen, auf dem Bildschirm „Details“ anzeigen und auf dem Bildschirm **Bearbeiten und Erstellen** bearbeiten.

So fügen Sie ein **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement hinzu:

1. Fügen Sie einem Bildschirm und anschließend ein **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement hinzu, und legen Sie dann die **[DataSource](controls/control-form-detail.md)**-Eigenschaft des Formulars auf **Ice Cream** fest.
2. Legen Sie die **[Item](controls/control-form-detail.md)**-Eigenschaft auf **Gallery1.Selected** fest.

Sie können nun die Felder auswählen, die auf dem Bildschirm angezeigt werden sollen. Sie können auch den Kartentyp auswählen, der für jedes Feld angezeigt werden soll. Wenn Sie Änderungen im rechten Bereich vornehmen, wird die **[DataField](controls/control-card.md)**-Eigenschaft auf jedem **[Karten](controls/control-card.md)**-Steuerelement auf das Feld festgelegt, mit dem Ihr Benutzer interagieren wird.  Ihr Bildschirm sollte diesem Beispiel ähneln:

![„Formular anzeigen“ für die Eiscreme-Datenquelle](./media/working-with-forms/icecream-edit.png)

Diese beiden Eigenschaften stimmen mit den Eigenschaften auf dem **[Formular anzeigen](controls/control-form-detail.md)**-Steuerelement überein.  Allein mit diesen Eigenschaften können die Details eines Datensatzes angezeigt werden.  

Das **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement bietet zudem die Funktion **[SubmitForm](functions/function-form.md)**, mit der Änderungen zurück in die Datenquelle geschrieben werden können. Mithilfe dieser Funktion und einem Schaltflächen- oder Bild-Steuerelement können die Änderungen eines Benutzers gespeichert werden.

* Fügen Sie ein **[Schaltflächen](controls/control-button.md)**-Steuerelement hinzu, legen Sie dessen **[Text](controls/properties-core.md)**-Eigenschaft auf **Save** (Speichern) und dessen **[OnSelect](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
  **SubmitForm( Form1 )**

![Bearbeitungsformular für die Eiscreme-Datenquelle](./media/working-with-forms/edit-icecream-save.png)

So fügen Sie Navigationselemente zu und von diesem Bildschirm hinzu:

1. Fügen Sie ein weiteres **[Schaltflächen](controls/control-button.md)**-Steuerelement hinzu, legen Sie dessen **[Text](controls/properties-core.md)**-Eigenschaft auf **Cancel** (Abbrechen) und dessen **[OnSelect](controls/properties-core.md)**-Eigenschaft auf diese Formel fest: <br>**ResetForm( Form1 ); Back()**
   
    Diese Formel verwirft alle ungespeicherten Änderungen und öffnet den vorherigen Bildschirm.
   
    ![„Formular anzeigen“ für die Eiscreme-Datenquelle](./media/working-with-forms/edit-icecream-cancel.png)
2. Legen Sie die **[OnSuccess](controls/control-form-detail.md)**-Eigenschaft des Formulars auf **Back()** fest.
   
    Wenn die Updates erfolgreich gespeichert wurden, wird der vorherige Bildschirm (in diesem Fall der Bildschirm „Details“) automatisch geöffnet.
   
    ![„Formular bearbeiten“ mit hinzugefügter „OnSuccess“-Regel](./media/working-with-forms/edit-icecream-onsuccess.png)
3. Fügen Sie auf dem **Display**-Bildschirm (Anzeigen) eine Schaltfläche hinzu, legen Sie deren **[Text](controls/properties-core.md)**-Eigenschaft auf **Edit** (Bearbeiten) und dessen **[OnSelect](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br> **Navigate( Screen3, None )**
   
    ![„Formular anzeigen“ mit hinzugefügter Schaltfläche „Bearbeiten“](./media/working-with-forms/viewform-icecream-edit.png)

Sie haben eine grundlegende App mit drei Bildschirmen zum Anzeigen und Eingeben von Daten erstellt.  Um sie zu testen, rufen Sie den Katalog-Bildschirm auf, und drücken Sie dann F5 (oder klicken Sie auf die Vorschauschaltfläche (Rechtspfeil) oben rechts am Bildschirmrand). Die rosa Punkt zeigt an, wo der Benutzer bei jedem Schritt auf den Bildschirm klickt oder tippt.

![Testen Sie die Eiscreme-App](./media/working-with-forms/try-icecream.png)

## <a name="create-a-record"></a>Erstellen eines Datensatzes
Der Benutzer interagiert sowohl zum Aktualisieren als auch zum Erstellen von Datensätzen mit dem gleichen **Bearbeitungsformular**. Wenn der Benutzer einen Datensatz erstellen möchte, wechselt die **[NewForm](functions/function-form.md)**-Funktion den Modus des Formulars auf **New** (Neu).

Wenn sich das Formular im Modus **New** befindet, wird der Wert der einzelnen Felder auf die Standardwerte der Datenquelle festgelegt. Der Datensatz für die **[Item](controls/control-form-detail.md)**-Eigenschaft des Formulars wird ignoriert.  

Wenn der Benutzer zum Speichern des neuen Datensatzes bereit ist, wird **[SubmitForm](functions/function-form.md)** ausgeführt. Nachdem das Formular erfolgreich gesendet wurde, wechselt das Formular zurück in den Modus **EditMode**.  

Fügen Sie auf dem ersten Bildschirm eine **neue** Schaltfläche hinzu:

1. Fügen Sie auf dem Katalog-Bildschirm ein **[Schaltflächen](controls/control-button.md)**-Steuerelement hinzu.
2. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft der Schaltfläche auf **New** (Neu) und ihre **[OnSelect](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **NewForm( Form1 ); Navigate( Screen3, None )**
   
    Mit dieser Formel wechselt das **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement auf **Screen3** in den Modus **New** und öffnet den Bildschirm, damit der Benutzer ihn auffüllen kann.

![„Formular anzeigen“ mit hinzugefügter Schaltfläche „Bearbeiten“](./media/working-with-forms/gallery-icecream-new.png)

Wenn sich der Bildschirm „Bearbeiten und Erstellen“ öffnet, ist das Formular leer, und der Benutzer kann Elemente einfügen. Wenn der Benutzer auf die Schaltfläche **Save** klickt, stellt die **[SubmitForm](functions/function-form.md)**-Funktion sicher, dass ein Datensatz erstellt und nicht aktualisiert wird. Wenn der Benutzer auf die Schaltfläche **Cancel** klickt, ändert die **[ResetForm](functions/function-form.md)**-Funktion das Formular in den **Edit**-Modus zurück, und die **[Back](functions/function-navigate.md)**-Funktion öffnet den Bildschirm zum Durchsuchen des Katalogs.

## <a name="delete-a-record"></a>Löschen eines Datensatzes
1. Fügen Sie auf dem **Display**-Bildschirm (Anzeigen) eine Schaltfläche hinzu, und legen Sie deren **[Text](controls/properties-core.md)**-Eigenschaft auf **Delete** (Löschen) fest.
2. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:
   <br>**Remove( 'Ice Cream', Gallery1.Selected ); Back()**
   
    ![„Formular anzeigen“ mit hinzugefügter Schaltfläche „Bearbeiten“](./media/working-with-forms/viewform-icecream-remove.png)

## <a name="handling-errors"></a>Behandeln von Fehlern
In dieser App tritt ein Fehler auf, wenn der Wert eines Felds nicht gültig oder ein erforderliches Feld leer ist, wenn keine Verbindung zum Netzwerk besteht oder wenn andere Probleme auftauchen.  

Wenn **[SubmitForm](functions/function-form.md)** aus irgendeinem Grund einen Fehler auslöst, enthält die **Error**-Eigenschaft des **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelements eine Fehlermeldung für den Benutzer. Anhand dieser Informationen sollte der Benutzer das Problem beheben und die Änderung erneut übermitteln oder das Update abbrechen können.

1. Fügen Sie auf dem Bildschirm „Bearbeiten und Erstellen“ ein **[Label](controls/control-text-box.md)**-Steuerelement hinzu, und platzieren Sie es direkt unter der Schaltfläche **Speichern**. Alle Fehler sind leicht zu entdecken, nachdem der Benutzer die Änderungen durch einen Klick auf dieses Steuerelement gespeichert hat.

2. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft des **[Label](controls/control-text-box.md)**-Steuerelements auf **Form1.Error** fest.

    ![„Formular anzeigen“ mit hinzugefügter Schaltfläche „Bearbeiten“](./media/working-with-forms/edit-icecream-error.png)

Die **[AutoHeight](controls/control-text-box.md)**-Eigenschaft auf diesem Steuerelement ist in einer App, die PowerApps aus Daten generiert, auf *TRUE* festgelegt, damit kein Speicherplatz beansprucht wird, wenn kein Fehler auftritt. Die Eigenschaften **[Height](controls/properties-size-location.md)** und **[Y](controls/properties-size-location.md)** des **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelements werden auch dynamisch angepasst, damit dieses Steuerelement wächst, wenn ein Fehler auftritt. Generieren Sie eine App aus bestehenden Daten, und prüfen Sie diese Eigenschaften, um weitere Informationen zu erhalten. Das Textfeld-Steuerelement für Fehler ist sehr kurz, wenn kein Fehler aufgetreten ist, weswegen Sie möglicherweise die Ansicht **Advanced** (Erweitert) (in der Registerkarte **Ansicht**) öffnen müssen, um dieses Steuerelement auszuwählen.

![App aus dem Datenbearbeitungsformular mit ausgewähltem Fehlertext-Steuerelement](./media/working-with-forms/edit-assets-error1.png)

![App aus dem Datenbearbeitungsformular mit ausgewähltem Formular-Steuerelement](./media/working-with-forms/edit-assets-error2.png)

## <a name="refresh-data"></a>Aktualisieren von Daten
Die Datenquelle wird bei jedem Öffnen der App aktualisiert. Manchmal möchten Benutzer die Datensätze im Katalog aber aktualisieren, ohne die App zu schließen. Fügen Sie dazu eine Schaltfläche **Refresh** (Aktualisieren) ein, damit Benutzer Daten manuell aktualisieren können:

1. Fügen Sie auf dem Bildschirm mit dem **[Katalog](controls/control-gallery.md)**-Steuerelement ein **[Schaltflächen](controls/control-button.md)**-Steuerelement hinzu, und legen Sie dessen **[Text](controls/properties-core.md)**-Eigenschaft auf **Refresh** fest.

2. Legen Sie die Eigenschaft **[OnSelect](controls/properties-core.md)** dieses Steuerelements auf die folgende Formel fest:<br> **Refresh( 'Ice Cream' )**

    ![Aktualisieren der Datenquelle](./media/working-with-forms/browse-icecream-refresh.png)

## <a name="search-and-sort-the-gallery"></a>Durchsuchen und Sortieren des Katalogs
Bisher wurde noch nicht über zwei Steuerelemente oben im Bildschirm zum Durchsuchen der App gesprochen, die PowerApps aus Daten erstellt. Mithilfe dieser Steuerelemente können Benutzer nach mindestens einem Datensatz suchen und die Liste der Datensätze in aufsteigender oder absteigender Reihenfolge sortieren, oder beides.

![Sortieren und Durchsuchen von Steuerelementen auf dem Bildschirm zum Durchsuchen](./media/working-with-forms/afd-browse-search-sort.png)

Wenn der Benutzer auf die Sortierschaltfläche klickt, wird die Sortierreihenfolge des Katalogs umgekehrt. Um dieses Verhalten hervorzurufen, verwenden wir eine *Kontextvariable*, um die Richtung zu verfolgen, in der der Katalog sortiert wird. Wenn der Benutzer diese Schaltfläche auswählt, wird die Variable aktualisiert und die Richtung umgekehrt. Die **[OnSelect](controls/properties-core.md)**-Eigenschaft der Sortierschaltfläche wird auf diese Formel festgelegt: **UpdateContext( {SortDescending1: !SortDescending1} )**

Die **[UpdateContext](functions/function-updatecontext.md)**-Funktion erstellt die **SortDescending1**-Kontextvariable, wenn sie nicht bereits vorhanden ist. Die Funktion liest den Wert der Variablen und legt diesen mithilfe des **!**-Operators auf das logische Gegenteil fest. Wenn der Wert *TRUE* lautet, entspricht die Variable *FALSE*. Wenn der Wert *FALSE* lautet, entspricht die Variable *TRUE*.

Die Formel für die **[Items](controls/properties-core.md)**-Eigenschaft des **[Katalog](controls/control-gallery.md)**-Steuerelements verwendet diese Kontextvariable zusammen mit dem Text im **TextSearchBox1**-Steuerelement:

    Gallery1.Items = Sort( If( IsBlank(TextSearchBox1.Text),
                               Assets,
                               Filter( Assets,
                                       TextSearchBox1.Text in Text(ApproverEmail) ) ),
                            ApproverEmail,
                            If(SortDescending1, Descending, Ascending) )

Lassen Sie uns das noch einmal aufgliedern:

* Äußerlich gibt es die **[Sort](functions/function-sort.md)**-Funktion, die drei Argumente annimmt: eine Tabelle, ein Feld, nach dem sortiert wird, und eine Richtung, nach der ebenfalls sortiert wird.  
  
  * Die Sortierrichtung wird der Kontextvariablen entnommen, die umgeschaltet, wenn der Benutzer das **ImageSortUpDown1**-Steuerelement auswählt. Der Wert *TRUE*/*FALSE* wird in die Konstanten **Descending** (Absteigend) und **Ascending** (Aufsteigend) übersetzt.
  * Das Feld, nach dem sortiert wird, ist an **ApproverEmail** gebunden. Wenn Sie die Felder ändern, die im Katalog angezeigt werden, müssen Sie auch dieses Argument ändern.
* Innerlich gibt es die **[Filter](functions/function-filter-lookup.md)**-Funktion, die eine Tabelle als Argument und einen für jeden Datensatz auszuwertenden Ausdruck annimmt.
  
  * Die Tabelle ist die rohe **Assets**-Datenquelle, den Ausgangspunkt vor dem Filtern oder Sortieren darstellt.
  * Der Ausdruck sucht nach einer Instanz der Zeichenfolge in **TextSearchBox1** innerhalb des **ApproverEmail**-Felds.  Wenn Sie die Felder ändern, die im Katalog angezeigt werden, müssen Sie wie gesagt auch dieses Argument aktualisieren.
  * Wenn **TextSearchBox1** leer ist, sollen alle Datensätze angezeigt werden, und die **[Filter](functions/function-filter-lookup.md)**-Funktion wird umgangen.

Dies ist nur ein mögliches Beispiel. Sie können je nach den Anforderungen der App eigene Formeln für die **[Items](controls/properties-core.md)**-Eigenschaft erstellen, indem Sie die **[Filter](functions/function-filter-lookup.md)**, **[Sort](functions/function-sort.md)**- und andere Funktionen und Operatoren zusammen erstellen.    

## <a name="screen-design"></a>Bildschirmdesign
Bisher noch nicht wurden die weiteren Möglichkeiten zum Verteilen von Steuerelementen auf Bildschirmen besprochen. Denn Ihnen stehen zahlreiche Optionen zur Verfügung, und die beste Wahl hängt von den spezifischen Anforderungen Ihrer App ab.

Da der Platz auf dem Bildschirmen von Mobiltelefonen so beschränkt ist, möchten Sie wahrscheinlich auf unterschiedlichen Bildschirmen durchsuchen, anzeigen und bearbeiten/erstellen. In diesem Thema öffnen die Funktionen **[Navigate](functions/function-navigate.md)** und **[Back](functions/function-navigate.md)** die jeweiligen Bildschirme.  

Auf einem Tablet können Sie auf zwei oder sogar einem Bildschirm durchsuchen, anzeigen und bearbeiten/erstellen. Für Letzteres ist weder die **[Navigate](functions/function-navigate.md)** noch **[Back](functions/function-navigate.md)**-Funktion erforderlich.

Wenn der Benutzer an demselben Bildschirm arbeitet, müssen Sie darauf achten, dass der Benutzer die Auswahl im **[Katalog](controls/control-gallery.md)** nicht ändern kann und keine Änderungen im **[Formular bearbeiten](controls/control-form-detail.md)**-Steuerelement verloren gehen.  Um zu verhindern, dass den Benutzer einen anderen Datensatz auswählen, wenn Änderungen an einem anderen Datensatz noch gespeichert wurden, legen Sie die **[Disabled](controls/properties-core.md)**-Eigenschaft (Deaktiviert) des Katalogs auf diese Formel fest:<br>
**EditForm.Unsaved**

