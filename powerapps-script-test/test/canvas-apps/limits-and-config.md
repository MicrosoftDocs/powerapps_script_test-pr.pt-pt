---
title: Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps | Microsoft-Dokumentation
description: Systemanforderungen, Einschränkungen und Konfigurationswerte für in PowerApps erstellte Canvas-Apps
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/07/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5ba279e361dfe450de1187cf6aca87bc026178ba
ms.sourcegitcommit: 60006ce9cb21c59e588c00f2ba5c41ffebbbba09
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/30/2018
ms.locfileid: "47456296"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps
In diesem Artikel werden Anforderungen für Geräteplattformen und Webbrowser sowie Einschränkungen und Konfigurationswerte für PowerApps behandelt.

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>Unterstützte Plattformen für das Ausführen von Canvas-Apps mithilfe der PowerApps-App

| **Mindestens erforderlich** | **Empfohlen** |
| --- | --- |
| iOS 9.3 oder höher |iOS 10 oder höher mit mindestens 2 GB RAM |
| Android 5 oder höher |Android 7 oder höher mit mindestens 4 GB RAM |
| Windows 8.1 oder höher (nur PC) |Windows 10 Fall Creators Update mit mindestens 8 GB RAM|

## <a name="supported-browsers-for-running-canvas-apps"></a>Unterstützte Browser für das Ausführen von Canvas-Apps

| **Browser** | **Betriebssystem** |
| --- | --- |
| Google Chrome (aktuelle Version)<br>(empfohlen) |Windows 7 SP1, 8.1 und 10 <br>Android 5 oder höher <br>iOS 8 oder höher<br>macOS |
| Microsoft Edge (neueste Version)<br>(empfohlen) |Windows 10 |
| Microsoft Internet Explorer 11 (mit deaktivierter Kompatibilitätsansicht) |Windows 7 SP1, 8.1 und 10 |
| Mozilla Firefox (aktuelle Version) |Windows 7 SP1, 8.1 und 10 <br> Android 5 oder höher <br>iOS 8 oder höher <br>macOS |
| Apple Safari (aktuelle Version) |iOS 8 oder höher <br>macOS |

## <a name="supported-browsers-for-powerapps-studio"></a>Unterstützte Browser für PowerApps Studio

| **Browser** | **Betriebssystem** |
| --- | --- |
| Google Chrome (aktuelle Version)<br>(empfohlen) |Windows 7 SP1, 8.1 und 10 <br>macOS |
| Microsoft Edge (neueste Version)<br>(empfohlen) |Windows 10 |
| Microsoft Internet Explorer 11 (mit deaktivierter Kompatibilitätsansicht) |Windows 7 SP1, 8.1 und 10 |

## <a name="request-limits"></a>Anforderungsbegrenzungen
Diese Begrenzungen gelten für jede einzelne ausgehende Anforderung:

| Name | Maximale Anzahl |
| --- | --- |
| Timeout |180 Sekunden |
| Wiederholungsversuche |4 |

> [!NOTE]
> Der Wert für die Anzahl der Wiederholungsversuche kann variieren. Bei bestimmten Fehlerbedingungen ist ein wiederholter Versuch nicht erforderlich.

## <a name="ip-addresses"></a>IP-Adressen
Anforderungen von PowerApps verwenden IP-Adressen, die vom Bereich der [Umgebung](../../administrator/environments-overview.md) abhängig sind, in der sich die App befindet. Es werden keine für PowerApps-Szenarios verfügbaren vollqualifizierten Domänennamen veröffentlicht.

Aufrufe, die von einer API erfolgen, die durch eine App verbunden ist (z.B. die SQL-API oder die SharePoint-API), stammen von der IP-Adresse, die weiter unten in diesem Thema angegeben wird.

Sie sollten diese Adressen beispielsweise verwenden, wenn Sie eine Whitelist mit IP-Adressen für eine Azure SQL-Datenbank erstellen müssen.

> [!IMPORTANT]
>   Wenn Sie bereits über Konfigurationen verfügen, aktualisieren Sie diese so schnell wie möglich (vor dem 30. September 2018), sodass diese die in der folgenden Liste aufgeführten IP-Adressen für die Regionen umfassen, in denen Ihre PowerApps-Apps vorhanden sind, und diesen entsprechen.

| Region | Ausgehende IP |
| --- | --- |
| Asien | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19, 52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 52.187.53.78, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124, 23.97.72.250  |
| Australien  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174, 13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.188.38, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35, 13.70.88.23 |
| Brasilien | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Kanada | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152, 52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56, 52.229.123.161, 52.233.27.68 |
| Europa | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 52.178.37.42, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254, 52.164.249.26, 137.117.161.181 |
| Indien  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218, 52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.49.180, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245, 52.172.153.107 |
| Japan | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248, 104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 104.214.151.229, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229, 13.78.121.151 |
| Vereinigtes Königreich | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| USA | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49, 104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191 |
| USA (Frühzeitiger Zugriff)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157, 52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 52.161.31.35, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29, 13.66.208.24 |


## <a name="required-services"></a>Erforderliche Dienste
In dieser Liste werden alle Dienste aufgeführt, mit denen PowerApps Studio kommuniziert; zudem wird ihr Verwendungszweck angegeben. Ihr Netzwerk darf diese Dienste **nicht** blockieren.

| Domäne(n) | Protokolle | Verwendung |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |Laufzeit der Connector/APIs |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph: Zum Abrufen von Benutzerinformationen (z.B. Profilfotos) |
| gallery.azure.com |https |Beispiel- und Vorlagen-Apps |
| *.azure-apim.net |https |API-Hubs: Verschiedene Unterdomänen für jedes Gebietsschema |
| *.powerapps.com |https |WebAuth + Portal |
| *.azureedge.net |https |WebAuth |
| *.blob.core.windows.net |https |Blob Storage |
| vortex.data.microsoft.com |https |Telemetrie |

> [!NOTE]
> Wenn Sie ein VPN verwenden, muss dieses so konfiguriert sein, dass „localhost“ vom Tunneling für PowerApps Mobile ausgeschlossen wird.
