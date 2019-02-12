---
title: Übersicht über die Power BI-Verbindung | Microsoft-Dokumentation
description: Liste der verfügbaren Power BI-Verbindungen
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/12/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 73ce15ff171ce72b9364844ed77f6e3aed079a64
ms.sourcegitcommit: 3dc330d635aaf5bc689efa6bd39826d6e396c832
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48875805"
---
# <a name="connect-to-power-bi-from-powerapps"></a>Herstellen einer Verbindung mit Power BI aus PowerApps
![Power BI](./media/connection-powerbi/powerbiicon.png)

Power BI ist eine Suite von Business Analytics-Tools zum Analysieren von Daten und Teilen von Erkenntnissen. Mit funktionsreichen Dashboards auf jedem Gerät behalten Sie die Kontrolle über Ihr Geschäft und erhalten schnell Antworten. Sie können in Ihrer App den Status der Datenwarnungen überprüfen, die Sie im Power BI-Dienst eingerichtet haben. Weitere Informationen zu Datenwarnungen in Power BI finden Sie auf der [Dokumentationsseite](https://docs.microsoft.com/power-bi/service-set-data-alerts).

In diesem Thema wird gezeigt, wie Sie die Power BI-Verbindung in einer App verwenden, und die verfügbaren Funktionen werden aufgelistet.

## <a name="prerequisites"></a>Voraussetzungen
* [Registrieren](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
* Die Power BI-[Verbindung](https://powerapps.microsoft.com/tutorials/add-manage-connections/) hinzufügen
* Eine App aus einer [Vorlage](https://powerapps.microsoft.com/tutorials/get-started-test-drive/), aus [Daten](https://powerapps.microsoft.com/tutorials/get-started-create-from-data/) oder [von Grund auf neu](https://powerapps.microsoft.com/tutorials/get-started-create-from-blank/) erstellen

## <a name="use-the-power-bi-connection-in-your-app"></a>Verwenden der Power BI-Verbindung in der App
### <a name="list-the-alerts-that-youve-set-up-in-the-power-bi-service"></a>Auflisten der Warnungen, die Sie im Power BI-Dienst eingerichtet haben
1. Wählen Sie im Menü **Insert** (Einfügen) die Option **Katalog** aus, und fügen Sie eine der **Text galleries** (Textkataloge) hinzu.
2. Um die Warnungen des aktuellen Benutzers anzuzeigen, legen Sie die [Items](../controls/properties-core.md)-Eigenschaft des Katalogs auf die folgende Formel fest:

   `PowerBI.GetAlerts()`

Der Katalog wird mit der Liste der Warnungen aktualisiert. Für jede Warnung erhalten Sie den Namen der Warnung, die ID der Warnung und die ID des Gruppenarbeitsbereichs, in dem die Warnung konfiguriert wurde. Sie benötigen die Warnungs-ID, um weitere Informationen zur Warnung zu erhalten.

### <a name="view-the-status-of-an-alert"></a>Anzeigen des Status einer Warnung
Um den Status der Warnung anzuzeigen, rufen Sie die CheckAlertStatus-Funktion mit der Warnungs-ID auf, die Sie im obigen Schritt erhalten haben.

Die Warnungs-ID kann entweder als Literalzeichenfolge (z. B. „1234“) oder als Verweis auf einen durch den Aufruf von GetAlerts() aufgefüllten Katalogabschnitt (z. B. Gallery1.Selected.alertId) übergeben werden.

Um den Vorgang fortzusetzen, fügen Sie eine Bezeichnung hinzu, und legen Sie dessen [Text](../controls/properties-core.md)-Eigenschaft auf eine der folgenden Formeln fest:

* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertTitle`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).currentTileValue`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertThreshold`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).isAlertTriggered`

Die Bezeichnung wird mit dem aktuellen Status der Warnung aktualisiert.

## <a name="view-the-available-functions"></a>Anzeigen der verfügbaren Funktionen
Diese Verbindung umfasst die folgenden Funktionen:

| Funktionsname | Beschreibung |
| --- | --- |
| GetAlerts |Listet die Warnungen auf, die Sie im Power BI-Dienst eingerichtet haben. |
| CheckAlertStatus |Überprüft den Status einer bestimmten Warnung. |

## <a name="getalerts"></a>GetAlerts
Auflisten der Warnungen, die Sie im Power BI-Dienst eingerichtet haben.

#### <a name="input-properties"></a>Eingabeeigenschaften
Keine

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| value |Array |Nein |Ein Array der Datenwarnungen, die Sie im Power BI-Dienst eingerichtet haben. Jedes Element im Array enthält: <ul><li>alertTitle: der Titel der Warnung</li><li>alertId: die ID der Warnung</li><li>groupId: die ID der Gruppe, in der die Warnung erstellt wurde</li></ul> |

## <a name="checkalertstatus"></a>CheckAlertStatus
Überprüfen des Status einer Warnung.

> [!NOTE]
> Anforderungen an diesen Endpunkt werden pro Warnung gedrosselt, wenn die Funktion zu häufig aufgerufen wird.

#### <a name="input-properties"></a>Eingabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| alertId |Ganze Zahl |Ja |Die von GetAlerts zurückgegebene ID der Warnung |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| tileValue |Zahl |Nein |Der Wert der Kachel, als die Warnung ausgelöst wurde |
| tileUrl |Zeichenfolge |Nein |Die URL für die Kachel, die die Warnung aufweist |
| alertTitle |Zeichenfolge |Nein |Der Name der Warnung |
| isAlertTriggered |Boolesch |Nein |Gibt an, ob die Warnung derzeit ausgelöst ist |
| alertThreshold |Zahl |Nein |Der Schwellenwert, ab dem die Warnung ausgelöst wird |

## <a name="helpful-links"></a>Nützliche Links
Alle [verfügbaren Verbindungen](../connections-list.md).  
Erfahren Sie, wie Sie Ihren Apps [Verbindungen hinzufügen](../add-manage-connections.md).

