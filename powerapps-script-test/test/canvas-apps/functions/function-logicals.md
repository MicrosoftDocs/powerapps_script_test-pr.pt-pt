---
title: Funktionen „And“, „Or“ und „Not“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „And“, „Or“ und „Not“ in PowerApps
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
ms.openlocfilehash: 438076c5e1b3e0643af809755078fbc491cea9c5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42850348"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>Die Funktionen „And“, „Or“ und „Not“ in PowerApps
Boolesche Logikfunktionen, die oft dazu verwendet werden, die Ergebnisse von Vergleichen und Tests zu bearbeiten

## <a name="description"></a>Beschreibung
Die **And**-Funktion gibt **TRUE** zurück, wenn alle ihre Argumente **TRUE** sind.  Der **&&**-[Operator](operators.md) entspricht **And**.

Die **Or**-Funktion gibt **TRUE** zurück, wenn eines der Argumente **TRUE** ist.  Der **||**-Operator entspricht **Or**.

Die **Not**-Funktion gibt **TRUE** zurück, wenn ihr Argument **FALSE** ist; sie gibt **FALSE** zurück, wenn ihr Argument **TRUE** ist.  Der **!**-Operator entspricht **Not**.

Diese Funktionen arbeiten mit logischen Werten. Ihnen können keine Zahl oder Zeichenfolge direkt übergeben werden; stattdessen muss ein Vergleich oder Test vorgenommen werden. Beispielsweise ist ein Vergleich wie **x > 1** eine logische Formel, die den booleschen Wert **TRUE** ergibt, wenn **x** größer als **1** ist. Wenn **x** kleiner als **1** ist, ergibt die Formel **FALSE**.

## <a name="syntax"></a>Syntax
**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

* *LogicalFormula(s)*: erforderlich.  Logische Formeln, die bewertet und verarbeitet werden sollen

## <a name="examples"></a>Beispiele
### <a name="step-by-step"></a>Schritt für Schritt
Verwenden Sie diese Funktion, um zu bestimmen, ob der Wert eines Schiebereglers außerhalb des Bereichs zwischen 50 und 100 liegt:

**Or(Slider1.Value < 50, Slider1.Value> 100)**

Wenn eine [Tabelle](../working-with-tables.md) z.B. eine **Dept**-[Spalte](../working-with-tables.md#columns) (Schulden) und eine **Salary**-Spalte (Einkommen) enthält, können Sie diese Funktion in einer **Result**-Spalte (Ergebnis) verwenden, um **TRUE** in allen Zeilen anzuzeigen, in denen der Wert in der **Dept**-Spalte **HR** ist oder der Wert in der **Salary**-Spalte größer als **200.000** ist:

**Or(Dept = HR, Salary >= 200000)**

Verwenden Sie alternativ den ||-Operator, um die gleichen Ergebnisse wie die vorherige Formel zurückzugeben:

**Slider1.Value < 50 || Slider1.Value> 100**

**Dept = "HR" || Salary > 200000**

