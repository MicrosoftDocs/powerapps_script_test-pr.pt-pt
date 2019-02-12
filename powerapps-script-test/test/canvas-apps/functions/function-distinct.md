---
title: Funktion „Distinct“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Distinct-Funktion in PowerApps
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
ms.openlocfilehash: 17a2f2cfca16c5589f74ac434b36326037146b16
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843196"
---
# <a name="distinct-function-in-powerapps"></a>Distinct-Funktion in PowerApps
Fasst [Datensätze](../working-with-tables.md#records) aus einer [Tabelle](../working-with-tables.md) zusammen, wobei Duplikate entfernt werden.

## <a name="description"></a>Beschreibung
Die **Distinct**-Funktion wertet eine Formel für jeden Datensatz einer Tabelle aus. **Distinct** gibt eine Tabelle mit einer Spalte mit den Ergebnissen zurück, wobei doppelte Werte entfernt wurden.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

## <a name="syntax"></a>Syntax
**Distinct**( *Table*, *Formula* )

* *Tabelle* (erforderlich):  Die Tabelle, die übergreifend ausgewertet werden soll.
* *Formel* (erforderlich):  Die für jeden Datensatz auszuwertende Formel.

## <a name="example"></a>Beispiel
Wenn Sie eine Tabelle **Mitarbeiter** mit einer Spalte **Abteilung** haben, würde diese Funktion jeden individuellen Abteilungsnamen in dieser Spalte auflisten, unabhängig davon, wie oft jeder Name in der Spalte angezeigt wird:

**Distinct(Employees, Department)**

