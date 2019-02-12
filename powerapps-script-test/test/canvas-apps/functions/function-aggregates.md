---
title: Funktionen „Average“, „Max“, „Min“, „StdevP“, „Sum“ und „VarP“ | Microsoft-Dokumentation
description: Referenzinformationen für die Funktionen „Average“, „Max“, „Min“, „StdevP“, „Sum“ und „VarP“ in PowerApps einschließlich Syntax und Beispielen
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/15/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bae3c031864e94c803086c4cd349679995d766cc
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862172"
---
# <a name="average-max-min-stdevp-sum-and-varp-functions-in-powerapps"></a>Funktionen „Average“, „Max“, „Min“, „StdevP“, „Sum“ und „VarP“ in PowerApps
Aggregatfunktionen, die eine Menge von Zahlen zusammengefassten

## <a name="description"></a>Beschreibung
Die **Average**-Funktion berechnet den Durchschnitt bzw. das arithmetische Mittel der Argumente.

Die **Max**-Funktion etabliert den Höchstwert.

Die **Min**-Funktion sucht den Mindestwert.

Die **Sum**-Funktion berechnet die Summe der Argumente.

Die **StdevP**-Funktion berechnet die Standardabweichung der Argumente.

Die **VarP**-Funktion berechnet die Varianz der Argumente.

Sie können die Werte für diese Funktionen angeben als:

* getrennte Argumente. **Sum (1, 2, 3)** beispielsweise gibt den Wert 6 zurück.
* eine [Tabelle](../working-with-tables.md) und eine Formel, die die Tabelle verarbeitet.  Das Aggregat wird anhand der Werte der Formel für jeden [Datensatz](../working-with-tables.md#records) berechnet.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Diese Funktionen verarbeiten nur numerische Werte. Andere Typen von Werten wie Zeichenfolgen oder Datensätze werden ignoriert. Verwenden Sie die  **[Value](function-value.md)**-Funktion zum Konvertieren einer Zeichenfolge in eine Zahl.

Die Funktionen **Average**, **Max**, **Min** und **Sum** können delegiert werden, wenn sie mit einer [Datenquelle verwendet werden, die Delegierung für diese Funktionen unterstützt](../delegation-list.md).  **StdevP** und **VarP** können jedoch für keine Datenquellen delegiert werden.  Wenn Delegierung nicht unterstützt wird, wird nur der erste Teil der Datenquelle abgerufen, und anschließend wird die Funktion lokal angewendet.  Das Ergebnis ist dann ggf. kein umfassendes Ergebnis.  Bei der Erstellung wird eine Delegierungswarnung angezeigt, um Sie an diese Einschränkung zu erinnern und die Umstellung auf delegierbare Alternativen vorzuschlagen, soweit dies möglich ist. Weitere Informationen finden Sie unter [Grundlagen der Delegierung](../delegation-overview.md).

## <a name="syntax"></a>Syntax
**Average**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Max**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Min**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Sum**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**StdevP**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**VarP**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )

* *NumericalFormula(s)*: erforderlich.  Die zu verarbeitenden numerischen Werte.

**Average**( *Table*, *NumericalFormula* )<br>**Max**( *Table*, *NumericalFormula* )<br>**Min**( *Table*, *NumericalFormula* )<br>**Sum**( *Table*, *NumericalFormula* )<br>**StdevP**( *Table*, *NumericalFormula* )<br>**VarP**( *Table*, *NumericalFormula* )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *NumericalFormula*: erforderlich. Die für jeden Datensatz auszuwertende Formel. Das Ergebnis dieser Formel wird für die Aggregation verwendet. Sie können die Spalten der Tabelle in der Formel verwenden.

## <a name="examples"></a>Beispiele
### <a name="step-by-step"></a>Schritt für Schritt
Sie haben eine [Datenquelle](../working-with-data-sources.md) mit dem Namen **Sales**, die eine Spalte**CostPerUnit** mit den Kosten pro Einheit und eine Spalte **UnitsSold** mit den verkauften Einheiten enthält, und Sie legen die **[Text](../controls/properties-core.md)**-Eigenschaft einer Bezeichnung auf diese Funktion fest:<br>
**Sum(Sales, CostPerUnit * UnitsSold)**

Die Bezeichnung zeigt den Gesamtumsatz an, der sich aus der Multiplikation der Werte in diesen Spalten für jeden Datensatz ergibt. Anschließend werden die Ergebnisse aller Datensätze addiert:<br>![Berechnen des Gesamtumsatzes von verkauften Einheiten und der Kosten pro Einheit](./media/function-aggregates/total-sales.png)

Hier ein anderes Beispiel: Sie verfügen über mehrere Schieberegler mit dem Namen **Slider1**, **Slider2** und **Slider3** und eine Bezeichnung mit der **[Text](../controls/properties-core.md)**-Eigenschaft, die auf diese Formel festgelegt ist:<br>
**Sum(Slider1.Value, Slider2.Value, Slider3.Value)**

Die Bezeichnung zeigt die Summe aller Werte an, die für die Schieberegler festgelegt wurden.

