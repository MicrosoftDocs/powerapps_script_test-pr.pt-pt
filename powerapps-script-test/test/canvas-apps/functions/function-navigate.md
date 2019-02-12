---
title: Funktionen „Back“ und „Navigate“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Back“ und „Navigate“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/08/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bf656c33bcfdc0114c1ff44936dd38fc7145158e
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42857083"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Funktionen „Back“ und „Navigate“ in PowerApps
Ändern, welcher Bildschirm angezeigt wird

## <a name="overview"></a>Übersicht
Die meisten Apps umfassen mehrere Bildschirme.  Verwenden Sie die Funktionen **Back** und **Navigate**, um zu ändern, welcher Bildschirm angezeigt wird. Legen Sie z.B. die **[OnSelect](../controls/properties-core.md)**-Eigenschaft einer Schaltfläche auf eine Formel fest, die eine **Navigate**-Funktion enthält, wenn Sie einen anderen Bildschirm anzeigen möchten, wenn ein Benutzer diese Schaltfläche auswählt. In dieser Formel können Sie einen visuellen Übergang, wie z.B. **Fade** angeben, um zu steuern, wie ein Bildschirm zu einem anderen Bildschirm wechselt.  

Die Funktionen **Back** und **Navigate** ändern nur, welcher Bildschirm angezeigt wird. Bildschirme, die momentan nicht angezeigt werden, werden weiterhin im Hintergrund ausgeführt. Sie können Formeln erstellen, die sich auf Eigenschaften von Steuerelementen auf einem anderen Bildschirm beziehen. Beispielsweise kann ein Benutzer den Wert des Schiebereglers auf einem Bildschirm ändern, zu einem anderen Bildschirm navigieren, der diesen Wert in einer Formel verwendet, und sehen, wie sich dies darauf auswirkt, was auf dem neuen Bildschirm geschieht.  Der Benutzer kann dann wieder zum ursprünglichen Bildschirm zurück navigieren und sehen, dass der Wert des Schiebereglers beibehalten wurde.

