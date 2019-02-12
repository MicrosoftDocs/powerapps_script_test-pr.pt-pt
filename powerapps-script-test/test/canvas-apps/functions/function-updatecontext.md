---
title: Funktion „UpdateContext“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „UpdateContext“ in PowerApps
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
ms.openlocfilehash: 6f89887d05f4b4885e66335457357a089ceaf90f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865507"
---
# <a name="updatecontext-function-in-powerapps"></a>Funktion „UpdateContext“ in PowerApps
Erstellt oder aktualisiert die [Kontextvariablen](../working-with-variables.md#create-a-context-variable) des aktuellen Bildschirms.

## <a name="overview"></a>Übersicht
Verwenden Sie die **UpdateContext**-Funktion zum Erstellen einer Kontextvariablen, die vorübergehend eine Information enthält, wie z.B. wie oft ein Benutzer auf eine Schaltfläche geklickt hat oder das Ergebnis eines Datenvorgangs.

Kontextvariablen beziehen sich auf einem Bildschirm, was bedeutet, dass eine Formel, die auf eine Kontextvariable auf einem anderen Bildschirm verweist, nicht erstellt werden kann. Wenn Sie eine anderes Programmiertool verwendet haben, können Sie sich eine Kontextvariable wie eine lokale Variable vorstellen.  Verwenden Sie die [**Set**-Funktion ](function-set.md), um mit globalen Variablen zu arbeiten, die in der App verfügbar sind.  

PowerApps basiert auf Formeln, die automatisch neu berechnet werden, während der Benutzer mit einer App interagiert.  Kontextvariablen haben nicht diesen Vorteil und können das Erstellen und Verstehen Ihrer App erschweren.  Konsultieren Sie vor der Verwendung einer Kontextvariablen den Artikel [Working with Variables (Mit Variablen arbeiten)](../working-with-variables.md).

## <a name="description"></a>Beschreibung
Übergeben Sie zum Erstellen oder Aktualisieren einer Kontextvariable einen einzelne [Datensatz](../working-with-tables.md#records) an die **UpdateContext**-Funktion. Geben Sie in jedem Datensatz den Namen einer [Spalte](../working-with-tables.md#columns) an, die den Namen der Variablen und den festzulegenden Wert definiert oder diesem entspricht.

* Wenn Sie den Namen einer Variablen, die Sie zuvor festgelegt haben, angeben, legt **UpdateContext** den Wert der Variablen auf den Wert fest, den Sie angeben.
* Wenn Sie den Namen einer Variablen, die noch nicht vorhanden ist, angeben, erstellt **UpdateContext** eine Variable mit diesem Namen und legt den Wert dieser Variablen auf den Wert fest, den Sie angeben.
* Wenn Sie zuvor eine Variable definiert haben, aber diese nicht in dieser **UpdateContext**-Formel angeben haben, bleibt deren Wert unverändert.

Kontextvariablen werden implizit mithilfe der **UpdateContext**- oder der [**Navigate**-Funktion](function-navigate.md) erstellt.  Eine explizite Deklaration ist nicht erforderlich.  Wenn Sie sämtliche Verweise von **UpdateContext** und **Navigate** auf eine Kontextvariable entfernen, ist die betreffende Kontextvariable nicht mehr vorhanden.  Legen Sie zum Leeren einer Variablen ihren Wert auf das Ergebnis der [**Blank**-Funktion](function-isblank-isempty.md) fest.

Sie können die Werte, Definitionen und Verwendungen Ihrer Variablen in der Ansicht „Variablen“ unter dem Menü „Datei“ in der Erstellungsumgebung anzeigen.

Sie verweisen anhand des Spaltennamens der Variablen auf eine Kontextvariable in einer Formel. **UpdateContext( { ShowLogo: true } )** erstellt z.B. eine Kontextvariable mit dem Namen **ShowLogo** und legt deren Wert auf **TRUE** fest. Anschließend können Sie den Wert dieser Kontextvariablen mit dem Namen **ShowLogo** in einer Formel verwenden.  Sie können **ShowLogo** als Formel für die Eigenschaft **Visible** eines Bildsteuerelements schreiben und dieses Steuerelement anzeigen oder verbergen, abhängig davon, ob der Wert der Variable **TRUE** oder **FALSE** ist.

Wie in den Beispielen weiter unten in diesem Thema gezeigt, können Kontextvariablen verschiedene Arten von Informationen enthalten, u.a. folgende:

* einen einzelnen Wert
* einen Datensatz
* eine Tabelle
* einen Objektverweis
* jedes Ergebnis einer Formel

Eine Kontextvariable behält ihren Wert bei, bis die App geschlossen wird.  Wenn Sie eine Kontextvariable definieren und Sie deren Wert auf einem bestimmten Bildschirm festlegen, bleibt diese Informationen erhalten, selbst wenn der Benutzer zu einem anderen Bildschirm wechselt.  Sobald die App geschlossen wird, geht der Wert der Kontextvariablen verloren; er muss neu erstellt werden, wenn die App wieder geladen wird.  

Jede Kontextvariable ist auf einen Bildschirm begrenzt. Wenn Sie eine Kontextvariable auf einem Bildschirm definieren und diese Variable auf einem anderen Bildschirm ändern möchten, müssen Sie eine Formel basierend auf der **[Navigate](function-navigate.md)**-Funktion erstellen.  Sie können auch eine globale Variable verwenden.

**UpdateContext** weist keinen Rückgabewert auf; Sie können diese Funktion nur innerhalb einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**UpdateContext**( *UpdateRecord* )

* *UpdateRecord*: erforderlich. Ein Datensatz, der den Namen von mindestens eine Spalte und eine Wert für diese Spalte enthält. Eine Kontextvariable wird für jede Spalte und den von Ihnen angegebenen Wert erstellt oder aktualisiert.

**UpdateContext**( { *ContextVariable1*: *Value1* [, *ContextVariable2*: *Value2* [, ... ] ] } )

* *Kontextvariable1*: erforderlich.  Der Name der zu erstellenden oder zu aktualisierenden Kontextvariablen
* *Wert1*: erforderlich.  Der der Kontextvariablen zuzuweisende Wert
* *Kontextvariable2*: *Wert2*,...: optional. Zusätzliche zu erstellende oder zu aktualisierende Kontextvariablen und deren Werte

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **UpdateContext( {&nbsp;Counter:&nbsp;1&nbsp;} )** |Erstellt oder ändert die **Counter**-Kontextvariable und legt deren Wert auf **1** fest |**Counter** hat den Wert **1**. Mit dem Namen **Counter** können Sie in einer Formel auf diese Variable verweisen. |
| **UpdateContext( {&nbsp;Counter:&nbsp;2&nbsp;} )** |Legt den Wert für die **Counter**-Kontextvariable aus dem vorherigen Beispiel auf **2** fest |**Counter** hat den Wert **2**. |
| **UpdateContext( {&nbsp;Name:&nbsp;"Lily",&nbsp;Score:&nbsp;10&nbsp;} )** |Erstellt oder ändert die Kontextvariablen **Name** und **Score** und legt deren Werte auf **Lily** bzw. **10** fest. |**Name** hat den Wert **Lily**, und **Score** hat den Wert **10**. |
| **UpdateContext( {&nbsp;Person:&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;} )** |Erstellt oder ändert die Kontextvariable **Person** und legt deren Wert auf einen Datensatz fest. Der Datensatz enthält zwei Spalten mit den Namen **Name** und **Address**. Der Wert der **Name**-Spalte ist **Milton**, und der Wert der **Address**-Spalte ist **1 Main St**. |**Person** hat den Wert des Datensatzes **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}**.<br><br>Verweisen Sie mit dem Namen **Person** auf den kompletten Datensatz, oder verweisen Sie auf eine einzelne Spalte dieses Datensatzes mit **Person.Name** oder **Person.Address**. |
| **UpdateContext( {&nbsp;Person: Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;) }&nbsp;)** |Arbeitet mit der **[Patch](function-patch.md)**-Funktion zusammen, um die **Person**-Kontextvariable durch Festlegen des Werts von der **Address**-Spalte auf **2 Main St** zu aktualisieren. |**Person** hat nun den Wert des Datensatzes **{&nbsp;Name:&nbsp;"Milton", Adresse:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}**. |

