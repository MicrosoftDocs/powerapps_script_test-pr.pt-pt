---
title: Funktionen „If“ und „Switch“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „If“- und „Switch“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 40ac3089d3563d220ddac29197b0902f4de88a25
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836325"
---
# <a name="if-and-switch-functions-in-powerapps"></a>Die Funktionen „If“- und „Switch“ in PowerApps
Bestimmt, ob eine beliebige Bedingung in einer Menge TRUE ist (**If**) oder ob das Ergebnis einer Formel mit einem beliebigen Wert in einer Menge übereinstimmt (**Switch**) und gibt anschließend ein Ergebnis zurück oder führt eine Aktion aus.

## <a name="description"></a>Beschreibung
Die **If**-Funktion testet eine oder mehrere Bedingungen, bis das Ergebnis **TRUE** gefunden wird. Wenn ein solches Ergebnis gefunden wird, erfolgt die Rückgabe eines entsprechenden Werts. Wenn kein solches Ergebnis gefunden wird, erfolgt die Rückgabe eines Standardwerts. In beiden Fällen kann der zurückgegebene Wert eine zu zeigende Zeichenfolge, eine auszuwertende Formel oder eine andere Form von Ergebnis sein.

Die **Switch**-Funktion wertet eine Formel aus und bestimmt, ob das Ergebnis mit einem Wert in einer Sequenz übereinstimmt, die Sie angeben. Wenn eine Übereinstimmung gefunden wird, erfolgt die Rückgabe eines entsprechenden Werts. Wenn keine Übereinstimmung gefunden wird, erfolgt die Rückgabe eines Standardwerts. In beiden Fällen kann der zurückgegebene Wert eine zu zeigende Zeichenfolge, eine auszuwertende Formel oder eine andere Form von Ergebnis sein.

**If** und **Switch** sind sehr ähnlich, doch sollten Sie die beste Funktion für die jeweilige Situation verwenden:

* Verwenden Sie **If**, um eine einzelne Bedingung auszuwerten. Die gebräuchlichste Syntax für diese Funktion ist **If**( *Bedingung*, *ThenResult*, *DefaultResult* ), die das gängige Muster „if ...  then … else ...“ bereitstellt, das Sie aus anderen Programmiersprachen kennen.
* Verwenden Sie **If**, um mehrere unabhängige Bedingungen auszuwerten. In PowerApps können Sie (im Gegensatz zu Microsoft Excel) mehrere Bedingungen angegeben, ohne **If**-Formeln schachteln zu müssen.
* Verwenden Sie **Switch**, um eine einzelne Bedingung im Abgleich mit mehreren möglichen Übereinstimmungen auszuwerten. Sie können auch in diesem Fall **If** verwenden, doch dann müssen Sie die Formel für jede mögliche Übereinstimmung wiederholen.

Sie können diese beiden Formeln in [Verhaltensformeln](../working-with-formulas-in-depth.md) verwenden, um eine Verzweigung zwischen zwei oder mehr Aktionen zu erstellen. Nur eine Verzweigung löst eine Aktion aus. Bedingungen und Übereinstimmungen werden in der Reihenfolge ausgewertet und angehalten, wenn eine Bedingung **TRUE** ist oder eine Übereinstimmung gefunden wird.

*Blank* wird zurückgegeben, wenn keine Bedingungen **TRUE** sind, keine Übereinstimmungen gefunden werden und Sie kein Standardergebnis angeben.

## <a name="syntax"></a>Syntax
**If**( *Condition*, *ThenResult* [, *DefaultResult* ] )<br>**If**( *Condition1*, *ThenResult1* [, *Condition2*, *ThenResult2*, ... [ , *DefaultResult* ] ] )

