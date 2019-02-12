---
title: Grundlegendes zu Variablen in Canvas-Apps | Microsoft-Dokumentation
description: Referenzinformationen zum Arbeiten mit Zustands- und Kontextvariablen und Sammlungen in Canvas-Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bd5ca15f4c76e1ca69fe143d085e112cdc014dec
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849177"
---
# <a name="understand-canvas-app-variables-in-powerapps"></a>Grundlegendes zu Canvas-App-Variablen in PowerApps

Wenn Sie eine anderes Programmiertool verwenden, wie z.B. Visual Basic oder JavaScript, fragen Sie sich möglicherweise: **Wo sind die Variablen?** PowerApps ist etwas anders und erfordert einen anderen Ansatz. Statt auf eine Variable zurückzugreifen, wenn Sie eine Canvas-App erstellen, sollten Sie sich die Frage stellen: **Wie würde ich in Excel verfahren?**

In anderen Tools haben Sie möglicherweise eine explizite Berechnung ausgeführt und das Ergebnis in einer Variablen gespeichert. Allerdings berechnen sowohl PowerApps als auch Excel automatisch Formeln neu, sobald die Eingabedaten geändert werden, sodass Sie üblicherweise keine Variablen erstellen oder aktualisieren müssen. Wenn Sie diesen Ansatz wann immer möglich verwenden, können Sie Ihre App leichter erstellen, verstehen und warten.

In einigen Fällen müssen Sie Variablen in PowerApps verwenden, wodurch das Modell von Excel um [Verhaltensformeln](working-with-formulas-in-depth.md) erweitert wird. Diese Formeln werden z.B. ausgeführt, wenn ein Benutzer eine Schaltfläche auswählt. Innerhalb einer Verhaltensformel ist es oft hilfreich, eine Variable festzulegen, die in anderen Formeln verwendet werden soll.

Vermeiden Sie im allgemeinen das Verwenden von Variablen. Manchmal hat jedoch nur eine Variable die Auswirkungen, die Sie benötigen.

## <a name="translate-excel-into-powerapps"></a>Excel in PowerApps übersetzt

### <a name="excel"></a>Excel
Betrachten Sie die Funktionsweise von Excel. Eine Zelle kann einen Wert, z.B. eine Zahl oder eine Zeichenfolge, oder eine Formel enthalten, die auf den Werten der anderen Zellen basiert. Nachdem der Benutzer einen anderen Wert in eine Zelle eingibt, berechnet Excel automatisch alle Formeln, die von dem neuen Wert abhängig sind. Zum Aktivieren dieses Verhaltens müssen Sie nichts programmieren.

![](media/working-with-variables/excel-recalc.png)

Excel verfügt nicht über Variablen. Der Wert einer Zelle, die eine Formel enthält, ändert sich abhängig von seiner Eingabe; es gibt allerdings keine Möglichkeit, das Ergebnis einer Formel in einer Zelle oder an einer anderen Stelle zu speichern. Wenn Sie den Wert einer Zelle ändern, ändert sich möglicherweise das gesamte Arbeitsblatt, und alle zuvor berechneten Werte gehen verloren.  Ein Excel-Benutzer kann Zellen kopieren und einfügen, aber dies unterliegt der manuellen Eingabe des Benutzers und ist mit Formeln nicht möglich.

### <a name="powerapps"></a>PowerApps
Apps, die Sie in PowerApps erstellen, verhalten sich ähnlich wie Excel. Statt Zellen zu aktualisieren, können Sie Steuerelemente überall auf dem Bildschirm hinzufügen und sie für den Einsatz in Formeln benennen.

Sie können z.B. das Verhalten von Excel in einer App replizieren, indem Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) mit dem Namen **TextBox1**, und zwei **[Texteingabe](controls/control-text-input.md)**-Steuerelement mit den Namen **TextInput1** und **TextInput2** hinzufügen. Wenn Sie anschließend die **[Text](controls/properties-core.md)**-Eigenschaft von **TextBox1** auf **TextInput1 + TextInput2** festlegen, wird immer automatisch die Summe der Zahlen angezeigt, die sich in **TextInput1** und **TextInput2** befinden.

