---
title: Erste Schritte mit Formeln in einer Canvas-App | Microsoft-Dokumentation
description: Verwenden Sie in PowerApps Formeln, um eine Canvas-App anzupassen.
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
ms.openlocfilehash: 78dd0f5af1051abcb7aa5fa067c72732874d7b32
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865461"
---
# <a name="get-started-with-canvas-app-formulas-in-powerapps"></a>Erste Schritte mit Canvas-App-Formeln in PowerApps

Konfigurieren Sie Ihre Canvas-App mit Formeln, die nicht nur Werte berechnen und andere Aufgaben ausführen (wie in Excel), sondern auch auf Benutzereingaben reagieren (wie eine App es erfordert).

* In Excel erstellen Sie Formeln, um z.B. Zellen zu füllen und Tabellen und Diagramme zu erstellen.
* In PowerApps erstellen Sie ähnliche Formeln, da Sie Steuerelemente anstelle von Zellen konfigurieren. Darüber hinaus erstellen Sie Formeln, die speziell für Apps anstatt für Arbeitsblätter gelten.

Sie erstellen beispielsweise eine Formel, um zu bestimmen, wie Ihre App reagiert, wenn Benutzer eine Schaltfläche auswählen, einen Schieberegler anpassen oder andere Eingaben bereitstellen. Diese Formeln zeigen möglicherweise einen anderen Screen an, aktualisieren eine App-externe Datenquelle oder erstellen eine Tabelle, die eine Teilmenge der Daten in einer vorhandenen Tabelle enthält.

Sie können verschiedene Formeln für eine Vielfalt an Szenarios verwenden. Sie können z.B. das GPS Ihres Geräts, ein Kartensteuerelement und eine Formel verwenden, die **Location.Latitude** und **Location.Longitude** verwendet, um Ihre aktuelle Position anzuzeigen. Während Sie sich bewegen, verfolgt die Karte automatisch Ihren Standort.

Dieses Thema bietet nur eine Übersicht über das Arbeiten mit Formeln. Weitere Informationen und die vollständige Liste der Funktionen, Operatoren und anderen Bausteine, die Sie verwenden können, finden Sie unter [Formula reference for PowerApps](formula-reference.md) (Formelreferenz für PowerApps).

## <a name="prerequisites"></a>Voraussetzungen

