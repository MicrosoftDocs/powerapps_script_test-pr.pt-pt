---
title: Anpassen einer Karte | Microsoft-Dokumentation
description: Ändern des Standardsteuerelements, das in PowerApps auf einer Karte in einem Details- oder Edit-Formular angezeigt wird
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 31c0810b9da5a52bcd5cc3b28b6def858541e15b
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42841784"
---
# <a name="customize-a-card-in-powerapps"></a>Anpassen einer Karte in PowerApps
Führen Sie eine grundlegende Anpassung (ohne Entsperren einer Karte) durch, indem Sie beispielsweise das Steuerelement ändern. Erweiterte Anpassung (mit Aufheben der Sperre einer Karte), indem Sie z.B. ein Steuerelement hinzufügen, das für diese Karte standardmäßig nicht verfügbar ist.

Eine Übersicht finden Sie unter [Grundlegendes zu Datenkarten](working-with-cards.md).

## <a name="prerequisites"></a>Voraussetzungen

* Grundlegende Informationen zum [Hinzufügen und Konfigurieren von Steuerelementen](add-configure-controls.md).
* Sie können diesen Artikel zur allgemeinen Information verwenden oder die in den folgenden Artikeln beschriebenen Vorgänge exakt ausführen:

  1. [Generate an app (Generieren einer App)](data-platform-create-app.md)
  2. [Customize its gallery (Anpassen des Katalogs)](customize-layout-sharepoint.md)
  3. [Customize its forms (Anpassen der Formulare)](customize-forms-sharepoint.md)

## <a name="customize-a-locked-card"></a>Anpassen einer gesperrten Karte
Ersetzen Sie in diesem Verfahren ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement durch ein **[Schieberegler](controls/control-slider.md)**-Steuerelement, ohne die Karte zu entsperren.

1. Melden Sie sich bei [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

    ![PowerApps-Startseite](./media/customize-card/sign-in.png)

1. Öffnen Sie die App, die Sie generiert und angepasst haben, klicken Sie auf **EditForm1**, und öffnen Sie dann den Bereich **Daten**, indem Sie im Bereich rechts auf **Konten** klicken.

1. Klicken Sie in der Liste der Felder auf den Pfeil nach unten, damit für die **Anzahl der Mitarbeiter** eine Liste von Optionen angezeigt wird, und klicken Sie anschließend auf **Schieberegler bearbeiten**.

    ![Dropdownliste der Optionen für eine Zahlenkarte](./media/customize-card/card-selector.png)

    Der Bildschirm spiegelt die vorgenommene Änderung wider.

    ![EditForm1 mit Schieberegler-Steuerelement](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>Entsperren und Anpassen einer Karte
In diesem Verfahren entsperren Sie eine Karte und ersetzen anschließend ein **[Schalter](controls/control-toggle.md)** -Steuerelement durch ein **[Kontrollkästchen](controls/control-check-box.md)** -Steuerelement.

1. Rufen Sie das Feld **Send Marketing Materials** (Marketingmaterialien senden) in **EditForm1** ab.

    ![Anzeigen des Felds „Send Marketing Materials“ (Marketingmaterialien senden)](./media/customize-card/show-field.png)

2. Wenn Sie diese Karte ausgewählt haben, klippen oder tippen Sie erst im oberen Bereich recht auf **Erweitert** und dann auf das Schlosssymbol, um die Karte zu entsperren.

    ![Anzeigen des Felds „Send Marketing Materials“ (Marketingmaterialien senden)](./media/customize-card/unlock-card.png)

1. Löschen Sie in der Karte das **Schalter**-Steuerelement, fügen Sie ein **Kontrollkästchen**-Steuerelement hinzu, und nennen Sie das neue Steuerelement z.B. **chkMktg**.

    ![„Schalter“ durch „Kontrollkästchen“ ersetzen](./media/customize-card/add-checkbox.png)

1. Wählen Sie die Karte aus, die Sie gerade aktualisiert haben.

    ![Karte auswählen](./media/customize-card/select-card.png)

1. Überprüfen Sie auf der rechten Seite, ob die Registerkarte **Erweitert** immer noch angezeigt wird, und klicken oder tippen Sie dann auf **Weitere Optionen**.

    ![Schaltfläche „Weitere Optionen“](./media/customize-card/more-options.png)

1. Ändern Sie den Wert der **Update**-Eigenschaft der Karte in den folgenden Ausdruck:
<br>`chkMktg.Value`

1. Ändern Sie den Wert der **Y**-Eigenschaft der Fehlermeldung zu dieser Karte in den folgenden Ausdruck:<br>
`chkMktg.Y + chkMktg.Height`

    ![Fehlermeldung für die neue Karte auswählen](./media/customize-card/select-error.png)

1. Ändern Sie den Wert der **Text**-Eigenschaft Ihres neuen **chkMktg**-Steuerelements in **Ja**.

    Dann werden auf dem Bildschirm Ihre Änderungen angezeigt und die Fehler behoben.

    ![Letzte Anzeige mit behobenen Fehlern](./media/customize-card/final-screen.png)

## <a name="next-steps"></a>Nächste Schritte
Da Sie jetzt einen grundlegenden Überblick darüber haben, wie Sie eine App generieren und einen Katalog, ein Formular und eine Karte anpassen können, sollten Sie Ihre [App von Grund auf neu erstellen können](data-platform-create-app-scratch.md).
