---
title: Funktion „Find“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Find“ in PowerApps
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
ms.openlocfilehash: 04f257b40e778d3611203f2bdc17aad5554a4ac6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865952"
---
# <a name="find-function-in-powerapps"></a>Funktion „Find“ in PowerApps
Sucht nach einer Textzeichenfolge in einer anderen Zeichenfolge (falls vorhanden)

## <a name="description"></a>Beschreibung
Die **Find**-Funktion sucht innerhalb einer anderen Zeichenfolge nach einer Zeichenfolge und beachtet dabei Groß-/Kleinschreibung. Wenden Sie zuerst die **[Lower](function-lower-upper-proper.md)**-Funktion auf die Argumente an, um die Groß-und Kleinschreibung außer Acht zu lassen.

**Find** gibt die Anfangsposition der Zeichenfolge zurück, die gefunden wurde.  Position 1 ist das erste Zeichen der Zeichenfolge. **Find** gibt *blank* zurück, wenn die Zeichenfolge, in der Sie suchen, nicht die Zeichenfolge enthält, nach der Sie suchen.

## <a name="syntax"></a>Syntax
**Find**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *ZuSuchendeZeichenfolge*: erforderlich.  Die zu suchende Zeichenfolge
* *InnerhalbDerZeichenfolge*: erforderlich.  Die Zeichenfolge, in der gesucht werden soll
* *Anfangsposition*: optional.  Die Anfangsposition der Suche.  Position 1 ist das erste Zeichen.

