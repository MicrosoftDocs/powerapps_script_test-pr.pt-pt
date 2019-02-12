---
title: Funktionen „Acos“, „Acot“, „Asin“, „Atan“, „Atan2“, „Cos“, „Cot“, „Degrees“, „Pi“, „Radians“, „Sin“ und „Tan“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Abs“ und „Sqrt“ in PowerApps
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
ms.openlocfilehash: 6eab89f436bc00ae0c447494607b5c1bb0cec875
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833111"
---
# <a name="acos-acot-asin-atan-atan2-cos-cot-degrees-pi-radians-sin-and-tan-functions-in-powerapps"></a>Funktionen „Acos“, „Acot“, „Asin“, „Atan“, „Atan2“, „Cos“, „Cot“, „Degrees“, „Pi“, „Radians“, „Sin“ und „Tan“ in PowerApps
Berechnen trigonometrische Werte

## <a name="description"></a>Beschreibung
### <a name="primary-functions"></a>Primäre Funktionen
Die **Cos**-Funktion gibt den Kosinus des Arguments, einen Winkel im Bogenmaß, zurück.

Die **Cot**-Funktion gibt den Kotangens des Arguments, einen Winkel im Bogenmaß, zurück.

Die **Sin**-Funktion gibt den Sinus des Arguments, einen Winkel im Bogenmaß, zurück.

Die **Tan**-Funktion gibt den Tangens des Arguments, einen Winkel im Bogenmaß, zurück.

### <a name="inverse-functions"></a>Umkehrfunktionen
Die **Acos**-Funktion gibt den Arkuskosinus oder umgekehrten Kosinus des Arguments zurück. Der Arkuskosinus ist der Winkel, dessen Kosinus das Argument ist.  Der zurückgegebene Winkel wird im Bogenmaß im Bereich von 0 (null) bis &pi; angegeben.

Die **Acot**-Funktion gibt den Hauptwert des Arkuskotangens oder des umgekehrten Kotangens des Arguments zurück.  Der zurückgegebene Winkel wird im Bogenmaß im Bereich von 0 (null) bis &pi; angegeben.

Die **Asin**-Funktion gibt den Arkussinus oder umgekehrten Kosinus des Arguments zurück. Der Arkussinus ist der Winkel, dessen Sinus das Argument ist.  Der zurückgegebene Winkel wird im Bogenmaß im Bereich von -&pi;/2 bis &pi;/2 angegeben.

Die **Atan**-Funktion gibt den Arkustangens oder umgekehrten Tangens des Arguments zurück. Der Arkustangens ist der Winkel, dessen Tangens das Argument ist. Der zurückgegebene Winkel wird im Bogenmaß im Bereich von -&pi;/2 bis &pi;/2 angegeben.

