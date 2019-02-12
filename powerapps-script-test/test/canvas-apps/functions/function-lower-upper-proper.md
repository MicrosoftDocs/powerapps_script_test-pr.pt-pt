---
title: Funktionen „Lower“, „Upper“ und „Proper“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Lower-, Upper- und Proper-Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 72e1bd234a9cbccc24cf35723ee10bacd175b278
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865829"
---
# <a name="lower-upper-and-proper-functions-in-powerapps"></a>Lower-, Upper- und Proper-Funktionen in PowerApps
Konvertiert Buchstaben in einer Textzeichenfolge in alle Kleinbuchstaben, Großbuchstaben oder den richtigen Fall.

## <a name="description"></a>Beschreibung
Die Funktionen **Lower**, **Upper**, und **Proper** konvertieren, die Groß-/Kleinschreibung in Zeichenfolgen.

* **Lower** konvertiert alle Großbuchstaben in Kleinbuchstaben.
* **Upper** konvertiert alle Kleinbuchstaben in Großbuchstaben.
* **Proper** konvertiert den ersten Buchstaben jedes Worts in Großbuchstaben, wenn es Kleinbuchstaben sind, und andere Großbuchstaben in Kleinbuchstaben.

Alle drei Funktionen ignorieren Zeichen, die nicht aus Buchstaben bestehen.

Wenn Sie eine einzelne Zeichenfolge übergeben, ist der Rückgabewert die konvertierte Version dieser Zeichenfolge.  Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) übergeben, die Zeichenfolgen enthält, ist der Rückgabewert eine einspaltige Tabelle mit konvertierten Zeichenfolgen. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

## <a name="syntax"></a>Syntax
**Lower**( *Zeichenfolge* )<br>**Upper**( *Zeichenfolge* )<br>**Proper**( *Zeichenfolge* )

* *Zeichenfolge*: erforderlich. Die zu konvertierende Zeichenfolge

**Lower**( *EinspaltigeTabelle* )<br>**Upper**( *EinspaltigeTabelle* )<br>**Proper**( *EinspaltigeTabelle* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die konvertiert werden soll.

## <a name="examples"></a>Beispiele
### <a name="single-string"></a>Einzelne Zeichenfolge
In den Beispielen in diesem Abschnitt wird ein Texteingabe-Steuerelement mit dem Namen **Author** als [Datenquelle](../working-with-data-sources.md) verwendet. Das Steuerelement enthält die Zeichenfolge „E. E. CummINGS“.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Lower(&nbsp;Author.Text&nbsp;)** |Konvertiert alle Großbuchstaben in der Zeichenfolge in Kleinbuchstaben. |„e. e. cummings“ |
| **Upper(&nbsp;Author.Text&nbsp;)** |Konvertiert alle Kleinbuchstaben in der Zeichenfolge in Großbuchstaben. |„E. E. CUMMINGS“ |
| **Proper(&nbsp;Author.Text&nbsp;)** |Konvertiert den ersten Buchstaben jedes Worts in Großbuchstaben, wenn es Kleinbuchstaben sind, und andere Großbuchstaben in Kleinbuchstaben. |„E. E. Cummings“ |

### <a name="single-column-table"></a>Einspaltige Tabelle
Die Beispiele in diesem Abschnitt konvertieren Zeichenfolgen aus der [Spalte](../working-with-tables.md#columns) **Address** der Datenquelle **People**, die diese Daten enthalten:

![](media/function-lower-upper-proper/people-table.png)

Jede Formel gibt eine einspaltige Tabelle zurück, die die konvertierten Zeichenfolgen enthält.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Lower( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |Konvertiert alle Kleinbuchstaben in Großbuchstaben. |<style> img { max-width:none; } </style> ![](media/function-lower-upper-proper/people-table-lower.png) |
| **Upper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |Konvertiert alle Kleinbuchstaben in Großbuchstaben. |![](media/function-lower-upper-proper/people-table-upper.png) |
| **Proper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |Konvertiert den ersten Kleinbuchstaben jedes Worts in Großbuchstaben und Großbuchstaben in Kleinbuchstaben. |![](media/function-lower-upper-proper/people-table-proper.png) |

### <a name="step-by-step-example"></a>Schritt-für-Schritt-Beispiel
1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement hinzu, und benennen Sie es **Source**.
2. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](../controls/properties-core.md)** auf diese Funktion fest:<br>**Proper(Source.Text)**
3. Drücken Sie F5, und geben Sie anschließend **WE ARE THE BEST!** (WIR SIND DIE BESTEN!) ein. in das Feld **Quelle** ein.<br>Die Bezeichnung zeigt **We Are The Best!** (WIR SIND DIE BESTEN!).