![](media/working-with-variables/recalc1.png)

Beachten Sie, dass das **TextBox1**-Steuerelement ausgewählt ist, dessen **[Text](controls/properties-core.md)**-Formel in der Bearbeitungsleiste am oberen Rand des Bildschirms angezeigt wird.  Hier finden Sie die Formel **TextInput1 + TextInput2**.  Diese Formel erstellt eine Abhängigkeit zwischen diesen Steuerelementen, genauso wie Abhängigkeiten zwischen den Zellen in einer Excel-Arbeitsmappe erstellt werden.  Ändern Sie den Wert von **TextInput1**:

![](media/working-with-variables/recalc2.png)

Die Formel für **TextBox1** wurde automatisch neu berechnet; der neue Wert wird angezeigt.

In PowerApps können Sie Formeln nicht nur verwenden, um den primären Wert eines Steuerelements zu bestimmen, sondern auch, um Eigenschaften, wie z.B. das Format, zu bestimmen. Im nächsten Beispiel zeigt eine Formel für die **[Color](controls/properties-color-border.md)**-Eigenschaft der Bezeichnung automatisch negative Werte rot an. Die **[If](functions/function-if.md)**-Funktion ist Ihnen wahrscheinlich aus Excel vertraut:
<br>**If( Value(TextBox1.Text) < 0, Red, Black )**

![](media/working-with-variables/recalc-color1.png)

Wenn das Ergebnis der Berechnung in **TextBox1.Text** negativ ist, wird die Zahl rot angezeigt:

![](media/working-with-variables/recalc-color2.png)

Sie können verschiedene Formeln für eine Vielfalt an Szenarios verwenden:

