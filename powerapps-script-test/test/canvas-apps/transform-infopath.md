---
title: Transformieren des InfoPath-Formulars in eine Canvas-App | Microsoft-Dokumentation
description: Starten Sie zum Transformieren Ihres InfoPath-Formulars in PowerApps mit Informationen zu üblichen Szenarios, und erfahren Sie, wie Sie diese Elemente in einer Canvas-App erstellen.
author: richardriley99
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/05/2018
ms.author: rriley
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c2d72368b36f2de854a0aa575f9ef44f2f966ace
ms.sourcegitcommit: 2300de0a0486187762f830068c872116d5b04c32
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806223"
---
# <a name="transform-your-infopath-form-to-powerapps"></a>Transformieren des InfoPath-Formulars in ein PowerApps-Formular

Erstellen Sie gerne nützliche Formulare in InfoPath und möchten lernen, wie Sie diese auf einer robusteren Plattform bereitstellen?

## <a name="key-advantages-of-powerapps-over-infopath"></a>Hauptvorteile von PowerApps im Vergleich zu InfoPath

Wie die meisten InfoPath-Poweruser nutzen Sie Ihre hervorragenden Fähigkeiten sicher schon seit einiger Zeit, um beeindruckende Formulare zu erstellen. Sie sind zwar mit den von Ihnen erstellten Formularen sehr zufrieden, wissen aber auch, dass diese ihre Grenzen haben: Sie sind &quot;nicht mehr zeitgemäß&quot;, bieten keine ideale Benutzeroberfläche für mobile Geräte und lassen sich nicht mit anderen Diensten verbinden, ohne Code zu schreiben. Zudem ist ihre Zukunftsfähigkeit ungewiss.

Das PowerApps-Team hat von diesen und vielen anderen Herausforderungen gehört. Sie haben hart daran gearbeitet, die Benutzererfahrung zu verbessern und Ihnen das Erstellen von Canvas-Apps mithilfe Ihrer bestehenden Geschäfts- und Technologiefähigkeiten zu ermöglichen. Mithilfe von PowerApps können Sie schnell die richtigen Geschäftslösungen erstellen und implementieren, ohne Code schreiben zu müssen.

**PowerApps für eine leistungsstarke Zukunft**  
PowerApps ist eine Software-as-a-Service-Plattform (SaaS), mit der Sie schnell und ohne zusätzlichen Aufwand hochfunktionale Apps erstellen können, die Sie im Web, in SharePoint, in Dynamics 365, in Teams, in Power BI oder auf einem mobilen Gerät bereitstellen können. Und weil Sie die Apps bereitstellen können, indem Sie einfach die URL zu Ihrer veröffentlichten App weitergeben, sind sie ebenso einfach zu aktualisieren.

**Teilen Ihrer Apps**  
Haben Sie schon mal versucht, eine App zu erstellen und sie dann für iOS- oder Android-Geräte zu veröffentlichen? Das ist gar nicht so einfach. Wenn Sie eine zweite App bereitstellen oder Ihre vorhandene App aktualisieren möchten, müssen Ihre Benutzer wesentlich mehr Schritte ausführen. Mit PowerApps ist dies anders. Ihre Benutzer installieren PowerApps Mobile auf ihren Geräten und melden sich an. Und voilà – schon stehen ihnen all die hochfunktionalen Apps zur Verfügung, die Sie für sie freigegeben haben. Wenn Sie in Zukunft diese Apps aktualisieren oder neue Apps freigeben, werden die Apps auf den Geräten der Benutzer angezeigt. Mobile Apps ohne den Aufwand für die Geräteverwaltung sind ein großer Gewinn für Sie und Ihr Unternehmen.

**Apropos mobile Geräte**  
Mit PowerApps können Sie die Leistungsfähigkeit der mobilen Geräte der Benutzer für sich nutzen. Über Ihre App haben Sie Zugriff auf die Beschleunigung, die Kamera, den Kompass, die Verbindungsinformationen und die Positionssignale. Bei der Erstellung von Apps eröffnet ihnen dies eine ganze Welt von Möglichkeiten. Und auch die Touchfunktionalität läuft in PowerApps ganz automatisch, d.h. Sie müssen bei der App-Erstellung nichts zusätzlich programmieren.

