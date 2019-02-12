---
title: Grundlegendes zu lokalen Datengateways für Canvas-Apps | Microsoft-Dokumentation
description: Referenzinformationen zu lokalen Datengateways, einschl. Installation in PowerApps und Problembehandlung
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/20/2017
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5dcc07f3ba9b9b4baca39cf2090a2c57cb7e67b7
ms.sourcegitcommit: 967812754d8e5b1ff72baa35ffbe548f3b9b0085
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726927"
---
# <a name="understand-on-premises-data-gateways-for-canvas-apps"></a>Grundlegendes zu lokalen Datengateways für Canvas-Apps
## <a name="installation-and-configuration"></a>Installation und Konfiguration
**Voraussetzungen**

Minimum:

* .NET 4.5 Framework
* 64-Bit-Version von Windows 7 oder Windows Server 2008 R2 (oder höher)

Empfohlen:
* 8-Kern-CPU
* 8 GB Arbeitsspeicher
* 64-Bit-Version von Windows 2012 R2 (oder höher)

Zu berücksichtigende Aspekte:

* Ein Gateway kann nicht auf einem Domänencontroller installiert werden.
* Sie sollten kein Gateway auf einem Computer wie einem Laptop installieren, der ausgeschaltet, im Energiesparmodus oder nicht mit dem Internet verbunden sein könnte, da das Gateway in diesen Fällen nicht ausgeführt werden kann. Darüber hinaus kann die Verwendung eines Drahtlosnetzwerks die Leistung des Gateways beeinträchtigen.

**Installation eines Gateways**

