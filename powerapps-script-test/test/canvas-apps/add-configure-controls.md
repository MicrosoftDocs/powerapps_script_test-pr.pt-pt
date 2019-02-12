---
title: Hinzufügen und Konfigurieren eines Canvas-App-Steuerelements | Microsoft-Dokumentation
description: Hier erhalten Sie schrittweise Anweisungen, anhand derer Sie Canvas-App-Steuerelemente direkt, über die Symbolleiste, auf der Registerkarte „Eigenschaften“ oder in der Bearbeitungsleiste hinzufügen und konfigurieren können.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 07/10/2017
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 03f768124b2b7260995fe89120091e85e4cdaa0d
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42826493"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>Hinzufügen und Konfigurieren eines Canvas-App-Steuerelements in PowerApps

Fügen Sie Ihrer Canvas-App vielfältige Benutzeroberflächenelemente hinzu, und konfigurieren Sie Aspekte ihrer Darstellung und ihres Verhaltens direkt, über die Symbolleiste, auf der Registerkarte **Eigenschaften** oder in der Bearbeitungsleiste. Diese Elemente der Benutzeroberfläche werden als Steuerelemente bezeichnet, während die von Ihnen konfigurierten Aspekte als Eigenschaften bezeichnet werden.

## <a name="prerequisites"></a>Voraussetzungen

