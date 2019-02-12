---
title: Übersicht über die Microsoft Translator-Verbindung | Microsoft-Dokumentation
description: Anleitung zum Herstellen einer Verbindung mit Microsoft Translator, einige Beispiele für die erforderlichen Schritte und Auflistung aller Funktionen
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: lanced
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 405dcf432526206aa3a5f341a38e2ae5547cea1f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42858283"
---
# <a name="connect-to-microsoft-translator-from-powerapps"></a>Herstellen einer Verbindung mit Microsoft Translator aus PowerApps
![Microsoft Translator](./media/connection-microsoft-translator/translatoricon.png)

Fügen Sie den Connector für Microsoft Translator hinzu, um übersetzten Text in einem **Label**-Steuerelement (Bezeichnung) in Ihrer App anzuzeigen. Beispielsweise können Sie ein Eingabetextfeld erstellen, mit dem der Benutzer aufgefordert wird, Text zum Übersetzen einzugeben. In einer anderen Bezeichnung können Sie den übersetzten Text anzeigen.

In diesem Thema wird gezeigt, wie Sie die Microsoft Translator-Verbindung erstellen und in einer App verwenden, und es werden die verfügbaren Funktionen aufgeführt.

> [!NOTE]
> Dieser Connector ist auf 150 Aufrufe pro Benutzer und Tag beschränkt.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-microsoft-translator"></a>Herstellen einer Verbindung mit Microsoft Translator
1. Öffnen Sie PowerApps, wählen Sie **Neu** aus, und erstellen Sie eine **Leere App**. Wählen Sie das Layout für Smartphone oder Tablet aus. Das Tablet-Layout bietet Ihnen einen größeren Arbeitsbereich:  

   ![Öffnen einer leeren App](./media/connection-microsoft-translator/blank-app.png)
2. Klicken oder tippen Sie im rechten Bereich auf die Registerkarte **Daten** und dann auf **Datenquelle hinzufügen**.
3. Wählen Sie **Neue Verbindung** und anschließend **Microsoft Translator** aus:  

    ![Herstellen einer Verbindung mit Microsoft Translator](./media/connection-microsoft-translator/addconnection.png)

    ![Herstellen einer Verbindung mit Microsoft Translator](./media/connection-microsoft-translator/add-translator.png)
4. Wählen Sie **Verbinden** aus. Die Verbindung wird unter **Datenquellen** angezeigt:  

    ![Herstellen einer Verbindung mit Microsoft Translator](./media/connection-microsoft-translator/translatordatasource.png)

## <a name="use-the-microsoft-translator-connection-in-your-app"></a>Verwenden der Microsoft Translator-Verbindung in Ihrer App
### <a name="translate-text"></a>Übersetzen von Text
1. Klicken Sie im Menü **Insert** (Einfügen) auf **Text**, und wählen Sie dann **Texteingabe** (Texteingabe) aus. Benennen Sie das Texteingabe-Steuerelement in **Source** um:  

    ![Umbenennen](./media/connection-microsoft-translator/renametosource.png)
2. Fügen Sie eine **Dropdown**-Liste hinzu (Menü **Einfügen** > **Steuerelemente**), benennen Sie sie in **TargetLang** um, und verschieben Sie sie unter **Source**.
3. Legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft von **TargetLang** auf die folgende Formel fest:  

    `MicrosoftTranslator.Languages()`