[Kontextvariablen](../working-with-variables.md#create-a-context-variable) werden ebenfalls beibehalten, wenn ein Benutzer zwischen Bildschirmen navigiert. Sie können **Navigate** verwenden, um eine oder mehrere Kontextvariablen für den Bildschirm festzulegen, den die Formel anzeigen wird. Dies ist die einzige Möglichkeit, von außerhalb des Bildschirms eine Kontextvariable festzulegen. Sie können diesen Ansatz verwenden, um Parameter an einen Bildschirm zu übergeben. Wenn Sie ein anderes Programmiertool verwendet haben, ähnelt diese Vorgehensweise der Übergabe von Parametern an Prozeduren.

## <a name="description"></a>Beschreibung
### <a name="back"></a>Back
Die Funktion **Back** zeigt den Bildschirm an, der zuletzt angezeigt wurde. Sie geben keine Argumente für diese Funktion an.

### <a name="navigate"></a>Navigate
Geben Sie im ersten Argument den Namen des Bildschirms an, der angezeigt werden soll.  

 Geben Sie im zweiten Argument an, wie der alte Bildschirm auf den neuen Bildschirm wechselt:

| „Transition“-Argument | Beschreibung |
| --- | --- |
| **ScreenTransition.Cover** |Der neue Bildschirm gleitet in die Ansicht und deckt dabei den aktuellen Bildschirm ab. |
| **ScreenTransition.Fade** |Der alte Bildschirm wird ausgeblendet, um den neuen Bildschirm anzuzeigen. |
| **ScreenTransition.None** |Der alte Bildschirm wird schnell durch den neuen Bildschirm ersetzt. |
| **ScreenTransition.UnCover** |Der alte Bildschirm gleitet aus der Ansicht und löst dabei die Abdeckung des neuen Bildschirms. |

Sie können **Navigate** verwenden, um Kontextvariablen des neuen Bildschirms zu erstellen oder zu aktualisieren. Als optionales drittes Argument übergeben Sie einen [Datensatz](../working-with-tables.md#records), der den Kontextvariablennamen als [Spaltennamen](../working-with-tables.md#columns) sowie den neuen Wert für die Kontextvariable enthält.  Dieser Datensatz ist identisch mit dem Datensatz, den Sie mit der **[UpdateContext](function-updatecontext.md)**-Funktion verwenden.

Legen Sie die **[OnHidden](../controls/control-screen.md)**-Eigenschaft des alten Bildschirms, die **[OnVisible](../controls/control-screen.md)**-Eigenschaft des neuen Bildschirms oder beide fest, um während des Übergangs zusätzliche Änderungen vorzunehmen. Die **App.ActiveScreen**-Eigenschaft wird aktualisiert, um die Änderung zu übernehmen.

**Back** gibt in der Regel **TRUE** zurück, gibt jedoch **FALSE** zurück, wenn sich der Benutzer auf dem ersten angezeigten Bildschirm befindet und es keinen vorherigen Bildschirm gibt.  **Navigate** gibt in der Regel **TRUE** zurück, gibt jedoch **FALSE** zurück, wenn ein Problem mit einem der Argumente vorliegt.

Sie können diese Funktionen nur in einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**Back**()

**Navigate**( *Bildschirm*, *Übergang* [, *Kontextaktualisierungs-Datensatz* ] )

* *Bildschirm*: Erforderlich. Der anzuzeigende Bildschirm.
* *Übergang*: Erforderlich.  Der visuelle Übergang, der zwischen dem aktuellen Bildschirm und dem nächsten Bildschirm verwendet werden soll. Weitere Informationen finden Sie in der Liste der gültigen Werte für dieses Argument weiter oben in diesem Thema.
* *Kontextaktualisierungs-Datensatz*: Optional.  Ein Datensatz, der den Namen mindestens einer Spalte und einen Wert für jede Spalte enthält. Dieser Datensatz aktualisiert die Kontextvariablen des neuen Bildschirms wie bei der Übergabe an die **[UpdateContext](function-updatecontext.md)**-Funktion.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Navigate( Details, ScreenTransition.None )** |Zeigt den **Detailbildschirm** ohne Übergang oder Änderung des Werts einer Kontextvariablen an. |Der **Detailbildschirm** erscheint schnell. |
| **Navigate( Details, ScreenTransition.Fade )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an.  Kein Wert einer Kontextvariablen wird geändert. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an und aktualisiert den Wert der Kontextvariable **ID** auf **12**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen, und die Kontextvariable **ID** auf diesem Bildschirm wird auf **12** festgelegt. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an. Aktualisiert den Wert der Kontextvariable **ID** auf **12** und aktualisiert den Wert der Kontextvariable **Shade** auf **Color.Red**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. Die Kontextvariable **ID** auf dem **Detailbildschirm** wird auf **12** festgelegt, und die Kontextvariable **Shade** wird auf **Color.Red** festgelegt. Wenn Sie die **Fill**-Eigenschaft eines Steuerelements auf dem **Detailbildschirm** auf **Shade** festlegen, würde dieses Steuerelement rot angezeigt werden. |

### <a name="step-by-step"></a>Schritt für Schritt
1. Benennen Sie den Standardbildschirm **DefaultScreen**, fügen Sie eine Bezeichnung zu ihm hinzu, und legen Sie die **[Text](../controls/properties-core.md)**-Eigenschaft dieser Bezeichnung so fest, dass diese **Default** anzeigt.
2. Fügen Sie einen Bildschirm hinzu, und nennen Sie diesen **AddlScreen**.
3. Fügen Sie eine Bezeichnung zu **AddlScreen** hinzu, und legen Sie die **[Text](../controls/properties-core.md)**-Eigenschaft der Bezeichnung so fest, dass diese **Addl** anzeigt.
4. Fügen Sie eine Schaltfläche zu **AddlScreen** hinzu, und legen Sie ihre **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br>**Navigate(DefaultScreen, ScreenTransition.Fade)**
5. Drücken Sie von **AddlScreen** aus auf F5, und wählen Sie anschließend die Schaltfläche aus.<br>**DefaultScreen** wird angezeigt.

[Ein weiteres Beispiel](../add-screen-context-variables.md)

