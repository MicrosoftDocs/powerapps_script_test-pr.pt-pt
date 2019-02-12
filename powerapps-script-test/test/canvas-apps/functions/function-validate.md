---
title: Funktion „Validate“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Validate“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d92236d630005b4608719efaadef4537984bc3d6
ms.sourcegitcommit: 5a1864d1531b55b332749437674fd1378e1f55ca
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307836"
---
# <a name="validate-function-in-powerapps"></a>Funktion „Validate“ in PowerApps
Die **Validate**-Funktion überprüft, ob der Wert einer einzelnen [Spalte](../working-with-tables.md#columns) oder eines vollständigen [Datensatzes](../working-with-tables.md#records) für eine [Datenquelle](../working-with-data-sources.md) gilt.  

## <a name="description"></a>Beschreibung
Bevor ein Benutzer eine Änderung von Daten übermittelt, können Sie unmittelbar Feedback zur Gültigkeit dieser Übermittlung geben, was zu einer besseren Benutzerfreundlichkeit führt.

Datenquellen können Informationen dazu bereitstellen, was gültige Werte in einem Datensatz auszeichnen. Diese Informationen können viele Einschränkungen enthalten, z.B.:

* ob eine Spalte einen Wert erfordert
* wie lang eine Textzeichenfolge sein kann
* wie groß oder klein eine Zahl sein kann
* wie früh oder spät ein Datum sein kann

Die **Validate**-Funktion verwendet diese Informationen, um zu bestimmen, ob ein Wert gültig ist, und um eine entsprechende Fehlermeldung zurückzugeben, falls dies nicht der Fall ist. Sie können die **[DataSourceInfo](function-datasourceinfo.md)**-Funktion verwenden, um die gleichen Informationen anzuzeigen, die **Validate** verwendet.

Datenquellen stellen unterschiedlich viele Gültigkeitsinformationen zur Verfügung, manchmal sogar gar keine. **Validate** kann Werte nur basierend auf diesen Informationen überprüfen. Auch wenn **Validate** kein Problem findet, kann bei der Anwendung der Datenänderung dennoch ein Fehler auftreten. Sie können die **[Errors](function-errors.md)**-Funktion verwenden, um Informationen über den Fehler abzurufen.

Wenn **Validate** ein Problem findet, gibt die Funktion eine Fehlermeldung zurück, die Sie dem Benutzer der App anzeigen können. Wenn alle Werte gültig sind, gibt **Validate** [blank](function-isblank-isempty.md) zurück. Beim Arbeiten mit einer [Sammlung](../working-with-data-sources.md#collections), die über keine Gültigkeitsinformationen verfügt, sind Werte immer gültig.

## <a name="syntax"></a>Syntax
**Validate**( *Datenquelle*, *Spalte*, *Wert* )

* *Datenquelle*: Erforderlich. Die Datenquelle, mit der überprüft werden soll.
* *Spalte*: Erforderlich. Die Spalte, die überprüft werden soll.
* *Wert*: Erforderlich. Der Wert für die ausgewählte Spalte, die überprüft werden soll.

**Validate**( *Datenquelle*, *UrsprünglicherDatensatz*, *Updates* )

* *Datenquelle*: Erforderlich. Die Datenquelle, mit der überprüft werden soll.
* *UrsprünglicherDatensatz*: Erforderlich.  Der Datensatz, für den Updates überprüft werden sollen.
* *Updates*: Erforderlich.  Die Änderungen, die am ursprünglichen Datensatz vorgenommen werden sollen.

## <a name="examples"></a>Beispiele
Für diese Beispiele müssen die Werte in der Spalte **Percentage** (Prozentzahl) der Datenquelle **Scores** (Ergebnisse) zwischen 0 und (einschließlich) 100 liegen. Wenn die Daten die Überprüfung bestehen, gibt die Funktion *blank* zurück. Andernfalls gibt die Funktion eine Fehlermeldung zurück.

### <a name="validate-with-a-single-column"></a>Überprüfen mit einer einzelnen Spalte

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Validate( Scores, Percentage, 10 )** |Überprüft, ob **10** ein gültiger Wert für die Spalte **Percentage** in der Datenquelle **Scores** ist. |*blank* |
| **Validate( Scores, Percentage, 120 )** |Überprüft, ob **120** ein gültiger Wert für die Spalte **Percentage** in der Datenquelle **Scores** ist. |"Values must be between 0 and 100." (Werte müssen zwischen 0 und 100 liegen.) |

### <a name="validate-with-a-complete-record"></a>Überprüfen mit einem vollständigen Datensatz

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Validate( Scores, EditRecord, Gallery.Updates )** |Überprüft, ob die Werte in allen Spalten für die Datenquelle **Scores** (Bewertungen) gültig sind. In diesem Beispiel lautet der Wert der **Percentage**-Spalte (Prozentsatz) **10**. |*blank* |
| **Validate( Scores, EditRecord, Gallery.Updates )** | Überprüft, ob die Werte in allen Spalten für die Datenquelle **Scores** (Bewertungen) gültig sind. In diesem Beispiel lautet der Wert der **Percentage**-Spalte (Prozentsatz) lautet **120**. |"Values must be between 0 and 100." (Werte müssen zwischen 0 und 100 liegen.) |

