---
title: Grundlegendes zu Datenkarten | Microsoft-Dokumentation
description: Verwenden Sie in PowerApps Formularkarten zum Sammeln und Anzeigen von Informationen aus einer Datenquelle.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: db0e42a45af217e9e5703242c2a5a867a52b687b
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42850528"
---
# <a name="understand-data-cards-in-powerapps"></a>Grundlegendes zu Datenkarten in PowerApps

**[Card](controls/control-card.md)**-Steuerelemente sind die Bausteine der Steuerelemente **[Formular bearbeiten](controls/control-form-detail.md)** und **[Formular anzeigen](controls/control-form-detail.md)** in Canvas-Apps. Das Formular stellt den gesamten Datensatz dar, und jede Karte stellt ein einzelnes Feld dieses Datensatzes dar.

Am einfachsten können Sie mit Karten im rechten Bereich interagieren, nachdem Sie ein Formularsteuerelement im Designarbeitsbereich ausgewählt haben. In diesem Bereich können Sie auswählen, welche Felder auf welche Weise in welcher Reihenfolge angezeigt werden sollen. In diesem Beispiel wird ein **Bearbeitungsformular**-Steuerelement in einer App veranschaulicht, die anhand der SharePoint-Liste **Assets** erstellt wurde.

![Erster Bildschirm](./media/working-with-cards/first-screen.png)

Weitere Informationen zu den ersten Schritten mit Karten finden Sie unter [Add a form (Formular hinzufügen)](add-form.md) und [Understand data forms (Grundlegendes zu Datenformularen)](working-with-forms.md). Im weiteren Verlauf dieses Themas wird ausführlicher erläutert, wie Karten funktionieren, und wie Sie sie anpassen oder sogar Ihre eigenen Karten erstellen können.

## <a name="predefined-cards"></a>Vordefinierte Karten

PowerApps bietet einen vordefinierten Satz von Smartcards, die für Zeichenfolgen, Zahlen und andere Datentypen geeignet sind. Im rechten Bereich finden Sie die verfügbaren Varianten; hier können Sie auch die für ein Feld verwendete Karte anpassen:

![](./media/working-with-cards/selected-card.png)

In diesem Beispiel wird eine Karte für einzeiligen Text verwendet, aber der Text der URL ist länger als in einer einzelnen Zeile angezeigt werden kann. Ändern Sie diese Karte also in eine Karte für mehrzeiligen Text, damit Ihr Benutzer mehr Spielraum zum Bearbeiten hat:

![](./media/working-with-cards/multiline-edit.png)

Verschiedene Felder dieser Datenquelle werden nicht angezeigt, Sie können jedoch die einzelnen Felder ein- oder ausblenden, indem Sie das entsprechende Kontrollkästchen aktivieren. In diesem Beispiel wird veranschaulicht, wie das Feld **SecurityCode** angezeigt wird.

![](./media/working-with-cards/add-security-code.png)

## <a name="customize-a-card"></a>Eine Karte anpassen
Karten enthalten andere Steuerelemente. Der Benutzer gibt in einem **Bearbeitungsformular**-Steuerelement Daten in einem standardmäßigen **[Texteingabe](controls/control-text-input.md)**-Steuerelement ein, das Sie von der Registerkarte **Einfügen** hinzufügen.  

Arbeiten wir schrittweise ein Beispiel dafür durch, wie Sie das Erscheinungsbild einer Karte ändern können, indem Sie ihre Steuerelemente bearbeiten.

1. Kehren Sie zunächst zu der Karte zurück, die Sie als letztes hinzugefügt haben, und machen Sie das Feld **SecurityCode** (Sicherheitscode) ausfindig. Wählen Sie diese Karte aus, indem Sie einmal darauf klicken oder tippen:
   
    ![](./media/working-with-cards/select-security-code.png)
2. Klicken oder tippen Sie auf das **[Texteingabe](controls/control-text-input.md)**-Steuerelement auf der Karte, um es auszuwählen.
   
    ![](./media/working-with-cards/select-text-input.png)
3. Verschieben Sie das Steuerelement auf der Karte durch Ziehen des Auswahlfelds, und ändern Sie die Größe des Steuerelements mithilfe der Ziehpunkte am Rand des Auswahlfelds:
   
    ![](./media/working-with-cards/customize-text-input.png)  