* *Condition(s)*: Erforderlich. Auf **TRUE** zu testende Formeln. Solche Formeln enthalten häufig Vergleichs-[Operatoren](operators.md) (z.B. **<** ,  **>** und **=**) sowie Testfunktionen wie **[IsBlank](function-isblank-isempty.md)** und **[IsEmpty](function-isblank-isempty.md)** .
* *ThenResult(s*: Erforderlich. Der entsprechende Wert für eine Bedingung, die **TRUE** ergibt, soll zurückgegeben werden.
* *DefaultResult*: Optional. Dies ist der zurückzugebende Wert, wenn keine Bedingung mit **TRUE** ausgewertet wird.  Wenn Sie dieses Argument nicht angeben, wird *blank* zurückgegeben.

**Switch**( *Formel*, *Übereinstimmung1*, *Ergebnis1* [, *Übereinstimmung2*, *Ergebnis2*, ... [, *DefaultResult* ] ] )

* *Formula*: Erforderlich. Die für Übereinstimmungen auszuwertende Formel.  Diese Formel wird nur einmal ausgewertet.
* *Übereinstimmung(en)*: Erforderlich. Werte für einen Vergleich mit dem Ergebnis der *Formel*.  Wird eine genaue Übereinstimmung gefunden, wird das entsprechende *Ergebnis* zurückgegeben.
* *Ergebnis(se)*: Erforderlich. Der entsprechende Wert, der zurückgegeben wird, wenn eine genaue Übereinstimmung gefunden wird.
* *DefaultResult*: Optional. Wenn keine genaue Übereinstimmung gefunden wird, wird dieser Wert zurückgegeben. Wenn Sie dieses Argument nicht angeben, wird *blank* zurückgegeben.

## <a name="examples"></a>Beispiele
### <a name="values-in-formulas"></a>Werte in Formeln
In den folgenden Beispielen wird ein **Schieberegler**-Steuerelement mit dem Namen **Slider1** mit dem Wert **25** verwendet.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1" )** |Für die Bedingung gilt **TRUE**, und das entsprechende Ergebnis wird zurückgegeben. |"Result1" |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", "Result2" )** |Für die Bedingung gilt **TRUE**, und das entsprechende Ergebnis wird zurückgegeben. |"Result1" |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1" )** |Die Bedingung ist **FALSE**, und es wird kein *Standardergebnis* bereitgestellt. |*blank* |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", "Result2" )** |Die Bedingung ist **FALSE**, ein *Standardergebnis* wurde bereitgestellt und wird zurückgegeben. |"Result2" |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", Slider1.Value&nbsp;>&nbsp;0, "Result2" )** |Die erste Bedingung ergibt **TRUE**, und das entsprechende Ergebnis wird zurückgegeben. Die zweite Bedingung ist auch **TRUE**, aber sie wird nicht ausgewertet, weil sie später in der Argumentliste als eine Bedingung vorkommt, die mit **TRUE** auswertet wird. |"Result1" |
| **If( IsBlank(&nbsp;Slider1.Value&nbsp;), "Result1", IsNumeric(&nbsp;Slider1.Value&nbsp;), "Result2" )** |Die erste Bedingung ergibt **FALSE**, weil der Schieberegler nicht *blank* ist. Die zweite Bedingung ergibt **TRUE**, da der Wert des Schiebereglers eine Zahl ist und das entsprechende Ergebnis zurückgegeben wird. |"Result2" |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", Slider1.Value&nbsp;>&nbsp;50, "Result2", "Result3")** |Die erste und zweite Bedingung ergeben **FALSE**, ein *Standardergebnis* wurde bereitgestellt und wird zurückgegeben. |"Result3" |
| **Switch (Slider1.Value, 25, "Result1")** |Der Wert des Schiebereglers entspricht dem ersten Wert, der überprüft werden soll, und das entsprechende Ergebnis wird zurückgegeben. |"Result1" |
| **Switch( Slider1.Value, 20, "Result1", 25, "Result2", 30, "Result3" )** |Der Wert des Schiebereglers entspricht dem zweiten Wert, der überprüft werden soll, und das entsprechende Ergebnis wird zurückgegeben. |"Result2" |
| **Switch( Slider1.Value, 20, "Result1", 10, "Result2", 0, "Result3", "DefaultResult" )** |Der Wert des Schiebereglers stimmt mit keinem zu überprüfenden Wert überein.  Ein *DefaultResult* (Standardergebnis) wurde bereitgestellt, das zurückgegeben wird. |"DefaultResult" |

### <a name="branching-in-behavior-formulas"></a>Verzweigungen in Verhaltensformeln
In den folgenden Beispielen enthält ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement mit dem Namen **FirstName** den Wert „John“.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **If (! IsBlank( FirstName.Text ), Navigate(&nbsp;Screen1, ScreenTransition.None ) )** |Die Bedingung ergibt **TRUE**, weshalb die  **[Navigate](function-navigate.md)**-Funktion ausgeführt wird. Sie können die **[IsBlank](function-isblank-isempty.md)**-Funktion verwenden, um zu testen, ob ein erforderliches Formularfeld ausgefüllt wurde.  Falls **FirstName** [leer](function-isblank-isempty.md) wäre, hätte diese Formel keine Auswirkung. |**TRUE**<br><br>Die Anzeige wird zu **Screen1** geändert. |
| **If( IsBlank( FirstName.Text ), Navigate(&nbsp;Screen1, ScreenTransition.None ), Back() )** |Ohne den Operator **!** ergibt die Bedingung den Wert **FALSE**, sodass die **[Navigate](function-navigate.md)**-Funktion nicht ausgeführt wird. Der **[Back](function-navigate.md)**-Funktion wurde ein *Standardergebnis* bereitgestellt, sodass sie ausgeführt wird. |**TRUE**<br><br>Die Anzeige wird auf den Bildschirm zurückgesetzt, der zuvor angezeigt wurde. |
| **Switch( FirstName.Text, "Carlos", Navigate(&nbsp;Screen1, ScreenTransition.None ), "Kirstin", Navigate( Screen2, ScreenTransition.None ), "John", Navigate( Screen3, ScreenTransition.None ) )** |Der Wert von **FirstName.Text** wird mit „Carlos“, „Kirstin“ und „John“ (in dieser Reihenfolge) verglichen. Eine Übereinstimmung mit „John“ wird gefunden, weshalb die App zu **Screen3** navigiert. |**TRUE**<br><br>Die Anzeige wird in **Screen3** geändert. |

### <a name="step-by-step"></a>Schritt für Schritt
1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement hinzu, und nennen Sie es **Text1**, wenn es diesen Namen nicht bereits standardmäßig hat.
2. Geben Sie in **Text1** den Wert **30** ein.
3. Fügen Sie ein **Label**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **If( Value(Text1.Text) < 20, "Viel mehr bestellen!", Value(Text1.Text) < 40, "Mehr bestellen!", Text1.Text )**
   
    Das **Bezeichnung**-Steuerelement zeigt **Mehr bestellen!**, da der Wert von **Text1** größer als 20, aber kleiner als 40 ist.
4. Geben Sie in **Text1** den Wert **15** ein.
   
    Das **Bezeichnung**-Steuerelement zeigt **VIELE mehr bestellen!**, da der Wert von **Text1** kleiner als 20 ist.
5. Geben Sie in **Text1** den Wert **50** ein.
   
    Das **Bezeichnung**-Steuerelement zeigt den Wert, den Sie eingegeben haben, da er größer als 40 ist.

