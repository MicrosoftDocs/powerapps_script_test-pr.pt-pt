---
title: Verwenden von Cognitive Services in PowerApps | Microsoft-Dokumentation
description: Erstellen Sie eine einfache Canvas-App, die die Textanalyse-API von Microsoft Cognitive Services verwendet, um Text zu analysieren.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/08/2017
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: df823f68842ad3c7a7497e6dce9cc3540520527e
ms.sourcegitcommit: 3dc330d635aaf5bc689efa6bd39826d6e396c832
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48875874"
---
# <a name="use-cognitive-services-in-powerapps"></a>Verwenden von Cognitive Services in PowerApps
In diesem Artikel wird erläutert, wie Sie eine einfache Canvas-App erstellen, die die [Textanalyse-API von Microsoft Cognitive Services](https://docs.microsoft.com/azure/cognitive-services/text-analytics/overview) verwendet, um Text zu analysieren. Es wird veranschaulicht, wie die Textanalyse-API eingerichtet und mit dem [Textanalyse-Connector](https://docs.microsoft.com/connectors/cognitiveservicestextanalytics/) verbunden wird. Anschließend wird beschrieben, wie eine Canvas-App erstellt wird, die die API aufruft.

> [!NOTE]
> Wenn Sie mit dem Erstellen von Apps in PowerApps nicht vertraut sind, empfehlen wir Ihnen, [App von Grund auf neu erstellen](get-started-create-from-blank.md) durchzulesen, bevor Sie in diesen Artikel einsteigen.

## <a name="introduction-to-microsoft-cognitive-services"></a>Einführung in Microsoft Cognitive Services
Microsoft Cognitive Services umfasst eine Reihe von verfügbaren APIs, SDKs und Diensten, mit denen Sie Ihre Anwendungen intelligenter, ansprechender und besser strukturiert gestalten können. Mit diesen Diensten können Sie in Ihren Anwendungen auf einfache Weise intelligente Funktionen hinzufügen – z.B. Stimmungs- und Videoerkennung; Gesichtserkennung, Erkennung von Sprach- und Sehvermögen sowie Verständnis von Spracheingaben und Sprachen.

Wir legen in diesem Artikel bei der Arbeit mit der Textanalyse-API den Schwerpunkt auf das „Sprachverständnis“. Anhand dieser API können Sie Stimmung, Schlüsselbegriffe, Themen und Sprache in Ihren Texten erkennen. Schauen wir uns zunächst eine Demo der API an; dabei müssen wir uns für eine Vorschauversion registrieren.

### <a name="try-out-the-text-analytics-api"></a>Erkunden der Textanalyse-API
Für die API ist eine Online-Demo verfügbar: Sie können sich mit ihrer Funktionsweise vertraut machen und den JSON einsehen, der vom Dienst zurückgegeben wird.

1. Rufen Sie die Seite [Textanalyse-API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) auf.

2. Verwenden Sie im Abschnitt **Demo anzeigen** den Beispieltext, oder geben Sie einen eigenen Text ein. Klicken oder tippen Sie dann auf **Analysieren**. 
   
    ![Demo zur Textanalyse-API](./media/cognitive-services-api/text-analytics-demo.png)

3. Auf der Seite werden auf der Registerkarte **Analyzed text** (Analysierter Text) formatierte Ergebnisse und auf der Registerkarte **JSON** die JSON-Antwort angezeigt. [JSON](http://json.org/) ist eine Möglichkeit der Darstellung von Daten – in diesem Fall der von der Textanalyse-API zurückgegebenen Daten.

## <a name="sign-up-for-the-text-analytics-api"></a>Registrieren für die Textanalyse-API
Die API ist als kostenlose Vorschauversion erhältlich und mit einem Azure-Abonnement verbunden. Sie verwalten die API über das Azure-Portal.

1. Wenn Sie über kein Azure-Abonnement verfügen, [registrieren Sie sich für ein kostenloses Abonnement](https://azure.microsoft.com/free/).

2. Melden Sie sich bei Ihrem Azure-Konto an.

3. Wechseln Sie zum [Blatt zum Erstellen von Cognitive Services](https://go.microsoft.com/fwlink/?LinkId=761108) im Azure-Portal.

4. Geben Sie Informationen für die Textanalyse-API ein. Siehe dazu die folgende Abbildung. Wählen Sie den Tarif **F0** (kostenlos).
   
    ![Erstellen der Textanalyse-API](./media/cognitive-services-api/azure-create.png)

5. Klicken oder tippen Sie unten links auf **Erstellen**.

6. Klicken oder tippen Sie im **Dashboard** auf die soeben erstellte API.
   
    ![Azure-Dashboard](./media/cognitive-services-api/azure-dashboard.png)

7. Klicken oder tippen Sie auf **Schlüssel**.
   
    ![Azure-Menü](./media/cognitive-services-api/azure-menu-keys.png)

8. Kopieren Sie einen der Schlüssel auf der rechten Bildschirmseite. Dieser Schlüssel wird später beim Erstellen der Verbindung mit der API verwendet.
   
    ![API-Schlüssel](./media/cognitive-services-api/azure-keys.png)

## <a name="build-the-app"></a>Erstellen der App
Nun ist die Textanalyse-API einsatzbereit, und Sie können eine Verbindung mit der API aus PowerApps herstellen sowie eine App erstellen, die die API aufruft. Dies ist eine App mit einem einzigen Bildschirm, die ähnliche Funktionen wie die Demo auf der Seite „Textanalyse-API“ bietet. Legen Sie los!

### <a name="create-the-app-and-add-a-connection"></a>Erstellen der App und Hinzufügen einer Verbindung
Zunächst erstellen Sie eine leere Smartphone-App und fügen eine Verbindung mit dem **Textanalyse**-Connector hinzu. Wenn Sie zu diesen Aufgaben weitere Informationen benötigen, lesen Sie die Artikel [App von Grund auf neu erstellen](get-started-create-from-blank.md) und [Verwalten der Verbindungen in PowerApps](add-manage-connections.md).

1. Wählen Sie auf [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) die Option **Mit leerer App starten** > ![Symbol für Telefon-App](./media/cognitive-services-api/icon-phone-app.png) (Telefon) > **Diese App erstellen** aus.

    ![Mit leerer App starten](./media/cognitive-services-api/start-from-blank.png)

2. Wählen Sie im mittleren Bereich von PowerApps Studio **Mit Daten verbinden** aus.

3. Klicken oder tippen Sie im Bereich **Daten** auf **Neue Verbindung** > **Textanalyse**.

4. Kopieren Sie Ihren Schlüssel in **Kontoschlüssel**, und klicken oder tippen Sie auf **Erstellen**.
   
    ![Textanalyse-Connector](./media/cognitive-services-api/create-connection-ta.png)

### <a name="add-controls-to-the-app"></a>Hinzufügen von Steuerelementen zur App
Der nächste Schritt beim Erstellen der App besteht im Hinzufügen aller Steuerelemente. Normalerweise fügen wir beim Erstellen der Apps den Steuerelementen direkt Formeln hinzu. Hier konzentrieren wir uns jedoch zunächst auf das Erstellen der Apps und fügen erst im nächsten Abschnitt einige Formeln hinzu. In der folgenden Abbildung wird die App mit allen Steuerelementen veranschaulicht.

![Fertig gestellte App](./media/cognitive-services-api/finished-app-no-data.png)

Befolgen Sie die Schritte unten, um diesen Bildschirm zu erstellen. Ist ein Steuerelementname angegeben, wird dieser Name in einer Formel im nächsten Abschnitt verwendet.

1. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Neuer Bildschirm** und anschließend auf **Scrollbarer Bildschirm**. 

2. Wählen Sie auf **Screen2** **[Title]** aus, und ändern Sie ihn in **Text Analysis**.

3. Fügen Sie ein **Bezeichnungs**-Steuerelement für den Einführungstext hinzu.

4. Fügen Sie ein **Texteingabe**-Steuerelement hinzu, sodass Sie Text zum Analysieren eingeben können. Benennen Sie das Steuerelement **tiTextToAnalyze**. Die App sollte nun wie in der folgenden Abbildung aussehen.
   
    ![App mit Titel, Untertitel und Texteingabe](./media/cognitive-services-api/partial-app-step1.png)

5. Fügen Sie drei **Kontrollkästchen**-Steuerelemente hinzu, sodass Sie auswählen können, welche API-Vorgänge ausgeführt werden sollen. Benennen Sie die Steuerelemente **chkLanguage**, **chkPhrases** und **chkSentiment**.

6. Fügen Sie eine Schaltfläche hinzu, sodass Sie die API nach dem Auswählen der auszuführenden Vorgänge aufrufen können. Die App sollte nun wie in der folgenden Abbildung aussehen.
   
    ![App mit Kontrollkästchen und Schaltfläche](./media/cognitive-services-api/partial-app-step2.png)

7. Fügen Sie drei **Bezeichnungs**-Steuerelemente hinzu. Die ersten beiden enthalten die Ergebnisse aus den API-Aufrufen für Stimmungs- und Spracherkennung; das dritte hingegen ist lediglich eine Einführung für den Katalog am unteren Rand des Bildschirms.

8. Fügen Sie ein Steuerelement vom Typ **Blank vertical gallery** (Leerer vertikaler Katalog) hinzu, und fügen Sie dem Katalog ein **Bezeichnungs**-Steuerelement hinzu. Der Katalog enthält Ergebnisse aus dem API-Aufruf für Schlüsselbegriffe. Die App sollte nun wie in der folgenden Abbildung aussehen.
   
    ![App mit Bezeichnungen und Katalog](./media/cognitive-services-api/partial-app-step3.png)

9. Wählen Sie im linken Bereich **Screen1** > Auslassungspunkte (**. . .**) > **Löschen** aus (dieser Bildschirm wird für die App nicht benötigt).

Diese App ist bewusst einfach gehalten, um sich auf das Aufrufen der Textanalyse-API zu konzentrieren. Natürlich könnten Sie einige Elemente hinzufügen, wie z.B. Logik zum Ein- und Ausblenden von Steuerelementen je nach den aktivierten Kontrollkästchen, Fehlerbehandlung, wenn der Benutzer keine Optionen auswählt usw.

### <a name="add-logic-to-make-the-right-api-calls"></a>Hinzufügen von Logik zum Ausführen der richtigen API-Aufrufe
Nun verfügen Sie über eine App, die ganz ordentlich aussieht, damit können aber noch keine Vorgänge ausgeführt werden. Dies ändern Sie jedoch gleich. Bevor wir uns mit den Details beschäftigen, betrachten Sie das Muster, dem die App folgt:

1. Die App führt bestimmte API-Aufrufe aus, je nach den Kontrollkästchen, die in der App aktiviert sind. Wenn Sie auf **Analyze text** (Text analysieren) klicken oder tippen, führt die App einen, zwei oder drei API-Aufrufe aus.

2. Die App speichert von der API zurückgegebene Daten in drei unterschiedlichen [Sammlungen](working-with-variables.md#create-a-collection): **languageCollect**, **sentimentCollect** und **phrasesCollect**.

3. Die App aktualisiert die **Text**-Eigenschaft für zwei der Bezeichnungen und die **Items**-Eigenschaft für den Katalog entsprechend dem Inhalt der drei Sammlungen.

Vor diesem Hintergrund fügen wir nun die Formel für die **OnSelect**-Eigenschaft der Schaltfläche hinzu. Hier liegt nun die ganze Zauberei.

```
If(chkLanguage.Value=true,

        ClearCollect(languageCollect, TextAnalytics.DetectLanguage({numberOfLanguagesToDetect:1, text:tiTextToAnalyze.Text}).detectedLanguages.name)

);

If(chkPhrases.Value=true,

        ClearCollect(phrasesCollect, TextAnalytics.KeyPhrases({language:"en", text:tiTextToAnalyze.Text}).keyPhrases)

);

If(chkSentiment.Value=true,

        ClearCollect(sentimentCollect, TextAnalytics.DetectSentiment({language:"en", text:tiTextToAnalyze.Text}).score)

)
```

Hier geht einiges vor sich, gehen wir also etwas näher darauf ein:

* Die **If**-Anweisungen sind einfach – wird ein bestimmtes Kontrollkästchen aktiviert, wird der API-Aufruf für den betreffenden Vorgang ausgeführt.

* Geben Sie in jedem Aufruf die entsprechenden Parameter an:

  * In allen drei Aufrufen geben Sie **tiTextToAnalyze.Text** als Eingabetext an.

  * In **DetectLanguage()** ist **numberOfLanguagesToDetect** als 1 hartcodiert, Sie könnten diesen Parameter aber auch entsprechend einer bestimmten Logik in der App übergeben.

  * In **KeyPhrases()** und **DetectSentiment()** ist **language** als „en“ hartcodiert. Auch dieser Parameter könnte entsprechend einer bestimmten Logik in der App übergeben werden. Sie könnten beispielsweise zuerst die Sprache erkennen und anschließend diesen Parameter entsprechend dem von **DetectLanguage()** zurückgegebenen Wert festlegen.

* Für jeden getätigten Aufruf fügen wir die Ergebnisse der entsprechenden Sammlung hinzu:

    * Fügen Sie für **languageCollect** den **name** der Sprache hinzu, der im Text erkannt wurde.

    * Fügen Sie für **phrasesCollect** die **keyPhrases** hinzu, die im Text erkannt wurden.

    * Fügen Sie für **sentimentCollect** den Stimmungs-**score** für den Text hinzu; dies ist ein Wert von 0-1, wobei 1 einer zu 100 % positiven Stimmung entspricht.

### <a name="display-the-results-of-the-api-calls"></a>Anzeigen der Ergebnisse der API-Aufrufe
Zum Anzeigen der Ergebnisse der API-Aufrufe verweisen Sie auf die entsprechende Sammlung in jedem Steuerelement:

1. Legen Sie die **Text**-Eigenschaft der Sprachbezeichnung auf folgenden Wert fest: `"The language detected is " & First(languageCollect).name`.
   
    Die **First()**-Funktion gibt den ersten (und in diesem Fall einzigen) Eintrag in **languageCollect** zurück, und die App zeigt **name** (das einzige Feld) für den Eintrag an.

2. Legen Sie die **Text**-Eigenschaft der Stimmungsbezeichnung auf folgenden Wert fest: `"The sentiment score is " & Round(First(sentimentCollect.Value).Value, 3)\*100 & "% positive."`.
   
    Diese Formel verwendet ebenfalls die **First()**-Funktion, ruft den **Value** (0-1) aus dem ersten und einzigen Eintrag ab und formatiert ihn anschließend als Prozentsatz.

3. Legen Sie die **Items**-Eigenschaft des Katalogs mit Schlüsselbegriffen auf folgenden Wert fest: `phrasesCollect`.
   
    Sie arbeiten nun mit einem Katalog, daher benötigen Sie nicht die **First()**-Funktion zum Abrufen eines Einzelwerts. Sie verweisen auf die Sammlung, und im Katalog werden die Schlüsselbegriffe als Liste angezeigt.

## <a name="run-the-app"></a>Ausführen der App

Nachdem die App jetzt fertig ist, können Sie sie ausführen und sehen, wie sie funktioniert: Klicken oder tippen Sie auf die Schaltfläche zum Ausführen in der rechten oberen Ecke ![Ausführen der App](./media/cognitive-services-api/icon-run-app.png). In der folgenden Abbildung sind alle drei Optionen ausgewählt, und der Text entspricht dem Standardtext auf der Seite „Textanalyse-API“.

![Fertig gestellte App mit Daten](./media/cognitive-services-api/finished-app.png)

Wenn Sie die Ausgabe dieser App mit der Seite „Textanalyse-API“ zu Beginn dieses Artikels vergleichen, stellen Sie fest, dass die Ergebnisse identisch sind.

Wir hoffen, dass Sie nun die Textanalyse-API ein bisschen besser verstehen, und dass Sie etwas Spaß daran hatten, sie in Ihre App einzubinden. Teilen Sie uns mit, ob es weitere Cognitive Services (oder generell andere Dienste) gibt, die wir in unseren Artikeln eingehender behandeln sollen. Wie immer bitten wir Sie darum, eventuelles Feedback und Fragen in den Kommentaren zu hinterlassen.

