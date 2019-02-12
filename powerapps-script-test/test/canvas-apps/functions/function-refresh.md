---
title: Funktion „Refresh“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Refresh“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2999665e5882245b594468b6babe67be575c5c1e
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843595"
---
# <a name="refresh-function-in-powerapps"></a>Funktion „Refresh“ in PowerApps
Aktualisiert die [Datensätze](../working-with-tables.md#records) einer [Datenquelle](../working-with-data-sources.md)

## <a name="description"></a>Beschreibung
Die **Refresh**-Funktion ruft eine neue Kopie einer Datenquelle ab.  Sie können die Änderungen anzeigen, die andere Benutzer vorgenommen haben.

**Refresh** weist keinen Rückgabewert auf; Sie können diese Funktion nur innerhalb einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**Refresh**( *Datenquelle* )

* *Datenquelle*: Erforderlich. Die Datenquelle, die Sie aktualisieren möchten.

## <a name="example"></a>Beispiel
In diesem Beispiel aktualisieren Sie die Datenquelle namens **IceCream** (Eiscreme), die mit den Daten in dieser Tabelle beginnt:

![](media/function-refresh/icecream.png)

Ein Benutzer auf einem anderen Gerät ändert die **Quantity** (Menge) des Datensatzes **Strawberry** (Erdbeere) auf **400**.  Diese Änderung wird erst angezeigt, wenn diese Formel ausgeführt wird:

**Refresh( IceCream )**

Nachdem diese Formel ausgeführt wurde, zeigen Kataloge, die mit der **IceCream**-Datenquelle verbunden sind, den aktualisierten Wert für **Strawberry** an:

![](media/function-refresh/icecream-after.png)