Die **Atan2**-Funktion gibt den Arkustangens oder umgekehrten Tangens der angegebenen *x*- und *y*-Koordinaten als Argumente zurück. Der Arkustangens ist der Winkel zwischen der *X*-Achse und einer Linie, die den Ursprung (0, 0) und Koordinaten (*x*, *y*) umfasst. Der Winkel wird im Bogenmaß im Bereich von -&pi; bis &pi;, ausgenommen -&pi; angegeben.  Ein positives Ergebnis entspricht einem Winkel gegen den Uhrzeigersinn von der *X*-Achse aus; ein negatives Ergebnis entspricht einem Winkel im Uhrzeigersinn.  **Atan2(&nbsp;*a*,&nbsp;*b*&nbsp;)** ist gleich **Atan(&nbsp;*b*/*a*&nbsp;)**, außer dass ***a*** mit der **Atan2**-Funktion gleich 0 (null) sein kann.

### <a name="helper-functions"></a>Hilfsfunktionen
Die **Degrees**-Funktion wandelt Bogenmaße in Grad um.  Das Bogenmaß &pi; ist gleich 180 Grad.

Die **Pi**-Funktion gibt die transzendente Zahl &pi; zurück, die mit 3.141592... beginnt.

Die **Radians**-Funktion wandelt Grad in Bogenmaß um.  

### <a name="notes"></a>Hinweise
Wenn Sie diesen Funktionen eine einzelne Zahl übergeben, ist der Rückgabewert ein einzelnes Ergebnis.  Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) übergeben, die Zahlen enthält, ist der Rückgabewert eine einspaltige Tabelle mit Ergebnissen, ein Ergebnis für jeden Datensatz in der Argumenttabelle. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.  

Wenn ein Argument zu einem nicht definierten Wert führen würde, ist das Ergebnis *blank* (leer).  Dies kann beispielsweise auftreten, wenn Umkehrfunktionen mit Argumenten verwendet werden, die sich außerhalb des gültigen Bereichs befinden.

## <a name="syntax"></a>Syntax
### <a name="primary-functions"></a>Primäre Funktionen
**Cos**( *Bogenmaß* )<br>**Cot**( *Bogenmaß* )<br>**Sin**( *Bogenmaß* )<br>**Tan**( *Bogenmaß* )

* *Bogenmaß*: Erforderlich. Der zu verarbeitende Winkel.

**Cos**( *EinspaltigeTabelle* )<br>**Cot**( *EinspaltigeTabelle* )<br>**Sin**( *EinspaltigeTabelle* )<br>**Tan**( *EinspaltigeTabelle* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Winkeln, die verarbeitet werden sollen.

### <a name="inverse-functions"></a>Umkehrfunktionen
**Acos**( *Zahl* )<br>**Acot**( *Zahl* )<br>**Asin**( *Zahl* )<br>**Atan**( *Zahl* )

* *Number*: erforderlich. Zahl, die verarbeitet wird.

**Acos**( *EinspaltigeTabelle* )<br>**Acot**( *EinspaltigeTabelle* )<br>**Asin**( *EinspaltigeTabelle* )<br>**Atan**( *EinspaltigeTabelle* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zahlen, die verarbeitet werden.

**Atan2**( *X*, *Y* )

* *X*: Erforderlich.  *X*-Achsenkoordinate.
* *Y*: Erforderlich.  *Y*-Achsenkoordinate.

### <a name="helper-functions"></a>Hilfsfunktionen
**Degrees**( *Bogenmaß* )

* *Bogenmaß*: Erforderlich.  Winkel im Bogenmaß, der in Grad konvertiert werden soll.

**Pi**()

**Radians**( *Grad* )

* *Degrees*: Erforderlich.  Der Winkel in Grad, der in Bogenmaß konvertiert werden soll.

## <a name="examples"></a>Beispiele
### <a name="single-number"></a>Einzelne Zahl

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Cos(&nbsp;1.047197&nbsp;)** |Gibt den Kosinus des Bogenmaßes 1,047197 oder von 60 Grad zurück. |0.5 |
| **Cot(&nbsp;Pi()/4&nbsp;)** |Gibt den Kotangens des Bogenmaßes 0,785398... oder von 45 Grad zurück. |1 |
| **Sin(&nbsp;Pi()/2&nbsp;)** |Gibt den Sinus des Bogenmaßes 1,570796... oder von 90 Grad zurück. |1 |
| **Tan(&nbsp;Radians(60)&nbsp;)** |Gibt den Tangens des Bogenmaßes 1,047197... oder von 60 Grad zurück. |1.732050... |
| **Acos(&nbsp;0.5&nbsp;)** |Gibt den Arkuskosinus von 0,5 im Bogenmaß zurück. |1.047197... |
| **Acot(&nbsp;1&nbsp;)** |Gibt den Arkuskotangens von 1 im Bogenmaß zurück. |0.785398... |
| **Asin(&nbsp;1&nbsp;)** |Gibt den Arkussinus von 1 im Bogenmaß zurück. |1.570796... |
| **Atan(&nbsp;1.732050&nbsp;)** |Gibt den Arkustangens von 1.732050 im Bogenmaß zurück. |1.047197... |
| **Atan2(&nbsp;5,&nbsp;3&nbsp;)** |Gibt den Arkustangens des Winkels zwischen der *X*-Achse und der Linie zurück, die den Ursprung (0,0) und die Koordinate (5,3) umfasst. Dieser Winkel beträgt etwa 31 Grad. |0.540419... |
| **Atan2(&nbsp;4,&nbsp;4&nbsp;)** |Gibt den Arkustangens des Winkels zwischen der *X*-Achse und der Linie zurück, die den Ursprung (0,0) und die Koordinate (4,4) umfasst. Dieser Winkel beträgt genau das Bogenmaß &pi;/4 oder 45 Grad. |0.785398... |
| **Degrees(&nbsp;1.047197&nbsp;)** |Gibt die entsprechende Gradzahl des Bogenmaßes 1,047197 zurück. |60 |
| **Pi()** |Gibt die transzendente Zahl &pi; zurück. |3.141592... |
| **Radians(&nbsp;15&nbsp;)** |Gibt die entsprechende Bogenmaßzahl für 15 Grad zurück. |0.261799... |

### <a name="single-column-table"></a>Einspaltige Tabelle
Die Beispiele in diesem Abschnitt verwenden eine [Datenquelle](../working-with-data-sources.md), die als **ValueTable** bezeichnet wird und die folgenden Daten enthält.  Der letzte Datensatz in der Tabelle ist das Bogenmaß &pi;/2 oder 90 Grad.

![](media/function-trig/values.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Cos(&nbsp;ValueTable&nbsp;)** |Gibt den Kosinus der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-cos.png) |
| **Cot(&nbsp;ValueTable&nbsp;)** |Gibt den Kotangens der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-cot.png) |
| **Sin(&nbsp;ValueTable&nbsp;)** |Gibt den Sinus der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-sin.png) |
| **Tan(&nbsp;ValueTable&nbsp;)** |Gibt den Tangens der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-tan.png) |
| **Acos(&nbsp;ValueTable&nbsp;)** |Gibt den Arkuskosinus der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-acos.png) |
| **Acot(&nbsp;ValueTable&nbsp;)** |Gibt den Arkuskotangens der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-acot.png) |
| **Asin(&nbsp;ValueTable&nbsp;)** |Gibt den Arkussinus der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-asin.png) |
| **Atan(&nbsp;ValueTable&nbsp;)** |Gibt den Arkustangens der einzelnen Zahlen in der Tabelle zurück. |<style> img { max-width: none } </style> ![](media/function-trig/values-atan.png) |
| **Degrees(&nbsp;ValueTable&nbsp;)** |Gibt die entsprechende Gradzahl für die einzelnen Zahlen in der Tabelle zurück, von denen angenommen wird, dass es sich dabei um Bogenmaße handelt. |<style> img { max-width: none } </style> ![](media/function-trig/values-degrees.png) |
| **Radians(&nbsp;ValueTable&nbsp;)** |Gibt die entsprechende Bogenmaßzahl für die einzelnen Zahlen in der Tabelle zurück, von denen angenommen wird, dass es sich dabei um Winkel im Gradmaß handelt. |<style> img { max-width: none } </style> ![](media/function-trig/values-radians.png) |