* Indem Sie das GPS Ihres Geräts verwenden, kann ein Kartensteuerelement mit einer Formel, die **Location.Latitude** und **Location.Longitude** verwendet, Ihre aktuelle Standort anzeigen.  Während Sie sich bewegen, verfolgt die Karte automatisch Ihren Standort.
* Andere Benutzer können [Datenquellen](working-with-data-sources.md) aktualisieren.  Andere Mitglieder Ihres Teams können z.B. die Elemente in einer SharePoint-Liste aktualisieren.  Wenn Sie eine Datenquelle aktualisieren, werden alle abhängigen Formeln automatisch neu berechnet, um die aktualisierten Daten widerzuspiegeln. Wenn Sie das Beispiel fortführen, können Sie beispielsweise die **[Items](controls/properties-core.md)**-Eigenschaft eines Katalogs auf die Formel **Filter (SharePointList)** festlegen, sodass automatisch die neu gefilterte Menge von [Datensätze](working-with-tables.md#records) angezeigt wird.

### <a name="benefits"></a>Vorteile
Das Erstellen von Apps mithilfe von Formeln hat viele Vorteile:

* Wenn Sie Excel kennen, kennen Sie PowerApps. Das Modell und die Formelsprache sind identisch.
* Wenn Sie schon mal andere Programmiertools verwendet haben, können Sie sich vorstellen, wie viel Code erforderlich wäre, um diese Beispiele zu realisieren.  In Visual Basic müssten Sie einen Ereignishandler für das Änderungsereignis für jedes Texteingabe-Steuerelement erstellen.  Der Code, der jede dieser Berechnung ausführen soll, ist redundant und könnte möglicherweise nicht mehr synchron abgerufen werden, oder Sie müssten eine gängige Unterroutine schreiben.  In PowerApps erreichen Sie das alles mit einer einzigen, einzeiligen Formel.
* Sie wissen genau, wo Sie suchen müssen, um zu erfahren, woher der Text in **TextBox1** stammt: die Formel in der **[Text](controls/properties-core.md)**-Eigenschaft.  Es gibt keine andere Möglichkeit, den Text dieses Steuerelements zu beeinflussen.  In einem herkömmlichen Programmiertool könnte jeder Ereignishandler und jede Unterroutine überall im Programm den Wert des Bezeichners ändern.  Dadurch kann es schwieriger sein, einzugrenzen, wann und wo eine Variable geändert wurde.
* Wenn der Benutzer ein Schieberegler-Steuerelement ändert und es sich dann noch mal anders überlegt, kann er den Schieberegler wieder auf den ursprünglichen Wert zurücksetzen.  Und es ist, als ob nichts geändert worden wäre: Die Anwendung zeigt die gleichen Steuerelementwerte wie vorher an.  Das Experimentieren und Fragen nach „Was wäre wenn“ hat keine Folgen, genauso wenig wie in Excel.  

Im Allgemeinen sind Sie bessergestellt, wenn Sie durch das Verwenden einer Formel einen Effekt erzielen können. Lassen Sie die Formel-Engine in PowerApps für Sie arbeiten.  

## <a name="know-when-to-use-variables"></a>Wann es sinnvoll ist, Variablen zu verwenden
Passen Sie Ihren einfachen Addierer an, sodass er sich wie eine traditionelle Rechenmaschine mit einer laufenden Summe verhält. Wenn Sie eine **Add**-Schaltfläche (Hinzufügen) auswählen, fügen Sie eine Zahl zur laufenden Summe hinzu. Wenn Sie eine **Clear**-Schaltfläche (Löschen) auswählen, setzen Sie die laufende Summe auf 0 (null) zurück.

![](media/working-with-variables/button-changes-state.png)

Ihre Rechenmaschine verwendet etwas, das es in Excel so nicht gibt: eine Schaltfläche. Sie können in dieser App die laufende Summe nicht mit Formeln allein berechnen, da ihr Wert von einer Reihe von Aktionen des Benutzers abhängt. Stattdessen muss die laufende Summe aufgezeichnet und manuell aktualisiert werden. Die meisten Programmiertools speichern diese Informationen in einer *Variablen*.    

Manchmal benötigen Sie für Ihre App eine Variable, um das zu erreichen, was Sie möchten.  Doch dieser Ansatz hat auch Nachteile:

* Sie müssen die laufende Summe manuell aktualisieren. Die automatische Berechnung erfüllt nicht Ihre Ansprüche.
* Die laufende Summe kann nicht mehr basierend auf den Werten anderer Steuerelemente berechnet werden. Dies hängt davon ab, wie oft der Benutzer die Schaltfläche **Add** (Hinzufügen) ausgewählt hat und welcher Wert sich jeweils in dem Texteingabe-Steuerelement befunden hat. Hat der Benutzer 77 eingegeben und **Hinzufügen** zweimal ausgewählt, oder hat er jeweils 24 und 130 für jede der Hinzufügungen angegeben? Nachdem die Summe 154 beträgt, können Sie den Unterschied nicht mehr feststellen.
* Änderungen der Gesamtsumme können aus verschiedenen Pfaden stammen. In diesem Beispiel kann sowohl die **Add**- als auch die **Clear**-Schaltflächen die Gesamtsumme aktualisieren. Wenn die App sich nicht wie erwartet verhält, ist welche Schaltfläche für das Problem verantwortlich?

## <a name="create-a-global-variable"></a>Erstellen einer globalen Variablen
Sie benötigen eine Variable, die die laufende Summe enthält, um unseren hinzufügenden Computer zu erstellen. Die einfachsten Variablen, mit denen Sie in PowerApps arbeiten können, sind *globale Variablen*.  

Funktionsweise von globalen Variablen:

* Sie legen den Wert der globalen Variablen mit der **[Set](functions/function-set.md)**-Funktion fest.  Durch **Set( MyVar, 1 )** wird die globale Variable **MyVar** auf den Wert **1** festgelegt.
* Sie verwenden die globale Variable, indem Sie mit der **Set**-Funktion auf den verwendeten Namen verweisen.  In diesem Fall gibt **MyVar** den Wert **1** zurück.
* Globale Variablen können beliebige Werte enthalten, z.B. Zeichenfolgen, Zahlen, Datensätze und [Tabellen](working-with-tables.md).

Erstellen Sie Ihre Rechenmaschine mithilfe einer globalen Variablen neu:

1. Fügen Sie ein Texteingabe-Steuerelement mit dem Namen **TextInput1** hinzu, und zwei Schaltflächen mit dem Namen **Button1** und **Button2**.

2. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **Button1** auf **"Add"** fest, und legen Sie die **Text**-Eigenschaft von **Button2** auf **"Clear"** fest.

3. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft einer **Add**-Schaltfläche auf folgende Formel fest, um die laufende Summe zu aktualisieren, wenn ein Benutzer die Schaltfläche auswählt:
   
    **Set( RunningTotal, RunningTotal + Text1 )**
   
    Wenn ein Benutzer erstmals die **Add**-Schaltfläche auswählt, und **[Set](functions/function-set.md)** aufgerufen wird, wird **RunningTotal** mit einem Standardwert von *blank* (leer) erstellt.  Beim Hinzufügen wird es als eine 0 (null) behandelt.
   
    ![](media/working-with-variables/global-variable-1.png)
4. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft der **Clear**-Schaltfläche auf folgende Formel fest, um die laufende Summe auf **0** festzulegen:
   
    **Set( RunningTotal, 0 )**
   
    ![](media/working-with-variables/global-variable-2.png)
5. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](controls/properties-core.md)**-Eigenschaft auf **RunningTotal** fest.
   
    Diese Formel wird automatisch neu berechnet und zeigt dem Benutzer den Wert von **RunningTotal** an, während sie sich auf Grundlage der vom Benutzer ausgewählten Schaltflächen ändert.
   
    ![](media/working-with-variables/global-variable-3.png)
