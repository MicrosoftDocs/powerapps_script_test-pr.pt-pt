---
title: Funktion „User“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „User“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f452fedfbb26394bcaf4d490fa608f066469fb53
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863447"
---
# <a name="user-function-in-powerapps"></a>Funktion „User“ in PowerApps
Gibt Informationen über den aktuellen Benutzer zurück.

## <a name="description"></a>Beschreibung
Die Funktion **User** gibt einen [Datensatz](../working-with-tables.md#records) mit Informationen über den aktuellen Benutzer zurück:

| Eigenschaft | Beschreibung |
| --- | --- |
| **User().Email** |E-Mail-Adresse des aktuellen Benutzers. |
| **User().FullName** |Vollständiger Name des aktuellen Benutzers, einschließlich Vor-und Nachnamen. |
| **User().Image** |Bild des aktuellen Benutzers. Dies ist eine Bild-URL der Form "blob:*Bezeichner*". Legen Sie die Eigenschaft **[Image](../controls/properties-visual.md)** des **[Image](../controls/control-image.md)**-Steuerelements auf diesen Wert fest, um das Bild in der App anzuzeigen. |

> [!NOTE]
> Die zurückgegebenen Informationen beziehen sich auf den aktuellen PowerApps-Benutzer.  Sie stimmen mit den Kontoinformationen überein, die in den PowerApps-Playern und in Studio angezeigt werden, die außerhalb von Apps mit Verfassern verfügbar sind.  Möglicherweise stimmen sie nicht mit den Informationen des aktuellen Benutzers in Office 365 oder anderen Diensten überein.

## <a name="syntax"></a>Syntax
**User**()

## <a name="examples"></a>Beispiele
Der aktuelle PowerApps-Benutzer weist die folgenden Informationen auf:

* Vollständiger Name: **"John Doe"**
* E-Mail-Adresse: **"john.doe@contoso.com"**
* Bild: ![](media/function-user/john-doe-picture.png) 

|       Formel       |                                                                    Beschreibung                                                                    |                                                 Ergebnis                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             Datensatz mit allen Informationen für den aktuellen PowerApps-Benutzer.                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 Die E-Mail-Adresse des aktuellen PowerApps-Benutzers.                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   Der vollständige Name des aktuellen PowerApps-Benutzers.                                                    |                                               "John Doe"                                                |
|  **User().Image**   | Die Bild-URL für den aktuellen PowerApps-Benutzer.  Legen Sie die Eigenschaft **Image** des **Image**-Steuerelements auf diesen Wert fest, um das Bild in der App anzuzeigen. | "blob:1234...5678"<br><br>Für **ImageControl.Image**:<br>![](media/function-user/john-doe-picture.png) |