Sie können die Größe des Steuerelements in der Karte anpassen, es verschieben und weitere Änderungen vornehmen, aber Sie können es nicht löschen, ohne es zunächst entsperrt zu haben.

## <a name="unlock-a-card"></a>Entsperren einer Karte
Karten sind selbst auch Steuerelemente, die über Eigenschaften und Formeln verfügen, genauso wie jedes andere Steuerelement – auch wenn sie selbst wiederum Steuerelemente enthalten. Wenn Sie ein Feld in einem Formular anzeigen möchten, erstellt der rechte Bereich automatisch die Karte für Sie und generiert die benötigten Formeln.  Diese Formeln finden sich auf der Registerkarte **Erweitert** im rechten Bereich:

![](./media/working-with-cards/advanced-locked.png)

Sie sehen umgehend eine der wichtigsten Eigenschaften der Karte: die **[DataField](controls/control-card.md)**-Eigenschaft (Datenfeld). Diese Eigenschaft gibt an, welches Feld der Datenquelle dem Benutzer angezeigt wird und was er auf dieser Karte bearbeiten kann.  

Auf der Registerkarte **Erweitert** gibt das Banner am oberen Rand an, dass die Eigenschaften dieser Karte gesperrt sind. Außerdem wird neben den Eigenschaften **[DataField](controls/control-card.md)**, **[DisplayName](controls/control-card.md)** und **[Required](controls/control-card.md)** ein Schlosssymbol angezeigt. Diese Formeln wurden im rechten Bereich erstellt, und das Schloss verhindert das versehentliche Ändern dieser Eigenschaften.

![](./media/working-with-cards/lock-icons.png)

Klicken oder tippen Sie auf das Banner oben, um die Smartcard zu entsperren, damit Sie diese Eigenschaften ändern können:

![](./media/working-with-cards/unlocked-card.png)

Ändern Sie **[DisplayName](controls/control-card.md)**, um ein Leerzeichen zwischen **Asset** und **ID** einzufügen. Durch diese Änderung ändern Sie das, was für Sie generiert wurde.  Im rechten Bereich hat diese Karte eine andere Bezeichnung:

![](./media/working-with-cards/change-display-name.png)

Jetzt können Sie diese Karte steuern und noch weiter an Ihre Bedürfnisse anpassen. Allerdings haben Sie nicht mehr wie vorher die Möglichkeit, die Darstellung der Karte zu ändern (z.B. von einzeiligem in mehrzeiligen Text). Sie haben die vordefinierten Karte in eine „benutzerdefinierte Karte“ umgewandelt, die Sie nun steuern können.  

> [!IMPORTANT]
> Wenn Sie eine Karte entsperrt haben, können Sie sie nicht wieder sperren. Entfernen Sie die Karte, und fügen Sie sie nochmals im rechten Bereich ein, um sie erneut zu sperren.

Sie haben vielfältige Möglichkeiten, um das Erscheinungsbild und das Verhalten einer entsperrten Karte zu ändern. Sie können in der Karte z.B. Steuerelemente hinzufügen oder löschen. Sie können beispielsweise über das Menü **Symbole** auf der Registerkarte **Einfügen** eine Sternform hinzufügen.

![](./media/working-with-cards/add-star.png)

Der Stern ist nun Bestandteil der Karte und verbleibt auf dieser, auch wenn Sie z.B. die Karten innerhalb des Formulars neu anordnen.

Ein weiteres Beispiel: Entsperren Sie die Karte **ImageURL**, und fügen Sie ihr von der Registerkarte **Einfügen** ein **Bild**-Steuerelement hinzu:

![](./media/working-with-cards/add-image.png)

Legen Sie auf der Bearbeitungsleiste die **Image**-Eigenschaft dieses Steuerelements auf *TextBox*.**Text** fest, wobei *TextBox* der Name des **Texteingabe**-Steuerelements ist, das die URL enthält:

> [!TIP]
> Drücken Sie die ALT-TASTE, um den Namen der einzelnen Steuerelemente anzuzeigen.

![](./media/working-with-cards/show-image.png)