6. Sehen sie sich eine Vorschau der App an, und Sie sehen die Rechenmaschine, wie sie oben beschrieben wurde.  Geben Sie eine Zahl im Textfeld ein, und drücken Sie mehrmals die Schaltfläche **Add**.  Kehren Sie anschließend zur Erstellung zurück, indem Sie die ESC-TASTE drücken.  
   
    ![](media/working-with-variables/global-variable-4.png)
7. Um den Wert der globalen Variablen anzuzeigen, wählen Sie das Menü **Datei** aus, und wählen Sie im linken Bereich **Variablen** aus.
   
    ![](media/working-with-variables/global-variable-file-1.png)
8. Wählen Sie die Variable aus, um alle Stellen zu ermitteln, an denen sie definiert ist.
   
    ![](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>Typen von Variablen
In PowerApps gibt es drei Typen von Variablen:

| Variablentyp | Umfang | Beschreibung | Functions |
| --- | --- | --- | --- |
| Globale Variablen |App |Sind am einfachsten zu verwenden.  Enthalten eine Zahl, eine Textzeichenfolge, einen booleschen Wert, einen Datensatz, eine Tabelle usw., auf die an einer beliebigen Stelle in der App verwiesen werden kann. |[**Set**](functions/function-set.md) |
| Kontextvariablen |Bildschirm |Ideal für die Übergabe von Werten an einen Bildschirm (ähnelt der Übergabe eines Parameters an eine Prozedur in anderen Sprachen).  Der Verweis ist nur aus einem Bildschirm möglich. |[**UpdateContext**](functions/function-navigate.md) |
| Sammlungen |App |Enthalten eine Tabelle, die Verweise von beliebigen Stellen in der App darstellen kann.  Ermöglichen es, dass der Inhalt der Tabelle geändert wird, und wird nicht in seiner Gesamtheit festgelegt. Können für die spätere Verwendung auf dem lokalen Gerät gespeichert werden. |[**Collect**](functions/function-savedata-loaddata.md)<br>usw. |

Alle Variablen werden implizit erstellt, wenn sie in den Funktionen **Set**, **UpdateContext**, **Navigate** und **Collect** verwendet werden.  Es gibt keine explizite Deklaration von Variablen wie in anderen Programmiertools.  Die Typen der Variablen werden ebenfalls von den darin platzierten Werten implizit abgeleitet.

Alle Variablen werden während der Ausführung der App im Speicher aufbewahrt.  Beim Schließen der App gehen die in den Variablen enthaltenen Werte verloren.  Sie können den Inhalt einer Variablen mit der **Patch**-Funktion oder der **Collect**-Funktion in einer Datenquelle speichern. Bei Sammlungen können Sie ihn mit der **SaveData**-Funktion auf dem lokalen Gerät speichern.  Beim erstmaligen Laden der App weisen alle Variablen den Wert *blank* (leer) auf.

Der Wert einer Variablen wird über den Variablennamen abgerufen.  Nach der Definition als **Set( MyColor, Red )** können Sie **MyVar** überall dort verwenden, wo ein Farbwert verwendet werden kann, und dieser wird durch den Wert **Red** ersetzt.  Eine globale Variable oder Sammlung kann denselben Namen wie eine Kontextvariable besitzen.  In einem solchen Fall hat die Kontextvariable Vorrang.  Sie haben immer noch die Möglichkeit, mit dem [Operator zur Mehrdeutigkeitsvermeidung](functions/operators.md#disambiguation-operator) **@[MyColor]** auf die globale Variable oder Sammlung zu verweisen.

## <a name="create-a-context-variable"></a>Erstellen Sie eine Kontextvariable
Im Folgenden wird erläutert, wie die Rechenmaschine mit einer Kontextvariablen und nicht mit einer globalen Variablen erstellt wird.    

Funktionsweise von Kontextvariablen:

* Erstellen und Festlegen der Kontextvariablen mithilfe der **[UpdateContext](functions/function-updatecontext.md)**-Funktion.  Wenn eine Kontextvariable noch nicht vorhanden ist, wenn sie zum ersten Mal aktualisiert wird, wird sie mit dem Standardwert *blank* erstellt.
* Sie erstellen und aktualisieren Kontextvariablen mit Datensätzen. In anderen Programmiertools verwenden Sie häufig „=“ für Zuweisungen, wie z.B. in „x = 1“.  Verwenden Sie stattdessen für Kontextvariablen **{ x: 1 }**. Wenn Sie eine Kontextvariable verwenden, verwenden Sie ihren Namen direkt.  
* Sie können eine Kontextvariable auch mithilfe der **[Navigate](functions/function-navigate.md)**-Funktion festlegen, wenn ein Bildschirm angezeigt wird. Wenn Sie sich einen Bildschirm als eine Art Prozedur oder Unterroutine vorstellen, ist dies vergleichbar mit der Parameterübergabe in anderen Programmiersprachentools.
* Mit Ausnahme von **[Navigate](functions/function-navigate.md)** sind Kontextvariablen auf den Kontext eines einzelnen Bildschirms beschränkt, wo sie ihren Namen erhalten.  Außerhalb dieses Kontexts können Sie sie weder verwenden noch festlegen.
* Kontextvariablen können jeden Wert enthalten, z.B. Zeichenfolgen, Zahlen, Datensätze und [Tabellen](working-with-tables.md).

Erstellen Sie Ihren hinzufügenden Computer mithilfe einer Kontextvariablen neu:

1. Fügen Sie ein Texteingabe-Steuerelement mit dem Namen **TextInput1** hinzu, und zwei Schaltflächen mit dem Namen **Button1** und **Button2**.

2. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **Button1** auf **"Add"** fest, und legen Sie die **Text**-Eigenschaft von **Button2** auf **"Clear"** fest.

3. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft einer **Add**-Schaltfläche auf folgende Formel fest, um die laufende Summe zu aktualisieren, wenn ein Benutzer die Schaltfläche auswählt:
   
    **UpdateContext( { RunningTotal: RunningTotal + Text1 } )**
   
    Wenn ein Benutzer erstmals die **Add**-Schaltfläche auswählt, und **[UpdateContext](functions/function-updatecontext.md)** aufgerufen wird, wird **RunningTotal** mit einem Standardwert von *blank* erstellt.  Beim Hinzufügen wird es als eine 0 (null) behandelt.
   
    ![](media/working-with-variables/context-variable-1.png)
4. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft der **Clear**-Schaltfläche auf folgende Formel fest, um die laufende Summe auf **0** festzulegen:
   
    **UpdateContext( { RunningTotal: 0 } )**
   
    Hier wird **[UpdateContext](functions/function-updatecontext.md)** erneut mit der Formel **UpdateContext( { RunningTotal: 0 } )** verwendet.
   
    ![](media/working-with-variables/context-variable-2.png)
5. Fügen Sie ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](controls/properties-core.md)**-Eigenschaft auf **RunningTotal** fest.
   
    Diese Formel wird automatisch neu berechnet und zeigt dem Benutzer den Wert von **RunningTotal** an, während sie sich auf Grundlage der vom Benutzer ausgewählten Schaltflächen ändert.
   
    ![](media/working-with-variables/context-variable-3.png)
6. Sehen sie sich eine Vorschau der App an, und Sie sehen die Rechenmaschine, wie sie oben beschrieben wurde.  Geben Sie eine Zahl im Textfeld ein, und drücken Sie mehrmals die Schaltfläche **Add**.  Kehren Sie anschließend zur Erstellung zurück, indem Sie die ESC-TASTE drücken.  
   
    ![](media/working-with-variables/context-variable-4.png)
7. Sie können den Wert einer Kontextvariablen beim Wechsel zu einem Bildschirm festlegen.  Dies ist hilfreich, wenn Sie den „Kontext“ bzw. die „Parameter“ von einem Bildschirm an einen anderen übergeben möchten.  Um dies zu veranschaulichen, fügen Sie einen neuen Bildschirm ein, und fügen Sie eine Schaltfläche ein, deren **OnSelect**-Eigenschaft wie folgt festgelegt ist:
   
    **Navigate( Screen1, None, { RunningTotal: -1000 } )**
   
    ![](media/working-with-variables/context-variable-5.png)
   
    Bei Auswahl dieser Schaltfläche auf **Screen2** (dies kann während des Erstellens erfolgen, wenn Sie die Schaltfläche kurz vor Abschluss auswählen) wird **Screen1** angezeigt, und die Kontextvariable **RunningTotal** wird auf -1000 festgelegt.
   
    ![](media/working-with-variables/context-variable-6.png)
8. Um den Wert der Kontextvariablen anzuzeigen, wählen Sie das Menü **Datei** aus, und wählen Sie im linken Bereich **Variablen** aus.
   
    ![](media/working-with-variables/context-variable-file-1.png)
9. Wählen Sie die Kontextvariable aus, um festzustellen, an welchen Stellen sie definiert ist und verwendet wird.
   
    ![](media/working-with-variables/context-variable-file-2.png)

## <a name="create-a-collection"></a>Sammlung erstellen
Veranschaulichen wir abschließend das Erstellen der Rechenmaschine mithilfe einer Sammlung.  Da eine Sammlung eine Tabelle enthält, die leicht geändert werden kann, legen wir fest, dass diese Rechenmaschine bei Eingabe der einzelnen Werte einen „Papierstreifen“ des Werts aufbewahrt.

Funktionsweise von Sammlungen:

* Erstellen Sie Sammlungen mithilfe der **[ClearCollect](functions/function-clear-collect-clearcollect.md)**-Funktion, oder legen Sie diese fest.  Sie können stattdessen die **[Collect](functions/function-clear-collect-clearcollect.md)**-Funktion verwenden; jedoch erfordert diese eine andere Variable statt die alte lediglich zu ersetzen.  
* Eine Sammlung ist eine Art von Datenquelle und somit eine Tabelle. Verwenden Sie die **[First](functions/function-first-last.md)**-Funktion, um auf einen einzelnen Wert in einer Sammlung zuzugreifen, und extrahieren Sie ein Feld aus dem resultierenden Datensatz. Wenn Sie einen einzelnen Wert mit **[ClearCollect](functions/function-clear-collect-clearcollect.md)** verwendet haben, ist dies das **Value**-Feld, wie in diesem Beispiel:<br>**First(** *VariableName* **).Value**

Erstellen Sie Ihre Rechenmaschine mithilfe einer Sammlung neu:

1. Fügen Sie ein  **[Texteingabe](controls/control-text-input.md)**-Steuerelement mit dem Namen **TextInput1** hinzu, und zwei Schaltflächen mit dem Namen **Button1** und **Button2**.

2. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft von **Button1** auf **"Add"** fest, und legen Sie die **Text**-Eigenschaft von **Button2** auf **"Clear"** fest.

3. Legen Sie die **[OnSelect](controls/properties-core.md)**-Eigenschaft einer **Add**-Schaltfläche auf folgende Formel fest, um die laufende Summe zu aktualisieren, wenn ein Benutzer die Schaltfläche auswählt:
   
    **Collect( PaperTape, TextInput1.Text )**
   
    Mit dieser Formel wird der neue Wert am Ende der Sammlung hinzugefügt.  Da ein einzelner Wert hinzugefügt wird, platziert **Collect** diesen automatisch in einer Tabelle mit einer Spalte; diese Spalte heißt **Value**, und wir werden die Tabelle später verwenden.
   
    ![](media/working-with-variables/papertape-1.png)
4. Damit der Papierstreifen gelöscht wird, wenn der Benutzer die Schaltfläche **Clear** auswählt, legen Sie die zugehörige **[OnSelect](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **Clear( PaperTape )**
   
    ![](media/working-with-variables/papertape-2.png)
5. Fügen Sie eine Bezeichnung hinzu, um die laufende Summe anzuzeigen, und legen Sie ihre **[Text](controls/properties-core.md)**-Eigenschaft auf folgende Formel fest:
   
    **Sum( PaperTape, Value )**
   
    ![](media/working-with-variables/papertape-3.png)
6. Um die Rechenmaschine auszuführen, drücken Sie F5, um die Vorschau zu öffnen, geben Sie im Texteingabe-Steuerelement Zahlen ein, und wählen Sie Schaltflächen aus.
   
    ![](media/working-with-variables/papertape-run-1.png)
7. Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren.
8. Fügen Sie zum Anzeigen des Papierstreifens ein **Datentabellen**-Steuerelement hinzu, und legen Sie dessen **[Items](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **PaperTape**
   
    Sie müssen auch die Spalten auswählen, die im rechten Bereich angezeigt werden. In diesem Fall wird die Spalte **Value** angezeigt:
   
    ![](media/working-with-variables/papertape-4.png)
9. Wählen Sie im **Dateimenü** **Collections** (Sammlungen) aus, um die Werte in Ihrer Sammlung anzuzeigen.
   
    ![](media/working-with-variables/papertape-file.png)
10. Fügen Sie zum Speichern und Abrufen der Sammlung zwei weitere Schaltflächensteuerelemente hinzu, und legen Sie deren Text auf **Load** und **Save** fest.  Legen Sie für **Load** die **OnSelect**-Eigenschaft wie folgt fest:
    
     **Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )**
    
     Zuerst muss die Sammlung geleert werden, da **LoadData** die gespeicherten Werte an das Ende der Sammlung anfügt.
    
     ![](media/working-with-variables/papertape-5.png)
11. Legen Sie für **Save** die **OnSelect**-Eigenschaft wie folgt fest:
    
     **SaveData( PaperTape, "StoredPaperTape" )**
    
     ![](media/working-with-variables/papertape-6.png)
12. Drücken Sie erneut F5, um die Vorschau aufzurufen, geben Sie Zahlen im Textsteuerelement ein, und wählen Sie Schaltflächen aus.  Wählen Sie die Schaltfläche **Save** aus.  Schließen Sie die App, und laden Sie sie neu. Wählen Sie die Schaltfläche **Load** aus, um die Sammlung neu zu laden.  
    
    > [!NOTE]
    > **SaveData** und **LoadData** funktionieren in PowerApps Studio nicht, in PowerApps Mobile dagegen schon.

