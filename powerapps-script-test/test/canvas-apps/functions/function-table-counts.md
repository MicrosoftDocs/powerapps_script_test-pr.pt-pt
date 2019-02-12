---
title: Funktionen „Count“, „CountA“, „CountIf“ und „CountRows“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiel für die Funktionen „Count“, „CountA“, „CounfIf“ und „CountRows“ in PowerApps
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
ms.openlocfilehash: 717baab028b480063f76b799a1267155464d8ac3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42828210"
---
# <a name="count-counta-countif-and-countrows-functions-in-powerapps"></a>Funktionen „Count“, „CountA“, „CounfIf“ und „CountRows“ in PowerApps
Zählen alle [Datensätze](../working-with-tables.md#records) in einer [Tabelle](../working-with-tables.md) oder alle Datensätze, die eine Bedingung erfüllen

## <a name="description"></a>Beschreibung
Die Funktion **Count** zählt die Datensätze, die eine Zahl in einer einspaltigen Tabelle enthalten.

Die Funktion **CountA** zählt die Datensätze, die in einer einspaltigen Tabelle nicht als *blank* dargestellt werden. Diese Funktion umfasst [leeren](function-isblank-isempty.md) Text ("") in der Zählung.

Die Funktion **CountIf** zählt die Datensätze in einer Tabelle, die für eine logische Formel **TRUE** ergeben.  Die Formel kann auf [Spalten](../working-with-tables.md#columns) der Tabelle verweisen.

Die Funktion **CountRows** zählt die Datensätze in einer Tabelle.

Jede dieser Funktionen gibt eine Zahl zurück.

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Syntax
**Count**( *EinspaltigeTabelle* )<br>
**CountA**( *SingleColumnTable* )

* *EinspaltigeTabelle*: erforderlich.  Die zu zählende Spalte mit Datensätzen.  

**CountIf**( *Tabelle*, *LogischeFormel* )

* *Tabelle* (erforderlich):  Die zu zählende Tabelle mit Datensätzen.
* *LogischeFormel*: Erforderlich.  Die für jeden Datensatz der Tabelle auszuwertende Formel.  Es werden Datensätze gezählt, die für diese Formel **TRUE** zurückgeben.  Die Formel kann auf Spalten der Tabelle verweisen.

**CountRows**( *Tabelle* )

* *Tabelle* (erforderlich):  Die zu zählende Tabelle mit Datensätzen.

## <a name="example"></a>Beispiel
1. Importieren oder Erstellen Sie eine [Sammlung](../working-with-data-sources.md#collections) mit dem Namen **Inventory**, wie im ersten Unterverfahren unter [Show images and text in a gallery (Anzeigen von Bildern und Text in einem Katalog)](../show-images-text-gallery-sort-filter.md) beschrieben.
2. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](../controls/properties-core.md)** auf diese Funktion fest:
   
    **CountIf(Inventory, UnitsInStock < 30)**
   
    Die Bezeichnung zeigt **2** an, da von zwei Produkten (Ganymed und Callisto) weniger als 30 Einheiten auf Lager sind.
3. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](../controls/properties-core.md)** auf diese Funktion fest:
   
    **CountA(Inventory.UnitsInStock)**
   
    Die Bezeichnung zeigt **5** an, die Anzahl der nicht leeren Zellen in der Spalte **UnitsInStock**.
4. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](../controls/properties-core.md)** auf diese Funktion fest:
   
    **CountRows(Inventory)**
   
    Die Bezeichnung zeigt **5** an, da die Sammlung fünf Zeilen enthält.