1. [Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.

2. Klicken oder tippen Sie in PowerApps Studio im Menü **Datei** auf **Neu** (nahe dem linken Rand).

    ![Option „Neu“ im Menü „Datei“](./media/add-configure-controls/file-new.png)

3. Klicken oder tippen Sie in der Kachel **Leere App** auf **Telefonlayout**.

    ![App von Grund auf neu erstellen](./media/add-configure-controls/blank-app.png)

4. Wenn Sie aufgefordert werden, die Einführung anzuschauen, klicken oder tippen Sie auf **Next** um sich mit wichtigen Bereichen der PowerApps Schnittstelle vertraut zu machen (oder klicken oder tippen Sie auf **Skip**).

    ![Begrüßungsbildschirm der Einführungsdemo](./media/add-configure-controls/quick-tour.png)

    Sie können sich die Einführung jederzeit später anschauen. Klicken oder tippen Sie hierzu auf das Fragezeichen-Symbol in der Nähe der oberen rechten Ecke, und klicken oder tippen Sie anschließend auf **Take the intro tour**.

## <a name="add-a-control"></a>Hinzufügen eines Steuerelements
Sie können beliebige Steuerelemente in einer Vielzahl von Kategorien hinzufügen, indem Sie auf die Registerkarte **Einfügen** der Symbolleiste klicken oder tippen, anschließend auf eine Kategorie und dann auf das gewünschte Steuerelement klicken oder tippen. Betrachten Sie in diesem Abschnitt die Steuerelemente in den einzelnen Kategorien, um sich mit den Typen von Steuerelementen vertraut zu machen, die Sie hinzufügen können und zu erfahren, wo Sie die einzelnen Typen ggf. zu finden sind.

Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf eine dieser Kategorien, und klicken oder tippen Sie auf das Steuerelement, das Sie hinzufügen möchten:

**Text**: Bezeichnung, Texteingabe, HTML-Text, Stifteingabe<br>
**Steuerelemente**: Schaltfläche, Dropdownliste, Datumsauswahl, Listenfeld, Kontrollkästchen, Optionsfeld, Ein-/Ausschalter, Schieberegler, Bewertung, Timer<br>
**Katalog**: Vertikal, Horizontal, Flexible Höhe, Leerzeichen vertikal, Leerzeichen horizontal, Leerzeichen flexible Höhe<br>
**Datentabelle**<br>
**Formulare**: Bearbeiten, Anzeigen, Entitätsformular<br>
**Medien**: Bild, Kamera, Barcode, Video, Audio, Mikrofon, Bild hinzufügen<br>
**Diagramme**: Säulendiagramm, Liniendiagramm, Kreisdiagramm<br>
**Symbole**

> [!TIP]
> Wenn Sie mehr Platz für Steuerelemente benötigen, können Sie einen [weiteren Bildschirm hinzufügen](add-screen-context-variables.md).

## <a name="configure-a-control-directly"></a>Direktes Konfigurieren eines Steuerelements
In diesem Verfahren fügen Sie ein **Label**-Steuerelement (Bezeichnung) hinzu und konfigurieren es, die gleichen Grundsätze gelten jedoch großenteils auch für andere Steuerelemente.

1. Klicken oder tippen Sie auf die Registerkarte **Einfügen** und anschließend auf **Bezeichnung**.

    ![Registerkarte „Einfügen“](./media/add-configure-controls/insert-text-box.png)

    Wenn Sie ein Steuerelement hinzufügen, wird dieses standardmäßig ausgewählt. Sie können auch ein vorhandenes Steuerelement auswählen, indem Sie darauf klicken oder tippen. Wenn ein Steuerelement ausgewählt ist, wird es von einem Auswahlfeld umschlossen, und andere Bereiche der Benutzeroberfläche werden geändert, sodass Sie das aktivierte Steuerelement konfigurieren können. Eine ausgewählte **Bezeichnung** ähnelt beispielsweise dieser Abbildung.

    ![Eine ausgewählte Bezeichnung](./media/add-configure-controls/selected-text-box.png)

    > [!IMPORTANT]
   > Wenn ein Steuerelement ausgewählt ist und Sie ein anderes Steuerelement oder einen leeren Bereich des Bildschirms auswählen, wird die Auswahl des ersten Elements aufgehoben.
2. Verringern Sie die Breite des **Label**-Steuerelements (Bezeichnung), indem Sie einen Ziehpunkt am rechten Rand des Auswahlfeldes nach links ziehen. (Der mittlere Ziehpunkt wird nur angezeigt, wenn Sie die Anzeige vergrößern.)

    ![Bezeichnung mit veränderter Größe](./media/add-configure-controls/shorter-text-box.png)

     Sie können die Größe eines Steuerelements auch ändern, indem Sie seine **[Height](controls/properties-size-location.md)**-Eigenschaft, **[Width](controls/properties-size-location.md)**-Eigenschaft oder beide Eigenschaften ändern, wie in diesem Artikel an späterer Stelle beschrieben.

3. Verschieben Sie das **Label**-Steuerelement (Bezeichnung), indem Sie das Auswahlfeld selbst ziehen (oder indem Sie **[X](controls/properties-size-location.md)**, **[Y](controls/properties-size-location.md)** oder beide Eigenschaften ändern, wie in diesem Artikel an späterer Stelle beschrieben).

4. Klicken Sie dreimal auf den im **Label**-Steuerelement (Bezeichnung) angezeigten Text, und geben Sie **Hello, world** ein.

    ![Bezeichnung mit benutzerdefiniertem Text](./media/add-configure-controls/change-text-directly.png)

     Sie können diesen Text auch ändern, indem Sie die **[Text](controls/properties-core.md)**-Eigenschaft dieses Steuerelements festlegen, wie in diesem Artikel an späterer Stelle beschrieben.

## <a name="configure-a-control-from-the-toolbar"></a>Konfigurieren eines Steuerelements über die Symbolleiste
Durch Konfigurieren eines Steuerelements über die Symbolleiste können Sie eine größere Anzahl von Optionen als beim direkten Konfigurieren eines Steuerelements angeben.

1. Klicken oder tippen Sie bei ausgewähltem **Label**-Steuerelement (Bezeichnung) auf die Registerkarte **Start** auf der Symbolleiste.

    ![Registerkarte „Start“](./media/add-configure-controls/home-tab.png)

2. Klicken oder tippen Sie auf **Ausfüllen**, und klicken und tippen Sie anschließend auf eine Farbe wie Aquamarin.

    ![Option „Ausfüllen“](./media/add-configure-controls/fill-option.png)

    Das **Label** -Steuerelement (Bezeichnung) spiegelt Ihre Auswahl wider.

    ![Bezeichnung mit aquamarinblauer Füllung](./media/add-configure-controls/change-fill.png)

3. Ändern Sie die Schriftfamilie und den Schriftgrad des Texts (z.B. in 18 pt. Georgia).

    ![Schriftart-Steuerelemente](./media/add-configure-controls/font-size.png)

    Das **Label** -Steuerelement (Bezeichnung) spiegelt Ihre Auswahl wider.

    ![18 pt. Georgia](./media/add-configure-controls/change-font.png)

4. Klicken oder tippen Sie auf die Registerkarte **Bezeichnung**, und klicken Sie anschließend auf **VertikalAusrichten** und auf **Oben**.

    ![Registerkarte „Textfeld“](./media/add-configure-controls/text-box-tab.png)

    Das **Label** -Steuerelement (Bezeichnung) spiegelt Ihre Auswahl wider.

    ![Bezeichnung, deren Text am oberen Rand des Feldes ausgerichtet ist](./media/add-configure-controls/change-align.png)

## <a name="configure-a-control-from-the-properties-tab"></a>Konfigurieren eines Steuerelements auf der Registerkarte „Eigenschaften“
Mithilfe der Registerkarte **Eigenschaften** können Sie ein Steuerelement konfigurieren, ohne eine Formel zu schreiben. In diesem Verfahren fügen Sie ein weiteres **Label**-Steuerelement (Bezeichnung) hinzu und konfigurieren es. Die gleichen Grundsätze gelten jedoch großenteils auch für andere Steuerelemente.

1. Fügen Sie ein weiteres **Label**-Steuerelement (Bezeichnung) entsprechend der obigen Beschreibung in diesem Thema hinzu.

2. Klicken oder tippen Sie bei ausgewähltem neuen Steuerelement im rechten Bereich auf die Registerkarte **Eigenschaften**.

    ![Bereich „Eigenschaften“](./media/add-configure-controls/properties-panel.png)

3. Geben Sie im Feld **Text** **Properties tab** ein.

    ![Bezeichnungstext im Bereich „Eigenschaften“](./media/add-configure-controls/properties-panel-text.png)

    Das **Label**-Steuerelement (Bezeichnung) weist den eingegebenen Text auf.

    ![Text im Zeichenbereich in „Eigenschaften“](./media/add-configure-controls/properties-panel-canvas-text.png)

4. Klicken oder tippen Sie auf das Symbol **Füllen** im Bereich **Eigenschaften**, und klicken oder tippen Sie anschließend auf eine Farbe.

    ![Farbe für Text im Bereich „Eigenschaften“](./media/add-configure-controls/properties-panel-color.png)

    Das **Label** -Steuerelement (Bezeichnung) spiegelt Ihre Auswahl wider.

    ![Farbe im Zeichenbereich in „Eigenschaften“](./media/add-configure-controls/properties-panel-canvas-color.png)

5. Klicken oder tippen Sie im Bereich „Eigenschaften“ auf die **Color**-Eigenschaft.

    ![Eigenschaft im Bereich „Eigenschaften“](./media/add-configure-controls/properties-panel-property.png)

    Der Wert der **Color**-Eigenschaft wird in der Bearbeitungsleiste hervorgehoben.

    ![Ausdruck der Eigenschaft im Bereich „Eigenschaften“](./media/add-configure-controls/properties-panel-property-expression.png)

6. Löschen Sie das zweite **Label**-Steuerelement (Bezeichnung), indem Sie darauf klicken oder tippen und anschließend „Löschen“ auswählen.

## <a name="configure-a-control-in-the-formula-bar"></a>Konfigurieren eines Steuerelements in der Bearbeitungsleiste
Mithilfe der Bearbeitungsleiste können Sie Eigenschaften festlegen, die nicht direkt, auf der Registerkarte **Eigenschaften** oder über die Symbolleiste festgelegt werden können. Sie können beispielsweise eine QuickInfo festlegen, die eingeblendet wird, wenn ein Benutzer auf das Steuerelement zeigt, jedoch nicht darauf klickt oder tippt. Sie können auch komplexe Formeln angeben, durch die der Funktionsumfang der App verbessert wird.

Wenn Sie bisher in diesem Artikel eine Änderung vorgenommen haben, wurde der Wert einer [Eigenschaft](reference-properties.md) des konfigurierten Steuerelements aktualisiert.

* Beim Ändern der Größe des Steuerelements haben Sie seine **[Width](controls/properties-size-location.md)**-Eigenschaft geändert.
* Beim Verschieben des Steuerelements haben Sie seine **[X](controls/properties-size-location.md)**-Eigenschaft und seine **[Y](controls/properties-size-location.md)**-Eigenschaft geändert.
* Beim Ändern des vom Steuerelement angezeigten Texts haben Sie seine **[Text](controls/properties-core.md)**-Eigenschaft geändert.

Anstatt ein Steuerelement direkt, auf der Registerkarte **Eigenschaften** oder über die Symbolleiste zu konfigurieren, können Sie auch den Wert einer Eigenschaft aktualisieren, indem Sie diese in der Eigenschaftenliste auswählen und anschließend einen Wert in der Bearbeitungsleiste angeben. Mit dieser Vorgehensweise können Sie Eigenschaften nach ihrer alphabetischen Reihenfolge durchsuchen, und Sie können mehr Werttypen angeben.

1. Klicken oder tippen Sie bei ausgewähltem verbleibenden **Label**-Steuerelement (Bezeichnung) in der Eigenschaftenliste auf **[Text](controls/properties-core.md)**, und geben Sie anschließend in der Bearbeitungsleiste **"My Company Name"** (einschließlich der Anführungszeichen) ein.

    ![Zeichenfolgenliteral in einer Bezeichnung](./media/add-configure-controls/text-literal.png)

    Wenn Sie eine Textzeichenfolge in Anführungszeichen einschließen, geben Sie an, dass sie genauso behandelt werden soll, wie Sie sie eingegeben haben. Stattdessen können Sie den Wert einer Eigenschaft auch in einer Formel einsetzen.

2. Klicken oder tippen Sie bei ausgewähltem **Label**-Steuerelement (Bezeichnung) in der Eigenschaftenliste auf **[Text](controls/properties-core.md)**, und geben Sie anschließend in der Bearbeitungsleiste **Today()** (ohne Anführungszeichen) ein.

    Das Steuerelement zeigt das aktuelle Datum an.

    ![Today-Funktion](./media/add-configure-controls/today-function.png)

    > [!TIP]
   > Sie haben verschiedene Möglichkeiten, [Datums- und Uhrzeitangaben zu formatieren](show-text-dates-times.md) und können zudem Berechnungen mit derartigen Daten ausführen.

## <a name="configure-two-controls-to-interact-with-each-other"></a>Konfigurieren von zwei miteinander interagierenden Steuerelementen
In diesem Verfahren fügen Sie ein Kontrollkästchen hinzu und konfigurieren dann die bereits vorhandene Bezeichnung so, dass sie nur angezeigt wird, wenn das Kontrollkästchen aktiviert ist.

1. Klicken oder tippen Sie auf die Registerkarte **Einfügen**.

    ![Registerkarte „Einfügen“](./media/add-configure-controls/insert-tab.png)

2. Klicken oder tippen Sie auf **Steuerelemente**, und klicken oder tippen Sie auf **Kontrollkästchen**.

    ![Kontrollkästchen einfügen](./media/add-configure-controls/insert-check-box.png)

3. Verschieben Sie das **Kontrollkästchen**-Steuerelement, sodass es sich unterhalb des **Label**-Steuerelements (Bezeichnung) befindet, und legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft des **Kontrollkästchen**-Steuerelements so fest, dass **Text anzeigen** angezeigt wird.

    ![Konfigurieren des Kontrollkästchens](./media/add-configure-controls/configure-check-box.png)

4. Lassen Sie das Steuerelement **Kontrollkästchen** ausgewählt, klicken oder tippen Sie auf seinen Namen direkt über der Registerkarte **Eigenschaften**, und geben Sie anschließend **MyCheckbox** ein.

    ![Umbenennen des Kontrollkästchens](./media/add-configure-controls/properties-panel-rename.png)

5. Klicken oder tippen Sie auf das **Label**-Steuerelement (Bezeichnung), um es auszuwählen.

6. Klicken oder tippen Sie auf der Registerkarte **Eigenschaften** auf die **Visible**-Eigenschaft (Sichtbar).

    ![Option „Sichtbar“](./media/add-configure-controls/properties-panel-visible-property.png)

7. Löschen Sie in der Bearbeitungsleiste den Text **true**, und geben bzw. fügen Sie dann diese Formel ein:

    **If(MyCheckbox.Value = true, true, false)**

    Diese **[If-Funktion](functions/function-if.md)** legt fest, dass die Bezeichnung nur dann angezeigt werden soll, wenn das Kontrollkästchen aktiviert ist. Da das Kontrollkästchen deaktiviert ist, wird das **Label**-Steuerelement (Bezeichnung) ausgeblendet (mit Ausnahme des Auswahlfeldes).

    ![Formel für „Sichtbar“](./media/add-configure-controls/visible-formula.png)

8. Klicken oder tippen Sie auf das **Kontrollkästchen**-Steuerelement, um diesem das Auswahlfeld hinzuzufügen, und klicken und tippen Sie erneut darauf, um ein Häkchen hinzuzufügen.

    Die **Bezeichnung** wird erneut angezeigt:

    ![Die Bezeichnung wird bei aktiviertem Kontrollkästchen angezeigt](./media/add-configure-controls/show-text.png)

9. Deaktivieren Sie das **Kontrollkästchen**-Steuerelement, um das **Label**-Steuerelement (Bezeichnung) auszublenden.

    ![Die Bezeichnung wird ausgeblendet, wenn das Kontrollkästchen deaktiviert ist](./media/add-configure-controls/hide-text.png)

Dies ist ein einfaches Beispiel; Sie können jedoch das Verhalten und das Erscheinungsbild Ihrer App konfigurieren, indem Sie eine oder mehrere einfache oder komplexe [Formeln](formula-reference.md) erstellen.

## <a name="rename-a-screen-or-a-control"></a>Umbenennen eines Bildschirms oder Steuerelements
Durch das Umbenennen eines Bildschirms oder eines Steuerelements können Sie Formeln erstellen, die leichter lesbar und einfacher zu verwalten sind.

1. Klicken oder tippen Sie auf den Bildschirm oder das Steuerelement, der bzw. das umbenannt werden soll.

2. Klicken oder tippen Sie im rechten Bereich auf den Namen des Steuerelements (direkt über der Registerkarte **Eigenschaften**), und geben Sie den gewünschten Namen ein.

    ![Umbenennen des Kontrollkästchens](./media/add-configure-controls/properties-panel-rename.png)

## <a name="find-and-select-a-screen-or-a-control"></a>Suchen und Auswählen eines Bildschirms oder Steuerelements
Sie können einen Bildschirm oder ein Steuerelement finden und auswählen, auch wenn dieser bzw. dieses ausgeblendet ist oder sich mit einem anderen Steuerelement überschneidet, indem Sie ihn bzw. es im linken Bereich suchen. In diesem Bereich wird entweder eine Miniaturansicht der einzelnen Bildschirme in der App oder eine hierarchische Ansicht aller Bildschirme und der darin enthaltenen Steuerelemente angezeigt.

* **Zum Wechseln zwischen den Miniaturansichten und der hierarchischen Ansicht** klicken oder tippen Sie rechts oben im Bereich auf ein Symbol.

    ![Umschalten der Ansichten](./media/add-configure-controls/toggle-view.png)

* **Zum Suchen eines Steuerelements** geben Sie ein oder mehrere Zeichen ein, um die Steuerelementnamen zu markieren, die den eingegebenen Text enthalten.

    Wenn Sie auf ein Suchergebnis klicken oder tippen, wählen Sie dieses Steuerelement in der App aus.

    ![Suchen in der Strukturansicht](./media/add-configure-controls/search.png)

* **Um einen Bildschirm nach oben oder unten zu verschieben, zu duplizieren, zu löschen oder umzubenennen** , klicken Sie mit der rechten Maustaste darauf (oder klicken oder tippen Sie auf die Auslassungspunkte daneben), und klicken oder tippen Sie dann auf die gewünschte Option.

    ![Kontextmenü in der Strukturansicht](./media/add-configure-controls/context.png)

* **Um einen Bildschirm zu kopieren/einzufügen, zu löschen oder umzubenennen** , klicken Sie mit der rechten Maustaste darauf (oder klicken oder tippen Sie auf die Auslassungspunkte daneben), und klicken oder tippen Sie dann auf die gewünschte Option.