**Vorkonfigurierte Features**  
Mit InfoPath arbeiten Sie in der Regel mit Daten aus einer einzigen Quelle. Schwierig wurde es allerdings, wenn Sie eine andere Quelle (z.B. eine SharePoint-Liste in einer anderen Websitesammlung) aktualisieren oder eine Verbindung mit externen Diensten herstellen wollten. Konzepte wie „CodeBehind“ haben Ihnen den Schlaf geraubt. PowerApps ist so konzipiert, dass Sie mit mehreren Datenquellen und Dienstverbindungen in einer App arbeiten können. Derzeit unterstützen [mehr als 200 Connectors](connections-list.md#all-standard-connectors) eine Kombination aus lokalen und cloudbasierten Daten, z.B. Microsoft Office 365- und Azure-Dienste wie Microsoft Flow und Dynamics 365. Sie können auch Verbindungen mit einer Vielzahl von Drittanbieterdiensten herstellen, beispielsweise Dropbox, Google, Salesforce, Slack sowie weiteren gängigen Zielen.

Jetzt können Sie Lösungen entwickeln, die sich an Benutzeranforderungen anpassen lassen und nicht von dem Speicherort der ursprünglichen Daten abhängen.

## <a name="powerapps-and-sharepoint-even-better-together"></a>PowerApps und SharePoint: gemeinsam noch besser

PowerApps ist ein großartiges Tool, um Ihr SharePoint-Erlebnis auf zwei Arten zu verbessern. Sie haben die Möglichkeit, entweder die Formulare für eine SharePoint-Liste anzupassen oder eine eigenständige App für die Arbeit mit SharePoint-Daten zu erstellen.

Die **Anpassung eines SharePoint-Formulars** ist eine praktische Methode, wenn Sie die Art und Weise anpassen möchten, in der Benutzer Elemente in einer Liste hinzufügen, anzeigen oder bearbeiten, die sie bei ihrer täglichen Arbeit verwenden. Wenn Sie auf **Formulare anpassen** klicken, wird eine &quot;Formular-App&quot; mit einem einzigen Bildschirm erstellt, in der die Modi (Neu/Bearbeiten/Ansicht) kontextabhängig geändert werden. SharePoint verwaltet diese Apps; ihre Berechtigungen sind die gleichen wie die Listenberechtigungen zum Bearbeiten bzw. Anzeigen.

Die **Erstellung einer PowerApps-Zeichenbereich-App aus SharePoint** ermöglicht es Ihnen, die App selbst auf einem mobilen Gerät auszuführen. Sie können die App auch in eine SharePoint-Seite einbetten. Mit einem Klick wird eine App mit drei Bildschirmen erstellt („Liste durchsuchen“, „Details anzeigen“ und „Element erstellen/aktualisieren“). Das Berechtigungs-/Freigabemodell für diese Apps ist nicht an SharePoint gebunden, sondern wird von PowerApps verwaltet.

Nachdem Sie nun den Unterschied zwischen den beiden Optionen kennen, erhalten Sie im folgenden Abschnitt einen Überblick über deren Verwendung.

## <a name="sharepoint-forms"></a>SharePoint-Formulare

Das PowerApps-Team und das SharePoint-Team haben gemeinsam eine neue Anpassungsmethode erstellt, die Sie mit SharePoint verwenden können. Wie die meisten InfoPath-Entwickler haben Sie sicherlich gelernt, wie Sie InfoPath einsetzen, um mit SharePoint zu interagieren. SharePoint ist ein großartiges Tool, allerdings sind die Standardformulare ein wenig umständlich und erlauben keine Anpassung oder Geschäftslogik ohne InfoPath. Zumindest war es bisher so.

Mit PowerApps können Sie nun Ihre Listenformulare als native Funktionalität anpassen. Und wenn Sie dies tun, erhalten Sie den vollen Leistungsumfang von PowerApps. Im folgenden Screenshot sehen Sie ein Beispiel für ein PowerApps-Formular mit eingebettetem Power BI-Bericht. Die gesamte Lösung wurde in weniger als 15 Minuten erstellt.

![SharePoint-Integration](./media/transform-infopath/sharepoint-integration.png)

Ein weiteres wichtiges Feature von PowerApps ist die Möglichkeit, eine Verbindung zu einer anderen SharePoint-Websitesammlung oder einer anderen Umgebung aus dem gleichen Formular herzustellen. Möchten Sie beispielsweise ein Formular erstellen, das Daten aus Ihrer SharePoint Online-Umgebung und lokalen SharePoint-Umgebung gleichzeitig anzeigt und aktualisiert? Kein Problem. Installieren Sie das [lokale Datengateway](gateway-management.md), und innerhalb weniger Minuten können Sie PowerApps, Power BI, Microsoft Flow und Azure Logic Apps mit Ihren lokalen Daten verbinden. Es sind keine Änderungen an Firewallregeln erforderlich. Sie können sogar noch einen Schritt weitergehen, in dem Sie diese App mit Microsoft Flow verbinden.

## <a name="a-standalone-sharepoint-app"></a>Eine eigenständige SharePoint-App

Verwenden Sie diese Methode, wenn Sie nicht nur die Funktion für Listenformulare aktualisieren, sondern eine vollständige, eigenständige App basierend auf Ihren SharePoint-Daten erstellen möchten. Dies ist auch der beste Weg für den Einstieg. So können Sie die Funktionsweise der PowerApps-Canvas kennenlernen und dann Apps aus einer Vielzahl von Datenquellen erstellen.

Führen Sie die folgenden Schritte aus, um loszulegen:

1. Öffnen Sie die SharePoint-Liste, von der aus Sie eine App erstellen möchten.
1. Wählen Sie in der Menüleiste **PowerApps** aus, und klicken Sie dann auf **App erstellen**.
1. Geben Sie einen Namen an, und klicken Sie auf **Erstellen**.

PowerApps erstellt eine App, die Sie dann anpassen können.

Starten Sie die Erstellung Ihrer ersten App mit einer einfachen benutzerdefinierten Liste, die nur einige wenige Felder verschiedener Typen enthält. So können Sie eine solide Grundlage erstellen und behalten den Überblick. Machen Sie sich keine Gedanken, Sie sind im Handumdrehen ein Profi und bereit, komplexe Apps in Angriff zu nehmen. Hilfreiche Informationen zum Erstellen Ihrer ersten App finden Sie in dieser [Dokumentation](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online) und in diesem [Communityvideo](https://youtu.be/BnYe_7fpZRM). Die folgenden Beispiele zeigen allgemeine InfoPath-Aufgaben und wie Sie sie in PowerApps erledigen. Jede davon baut auf einer einfachen SharePoint-Listen-App auf.

## <a name="how-do-you-do-that-with-powerapps"></a>Wie funktioniert das mit PowerApps?

Nun, da Sie die grundlegenden Konzepte kennen, gehen wir einen Schritt weiter. Ihre erste App haben Sie in der Tasche. Der folgende Abschnitt hilft Ihnen dabei, einige der gängigen InfoPath-Konzepte in PowerApps anzuwenden.

**Ausblenden, Anzeigen oder Sperren eines Felds basierend auf einem Wert**  
Erfolgreiche Formulare erzwingen häufig eine strikte Geschäftslogik, indem z.B. der Status eines Felds basierend auf einem Wert oder einer Aktion geändert wird. Mit PowerApps können Sie die **DisplayMode**-Eigenschaft eines Steuerelements auf **Edit** oder **View** festlegen, um anzugeben, ob ein Benutzer das Feld ändern kann. Sie können auch eine einfache **If**-Formel verwenden, um dieses Verhalten per Bedingung festzulegen. Wählen Sie zuerst die Karte aus, die Sie bearbeiten möchten, und klicken Sie dann auf das Schlosssymbol. Dieser Schritt entsperrt die Karte, sodass Sie den Wert ändern können.

![Aus- bzw. Einblenden gesperrter Datenkarten](./media/transform-infopath/hide-show-lock.png)

Scrollen Sie im rechten Bereich zur **DefaultMode**-Eigenschaft, sodass Sie diese bearbeiten können.

![If-Else-Anweisungsausdrücke](./media/transform-infopath/if-else-statement.png)

In diesem Beispiel verwenden Sie eine **If**-Formel:

```If(ThisItem.Color = "Blue", DisplayMode.View, DisplayMode.Edit)```

Diese Formel besagt Folgendes: Wenn das **Color**-Feld des aktuellen Elements auf **Blue** festgelegt ist, ist das **Animal**-Feld schreibgeschützt. Andernfalls kann das Feld bearbeitet werden.

Um die Karte auszublenden, anstatt sie als schreibgeschützt festzulegen, fügen Sie eine ähnliche Funktion in die **Visible**-Eigenschaft direkt oberhalb von **DisplayMode** ein.

Sie können beispielsweise auch eine Genehmigungsschaltfläche verwenden, die nur angezeigt wird, wenn die E-Mail-Adresse des Benutzers der E-Mail-Adresse der genehmigenden Person entspricht. (Hinweis: Verwenden Sie **User().Email**, um auf die E-Mail-Adresse des aktuellen Benutzers zuzugreifen.) Sie können also die E-Mail-Adresse der genehmigenden Person in **YourDataCard** speichern und dann die **Visible**-Eigenschaft der Schaltfläche auf diese Formel festlegen:

```If(YourDataCard.Text = User().Email, true, false)```

**Bedingte Formatierung**  
In ähnlicher Weise wie oben, wo Sie das Feld ausgeblendet haben, können Sie den Benutzern auch visuelles Feedback geben. Möglicherweise möchten Sie Text in Rot markieren, wenn der eingegebene Wert außerhalb des zulässigen Bereichs liegt, oder den Text und die Farbe der Uploadschaltfläche ändern, nachdem der Benutzer eine Datei hochgeladen hat. Beides können Sie in Eigenschaften wie **Color** oder **Visible** mithilfe einer Funktion umsetzen, z.B. **If**.

Sie könnten z.B. die **If**-Funktion zusammen mit der [IsMatch](functions/function-ismatch.md)-Funktion verwenden, um die Textfarbe des E-Mail-Felds in Rot zu ändern, wenn der Benutzer keine korrekt formatierte E-Mail-Adresse in das Eingabefeld eingibt. In diesem Fall legen Sie den **Color**-Wert von **TextInput1** (das Feld, in dem der Benutzer eine E-Mail-Adresse eingibt) auf die folgende Formel fest:

```If(IsMatch(TextInput1.Text, Email), Black, Red)```

**IsMatch** bietet eine Vielzahl von vordefinierten Mustern (wie E-Mail-Adressen) und die Möglichkeit, eigene Muster zu erstellen. Weitere Informationen zur bedingten Formatierung finden Sie in diesem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962).

**Implementieren der rollenbasierten Sicherheit**  
Die erste Funktion, die Sie ins Auge fassen sollten, lautet [DataSourceInfo](functions/function-datasourceinfo.md). Die Informationen, die Sie von der Datenquelle erhalten, variieren, aber häufig können Sie diese Formel verwenden, um zu prüfen, ob der Benutzer Zugriff auf die Daten hat (ersetzen Sie *YourDataSource* durch den Namen Ihrer Datenquelle):

```DataSourceInfo(YourDataSource, DataSourceInfo.EditPermission)```

So können Sie ein Formular oder eine Schaltfläche nur dann einblenden, wenn der Benutzer über Schreibzugriff verfügt. Die vollständige Liste der Informationen, die Sie in der Funktion abfragen können, finden Sie in der Dokumentation zu [DataSourceInfo](functions/function-datasourceinfo.md).

Wenn Sie Active Directory-Gruppen verwenden möchten, um den Zugriff auf Schaltflächen oder Formulare in Ihrer App zu verwalten, sind weitere Schritte erforderlich. Nutzen Sie hierzu die Flexibilität von PowerApps, und erstellen Sie Ihren eigenen Connector über die Microsoft Graph-API. Klingt schwierig? In diesem [Blogbeitrag](https://powerapps.microsoft.com/blog/implementing-role-based-permission/) finden Sie eine Schrittanleitung.

**Senden einer E-Mail aus Ihrer App**  
Sie können auf unterschiedliche Weise E-Mail-Nachrichten aus PowerApps senden. Der einfachste Weg ist der Office 365 Outlook-Connector. Mit diesem Connector können Sie eine Nachricht von Ihrer Adresse aus Ihrer App heraus versenden. Sie können auch E-Mail-Nachrichten und andere Aufgaben erhalten, die mit Ihrem Postfach interagieren. Informationen zum Senden von E-Mails finden Sie in dieser [Dokumentation](connections/connection-office365-outlook.md) und in diesem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349).

Sie können komplexere Nachrichten (z.B. im Rahmen eines SharePoint-Genehmigungsworkflows) senden, indem Sie Microsoft Flow verwenden und Ihre App mit dem Flow verbinden, den Sie erstellen. Sobald Ihre App mit Microsoft Flow verbunden ist, können Sie die umfassende Leistung einer Workflow-Engine nutzen, die – wie PowerApps – über sehr gute Verbindungen zu externen Daten und Diensten verfügt. Weitere Informationen zur Verbindung zwischen PowerApps und Microsoft Flow finden Sie in dieser [Dokumentation](using-logic-flows.md).

Wenn Sie die gesuchte E-Mail-Option noch nicht gefunden haben, können Sie auch die PowerApps-Connectors für Benchmark Email, Gmail, MailChimp, Outlook.com, SendGrid oder SMTP nutzen. Das ist das Schöne an PowerApps: Konnektivität.

**Workflows**  
Es ist schwer, über Geschäftsanwendungen und Geschäftslogik zu sprechen, ohne eine Workflow-Engine zu erwähnen. Die gute Nachricht ist, dass das PowerApps-Team das Rad nicht neu erfunden hat, um Ihnen noch eine Workflowengine zur Verfügung zu stellen. Stattdessen wird Ihnen ein stabiler Connector zum Microsoft Flow-Dienst geboten. Sie können Prozesse und Aufgaben für mehr als [200 verschiedene Dienste](https://flow.microsoft.com/connectors/) automatisieren, indem Sie die benutzerfreundliche Workflow-Engine nutzen. Weitere Informationen zur Verbindung zwischen PowerApps und Microsoft Flow finden Sie in dieser [Dokumentation](using-logic-flows.md).

**Variablen mit PowerApps**  
Beim Erstellen von Lösungen wird selbstverständlich davon ausgegangen, dass Variablen dazugehören. PowerApps bietet verschiedene Arten von Variablen. Nutzen Sie diese aber nur, wenn es wirklich notwendig ist. Anstatt darüber nachzudenken, Daten abzurufen, sie in einer Variablen zu speichern und dann auf die Variable zu verweisen, müssen Sie nur noch direkt auf diese Daten verweisen. Sie werden dieses Modell besser verstehen, wenn Sie es mit Excel vergleichen. In Excel ist die Summe keine Variable, sondern das Ergebnis der Addition anderer Felder. Wenn Sie diesen Wert also an anderer Stelle auf dem Blatt verwenden möchten, geben Sie die Zelle an, in der Sie die Summe berechnet haben. In der [Dokumentation](working-with-variables.md) finden Sie hierzu eine gute Erklärung. Seien Sie offen für einen anderen Denkprozess.

Wenn Sie dennoch Variablen benötigen (was in vielen Fällen vorkommt), erfahren Sie nun, welche unterschiedlichen Möglichkeiten Sie haben. Denken Sie daran, dass Sie mit PowerApps keine Variablen definieren müssen. Verwenden Sie einfach eine Funktion, um einen Namen und einen zu speichernden Wert festzulegen, und Ihre Variable wird erstellt. Sie können die von Ihnen erstellten Variablen anzeigen, indem Sie auf der Registerkarte **Ansicht** die Option **Variablen** auswählen. Variablen befinden sich im Arbeitsspeicher, und ihre Werte gehen beim Schließen der App verloren. Sie können folgende Arten von Variablen erstellen:

- Globale Variablen sind das, woran Sie zuerst denken. Geben Sie mit der [Set](functions/function-set.md)-Funktion einen Wert für eine globale Variable an, und machen Sie den Wert in der gesamten App verfügbar:

    ```Set(YourVariable, YourValue)```

    Dann können Sie in der gesamten App namentlich auf *YourVariable* verweisen.

- Kontextvariablen sind Variablen, die nur auf den Bildschirmen zur Verfügung stehen, für die sie definiert sind. Beim Verlassen des Bildschirms werden sie zurückgesetzt. Sie werden oft verwendet, um beispielsweise Informationen zu speichern, die von einem vorherigen Bildschirm übergeben wurden, oder um zu verfolgen, ob ein Formular abgeschickt wurde. Verwenden Sie zum Festlegen einer Kontextvariablen die Funktion [UpdateContext](functions/function-updatecontext.md), wie in diesem Beispiel veranschaulicht:

    ```UpdateContext( { Submitted: "true" } )```

    Dieses Beispiel legt den Wert einer Variablen namens **Submitted** auf **TRUE** fest. Sie können diese Formel zur Eigenschaft **OnSelect** einer Schaltfläche „Senden“ hinzufügen, um zu verfolgen, ob die Informationen übermittelt wurden, und alle Felder in schreibgeschützte Felder umzuwandeln.

- Sammlungen speichern Tabellen mit Informationen, die individuell aktualisiert werden können. Verwenden Sie [Collect](functions/function-clear-collect-clearcollect.md), um einen Warenkorb zu erstellen, für den der Benutzer verschiedene SharePoint-Elemente markiert, die er versenden möchte. Die Umsetzung dieses Konzepts wird in einem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180) veranschaulicht.

**Überlappende Dropdownmenüs**  
Hierarchische Dropdownlisten sind sehr praktisch, da Sie z.B. die Auswahl in einer Dropdownliste basierend auf dem in der vorherigen Dropdownliste ausgewählten Wert filtern können. In PowerApps werden diese oft durch zwei Datenquellen in Ihrer App erzeugt. Die erste Datenquelle sind die Daten, die Sie anzeigen oder aktualisieren, und die zweite Datenquelle speichert die Werte, um den Hierarchieeffekt zu erzielen. Diese Abbildung zeigt ein Beispiel der zweiten Datenquelle mit den Auswahlmöglichkeiten.

![Überlappende Dropdownmenüs](./media/transform-infopath/cascading-dropdowns.png)

In diesem Beispiel können Sie eine Dropdownliste namens **ddSelectType** hinzufügen und die **Items**-Eigenschaft der Liste auf folgende Formel festlegen:

```Distinct(Impacts, Title)```

Die Dropdownliste würde nur die folgenden Elemente anzeigen: Cost, Program Impact und Schedule. Dann können Sie eine zweite Dropdownliste hinzufügen und deren **Items**-Eigenschaft auf die folgende Formel festlegen:

```Filter(Impacts,ddSelectType.Selected.Value in SCategory)```

So einfach erhalten Sie überlappende Dropdownmenüs. Weitere Informationen finden Sie in diesem Beitrag des PowerApps-Teams [SharePoint: Cascading Dropdowns in 4 Easy Steps!](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) (SharePoint: Hierarchische Dropdownlisten in vier einfachen Schritten) oder in diesem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813). Keine Sorge: Sie können diese Aufgaben genauso einfach ohne SharePoint ausführen.