1. [Laden Sie das Installationsprogramm herunter](http://go.microsoft.com/fwlink/?LinkID=820931), und führen Sie es aus.

    ![Ausführen des Installationsprogramms](./media/gateway-reference/run-installer.png)

2. Klicken oder tippen Sie auf der ersten Seite des Installationsassistenten auf **Weiter**, um zu bestätigen, dass Sie die Erinnerung zum Installieren eines Gateways auf einem Laptop zur Kenntnis genommen haben.

    ![Erinnerung](./media/gateway-reference/laptop-reminder.png)

3. Geben Sie den Speicherort an, an dem Sie das Gateway installieren möchten, aktivieren Sie das Kontrollkästchen, um die Nutzungsbedingungen und die Datenschutzrichtlinie zu akzeptieren, und klicken oder tippen Sie dann auf **Installieren**.

4. Klicken oder tippen Sie in den **Benutzerkontensteuerung**-Dialogfeldern auf **Ja**, um den Vorgang fortzusetzen.

5. Auf dem nächsten Bildschirm des Assistenten klicken oder tippen Sie auf **Anmelden**, und geben Sie dann die Anmeldeinformationen an, mit denen Sie sich auch bei PowerApps anmelden.

    ![Anmelden](./media/gateway-reference/sign-in.png)

6. Klicken oder tippen Sie auf die Option, um ein neues Gateway zu registrieren, oder auf die Option, um ein vorhandenes Gateway zu migrieren, wiederherzustellen oder zu übernehmen, und klicken oder tippen Sie dann auf **Weiter**.

    ![Neues oder vorhandenes Gateway auswählen](./media/gateway-reference/new-existing.png)

   * Geben Sie zum Konfigurieren eines Gateways einen **Namen** und einen **Wiederherstellungsschlüssel** dafür ein, klicken oder tippen Sie auf **Konfigurieren** und dann auf **Schließen**.

       ![Konfigurieren eines neuen Gateways](./media/gateway-reference/configure-new.png)

       Geben Sie einen Wiederherstellungsschlüssel an, der aus mindestens acht Zeichen besteht, und bewahren Sie ihn an einem sicheren Ort auf. Sie benötigen diesen Schlüssel, wenn Sie das zugehörige Gateway migrieren, wiederherstellen oder übernehmen möchten.

   * Geben Sie zum Migrieren, Wiederherstellen oder Übernehmen eines vorhandenen Gateways den Namen des Gateways und den Wiederherstellungsschlüssel an, klicken oder tippen Sie auf **Konfigurieren**, und befolgen Sie dann alle weiteren Anweisungen.

       ![Ein vorhandenes Gateway wiederherstellen](./media/gateway-reference/recover-existing.png)

**Neustart des Gateways**

Das Gateway wird als Windows-Dienst ausgeführt, deshalb können Sie es auf verschiedene Weisen starten und beenden. Beispielsweise können Sie eine Eingabeaufforderung mit erweiterten Berechtigungen auf dem Computer öffnen, auf dem das Gateway ausgeführt wird, und dann einen der folgenden Befehle ausführen:

* Führen Sie diesen Befehl aus, um den Dienst zu beenden:<br>
  **net stop PBIEgwService**

* Führen Sie diesen Befehl aus, um den Dienst zu starten:<br>
  **net start PBIEgwService**

**Konfigurieren einer Firewall oder eines Proxys**

Informationen über das Bereitstellen von Proxyinformationen für Ihr Gateway finden Sie unter [Konfigurieren von Proxyeinstellungen](https://docs.microsoft.com/power-bi/service-gateway-proxy).

Sie können überprüfen, ob Ihre Firewall oder Ihr Proxy möglicherweise Verbindungen blockiert, indem Sie folgenden Befehl von einer PowerShell-Eingabeaufforderung ausführen. Dieser Befehl testet die Konnektivität mit dem Azure Service Bus. Es wird nur die Netzwerkkonnektivität getestet, und dies hat nichts mit dem Cloudserverdienst oder dem Gateway zu tun. Damit können Sie bestimmen, ob Ihr Computer eine Verbindung mit dem Internet herstellen kann.

**Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350**

Die Ergebnisse sollten diesem Beispiel ähneln. Wenn **TcpTestSucceeded** nicht **TRUE** ist, werden Sie möglicherweise durch eine Firewall blockiert.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

Wenn Sie einen vollständigen Test durchführen möchten, ersetzen Sie die Werte für **ComputerName** und **Port** durch die Werte, die unter **Konfigurieren von Ports** weiter unten in diesem Thema aufgeführt werden.

Die Firewall blockiert möglicherweise auch die Verbindungen, die der Azure Service Bus zu den Azure-Rechenzentren herstellt. Wenn dies der Fall ist, sollten Sie die IP-Adressen für Ihre Region für diese Rechenzentren auf die Whitelist setzen (die Blockierung aufheben). Eine Liste der Azure-IP-Adressen erhalten Sie [hier](https://www.microsoft.com/download/details.aspx?id=41653).

**Konfigurieren von Ports**

Das Gateway stellt eine ausgehende Verbindung mit dem Azure Service Bus her. Es kommuniziert über ausgehende Ports: TCP 443 (Standard), 5671, 5672, 9350 bis 9354. Für das Gateway sind keine eingehenden Ports erforderlich.

Erfahren Sie mehr über [Hybridlösungen](https://azure.microsoft.com/documentation/articles/service-bus-fundamentals-hybrid-solutions/).

Es wird empfohlen, dass Sie eine Whitelist mit IP-Adressen für Ihren Datenbereich in ihrer Firewall erstellen. Sie können die [IP-Liste des Microsoft Azure-Rechenzentrums](https://www.microsoft.com/download/details.aspx?id=41653) herunterladen, die wöchentlich aktualisiert wird.

> [!NOTE]
> In der IP-Liste des Azure-Rechenzentrums werden die Adressen in der [CIDR-Notation](http://whatismyipaddress.com/cidr) aufgelistet. Beispielsweise bedeutet 10.0.0.0/24 nicht 10.0.0.0 bis 10.0.0.24.

Hier finden Sie eine Liste der vollqualifizierten Domänennamen, die vom Gateway verwendet werden.

| Domänennamen | Ausgehende Ports | Beschreibung |
| --- | --- | --- |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443, 9350-9354 |Listener auf Service Bus Relay über TCP (erfordert 443 für Access Control-Tokenabruf) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| *.msftncsi.com |443 |Wird verwendet, um die Internetkonnektivität zu testen, wenn das Gateway vom Power BI-Dienst nicht erreicht werden kann. |

**Anmeldekonto**

Benutzer melden sich entweder mit einem Geschäfts- oder Schulkonto an. Dies ist Ihr Unternehmenskonto. Wenn Sie sich für ein Office 365-Angebot registriert und nicht Ihre tatsächliche geschäftliche E-Mail-Adresse angegeben haben, könnte sie so aussehen: nancy@contoso.onmicrosoft.com. Innerhalb eines Clouddiensts wird ihr Konto in einem Mandanten in Azure Active Directory (AAD) gespeichert. In den meisten Fällen entspricht der UPN Ihres AAD-Kontos der E-Mail-Adresse.

**Windows-Dienstkonto**

Das lokale Datengateway ist für die Verwendung von *NT SERVICE\PBIEgwService* für die Anmeldeinformation des Windows-Diensts konfiguriert. In der Standardeinstellung verfügt es über die Berechtigung für die Anmeldung als Dienst. Dies gilt im Kontext des Computers, auf dem Sie das Gateway installieren.

Dies ist nicht das Konto, das zum Herstellen einer Verbindung mit lokalen Datenquellen oder dem Geschäfts- oder Schulkonto verwendet wird, mit dem Sie sich bei den Clouddiensten anmelden.

Wenn bei Ihrem Proxyserver aufgrund der Authentifizierung Probleme auftreten, empfiehlt es sich, das Windows-Dienstkonto in ein Domänenbenutzerkonto oder verwaltetes Dienstkonto zu ändern, wie unter [Konfigurierung von Proxyeinstellungen](https://docs.microsoft.com/power-bi/service-gateway-proxy#changing-the-gateway-service-account-to-a-domain-user) beschrieben.

## <a name="tenant-level-administration"></a>Verwaltung auf Mandantenebene 

Aktuell können Mandantenadministratoren nicht alle Gateways an einer Stelle gesammelt verwalten, die für andere Benutzer installiert und konfiguriert sind.  Wenn Sie Mandantenadministrator sind, wird empfohlen, dass Sie alle Benutzer in Ihrer Organisation darum bitten, Sie für jedes installierte Gateway als Administrator hinzuzufügen. So können Sie alle Gateways in Ihrer Organisation über die Gatewayeinstellungen oder über [PowerShell-Befehle](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters) verwalten.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
#### <a name="general"></a>Allgemein
**Frage:** Welche Datenquellen werden vom Gateway unterstützt?  
**Antwort:** Zum Zeitpunkt der Erstellung dieses Dokuments:

* SQL Server
* SharePoint
* Oracle
* Informix
* FileSystem
* DB2

**Frage:** Benötige ich ein Gateway für Datenquellen in der Cloud wie z.B. SQL Azure?  
**Antwort:** Nein. Ein Gateway stellt nur eine Verbindung zu lokalen Datenquellen her.

**Frage:** Wie heißt der eigentliche Windows-Dienst?  
**Antwort:** Unter „Dienste“ heißt das Gateway **Power BI Enterprise Gateway Service**.

**Frage:** Gibt es eingehende Verbindungen zum Gateway aus der Cloud?  
**Antwort:** Nein. Das Gateway verwendet ausgehende Verbindungen zum Azure Service Bus.

**Frage:** Was geschieht, wenn ich ausgehende Verbindungen blockiere? Was muss ich öffnen?  
**Antwort:** In der Liste oben finden Sie die Ports und Hosts, die vom Gateway verwendet werden.

**Frage:** Muss das Gateway auf demselben Computer installiert werden wie die Datenquelle?  
**Antwort:** Nein. Das Gateway stellt eine Verbindung mit der Datenquelle mithilfe der bereitgestellten Verbindungsinformationen her. Stellen Sie sich das Gateway in diesem Sinn wie eine Clientanwendung vor. Es muss nur eine Verbindung zum bereitgestellten Servernamen herstellen können.

**Frage:** Wie ist die Latenzzeit für das Ausführen von Abfragen an eine Datenquelle über das Gateway? Was ist die beste Architektur?  
**Antwort:** Installieren Sie das Gateway so nahe an der Datenquelle wie möglich, um die Netzwerklatenz zu reduzieren. Wenn Sie das Gateway auf der Datenquelle installieren können, wird die Latenzzeit minimiert. Berücksichtigen Sie auch die Rechenzentren. Wenn Ihr Dienst zum Beispiel das Rechenzentrum im Westen der USA nutzt und SQL Server auf einem virtuellen Azure-Computer gehostet wird, möchten Sie, dass sich der virtuelle Azure-Computer auch im Westen der USA befindet. Dadurch werden die Latenzzeit minimiert und Gebühren für ausgehenden Datenverkehr auf dem virtuellen Azure-Computer vermieden.

**Frage:** Gibt es Anforderungen an die Netzwerkbandbreite?  
**Antwort:** Es wird empfohlen, über eine Netzwerkverbindung mit gutem Durchsatz zu verfügen. Jede Umgebung ist anders, und die Menge der übermittelten Daten wird sich auf die Ergebnisse auswirken. ExpressRoute könnte Ihnen dabei helfen, einen gewissen Durchsatz zwischen lokalen und Azure-Rechenzentren zu gewährleisten.

Sie können das Drittanbietertool [Azure Speed Test-App](http://azurespeedtest.azurewebsites.net/) verwenden, um Ihren Durchsatz zu messen.

**Frage:** Kann das Gateway Windows-Dienst mit einem Azure Active Directory-Konto ausgeführt werden?  
**Antwort:** Nein. Der Windows-Dienst muss über ein gültiges Windows-Konto verfügen. In der Standardeinstellung wird er mit der Dienst-SID *NT SERVICE\PBIEgwService* ausgeführt.

**Frage:** Wie werden Ergebnisse zurück an die Cloud übermittelt?  
**Antwort:** Dies erfolgt über den Azure Service Bus. Weitere Informationen finden Sie unter [Funktionsweise des Gateways](gateway-reference.md#how-the-gateway-works).

**Frage:** Wo werden meine Anmeldeinformationen gespeichert?  
**Antwort:** Die Anmeldeinformationen, die Sie für eine Datenquelle eingeben, werden verschlüsselt im Gatewayclouddienst gespeichert. Die Anmeldeinformationen werden auf dem Gateway lokal entschlüsselt.

**Frage:** Kann ich das Gateway in einem Umkreisnetzwerk (auch als DMZ bzw. demilitarisierte Zone bezeichnet) platzieren?  
**Antwort:** Für das Gateway ist eine Verbindung zur Datenquelle erforderlich. Wenn sich die Datenquelle nicht in Ihrem Umkreisnetzwerk befindet, kann das Gateway möglicherweise keine Verbindung herstellen. Zum Beispiel befindet sich der Computer, auf dem SQL Server ausgeführt wird, möglicherweise nicht in Ihrem Umkreisnetzwerk, und Sie können aus dem Umkreisnetzwerk keine Verbindung zu diesem Computer herstellen. Wenn Sie das Gateway in Ihrem Umkreisnetzwerk platzieren, kann das Gateway keine Verbindung zu dem Computer herstellen, auf dem SQL Server ausgeführt wird.

#### <a name="high-availabilitydisaster-recovery"></a>Hohe Verfügbarkeit und Notfallwiederherstellung
**Frage:** Ist es geplant, Szenarios mit Hochverfügbarkeit für das Gateway zu aktivieren?  
**Antwort:** Hochverfügbarkeit wird durch Verknüpfen von mindestens zwei Gateways in demselben Cluster aktiviert.  Für Gatewaycluster mit Hochverfügbarkeit ist das Update von November 2017 auf ein lokales Datengateway oder höher erforderlich.  Weitere Informationen finden Sie unter [Blogbeitragsankündigung](https://powerapps.microsoft.com/en-us/blog/gateway-high-availability-for-powerapps-and-flow).

**Frage:** Welche Optionen sind für die Notfallwiederherstellung verfügbar?  
**Antwort:** Sie können den Wiederherstellungsschlüssel zum Wiederherstellen oder Verschieben eines Gateways verwenden. Geben Sie beim Installieren des Gateways den Wiederherstellungsschlüssel an.

**Frage:** Was ist der Vorteil des Wiederherstellungsschlüssels?  
**Antwort:** Er bietet eine Möglichkeit zum Migrieren oder Wiederherstellen Ihrer Gatewayeinstellungen nach einem Notfall.

#### <a name="troubleshooting"></a>Problembehandlung
**Frage:** Wo befinden sich die Gatewayprotokolle?  
**Antwort:** Siehe [Tools](gateway-reference.md#tools) weiter unten in diesem Thema.

**Frage:** Wie kann ich sehen, welche Abfragen an die lokale Datenquelle übermittelt werden?  
**Antwort:** Sie können die Abfrageablaufverfolgung aktivieren, die auch die Abfragen umfasst, die gerade übermittelt werden. Denken Sie daran, sie nach der Problembehandlung wieder in den ursprünglichen Wert zu ändern. Wenn Sie die Abfrageablaufverfolgung aktiviert lassen, werden die Protokolle größer.

Sie können sich auch Tools ansehen, die die Datenquelle für die Abfrageablaufverfolgung bietet. Sie können beispielsweise erweiterte Ereignisse oder SQL Profiler für SQL Server und Analysis Services verwenden.

## <a name="how-the-gateway-works"></a>Funktionsweise des Gateways
![So funktioniert's](./media/gateway-reference/gateway-arch.png)

Wenn ein Benutzer mit einem Element interagiert, das mit einer lokalen Datenquelle verbunden ist:  

1. Der Clouddienst erstellt eine Abfrage zusammen mit den verschlüsselten Anmeldeinformationen für die Datenquelle und sendet die Abfrage an die Warteschlange für die Verarbeitung durch das Gateway.

2. Der Gatewayclouddienst analysiert die Abfrage und übermittelt die Anforderung mithilfe von Push an den [Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/).

3. Das lokale Datengateway fragt den Azure Service Bus nach ausstehenden Anforderungen ab.

4. Das Gateway erhält die Abfrage, entschlüsselt die Anmeldeinformationen und stellt mit diesen Anmeldeinformationen eine Verbindung zu der (den) Datenquelle(n) her.

5. Das Gateway übermittelt die Abfrage für die Ausführung an die Datenquelle.

6. Die Ergebnisse werden von der Datenquelle zurück an das Gateway und von dort aus an den Clouddienst übermittelt. Der Dienst verwendet dann die Ergebnisse.

## <a name="troubleshooting"></a>Problembehandlung
#### <a name="update-to-the-latest-version"></a>Aktualisieren auf die neueste Version
Viele Probleme können auftreten, wenn die Gatewayversion veraltet ist.  Es wird allgemein empfohlen, die neueste Version zu verwenden.  Wenn Sie das Gateway einen Monat oder länger nicht aktualisiert haben, empfiehlt es sich, die neueste Version des Gateways zu installieren und zu sehen, ob das Problem erneut auftritt.

#### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Fehler: Fehler beim Hinzufügen des Benutzers zur Gruppe.  (-2147463168   PBIEgwService   Leistungsprotokollbenutzer   )
Dieser Fehler wird möglicherweise angezeigt, wenn Sie versuchen, das Gateway auf einem Domänencontroller zu installieren, da dies nicht unterstützt wird. Sie müssen das Gateway auf einem Computer bereitstellen, der kein Domänencontroller ist.

## <a name="tools"></a>Tools
#### <a name="collecting-logs-from-the-gateway-configurator"></a>Sammeln von Protokollen über den Gateway-Konfigurator
Sie können mehrere Protokolle für das Gateway sammeln. Beginnen Sie immer mit den Protokollen!

**Installationsprotokolle**

%localappdata%\Temp\On-premises_data_gateway_*.log

**Konfigurationsprotokolle**

%localappdata%\Microsoft\on-premises data gateway\GatewayConfigurator*.log

**Enterprise Gateway-Dienstprotokolle**

C:\Users\PBIEgwService\AppData\Local\Microsoft\on-premises data gateway\Gateway*.log

**Ereignisprotokolle**

Die Protokolle des **lokalen Datengatewaydiensts** befinden sich unter **Anwendungs- und Dienstprotokolle**.

![Ereignisprotokolle](./media/gateway-reference/event-logs.png)

#### <a name="fiddler-trace"></a>Ablaufverfolgung mit Fiddler
[Fiddler](http://www.telerik.com/fiddler) ist ein kostenloses Tool von Telerik zur Überwachung des HTTP-Verkehrs.  Sie können den eingehenden und ausgehenden Datenverkehr mit dem Power BI-Dienst vom Clientcomputer aus prüfen. Dadurch können Fehler und sonstige zugehörige Informationen angezeigt werden.
