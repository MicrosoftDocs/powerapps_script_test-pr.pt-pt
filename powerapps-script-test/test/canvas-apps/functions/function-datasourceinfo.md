---
title: Funktion „DataSourceInfo“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „DataSourceInfo“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d856ccd086a919e206175c25eee19f435325fb8c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42835265"
---
# <a name="datasourceinfo-function-in-powerapps"></a>Funktion „DataSourceInfo“ in PowerApps
Stellt Informationen über eine [Datenquelle](../working-with-data-sources.md) bereit

## <a name="overview"></a>Übersicht
Datenquellen können eine Fülle von Informationen bereitstellen, um die Benutzerfreundlichkeit zu optimieren.

Sie können Informationen auf [Spaltenebene](../working-with-tables.md#columns) verwenden, um Benutzereingaben zu prüfen und dem Benutzer vor dem Verwenden der **[Patch](function-patch.md)**-Funktion sofort Feedback zu geben. Die **[Validate](function-validate.md)**-Funktion verwendet die gleichen Informationen.

Sie können Informationen auf Datenquellenebene z.B. verwenden, um die Schaltflächen **Bearbeiten** und **Neu** für Benutzer zu deaktivieren oder auszublenden, die keine Berechtigungen haben, [Datensätze](../working-with-tables.md#records) zu bearbeiten und zu erstellen.

Datenquellen stellen unterschiedlich viele Informationen zur Verfügung, manchmal sogar gar keine.  [Sammlungen](../working-with-data-sources.md#collections) stellen keine Informationen bereit. Wenn eine Information nicht bereitgestellt wird, wird ein Standardwert verwendet, oder es wird *blank* (leer) zurückgegeben.

## <a name="description"></a>Beschreibung
### <a name="column-information"></a>Spalteninformationen
Sie können **DataSourceInfo** verwenden, um Informationen über eine bestimmte Spalte einer Datenquelle zu erhalten:  

| Informationsargument | Ergebnistyp | Beschreibung |
| --- | --- | --- |
| **DataSourceInfo.DisplayName** |Zeichenfolge |Anzeigename für die Spalte. Wenn kein Anzeigename definiert ist, wird der Spaltennamen zurückgegeben. |
| **DataSourceInfo.MaxLength** |Number |Maximale Anzahl von Zeichen, die die Spalte enthalten kann. Gilt nur für Spalten, die Zeichenfolgen enthalten. Wenn ein Maximum nicht festgelegt ist, wird *blank* zurückgegeben. |
| **DataSourceInfo.MaxValue** |Number |Höchster numerischer Wert, den eine Spalte enthalten kann. Gilt nur für Spalten, die Zahlen enthalten. Wenn ein Maximum nicht festgelegt ist, wird *blank* zurückgegeben. |
| **DataSourceInfo.MinValue** |Number |Niedrigster numerischer Wert, den eine Spalte enthalten kann. Gilt nur für Spalten, die Zahlen enthalten. Wenn ein Minimum nicht festgelegt ist, wird *blank* zurückgegeben. |
| **DataSourceInfo.Required** |Boolescher Wert |Ist ein Wert für diese Spalte erforderlich? Wenn nicht von der Datenquelle festgelegt, wird **FALSE** zurückgegeben. |

Das dritte Argument ist der Name einer Spalte als Zeichenfolge.  Beispielsweise würde die Spalte **Phone** (Telefon) in der Sammlung **People** (Personen) würde als **"Phone"**, inklusive der doppelten Anführungszeichen, übergeben werden.

### <a name="data-source-information"></a>Datenquelleninformationen
Sie können **DataSourceInfo** auch dazu verwenden, Informationen über die Datenquelle als Ganzes abzurufen:  

| Informationsargument | Ergebnistyp | Beschreibung |
| --- | --- | --- |
| **DataSourceInfo.AllowedValues** |Boolescher Wert |Welche Arten von Berechtigungen können Benutzern für diese Datenquelle werden erteilt? Gibt *leer* zurück, wenn von der Datenquelle nicht festgelegt. |
| **DataSourceInfo.CreatePermission** |Boolescher Wert |Verfügt der aktuelle Benutzer über die Berechtigung zum Erstellen von Datensätzen in dieser Datenquelle? Wenn nicht von der Datenquelle festgelegt, wird **TRUE** zurückgegeben. |
| **DataSourceInfo.DeletePermission** |Boolescher Wert |Verfügt der aktuelle Benutzer über die Berechtigung zum Löschen von Datensätzen in dieser Datenquelle? Wenn nicht von der Datenquelle festgelegt, wird **TRUE** zurückgegeben. |
| **DataSourceInfo.EditPermission** |Boolescher Wert |Verfügt der aktuelle Benutzer über die Berechtigung zum Bearbeiten von Datensätzen in dieser Datenquelle? Wenn nicht von der Datenquelle festgelegt, wird **TRUE** zurückgegeben. |
| **DataSourceInfo.ReadPermission** |Boolescher Wert |Verfügt der aktuelle Benutzer über die Berechtigung zum Lesen von Datensätzen in dieser Datenquelle? Wenn nicht von der Datenquelle festgelegt, wird **TRUE** zurückgegeben. |

## <a name="syntax"></a>Syntax
**DataSourceInfo**( *Datenquelle*, *Information*, *Spaltenname* )

* *Datenquelle*: Erforderlich. Die zu verwendende Datenquelle.
* *Information*: Erforderlich. Der Typ von Information, den Sie abrufen möchten.
* *Spaltenname*: Optional. Bei Informationen auf Spaltenebene der Spaltenname als Zeichenfolge. Die Spalte **Phone** würde als **"Phone"**, inklusive der doppelten Anführungszeichen, übergeben werden. Für Informationen auf Datenbankebene kann das *Spaltenname*-Argument nicht verwendet werden.
  
    > [!NOTE]
  > Bei Excel- oder SharePoint-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, geben Sie jedes Leerzeichen als **"\_x0020\_"** an. **"Name der Spalte"** wird z.B. als **"Name_x0020_der_x0020_Spalte"** angegeben.

## <a name="examples"></a>Beispiele
In den Beispielen in diesem Abschnitt wird diese Datenquelle namens **IceCream** (Eiscreme) verwendet:

![](media/function-datasourceinfo/icecream.png)

Die Datenquelle hat zudem diese Informationen bereitgestellt:

* Der Anzeigename für **Quantity** (Menge) ist "Quantity on Hand" (Lagerbestand).
* Die maximale Länge von **Flavor** (Sorte) beträgt 30 Zeichen.
* Die Spalte **Flavor** muss einen Wert enthalten. Die Spalte **Quantity** ist nicht erforderlich.
* Der minimale Wert für **Quantity** ist 0.
* Der maximale Wert für **Quantity** ist 100.
* Der aktuelle Benutzer kann die Datensätze der Datenquelle **IceCream** lesen und bearbeiten, jedoch keine Datensätze erstellen oder löschen.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DisplayName,&nbsp;"Quantity"&nbsp;)** |Gibt den Anzeigenamen für die Spalte **Quantity** der Datenquelle **IceCream** zurück |"Quantity on Hand" (Lagerbestand) |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxLength,&nbsp;"Flavor"&nbsp;)** |Gibt die maximale Länge der Zeichenfolge für die Spalte **Flavor** der Datenquelle **IceCream** zurück. |30 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Flavor"&nbsp;)** |Ist die Spalte **Flavor** der Datenquelle **IceCream** erforderlich? |**TRUE** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Quantity"&nbsp;)** |Ist die Spalte **Quantity** der Datenquelle **IceCream** erforderlich? |**FALSE** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxValue,&nbsp;"Quantity"&nbsp;)** |Gibt den höchsten numerischen Wert für die Spalte **Quantity** der Datenquelle **IceCream** zurück |100 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MinValue,&nbsp;"Quantity"&nbsp;)** |Gibt den niedrigsten numerischen Wert für die Spalte **Quantity** der Datenquelle **IceCream** zurück |0 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.ReadPermission)** |Kann der aktuelle Benutzer Datensätze in der Datenquelle **IceCream** lesen? |**TRUE** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.EditPermission)** |Kann der aktuelle Benutzer Datensätze in der Datenquelle **IceCream** bearbeiten? |**TRUE** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.CreatePermission)** |Kann der aktuelle Benutzer Datensätze in der Datenquelle **IceCream** erstellen? |**FALSE** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DeletePermission)** |Kann der aktuelle Benutzer Datensätze in der Datenquelle **IceCream** löschen? |**FALSE** |