### <a name="step-by-step-example"></a>Schritt-für-Schritt-Beispiel
1. Benennen Sie den Bildschirm **Quelle**, fügen Sie einen anderen Bildschirm hinzu, und nennen Sie diesen **Ziel**.
2. Fügen Sie auf dem Bildschirm **Quelle** zwei Schaltflächen hinzu, und legen Sie ihre **[Text](../controls/properties-core.md)**-Eigenschaften so fest, dass eine **Englisch** und die andere **Spanisch** ist.
3. Legen Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft der Schaltfläche **Englisch** auf folgenden Ausdruck fest:<br>**Navigate(Target, ScreenTransition.Fade, {Language:"English"})**
4. Legen Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft der Schaltfläche **Spanisch** auf folgenden Ausdruck fest:<br>**Navigate(Target, ScreenTransition.Fade, {Language:"Spanish"})**
5. Fügen Sie auf dem Bildschirm **Ziel** eine Bezeichnung hinzu, und legen deren **[Text](../controls/properties-core.md)**-Eigenschaft auf folgenden Ausdruck fest:<br>**If(Language="English", "Hello!", "Hola!")**
6. Wählen Sie auf dem Bildschirm **Ziel** auf der Registerkarte **Einfügen** **Shapes** (Formen) aus, und wählen Sie dann den Rückwärtspfeil.
7. Legen Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft des Rückwärtspfeils auf folgende Formel fest:<br>**Navigate(Source, ScreenTransition.Fade)**
8. Drücken Sie auf dem Bildschirm **Quelle** F5, und wählen Sie dann die Schaltfläche für eine der beiden Sprachen.

    Auf dem Bildschirm **Ziel** wird eine Bezeichnung in der Sprache angezeigt, die mit der von Ihnen ausgewählten Schaltfläche übereinstimmt.
9. Wählen Sie den Rückwärtspfeil, um wieder zum Bildschirm **Quelle** zu gelangen, und wählen Sie dann die Schaltfläche für die andere Sprache.

    Auf dem Bildschirm **Ziel** wird eine Bezeichnung in der Sprache angezeigt, die mit der von Ihnen ausgewählten Schaltfläche übereinstimmt.
10. Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren.

[Ein weiteres Beispiel](../add-screen-context-variables.md)