* [Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.
* Erfahren Sie, wie Sie [ein Steuerelement](add-configure-controls.md) in PowerApps konfigurieren.

## <a name="show-a-simple-value"></a>Anzeigen eines einfachen Werts
In Excel können Sie eine bestimmte Dateneinheit eingeben, z.B. die Zahl **42** oder den Ausdruck **Hello World**, indem Sie sie in eine Zelle schreiben. Diese Zelle wird die Daten immer so anzeigen, wie Sie sie eingegeben haben. In PowerApps können Sie auch Dateneinheiten angeben, die sich nicht ändern, wenn Sie die Einstellung **[Text](controls/properties-core.md)** einer Bezeichnung auf genau die gewünschte Zeichenreihenfolge in doppelten Anführungszeichen festlegen.

1. Wählen Sie im Menü **File** (Datei) (am linken Rand des Bildschirms) **New** (New) aus.
2. Wählen Sie unter **Create an app** auf der Kachel **Blank app** die Option **Phone layout** aus.
   
    Die Bearbeitungsleiste befindet sich am oberen Bildschirmrand.
   
    ![Die Bearbeitungsleiste](./media/working-with-formulas/formula-bar.png)
   
    Diese Leiste besteht aus zwei Teilen:
   
   * *Eigenschaftenliste:* Jedes Steuerelement und jeder Bildschirm verfügt über eine [Reihe von Eigenschaften](reference-properties.md).  Verwenden Sie diese Liste, um eine bestimmte Eigenschaft auszuwählen.  
   * *Formel:* Die für diese Eigenschaft zu berechnende Formel besteht aus [Werten, Operatoren und Funktionen](formula-reference.md).
     
     In der Bearbeitungsleiste können Sie Eigenschaften des ausgewählten Steuerelements oder, wenn keine Steuerelemente ausgewählt sind, auch die des Screens anzeigen und bearbeiten.  Der Name des ausgewählten Steuerelements wird auf der Registerkarte **Content** (Inhalt) angezeigt:
     
     ![Die Inhaltsleiste zeigt das momentan ausgewählte Steuerelement.](./media/working-with-formulas/content-tab-selection.png)
     
     Sie können den Namen des ausgewählten Steuerelements in der Registerkarte **Content** ändern, indem Sie auf den Namen klicken.
3. Fügen Sie dem Bildschirm ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu.
   
    ![Text box-Steuerelement hinzugefügt](./media/working-with-formulas/add-a-label.png)
   
    Wenn Sie eine Bezeichnung hinzufügen, zeigt die Eigenschaftenliste automatisch die Eigenschaft **[Text](controls/properties-core.md)** an, die steuert, was das Steuerelement anzeigt. Der Wert dieser Eigenschaft ist standardmäßig **"Text"**.  
4. Legen Sie den Wert der Eigenschaft **[Text](controls/properties-core.md)** auf **"Hello World"** fest, indem Sie die Zeichenfolge in doppelten Anführungszeichen in die Bearbeitungsleiste eingeben:
   
    ![Verwendung der Bezeichnung „Hello World“](./media/working-with-formulas/label-hello-world.png)
   
    Die Bezeichnung gibt den neuen Wert wieder, während Sie ihn eingeben.  Möglicherweise wird auf dem Screen gelbe Ausrufezeichen angezeigt, während Sie etwas eingeben. Diese Symbole weisen auf Fehler hin, verschwinden allerdings, sobald Sie einen gültigen Wert eingegeben haben. Eine Zeichenfolge, die nicht in doppelten Anführungszeichen eingeschlossen ist, ist z.B. kein gültiger Wert.
   
    In Excel können Sie eine Zahl wie **42** anzeigen, indem Sie sie in eine Zelle eingeben oder indem Sie eine Formel verwenden, die zu dieser Zahl auflöst, wie z.B. **=SUM(30, 12)**. In PowerApps erreichen Sie denselben Effekt, indem Sie die Eigenschaft **Text** eines Steuerelements, z.B. einer Bezeichnung, auf **42** oder **Sum(30, 12)** festlegen. Die Zelle und die Bezeichnung zeigen daraufhin immer diese Zahl an, unabhängig von jeglichen Änderungen am Arbeitsblatt oder an der App.
   
    > [!NOTE]
   > In PowerApps werden Formeln weder ein Gleichheitszeichen noch ein Pluszeichen vorangestellt, wie es z.B. in Excel gebräuchlich ist. Die Bearbeitungsleiste behandelt standardmäßig jede Eingabe wie eine Formel. Formeln werden ebenso wenig in doppelte Anführungszeichen (") gesetzt, die Sie zuvor zum Angeben einer Textzeichenfolge verwendet haben.
5. Ersetzen Sie in der **[Text](controls/properties-core.md)**-Eigenschaft der Bezeichnung die Zeichenfolge **"Hello World"** durch **Sum(1, 2, 3)**.
   
    ![Die Eingabe der partiellen Funktion „Sum(1, 2, 3“ ohne eine schließende Klammer gibt Fehler zurück.](./media/working-with-formulas/label-sum-partial.png)
   
    Die Bearbeitungsleiste unterstützt Sie während der Eingabe, indem die Beschreibung und die erwarteten Argumente der Funktion angezeigt werden.  Wie bei dem schließenden doppelten Anführungszeichen in **"Hello World"** werden auf dem Screen so lange gelbe Ausrufezeichen angezeigt, die Fehler andeuten, bis die schließende Klammer für diese Formel gesetzt wird:
   
    ![Verwendung der vollständigen Formel „Sum(1, 2, 3)“](./media/working-with-formulas/label-sum.png)

## <a name="change-a-value-based-on-input"></a>Ändern eines Werts anhand der Eingabe
Geben Sie in Excel **=SUM(A1:A2)** in eine Zelle ein, um die Summe der Werte der Zellen A1 und A2 anzuzeigen. Wenn sich einer oder beide dieser Werte ändern, zeigt die Zelle mit der Formel automatisch das aktualisierte Ergebnis an.

![Veranschaulichung der Neuberechnung in Excel, indem zwei Zahlen addiert werden](./media/working-with-formulas/excel-recalc.png)

In PowerApps können Sie ein ähnliches Ergebnis erzielen, indem Sie Steuerelemente hinzufügen und deren Eigenschaften festlegen. In diesem Beispiel wird die Bezeichnung aus den vorherigen Schritten gezeigt und außerdem zwei **[Texteingabe](controls/control-text-input.md)**-Steuerelemente namens **TextInput1** und **TextInput2**.

![Veranschaulichung der Neuberechnung in PowerApps, indem zwei Zahlen addiert werden](./media/working-with-formulas/recalc1.png)

Unabhängig davon, welche Zahlen Sie in die Texteingabe-Steuerelemente eingeben, zeigt die Bezeichnung immer die Summe dieser Zahlen an, da ihre **[Text](controls/properties-core.md)**-Eigenschaft auf diese Formel festgelegt ist:
<br>**TextInput1 + TextInput2**

![Veranschaulichung der Neuberechnung in PowerApps, indem zwei Zahlen addiert werden](./media/working-with-formulas/recalc2.png)

In Excel können Sie eine bedingte Formatierung verwenden, um negative Werte z.B. in Rot anzuzeigen. In PowerApps verwenden Sie eine Formel, die die **[If](functions/function-if.md)**-Funktion enthält, welche sich ganz ähnlich verhält wie in Excel.

1. Legen Sie die **[Color](controls/properties-color-border.md)**-Eigenschaft des Textfelds auf diese Formel fest:<br>**If( Value(TextBox1.Text) < 0, Red, Black )**
   
    > [!NOTE]
   > Geben Sie in einer Formel die Eigenschaft eines Steuerelements an, indem Sie den Namen des Steuerelements gefolgt von einem Punkt und dem Namen der Eigenschaft angeben. Geben Sie z.B. die **[Text](controls/properties-core.md)**-Eigenschaft von **TextBox1** an, indem Sie **TextBox1.Text** eingeben.
   
    ![Veranschaulichung der Änderung der Farben einer Bezeichnung anhand ihres Werts in PowerApps Recalc](./media/working-with-formulas/recalc-color1.png)
2. Geben Sie in **TextInput1** und **TextInput2** zwei Zahlen an, die bei einer Addition eine negative Zahl ergeben.
   
    ![Veranschaulichung der Änderung der Farben einer Bezeichnung anhand ihres Werts in PowerApps Recalc](./media/working-with-formulas/recalc-color2.png)
   
    Der Wert in der Bezeichnung wird rot angezeigt.

## <a name="change-a-color-based-on-user-input"></a>Ändern einer Farbe anhand der Benutzereingabe
Sie können Ihre App mit Formeln konfigurieren, damit Benutzer die Darstellung oder das Verhalten Ihrer App ändern können. Sie können beispielsweise einen Filter erstellen, um nur Daten anzuzeigen, die eine vom Benutzer angegebene Zeichenfolge enthalten, oder Sie können es Benutzern erlauben, einen Datensatz zu sortieren, der auf einer bestimmten Spalte im Dataset basiert. In dieser Prozedur erlauben Sie es Benutzern, die Farbe des Screens zu ändern, indem Sie einen oder mehrere Schieberegler anpassen.

1. Entfernen Sie die Steuerelemente aus den vorherigen Prozeduren, oder erstellen Sie wie zuvor eine leere App, und fügen Sie drei Schieberegler-Steuerelemente hinzu:
   
    ![Hinzufügen eines Schieberegler-Steuerelements](./media/working-with-formulas/insert-slider.png)
2. Ordnen Sie die Schieberegler so an, dass sie sich nicht überlappen, fügen Sie drei Bezeichnungen hinzu, und schreiben Sie **Red** (Rot), **Green** (Grün) und **Blue** (Blau) hinein:
   
    ![Ordnen der Schieberegler und Hinzufügen von Bezeichnungen für jede Farbkomponente](./media/working-with-formulas/three-sliders.png)
3. Legen Sie die Eigenschaft **Max** eines jeden Schiebereglers auf 255 fest, was dem maximalen Wert einer Farbkomponente in der **[RGBA](functions/function-colors.md)**-Funktion entspricht.
   
    Sie können die Eigenschaft **Max** angeben, indem Sie sie in der Registerkarte **Content** oder in der Eigenschaftenliste auswählen:
   
    ![Ändern des maximalen Werts für jeden einzelnen Schieberegler](./media/working-with-formulas/three-sliders-max.png)
4. Wählen Sie den Screen aus, indem Sie neben die Steuerelemente klicken, und legen Sie Eigenschaft **[Fill](controls/properties-color-border.md)** (Füllen) des Screens auf folgende Formel fest:<br>**RGBA( Slider1.Value, Slider2.Value, Slider3.Value, 1 )**
   
    Wie bereits beschrieben können Sie mithilfe von **.** auf die Eigenschaften von Steuerelementen zugreifen Operator  **Slider1.Value** bezieht sich auf die **[Value](controls/properties-core.md)**-Eigenschaft (Wert) des Schiebereglers, die angibt, wo der Benutzer den Schieberegler hinsichtlich den **Min**- und **Max**-Werten platziert hat. Jedes Steuerelement wird beim Eingeben sowohl auf dem Screen als auch in der Bearbeitungsleiste farblich hervorgehoben:
   
    ![Ändern der Formel für die Füllfarbe des Screenhintergrunds; noch nicht abgeschlossen](./media/working-with-formulas/three-sliders-partial-rgba.png)
   
    Sobald Sie die schließende Klammer eingeben, ändert sich die Farbe des Screenhintergrunds auf Grundlage der Standardwerte der einzelnen Schieberegler, also **50**, in Dunkelgrau. Sobald Sie die Formel zu Ende eingegeben haben, wird sie berechnet und als Wert für die Füllfarbe des Hintergrunds verwendet. Sie können mit Ihrer App im Standardarbeitsbereich interagieren, ohne die Vorschau zu öffnen zu müssen:
   
    ![Ändern des maximalen Werts für jeden einzelnen Schieberegler](./media/working-with-formulas/three-sliders-complete-rgba.png)
5. Passen Sie die Schieberegler an, und zeigen Sie die Auswirkungen der Änderungen auf die Hintergrundfarbe an.
   
    Sobald ein Schieberegler verändert wird, wird die Formel, die die **[RGBA](functions/function-colors.md)**-Funktion enthält, neu berechnet, was wiederum sofort die Screendarstellung verändert.
   
    ![Änderung der Formel für die Füllfarbe des Screenhintergrunds; nun abgeschlossen](./media/working-with-formulas/three-sliders-example-colors.png)

## <a name="manage-app-behavior"></a>Verwalten des App-Verhaltens
Sie können Formeln nicht nur zur Durchführung von Berechnungen und der Änderung der Darstellung verwenden, sondern auch, um selbst aktiv zu werden. Sie können z.B. die Eigenschaft **[OnSelect](controls/properties-core.md)** einer Schaltfläche auf eine Formel festlegen, die die **[Navigate](functions/function-navigate.md)**-Funktion enthält. Wenn ein Benutzer die Schaltfläche auswählt, wird der Screen angezeigt, den Sie in der Formel angeben.

Sie können einige Funktionen wie **[Navigate](functions/function-navigate.md)** und **[Collect](functions/function-clear-collect-clearcollect.md)**, nur in Verhaltensformeln verwenden.  Die Formelreferenz macht Sie darauf aufmerksam, wenn eine Funktion nur in diesem Kontext verwendet werden kann.  

Sie können in einer Verhaltensformel mehr als eine Aktion durchführen, wenn Sie die Funktionen mit einem Semikolon (;) trennen. So z.B., wenn Sie eine Kontextvariable aktualisieren, Daten an eine Datenquelle verschieben und schließlich zu einem anderen Screen navigieren möchten.

## <a name="view-a-list-of-properties-by-category"></a>Anzeigen einer Eigenschaftenliste nach Kategorien
In der folgenden Eigenschaftenliste werden die Eigenschaften alphabetisch aufgeführt. Sie können aber auch alle Eigenschaften eines Steuerelements nach Kategorie anzeigen, wenn Sie auf der Registerkarte **View** (Ansicht) die Option **Advanced** (Erweitert) auswählen:

![die erweiterte Ansicht](./media/working-with-formulas/advanced-open.png)

Sie können Formeln in dieser Ansicht direkt bearbeiten.  Mit der Steuerelementauswahl am oberen Rand des Bereichs finden Sie schnell ein Steuerelement, mit dem Sie arbeiten können.  Mit der Eigenschaftensuche finden Sie außerdem schnell eine Eigenschaft dieses Steuerelements.

Diese Ansicht zeigt zu Beginn die wichtigsten Eigenschaften.  Klicken Sie auf den Pfeil nach unten am unteren Rand des Bereichs, um alle Eigenschaften anzuzeigen.  Jedes Steuerelement verfügt über eine lange Liste von Eigenschaften, die alle Aspekte des Verhaltens und der Darstellung des Steuerelements steuern. Sie können durch die Liste scrollen oder nach einer Eigenschaft suchen, indem Sie sie in das Feld am oberen Rand des Bereichs eingeben.

## <a name="formula-syntax"></a>Formelsyntax
Wenn Sie in der Bearbeitungsleiste eine Formel eingeben, werden unterschiedliche Syntaxelemente in unterschiedlichen Farben angezeigt, um die Lesbarkeit zu verbessern und das Verständnis langer Formeln zu erleichtern. Dies ist die Farbencodeliste in PowerApps.

![Syntaxhervorhebung](./media/working-with-formulas/syntax-highlighting.png)