Jetzt sehen Sie die Bilder und können deren URLs bearbeiten. Beachten Sie, dass Sie auch **Parent.Default** als **Image**-Eigenschaft hätten verwenden können, bei einer Änderung der URL durch den Benutzer würde dann jedoch keine Aktualisierung stattfinden.

Den gleichen Vorgang können Sie auch auf dem zweiten Bildschirm der App ausführen, wo Sie ein **Anzeigeformular**-Steuerelement verwenden, um die Details eines Datensatzes anzuzeigen. In diesem Fall empfiehlt es sich, die Bezeichnung auszublenden (legen Sie die **Visible**-Eigenschaft der Bezeichnung und nicht der Karte auf **FALSE** fest), da der Benutzer die URL auf diesem Bildschirm nicht bearbeitet:

![](./media/working-with-cards/show-image-display.png)

## <a name="interact-with-a-form"></a>Interagieren mit einem Formular
Nach dem Entsperren einer Karte können Sie ändern, wie sie mit dem Formular interagiert, in dem sie enthalten ist.

Im Folgenden finden Sie einige Richtlinien für die Funktionsweise von Steuerelementen mit ihrer Karte und mit dem Formular. Dies sind nur Richtlinien. Genauso wie mit jedem anderen Steuerelement in PowerApps können Sie Formel erstellen, die auf jedes beliebige Steuerelement in PowerApps verweisen – und dies gilt auch für Karten und Steuerelementen auf Karten. Seien Sie kreativ: Erstellen Sie eine Anwendung auf verschiedene Arten.  

### <a name="datafield-property"></a>DataField-Eigenschaft
Die wichtigste Eigenschaft auf der Karte ist die **[DataField](controls/control-card.md)**-Eigenschaft.  Diese Eigenschaft steuert die Validierung, die Aktualisierung von Feldern und andere Aspekte der Karte.

### <a name="information-flowing-in"></a>Informationsfluss (eingehend)
Als Container stellt das Formular **ThisItem** für alle Karten, die es enthält, zur Verfügung. Dieser Datensatz enthält alle Felder für den aktuellen, relevanten Datensatz.  

Die **[Default](controls/properties-core.md)**-Eigenschaft jeder Karte sollte auf **ThisItem**.*FieldName* festgelegt werden.  Unter bestimmten Umständen möchten Sie diesen Wert vor der Zuweisung umwandeln. Z.B. möchten Sie möglicherweise eine Zeichenfolge formatieren oder einen Wert in eine andere Sprache übersetzen.

Jedes Steuerelement der Karte sollte auf **Parent.Default** verweisen, um den Wert des Feld abrufen zu können. Diese Strategie bietet ein Maß an Datenkapselung für die Karte, damit sich die **[Default](controls/properties-core.md)**-Eigenschaft der Karte ändern kann, ohne die interne Formeln der Karte zu ändern.

Standardmäßig werden die Eigenschaften **DefaultValue** und **[Required](controls/control-card.md)** aus den Metadaten der Datenquelle genommen, auf der Grundlage der **[DataField](controls/control-card.md)**-Eigenschaft. Sie können diese Formeln mit Ihrer eigenen Logik überschreiben und die Metadaten der Datenquelle mithilfe der **[DataSourceInfo](functions/function-datasourceinfo.md)**-Funktion integrieren.

### <a name="information-flowing-out"></a>Informationsfluss (ausgehend)
Nachdem der Benutzer einen Datensatz mithilfe der Steuerelemente auf den Karten geändert hat, speichert die **[SubmitForm](functions/function-form.md)**-Funktion die Änderungen der Datenquelle. Wenn diese Funktion ausgeführt wird, liest das Formularsteuerelement die Werte der **[DataField](controls/control-card.md)**-Eigenschaft jeder Karte, um herauszufinden, welches Feld geändert werden soll.  

Des Formularsteuerelements liest auch den Wert der **[Update](controls/control-card.md)**-Eigenschaft jeder Karte. Dieser Wert wird in der Datenquelle für dieses Feld gespeichert. Hier können Sie eine weiter Transformierung anwenden, um eventuell die Transformierung umzukehren, die auf die **[Default](controls/properties-core.md)**-Formel der Karte angewendet wurde.

