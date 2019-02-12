---
title: Funktionen „Abs“, „Exp“, „Ln“, „Power“ und „Sqrt“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Abs“, „Sqrt“ und weitere Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/13/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 95406bff477a4d84a6125225ffc1e158ffb8c19a
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42827250"
---
# <a name="abs-exp-ln-power-and-sqrt-functions-in-powerapps"></a>Funktionen „Abs“, „Exp“, „Ln“, „Power“ und „Sqrt“ in PowerApps
Berechnen Absolutwerte, natürliche Logarithmen, Quadratwurzeln und die Ergebnisse der Potenzierung von *e* oder einer beliebigen Zahl zur angegebenen Potenz.

## <a name="description"></a>Beschreibung
Die Funktion **Abs** gibt den nicht negativen Wert ihres Arguments zurück. Wenn eine Zahl negativ ist, gibt **Abs** das positive Äquivalent zurück.

Die Funktion **Exp** gibt *e* zur Potenz ihres Arguments erhoben zurück.  Die transzendente Zahl *e* beginnt 2,7182818...

Die Funktion **Ln** gibt den natürlichen Logarithmus (zur Basis *e*) ihres Arguments zurück.

Die Funktion **Power** gibt eine zu einer Potenz erhobene Zahl zurück.  Sie ist mit der Verwendung des [**^**-Operators](operators.md) gleichbedeutend.

Die Funktion **Sqrt** gibt die Zahl zurück, die mit sich selbst multipliziert gleich ihrem Argument ist.

Wenn Sie eine einzelne Zahl übergeben, ist der Rückgabewert ein einzelnes Ergebnis, das auf der aufgerufenen Funktion basiert.  Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) übergeben, die Zahlen enthält, ist der Rückgabewert eine einspaltige Tabelle mit Ergebnissen, ein Ergebnis für jeden Datensatz in der Argumenttabelle. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.  

Wenn ein Argument zu einem nicht definierten Wert führen würde, ist das Ergebnis *leer*.  Dies kann z. B. bei Quadratwurzeln und Logarithmen von negativen Zahlen eintreten.

## <a name="syntax"></a>Syntax
**Abs**( *Zahl* )<br>**Exp**( *Zahl* )<br>**Ln**( *Zahl* )<br>**Sqrt**( *Zahl* )

* *Number*: erforderlich. Zahl, die verarbeitet wird.

**Power**( *Basis*, *Exponent* )

* *Basis*: erforderlich. Zu potenzierende Basiszahl.
* *Exponent*: erforderlich. Der Exponent, zu dem die Basiszahl potenziert wird.

**Abs**( *EinspaltigeTabelle* )<br>**Exp**( *EinspaltigeTabelle* )<br>**Ln**( *EinspaltigeTabelle* )<br>**Sqrt**( *EinspaltigeTabelle* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zahlen, die verarbeitet werden.

## <a name="examples"></a>Beispiele
### <a name="single-number"></a>Einzelne Zahl

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Abs( -55 )** |Gibt die Zahl ohne das negative Vorzeichen zurück. |55 |
| **Exp( 2 )** |Gibt die 2. Potenz von *e* zurück, also *e* \* *e*. |7,389056... |
| **Ln( 100 )** |Gibt den natürlichen Logarithmus (zur Basis *e*) der Zahl 100 zurück. |4,605170... |
| **Power( 5; 3 )** |Gibt die 3. Potenz von 5 zurück, also 5 \* 5 \* 5. |125 |
| **Sqrt( 9 )** |Gibt die Zahl zurück, die mit sich selbst multipliziert 9 ergibt. |3 |

### <a name="single-column-table"></a>Einspaltige Tabelle
Die Beispiele in diesem Abschnitt verwenden eine [Datenquelle](../working-with-data-sources.md), die als **Werttabelle** bezeichnet wird und diese Daten enthält:

![](media/function-numericals/values.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Abs(&nbsp;Werttabelle&nbsp;)** |Gibt den Absolutwert jeder Zahl in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-numericals/values-abs.png) |
| **Exp(&nbsp;Werttabelle&nbsp;)** |Gibt *e* potenziert mit jeder Zahl in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-numericals/values-exp.png) |
| **Ln(&nbsp;Werttabelle&nbsp;)** |Gibt den natürlichen Logarithmus der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-numericals/values-ln.png) |
| **Sqrt(&nbsp;Werttabelle&nbsp;)** |Gibt die Quadratwurzel der einzelnen Zahlen in der Tabelle zurück. |![](media/function-numericals/values-sqrt.png) |

### <a name="step-by-step-example"></a>Schritt-für-Schritt-Beispiel
1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement hinzu, und benennen Sie es **Source**.
2. Fügen Sie ein **Label**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>
   **Sqrt( Wert( Quelle.Text ) )**
3. Geben Sie eine Zahl in **Quelle** ein, und überprüfen Sie, ob das **Label**-Steuerelement (Bezeichnung) die Quadratwurzel der eingegebenen Zahl anzeigt.

