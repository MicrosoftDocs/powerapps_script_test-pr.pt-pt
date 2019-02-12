---
title: Funktion „Shuffle“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Shuffle“ in PowerApps
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
ms.openlocfilehash: 3fd93ce6cf9703e9e9fbf69c5826213d9aa78e02
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863566"
---
# <a name="shuffle-function-in-powerapps"></a>Funktion „Shuffle“ in PowerApps
Sortiert die [Datensätze](../working-with-tables.md#records) einer [Tabelle](../working-with-tables.md) nach dem Zufallsprinzip neu

## <a name="description"></a>Beschreibung
Die **Shuffle**-Funktion sortiert die Datensätze einer Tabelle neu.

**Shuffle** gibt eine Tabelle zurück, die über die gleichen [Spalten](../working-with-tables.md#columns) und die gleiche Anzahl von Zeilen als das Argument verfügt.

## <a name="syntax"></a>Syntax
**Shuffle**( *Tabelle* )

* *Tabelle* (erforderlich):  Die nach dem Zufallsprinzip zu sortierende Tabelle.

## <a name="example"></a>Beispiel
Wenn Sie Informationen zu Spielkarten in einer [Sammlung](../working-with-data-sources.md#collections) mit dem Namen **Deck** gespeichert hätten, würde diese Formel eine Kopie dieser Sammlung zurückgeben, die nach dem Zufallsprinzip sortiert wurde.

**Shuffle(Deck)**

