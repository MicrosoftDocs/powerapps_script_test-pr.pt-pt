---
title: Funktion „Language“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Language“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 45ffd324ff5409a49f1ec8c4c8ea3529c1cf5c5f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833284"
---
# <a name="language-function-in-powerapps"></a>Funktion „Language“ in PowerApps
Gibt das Sprachkennzeichen des aktuellen Benutzers zurück

## <a name="description"></a>Beschreibung
Die **Language**-Funktion gibt die Sprache, das Skript und die Region des aktuellen Benutzers als Sprachkennzeichen zurück.

Verwenden Sie die Sprachinformationen, um Ihre App über Gebietsschemas hinweg anzupassen.  Wenn Sie beispielsweise eine App erstellen, die in Italien und Frankreich verwendet wird, können Sie **Language** verwenden, um Ihren Benutzern an diesen anderen Orten automatisch italienische und französische Zeichenfolgen anzuzeigen. 

### <a name="language-tags"></a>Sprachkennzeichen
Ein *Sprachkennzeichen* kann eines der folgenden drei Formate aufweisen:

| Rückgabewert | Beschreibung |
| --- | --- |
| **"*lg&#8209;RE*"** |*lg* ist die zwei Zeichen umfassende Abkürzung für die Sprache und *RE* ist die zwei Zeichen umfassende Abkürzung für die Region.  Dies ist der häufigste Rückgabetyp.  Beispielsweise wird „en-GB“ für Großbritannien zurückgegeben. |
| **"*lg*"** |*lg* ist die zwei Zeichen umfassende Abkürzung für die Sprache.  Dies ist das Format, das verwendet wird, wenn PowerApps Informationen zur Sprache, jedoch keine Informationen zur bestimmten Region hat. |
| **"*lg&#8209;scrp&#8209;RE*"** |*lg* ist die zwei Zeichen umfassende Abkürzung für die Sprache, *scrp* ist die vier Zeichen umfassende Abkürzung für das Skript, und *RE* ist die zwei Zeichen umfassende Abkürzung für die Region. |

