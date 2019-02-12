---
title: Delegierbare Datenquellen in Canvas-Apps | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste mit allen unterstützten delegierbaren Datenquellen in Canvas-Apps.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/15/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 98931d4692a61839e0530682bd2d40258c07b7df
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42825761"
---
# <a name="delegable-data-sources-in-canvas-apps"></a>Delegierbare Datenquellen in Canvas-Apps
Wie im Artikel [Grundlagen der Delegierung](delegation-overview.md) ausführlich beschrieben, handelt es sich um Delegierung, wenn PowerApps die Verarbeitung von Daten an die Datenquelle delegiert, anstatt die Daten zur lokalen Verarbeitung in die Canvas-App zu verschieben.

Die Delegierung wird nur für tabellarische Datenquellen unterstützt. In dieser Liste sind die tabellarischen Datenquellen angegeben und mit einem Hinweis dazu versehen, ob die Delegierung unterstützt wird. Weitere Details hierzu finden Sie im nächsten Abschnitt.

* Common Data Service: **Ja**
* SharePoint: **Ja**
* SQL Server: **Ja**
* Dynamics 365: **Ja**
* Salesforce: **Ja**
* Dynamics 365 for Operations: Noch nicht
* Dynamics 365 for Financials: Noch nicht
* Dynamics NAV: Noch nicht
* Google Tabellen: Noch nicht

Es werden ständig weitere tabellarische Datenquellen und die Unterstützung der Delegierung hinzugefügt.

In diesem Dokument ist der aktuelle Status der unterstützten Delegierung pro Datenquelle angegeben.

## <a name="prerequisites"></a>Voraussetzungen

* Machen Sie sich mit dem Artikel [ Grundlagen der Delegierung](delegation-overview.md) vertraut.

## <a name="list-of-data-sources-and-supported-delegation"></a>Liste mit Datenquellen und Angabe zur Unterstützung der Delegierung
Diese Liste mit Datenquellen und delegierbaren Funktionen und Prädikaten wird regelmäßig aktualisiert, um den aktuellen Status der Unterstützung von Delegierungen in PowerApps widerzuspiegeln.

### <a name="top-level-delegable-functions"></a>Delegierbare Funktionen der obersten Ebene

| &nbsp; | Common Data Service | SharePoint | SQL Server | Dynamics 365 | Salesforce |
| --- | --- | --- | --- | --- | --- |
| Average |Nein |Nein |Ja |Nein |Nein |
| Filter |Ja |Ja |Ja |Ja |Ja |
| LookUp |Ja |Ja |Ja |Ja |Ja |
| Max. |Nein |Nein |Ja |Nein |Nein |
| Min |Nein |Nein |Ja |Nein |Nein |
| Search |Ja<sup>1</sup> |Nein |Ja |Ja |Ja |
| Sortieren |Ja |Ja |Ja |Ja |Ja |
| SortByColumns |Ja |Ja |Ja |Ja |Ja |
| Sum |Nein |Nein |Ja |Nein |Nein |

<sup>1</sup>Nur für Zeichenfolgenfelder

### <a name="filter-and-lookup-delegable-predicates"></a>Delegierbare Filter- und LookUp-Prädikate

| &nbsp; | Common Data Service | SharePoint | SQL Server | Dynamics 365 | Salesforce |
| --- | --- | --- | --- | --- | --- |
| Not |Ja |Nein |Ja |Ja |Ja |
| IsBlank |Nein |Nein |Ja |Ja |Nein |
| TrimEnds |Nein |Nein |Ja |Nein |Nein |
| Len |Nein |Nein |Ja |Nein |Nein |
| +, - |Nein |Nein |Ja |Nein |Nein |
| <, <=, =, <>, >, >= |Ja |Ja (nur =) |Ja |Ja |Ja |
| And (&&), Or (&#124;&#124;), Not (!) |Ja<sup>2</sup> |Ja (mit Ausnahme von „Not“ (!)) |Ja |Ja |Ja |
| in |Nein |Nein |Ja |Nein |Ja |
| StartsWith |Nein |Ja |Nein |Nein |Nein |

<sup>2</sup>Nur für Operatoren. And/Or/Not-Funktion wird nicht delegiert.