**Erstellen Sie keine einzelne Super-App**  
Mit PowerApps können Sie eine App aus einer anderen App aufrufen. Anstatt also ein InfoPath-Massenformular zu erstellen, das praktisch nur mit Kaugummi zusammenhält, können Sie eine Gruppe von Apps erstellen, die sich gegenseitig aufrufen und sogar Daten weitergeben. Auf diese Weise wird die Entwicklung erheblich vereinfacht.

## <a name="next-steps"></a>Nächste Schritte

Mit PowerApps und den Informationen in diesem Thema sind Sie nun bestens gerüstet, um die Welt mit Ihren Apps zu erobern. Im Folgenden finden Sie einige praktische Links – insbesondere die Website der PowerApps-Community ist sehr hilfreich. Treten Sie noch heute in die Community ein, denn in der Entwicklergemeinschaft erweitern Sie Ihre Kenntnisse viel schneller als alleine.

[**Referenz zu Formeln für PowerApps**](formula-reference.md): Immer eine gute Möglichkeit, sich inspirieren zu lassen. Stöbern Sie einfach in einigen der Standardfunktionen.

[**PowerApps-Community**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1): Sehen Sie sich Beispiele an, schließen Sie sich mit anderen zusammen, stellen und beantworten Sie Fragen, und helfen Sie der PowerApps-Community zu wachsen.
