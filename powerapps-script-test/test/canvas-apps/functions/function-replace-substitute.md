---
title: Funktionen „Replace“ und „Substitute“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen „Replace“ und „Substitute“ in PowerApps
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
ms.openlocfilehash: d403fc5d756934900664affc04619c5cc72af6ee
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834357"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>Die Funktionen „Replace“ und „Substitute“ in PowerApps
Ersetzen Sie einen Teil einer Textzeichenfolge durch eine andere Zeichenfolge.

## <a name="description"></a>Beschreibung
Die **Replace**-Funktion identifiziert den zu ersetzenden Text anhand der Anfangsposition und Länge.  

Die **Substitute**-Funktion identifiziert den zu ersetzenden Text anhand einer Übereinstimmung mit einer Zeichenfolge.  Wenn mehr als eine Übereinstimmung gefunden wird, können Sie steuern, welcher Typ ersetzt wird.

Wenn Sie eine einzelne Zeichenfolge übergeben, ist der Rückgabewert die geänderte Zeichenfolge.  Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) übergeben, die Zeichenfolgen enthält, ist der Rückgabewert eine einspaltige Tabelle mit geänderten Zeichenfolgen. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

## <a name="syntax"></a>Syntax
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *Zeichenfolge*: erforderlich. Die zu verarbeitende Zeichenfolge
* *Anfangsposition*: erforderlich.  Zeichenposition, ab der ersetzt werden soll. Das erste Zeichen von *String* befindet sich an Position 1.
* *AnzahlDerZeichen*: erforderlich.  Die Anzahl der zu ersetzenden Zeichen in *String*
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. Die Anzahl der Zeichen in diesem Argument kann sich von dem *NumberOfCharacters*-Argument unterscheiden.

**Substitute**( *Zeichenfolge*, *alte Zeichenfolge*, *NewString* [, *InstanceNumber* ])

* *Zeichenfolge*: erforderlich. Die zu verarbeitende Zeichenfolge
* *AlteZeichenfolge*: erforderlich.  Die zu ersetzende Zeichenfolge
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. *AlteZeichenfolge* und *NeueZeichenfolge* können unterschiedlich lang sein.
* *AnzahlDerInstanzen*: optional. Standardmäßig wird die erste Instanz von *OldString* ersetzt. Wenn *String* mehr als eine Instanz enthält, können Sie angeben, welche Instanz ersetzt wird.

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die verarbeitet werden sollen.
* *Anfangsposition*: erforderlich.  Zeichenposition, ab der ersetzt werden soll.  Das erste Zeichen einer jeden Zeichenfolge in der Tabelle ist an Position 1.
* *AnzahlDerZeichen*: erforderlich.  Die Zahl der zu ersetzenden Zeichen in jeder Zeichenfolge
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. Die Anzahl der Zeichen in diesem Argument kann sich von dem *NumberOfCharacters*-Argument unterscheiden.

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die verarbeitet werden sollen.
* *AlteZeichenfolge*: erforderlich.  Die zu ersetzende Zeichenfolge
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. *AlteZeichenfolge* und *NeueZeichenfolge* können unterschiedlich lang sein.
* *AnzahlDerInstanzen*: optional. Standardmäßig wird die erste Instanz von *OldString* ersetzt. Wenn die Tabelle mehr als eine Instanz enthält, können Sie festlegen, welche Instanz ersetzt werden soll.

