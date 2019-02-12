---
title: IfError-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die IfError-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b3d80c2bafb36bf4437a9c37541f5bb56945f3b4
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42851320"
---
# <a name="iferror-function-in-powerapps"></a>IfError-Funktion in PowerApps
Erkennt Fehler und stellt einen Alternativwert bereit oder führt eine Aktion aus.

## <a name="description"></a>Beschreibung
> [!NOTE]
> Diese Funktion ist Teil eines experimentellen Features, das möglicherweise in Zukunft überarbeitet wird.  Das hier beschriebene Verhalten ist nur verfügbar, wenn das Feature *Formula-level error management* (Fehlerverwaltung auf Formelebene) aktiviert ist.  Dabei handelt es sich um eine Einstellung auf App-Ebene, die standardmäßig deaktiviert ist.  Navigieren Sie zum Aktivieren des Features zuerst zur Registerkarte *Datei* und anschließend im linken Menü zu *App-Einstellungen* und *Experimentelle Features*.  Wir sind sehr an Ihrem Feedback interessiert und würden uns freuen, wenn Sie uns in den [PowerApps-Communityforen](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To) Ihre Meinung mitteilen würden.

Die **IfError**-Funktion überprüft nacheinander jedes Argument auf einen Fehlerwert und stoppt, sobald ein Wert auftritt, bei dem es sich nicht um einen Fehler handelt.  Die nachfolgenden Argumente werden ignoriert und nicht ausgewertet.

Verwenden Sie **IfError**, um Fehlerwerte durch gültige Werte zu ersetzen.  Wenn beispielsweise eine Benutzereingabe zu einer Division durch null führen kann, können Sie die Eingabe durch null oder einen anderen gültigen Wert ersetzen, der für Ihre App geeignet ist, sodass nachfolgende Berechnungen fortgesetzt werden können.

Verwenden Sie **IfError** in [Verhaltensformeln](../working-with-formulas-in-depth.md), um Aktionen auszuführen, Ergebnisse auf Fehler zu überprüfen und ggf. weitere Aktionen auszuführen oder mit [**Notify**](function-showerror.md) Fehlermeldungen für den Benutzer auszugeben.

Wenn alle Argumente für **IfError** zu einem Fehler führen, wird der Wert des letzten Arguments (also ein Fehlerwert) zurückgegeben. 

## <a name="syntax"></a>Syntax
**IfError**( *Wert*, *Ausweichformel1* [, *Ausweichformel2*, ... ] )

* *Value*: Erforderlich. Ein oder mehrere Formeln, die auf einen Fehlerwert geprüft werden. 
* *Ausweichformel(n)*: erforderlich. Die auszuwertenden Formeln und zurückzugebenden Werte, wenn für vorherige Argumente ein Fehler zurückgegeben wurde.  Die *Ausweichargumente* werden nacheinander ausgewertet, bis ein Wert gefunden wird, der kein Fehlerwert ist.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **IfError( 1, 2 )** |Das erste Argument ist kein Fehlerwert.  Es wird zurückgegeben, und nachfolgende Argumente werden nicht ausgewertet.   | 1 |
| **IfError( 1/0, 2 )** | Für das erste Argument wird ein Fehlerwert zurückgegeben (aufgrund der Division durch null).  Das zweite Argument wird ausgewertet. Der Wert ist kein Fehlerwert und wird zurückgegeben. | 2 | 
| **IfError( 1/0, Notify( "There was an internal problem", NotificationType.Error ) )** | Für das erste Argument wird ein Fehlerwert zurückgegeben (aufgrund der Division durch null).  Das zweite Argument wird ausgewertet, und dem Benutzer wird eine Fehlermeldung angezeigt.  Der Rückgabewert von **IfError** ist der Rückgabewert von **Notify** und wird in denselben Typ wie das erste Argument für **IfError** (eine Zahl) umgewandelt. | 1 |
| **IfError( 1/0, 1/0, 2, 1/0, 3 )** | Für das erste Argument wird ein Fehlerwert zurückgegeben (aufgrund der Division durch null).  Das zweite Argument wird ausgewertet und führt ebenfalls zu einem Fehlerwert (aufgrund einer weiteren Division durch null).  Das dritte Argument wird ausgewertet. Der Wert ist kein Fehlerwert und wird zurückgegeben.  Die Argumente vier und fünf werden ignoriert.  | 2 |

### <a name="step-by-step"></a>Schritt für Schritt

1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement hinzu, und nennen Sie es **TextEingabe1**, wenn es nicht standardmäßig so benannt ist.

2. Fügen Sie ein **[Label](../controls/control-text-box.md)**-Steuerelement hinzu, und nennen Sie es **Label1**, wenn es nicht standardmäßig so benannt ist.

3. Legen Sie für die **Text**-Eigenschaft von **Label1** die folgende Formel fest:

    **IfError( Value( TextEingabe1.Text ), -1 )**

4. Geben Sie in **TextEingabe1** die Zeichenfolge **1234** ein.  

    Für Label1 wird der Wert **1234** angezeigt, da es sich um eine gültige Eingabe für die Value-Funktion handelt.

5. Geben Sie in **TextEingabe1** die Zeichenfolge **ToInfinity** ein.

    Für Label1 wird der Wert **-1** angezeigt, da es sich nicht um eine gültige Eingabe für die Value-Funktion handelt.  Wenn die Value-Funktion nicht von IfError umschlossen wäre, würde für das Label kein Wert angezeigt werden, da der Fehlerwert als *leerer Wert* interpretiert würde. 