4. Fügen Sie eine Bezeichnung hinzu, verschieben Sie es unter **TargetLang**, und legen Sie seine **[Text](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:  

    `MicrosoftTranslator.Translate(Source.Text, TargetLang.Selected.Value)`
5. Geben Sie Text in **Source** ein, und wählen Sie unter **TargetLang** eine Sprache aus. In der Bezeichnung wird der eingegebene Text in der ausgewählten Sprache angezeigt:  

    ![Übersetzen von Text aus dem Englischen ins Spanische](./media/connection-microsoft-translator/translate-text.png)

### <a name="speak-translated-text"></a>Sprechen von übersetztem Text
Wenn Sie dies nicht bereits getan haben, führen Sie die Schritte im vorherigen Abschnitt aus, um Text zu übersetzen. In den folgenden Schritten werden die gleichen Steuerelemente verwendet.

1. Legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft der Dropdownliste **TargetLang** auf die folgende Formel fest:  

    `MicrosoftTranslator.SpeechLanguages()`
2. Benennen Sie die zweite Bezeichnung (nicht das Feld **Source**) in **Target** um.
3. Fügen Sie ein **Audio**-Steuerelement hinzu (Menü **Einfügen** > **Medien**), und legen Sie seine **Media**-Eigenschaft auf die folgende Formel fest:  

    `MicrosoftTranslator.TextToSpeech(Target.Text, TargetLang.Selected.Value)`
4. Drücken Sie F5, oder wählen Sie die Vorschauschaltfläche aus (![](./media/connection-microsoft-translator/preview.png)). Geben Sie Text in **Source** ein, wählen Sie eine Sprache in **TargetLang** aus, und wählen Sie dann die Wiedergabeschaltfläche im Audio-Steuerelement aus.

    Die App spielt eine Audioversion des eingegebenen Texts in der ausgewählten Sprache ab.
5. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.

### <a name="detect-the-source-language"></a>Erkennen der Ausgangssprache
In den folgenden Schritten werden die gleichen Texteingabe-Steuerelemente (**Source**) und Text (**Target**) verwendet. Sie können auch neue Steuerelemente erstellen, in diesem Fall müssen Sie nur die Namen in der Formel aktualisieren.

1. Wählen Sie das Text-Steuerelement **Target** aus, und legen Sie die **[Text](../controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:  

    `MicrosoftTranslator.Detect(Source.Text).Name`
2. Geben Sie Text in **Source** ein.

    In der Bezeichnung wird die Sprache des eingegebenen Texts angezeigt. In der Bezeichnung wird z.B. **Französisch** angezeigt, wenn Sie **Bonjour** eingeben oder **Italienisch**, wenn Sie **Ciao** eingeben.

## <a name="view-the-available-functions"></a>Anzeigen der verfügbaren Funktionen
Diese Verbindung umfasst die folgenden Funktionen:

| Funktionsname | Beschreibung |
| --- | --- |
| [Sprachen](connection-microsoft-translator.md#languages) |Ruft alle von Microsoft Translator unterstützten Sprachen ab |
| [Translate](connection-microsoft-translator.md#translate) |Übersetzt Text mit Microsoft Translator aus einer angegebenen Sprache |
| [Detect](connection-microsoft-translator.md#detect) |Erkennt die Ausgangssprache eines angegebenen Texts |
| [SpeechLanguages](connection-microsoft-translator.md#speechlanguages) |Ruft die verfügbaren Sprachen für die Sprachsynthese ab |
| [TextToSpeech](connection-microsoft-translator.md#texttospeech) |Konvertiert einen angegebenen Text in Sprache als Audiostream im Wave-Format |

### <a name="languages"></a>Sprachen
Sprachen abrufen: Ruft alle von Microsoft Translator unterstützten Sprachen ab

#### <a name="input-properties"></a>Eingabeeigenschaften
Keine

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Code |Zeichenfolge |Nein | |
| Name |Zeichenfolge |Nein | |

### <a name="translate"></a>Translate
Text übersetzen: Übersetzt Text mit Microsoft Translator aus einer angegebenen Sprache

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| query |Zeichenfolge |ja |Zu übersetzender Text |
| languageTo |Zeichenfolge |ja |Code der Zielsprache (Beispiel: „fr“) |
| languageFrom |Zeichenfolge |Nein |Ausgangssprache (wenn die Sprache nicht angegeben wird, versucht Microsoft Translator, sie automatisch zu erkennen) (Beispiel: en) |
| category |Zeichenfolge |Nein |Übersetzungskategorie (Standard: general) |

#### <a name="output-properties"></a>Ausgabeeigenschaften
Keine

### <a name="detect"></a>Detect
Sprache erkennen: Erkennt die Ausgangssprache eines angegebenen Texts

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| query |Zeichenfolge |ja |Text, dessen Sprache erkannt werden soll |

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Code |Zeichenfolge |Nein | |
| Name |Zeichenfolge |Nein | |

### <a name="speechlanguages"></a>SpeechLanguages
Sprachen abrufen: Ruft die verfügbaren Sprachen für die Sprachsynthese ab

#### <a name="input-properties"></a>Eingabeeigenschaften
Keine

#### <a name="output-properties"></a>Ausgabeeigenschaften

| Eigenschaftsname | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Code |Zeichenfolge |Nein | |
| Name |Zeichenfolge |Nein | |

### <a name="texttospeech"></a>TextToSpeech
Text in Sprache: Konvertiert einen angegebenen Text in Sprache als Audiostream im Wave-Format

#### <a name="input-properties"></a>Eingabeeigenschaften

| Name | Datentyp | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| query |Zeichenfolge |ja |Zu konvertierender Text |
| language |Zeichenfolge |ja |Sprachcode für die Sprachgenerierung (Beispiel: en-us) |

#### <a name="output-properties"></a>Ausgabeeigenschaften
Keine

## <a name="helpful-links"></a>Nützliche Links
Alle [verfügbaren Verbindungen](../connections-list.md).  
Erfahren Sie, wie Sie Ihren Apps [Verbindungen hinzufügen](../add-manage-connections.md).