Die **Valid**-Eigenschaft wird von den Metadaten der Datenquelle gesteuert, auf Grundlage der **[DataField](controls/control-card.md)**-Eigenschaft. Außerdem basiert sie auf der **[Required](controls/control-card.md)**-Eigenschaft und darauf, ob die **[Update](controls/control-card.md)**-Eigenschaft einen Wert enthält. Wenn der Wert für die **[Update](controls/control-card.md)**-Eigenschaft nicht gültig ist, bietet die **Fehler**-Eigenschaft eine benutzerfreundliche Fehlermeldung.

Wenn die **[DataField](controls/control-card.md)**-Eigenschaft einer Karte *blank* ist, ist die Smartcard lediglich ein Container für Steuerelemente. Seine Eigenschaften **Valid** und **[Update](controls/control-card.md)** werden nicht einbezogen, wenn das Formular gesendet wird.

## <a name="dissecting-an-example"></a>Analyse eines Beispiels
Sehen Sie sich die Steuerelemente an, aus denen eine einfache Dateneingabekarte besteht. Der Zwischenraum zwischen Steuerelementen wurde verbessert, um sie besser voneinander abgrenzen zu können:

![](./media/working-with-cards/dissect-card1.png)

Halten Sie die ALT-TASTE gedrückt, um die Namen der Steuerelemente anzuzeigen, aus denen diese Karte besteht:

![](./media/working-with-cards/dissect-card2.png)

Dies Karte funktioniert durch vier Steuerelemente:

| Name | Typ | Beschreibung |
| --- | --- | --- |
| **TextRequiredStar** |**[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) |Zeigt einen Stern an, der häufig in Dateneingabeformularen verwendet wird, um erforderliche Felder zu kennzeichnen |
| **TextFieldDisplayName** |**[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) |Zeigt den benutzerfreundlichen Namen dieses Felds an. Dieser Name kann von dem im Schema der Datenquelle abweichen. |
| **InputText** |**Eingabetext**-Steuerelement |Zeigt den anfänglichen Wert des Felds und ermöglicht es dem Benutzer, diesen Wert zu ändern |
| **TextErrorMessage** |**[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) |Zeigt eine benutzerfreundliche Fehlermeldung für den Benutzer an, wenn ein Problem mit der Validierung auftritt. Außerdem stellt es sicher, dass das Feld einen Wert hat, wenn einer erforderlich ist. |

Um diese Steuerelemente mit Daten aufzufüllen, können deren Eigenschaften von den Eigenschaften der Karte anhand dieser Schlüsselformeln gesteuert werden. Beachten Sie, dass keine dieser Formeln auf ein bestimmtes Feld verweist. Stattdessen stammen alle Informationen von der Karte.

| Control-Eigenschaft | Formel | Beschreibung |
| --- | --- | --- |
| **TextRequiredStar.Visible** |**Parent.Required** |Der Stern erscheint nur, wenn das Feld erforderlich ist. Eine Formel ist erforderlich, die von Ihnen oder den Metadaten der Datenquelle gesteuert wird. |
| **TextFieldDisplayName.Text** |**Parent.DisplayName** |Das Textfeld-Steuerelement zeigt den benutzerfreundlichen Namen, den Sie oder die Metadaten der Datenquelle bereitstellen, und die in der **[DisplayName](controls/control-card.md)**-Eigenschaft der Karte festgelegt wird. |
| **InputText.Default** |**Parent.Default** |Das Texteingabe-Steuerelements zeigt zuerst den Wert des Felds der Datenquelle, wie er vom Standardwert der Karte bereitgestellt wird. |
| **TextErrorMessage.Text** |**Parent.Error** |Wenn ein Überprüfungsproblem auftritt, bietet die **Error**-Eigenschaft der Karte eine entsprechende Fehlermeldung. |

Folgende Schlüsselformeln stehen zur Verfügung, um Informationen aus diesen Steuerelementen abzurufen und sie wieder in die Datenquelle einzufügen:

| Steuerelementname | Formel | Beschreibung |
| --- | --- | --- |
| **DataCard.DataField** |**"ApproverEmail"** |Der Name des Felds, das der Benutzer auf dieser Karte anzeigen und bearbeiten kann. |
| **DataCard.Update** |**InputText.Text** |Der zu überprüfende Wert, der wieder in die Datenquelle eingefügt werden soll, wenn **[SubmitForm](functions/function-form.md)** ausgeführt wird. |