PowerApps verwendet das [IETF BCP-47-Sprachkennzeichen](https://tools.ietf.org/html/bcp47)-Format.  

Um eine Liste der unterstützten Sprachkennzeichen anzuzeigen, geben Sie **Value( "1", )** in die Bearbeitungsleiste oder die erweiterte Ansicht ein, und scrollen Sie durch die Liste der Gebietsschemas, die für das zweite Argument vorgeschlagen werden.  

Die Funktionen **[Text](function-text.md)** und **[Value](function-value.md)** verwenden ebenfalls Sprachkennzeichen.  Verwenden Sie diese Funktionen, um auf global bewusste Weise von Textzeichenfolgen und in Textzeichenfolgen zu übersetzen.  Wenn ein Sprachtag an diese Funktionen übergeben wird und die Region keinen Unterschied machen würden, können Sie nur den Sprachteil des Kennzeichens verwenden.

## <a name="syntax"></a>Syntax
**Language**()

## <a name="examples"></a>Beispiele
### <a name="users-locale"></a>Gebietsschema des Benutzers
Es wird vorausgesetzt, dass das Hostbetriebssystem und/oder der Browser für den Standort das Standardgebietsschema verwenden.

| Formel | Ort | Rückgabewert |
| --- | --- | --- |
| **Language()** |Lissabon, Portugal |"pt-PT" |
| **Language()** |Rio de Janeiro, Brasilien |"pt-BR" |
| **Language()** |Atlanta, USA |"en-US" |
| **Language()** |Manchester, Großbritannien |"en-GB" |
| **Language()** |Paris, Frankreich |"fr-FR" |
| **Language()** |Roseau, Dominica |"en" |
| **Language()** |Belgrad, Serbien |"sr-cyrl-RS" oder "sr-latn-RS", je nach den Systemeinstellungen des Benutzers |

### <a name="localization-table"></a>Lokalisierungstabelle
Ein einfacher Ansatz zur Lokalisierung ist, ein Excel-Arbeitsblatt zu erstellen, wobei eine vom Autor definierte **TextID** einem übersetzten Text für die Sprache des Benutzers zugeordnet wird.  Obwohl Sie eine Sammlung oder eine andere Datenquelle für diese Tabelle verwenden könnten, haben wir uns für Excel entschieden, da Übersetzer die Tabelle somit einfach außerhalb der App bearbeiten und verwalten können.

1. Erstellen Sie die folgende Tabelle in Excel: 
   
    ![](media/function-language/loc-table.png)
   
    Der Eintrag mit *blank* in der Spalte **Language** wird als Standard verwendet, wenn für eine bestimmte Sprache keine bestimmte Textzeichenfolge vorhanden ist. Dieser Eintrag muss nach allen anderen Einträgen für eine bestimmte **TextID** erscheinen.
   
    Für unsere Zwecke müssen wir nur die Sprache des Gebietsschemas und nicht die Region betrachten.  Wenn regionale Aspekte wichtig wären, hätten wird den vollständigen Sprachkennzeichenwert in die Tabelle oben einschließen können. 
2. Verwenden Sie das Menüband **Insert** (Einfügen) und den Befehl **Table** (Tabelle), um eine ordnungsgemäße Excel-Tabelle daraus zu erstellen.  Diese wird standardmäßig **Table1** genannt, Sie können sie jedoch nennen, wie Sie möchten, indem Sie das Menüband **Table Tools/Design** (Tabellentools/-design) und das Textfeld **Tabellenname:** ganz auf der linken Seite verwenden.
3. Speichern Sie die Excel-Datei in Ihrem lokalen Dateisystem.   
4. Klicken oder tippen Sie im rechten Bereich in PowerApps auf die Registerkarte **Datenquellen** und dann auf **Datenquelle hinzufügen**.
5. Klicken oder tippen Sie auf **Der App statische Daten hinzufügen**, oder klicken oder tippen Sie auf die Excel-Datei, die Sie gespeichert haben, und klicken oder tippen Sie auf **Öffnen**.
6. Wählen Sie die Tabelle aus, die Sie erstellt haben, und klicken oder tippen Sie anschließend auf **Verbinden**.

Verwenden Sie in Ihrer App überall dort, wo Sie zuvor den Text **"Hello"** verwendet hätten, stattdessen diese Formel:

* **LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

Diese Formel schlägt den entsprechenden **LocalizedText**-Wert für die Sprache des Benutzers nach. Wenn dieser nicht gefunden wird, führt die Formel ein Fallback auf die Standardversion *blank* durch. 

Bedenken Sie, dass die übersetzten Zeichenfolgen in anderen Sprachen wesentlich länger sein könnten als sie in Ihrer Sprache sind.  In vielen Fällen müssen die Bezeichnungen und anderen Elemente, die die Zeichenfolgen in Ihrer Benutzerschnittstelle anzeigen, breiter sein, um sich dem anzupassen.

### <a name="translation-service"></a>Übersetzungsdienst
Sie können Text nach Bedarf übersetzen, indem Sie einen Übersetzungsdienst wie den Microsoft Translator-Dienst verwenden:  

1. Klicken oder tippen Sie im rechten Bereich in PowerApps auf die Registerkarte **Datenquellen** und dann auf **Datenquelle hinzufügen**.
2. Klicken oder tippen Sie auf **Microsoft Translator**.

Verwenden Sie in Ihrer App überall dort, wo Sie zuvor den Text **"Hello"** verwendet hätten, stattdessen diese Formel:

* **MicrosoftTranslator.Translate( "Hello", Language() )**

Der Microsoft Translator-Dienst verwendet die gleichen Sprachkennzeichen, die die **Language**-Funktion zurückgibt.

Dieser Ansatz hat einige Nachteile gegenüber dem vorherigen Beispiel, bei dem eine vorübersetzte Tabelle mit Textzeichenfolgen verwendet wurde:

* Die Übersetzung dauert einige Zeit und erfordert einen Aufruf eines Diensts über das Netzwerk hinweg.  Dadurch wird der übersetzte Text mit etwas Verzögerung in Ihrer App angezeigt. 
* Die Übersetzung erfolgt maschinell und entspricht möglicherweise nicht Ihren Erwartungen bzw. ist möglicherweise nicht die beste Wahl für die Situation in Ihrer App.

