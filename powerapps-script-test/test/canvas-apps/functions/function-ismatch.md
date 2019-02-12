---
title: Funktion „IsMatch“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „IsMatch“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/05/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f7612b648b3f1f5228fce93054f8732ec47767a8
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833514"
---
# <a name="ismatch-function-in-powerapps"></a>Funktion „IsMatch“ in PowerApps
Prüft, ob eine Zeichenfolge mit einem Muster übereinstimmt

## <a name="description"></a>Beschreibung
Die **IsMatch**-Funktion prüft, ob eine Textzeichenfolge mit einem Muster übereinstimmt, das normale Zeichen, vordefinierte Muster oder einen [regulären Ausdruck](#regular-expressions) enthält.  

Verwenden Sie **IsMatch**,um zu überprüfen, was ein Benutzer in ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement eingegeben hat. Beispielsweise können Sie überprüfen, ob der Benutzer eine gültige E-Mail-Adresse eingegeben hat, bevor das Ergebnis in der Datenquelle gespeichert wird. Wenn der Eintrag nicht mit Ihren Kriterien übereinstimmt, fügen Sie andere Steuerelemente hinzu, die den Benutzer zur Korrektur der Eingabe auffordern.

Standardmäßig sucht **IsMatch** nach Übereinstimmungen in Textzeichenfolgen und beachtet dabei Groß- und Kleinschreibung. Sie können dieses Verhalten ändern, indem Sie eine oder mehrere [**"MatchOptions"**](#match-options) angeben.

**IsMatch** gibt *TRUE* zurück, wenn die Zeichenfolge mit dem Muster übereinstimmt, oder *FALSE*, Wenn dies nicht der Fall ist.

## <a name="patterns"></a>Muster
Wenn Sie **IsMatch** verwenden, ist es wichtig, dass sie das entsprechende Muster beschreiben. Sie beschreiben das Muster als Testzeichenfolge als Kombination aus Folgendem:

* Normale Zeichen, z.B. **"Abc"** oder **"123"**
* Vordefinierte Muster, z.B. **Letter** (Buchstabe), **MultipleDigits** (mehrere Ziffern) oder **E-Mail**. (Die **Match**-Enumeration definiert diese Muster.)
* Reguläre Ausdruckcodes, z.B. **„\d+\s+\d+“** oder **„[a-z] +“**

Kombinieren Sie diese Elemente mithilfe des [Operators für Zeichenfolgenverkettung **&**](operators.md). **"abc" & Digit & "\s+"** ist beispielsweise ein gültiges Muster, das den Zeichen „a“, „b“ und „c“ gefolgt von einer Ziffer zwischen 0 und 9 entspricht, auf die mindestens ein Leerzeichen folgt.

### <a name="ordinary-characters"></a>Normales Zeichen
Das einfachste Muster ist eine Sequenz von normalen Zeichen, die exakt übereinstimmen sollen.

Die Zeichenfolge "Hello" entspricht z.B. genau dem Muster **„Hello“**. Nicht mehr und nicht weniger. Die Zeichenfolge „hello!“ stimmt wegen des Ausrufezeichens am Ende und der Kleinschreibung nicht mit dem Muster überein. (Unter ["MatchOptions"](#match-options) finden Sie Informationen zu Modifizierungsmöglichkeiten dieses Verhaltens.)

In der Mustersprache sind bestimmten Zeichen bestimmte Funktionen vorbehalten. Fügen Sie entweder vor dem Zeichen einen **\\** (umgekehrter Schrägstrich) ein, um anzugeben, dass das Zeichen als solches interpretiert werden soll, oder verwenden Sie eines der vordefinierten Muster. Diese Tabelle enthält die Sonderzeichen:

| Sonderzeichen | Beschreibung |
| --- | --- |
| **.** |Punkt |
| **?** |Fragezeichen |
| **&#42;** |Sternchen |
| **\+** |Plus |
| **( )** |Klammern |
| **[ ]** |eckige Klammern |
| **{ }** |geschweifte Klammern |
| **^** |Caretzeichen |
| **$** |Dollarzeichen |
| **&#124;** |senkrechter Strich |
| **\\** |umgekehrter Schrägstrich |

Als Übereinstimmung mit der Zeichenfolge „Hello?“ können Sie beispielsweise das Muster **„Hello\\?“** mit einem umgekehrten Schrägstrich vor dem Fragezeichen verwenden.

### <a name="predefined-patterns"></a>Vordefinierte Muster
Mit vordefinierten Mustern können Sie ganz leicht ein Zeichen aus einem Zeichensatz oder eine Sequenz aus mehreren Zeichen übereinstimmen. Verwenden Sie den [Operator für Zeichenfolgenverkettungen **&**](operators.md), um Ihre eigenen Textzeichenfolgen mit Membern der **Match**-Enumeration zu kombinieren:

| Match-Enumeration | Beschreibung | Reguläre Ausdrücke |
| --- | --- | --- |
| **Any** |Ordnet ein beliebiges Zeichen zu |**.** |
| **Comma** |Ordnet ein Komma zu |**,** |
| **Digit** |Ordnet eine einzelne Ziffer („0“ bis „9“) zu |**\\d** |
| **Email** |Ordnet eine E-Mail-Adresse zu, die ein at-Zeichen (\@) und einen Domänennamen enthält, der einen Punkt (.) enthält |**.+\@.+\\.[^\\.]{2,}** |
| **Hyphen** |Ordnet einen Bindestrich zu |**\\-** |
| **LeftParen** |Ordnet eine linke Klammer „(“ zu |**\\(** |
| **Letter** |Ordnet einen Buchstaben zu |**\\p{L}** |
| **MultipleDigits** |Ordnet mindestens eine Ziffer zu |**\\d+** |
| **MultipleLetters** |Ordnet mindestens einen Buchstaben zu |**\\p{L}+** |
| **MultipleNonSpaces** |Ordnet eine oder mehrere Zeichen zu, die keine Lücken (Leerzeichen, Registerkarte, Zeilenvorschub) hinzufügen. |**\\S+** |
| **MultipleSpaces** |Ordnet ein oder mehrere Zeichen zu, die Lücken (Leerzeichen, Registerkarte, Zeilenvorschub) hinzufügen. |**\\s+** |
| **NonSpace** |Ordnet ein einzelnes Zeichen zu, das keine Lücken hinzufügt |**\\S** |
| **OptionalDigits** |Ordnet 0, 1 oder mehrere Ziffern zu |**\\d** |
| **OptionalLetters** |Ordnet 0, 1 oder mehrere Buchstaben zu |**\\p{L}** |
| **OptionalNonSpaces** |Ordnet 0, 1 oder mehrere Zeichen zu, die keine Lücken hinzufügen |**\\S** |
| **OptionalSpaces** |Ordnet 0, 1 oder mehrere Zeichen zu, die Lücken hinzufügen |**\\s** |
| **Period** |Ordnet einen Punkt (.) zu |**\\.** |
| **RightParen** |Ordnet eine rechte Klammer „)“ zu |**\\)** |
| **Space** |Ordnet ein Zeichen zu, das Lücken hinzufügt |**\\s** |

Das Muster **"A" & MultipleDigits** entspricht dem Buchstaben „A“ gefolgt von einer oder mehreren Ziffern  

### <a name="regular-expressions"></a>Reguläre Ausdrücke
Das Muster **IsMatch** ist ein *regulärer Ausdruck*. Normale Zeichen und vordefinierte Muster, die oben beschrieben wurden, unterstützen Sie beim Erstellen von regulären Ausdrücken.  

Reguläre Ausdrücke sind sehr leistungsstark; sie stehen in vielen Programmiersprachen zur Verfügung und werden für eine Vielzahl von Aufgaben verwendet. In diesem Artikel können nicht alle Aspekte der regulären Ausdrücken beschreiben werden; allerdings können Sie im Internet viele weitere Informationen und Tutorials finden.  

Reguläre Ausdrücke haben unterschiedliche Dialekte; PowerApps verwendet eine Version von JavaScript. Weitere Informationen finden Sie unter [regular expression syntax (Syntax regulärer Ausdrücke)](http://msdn.microsoft.com/library/1400241x.aspx).

In der oben abgebildeten Tabelle der **Match**-Enumeration kann jede Enumeration in einen reguläre Ausdruck erweitert werden, der von der Textzeichenfolge in der Spalte „Regular Expression“ (Regulärer Ausdruck) definiert wird.

## <a name="match-options"></a>Übereinstimmungsoptionen
Sie können das Verhalten von **IsMatch** durch Angabe von einer oder mehreren Optionen anpassen, die Sie mit dem Operator für Zeichenfolgenverkettung (**&amp;**) kombinieren können.  

Standardmäßig prüft **IsMatch** auf eine vollständige Übereinstimmung mit der gesamte Textzeichenfolge.

| MatchOptions-Enumeration | Beschreibung | Auswirkungen auf den regulären Ausdruck |
| --- | --- | --- |
| **BeginsWith** |Das Muster muss ab dem Anfang des Texts übereinstimmen. |Fügt ein **^** am Anfang des regulären Ausdrucks ein |
| **Complete** |Standard.  Das Muster muss mit dem gesamten Text von Anfang bis Ende übereinstimmen. |Fügt ein **^** am Anfang und **$** am Ende des regulären Ausdrucks ein. |
| **Contains** |Das Muster muss irgendwo im Text vorkommen; allerdings muss es nicht zwangsläufig am Anfang oder Ende vorkommen. |Ändert nicht den regulären Ausdruck |
| **EndsWith** |Das Muster muss dem Ende des Texts entsprechen. |Fügt ein **$** am Ende des regulären Ausdrucks ein. |
| **IgnoreCase** |Ist für die Übereinstimmung von Groß- und Kleinbuchstaben verantwortlich. Standardmäßig wird bei der Übereinstimmung auf Groß- und Kleinschreibung geachtet. |Ändert nicht den regulären Ausdruck |
| **Multiline** |Zeilenübergreifende Übereinstimmung |Ändert nicht den regulären Ausdruck |

## <a name="syntax"></a>Syntax
**IsMatch**( *Text*, *Pattern* [, *Options* ] )

* *Text*: Erforderlich.  Die zu prüfende Textzeichenfolge
* *Pattern*: erforderlich.  Das zu prüfende Muster als Textzeichenfolge  Verketten Sie vordefinierte Muster, die die **Match**-Enumeration definiert, oder stellen Sie einen regulären Ausdruck zur Verfügung.
* *Options*: optional.  Eine Kombination der Textzeichenfolge aus **MatchOptions**-Enumerationswerten.  Standardmäßig wird **MatchOptions.Complete** verwendet.

## <a name="examples"></a>Beispiele
### <a name="ordinary-characters"></a>Normales Zeichen
Stellen Sie sich vor, dass die App ein **Texteingabe**-Steuerelement mit dem Namen **TextInput1** enthält.  Der Benutzer gibt Werte in dieses Steuerelement ein, die in einer Datenbank gespeichert werden sollen.   

Der Benutzer gibt **Hello World** in **Texteingabe1** ein.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **IsMatch( TextInput1.Text, "Hello world" )** |Prüft, ob die Benutzereingaben genau mit der Zeichenfolge „Hello World“ übereinstimmt |**TRUE** |
| **IsMatch( TextInput1.Text, "Good bye" )** |Prüft, ob die Benutzereingaben genau mit der Zeichenfolge "Good Bye" übereinstimmt |**FALSE** |
| **IsMatch( TextInput1.Text, "hello", Contains )** |Prüft, ob die Eingabe des Benutzers das Wort „Hello“ (Groß-/Kleinschreibung wird beachtet) enthält |**FALSE** |
| **IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )** |Prüft, ob die Eingabe des Benutzers das Wort „Hello“(Groß-/Kleinschreibung beachten) enthält. |**TRUE** |

### <a name="predefined-patterns"></a>Vordefinierte Muster

|                                                            Formel                                                            |                                                                Beschreibung                                                                |  Ergebnis   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| **IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit & Digit )** |                                              Ordnet eine US-Sozialversicherungsnummer zu                                               | **TRUE**  |
|                                           **IsMatch( "joan@contoso.com", Email )**                                            |                                                         Ordnet eine E-Mail-Adresse zu                                                          | **TRUE**  |
|                              **IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )**                               |                                   Ordnet eine Folge von Ziffern, einen Punkt (.) und dann 0 (null) oder mehrere Ziffern zu                                   | **TRUE**  |
|                                **IsMatch( "123", MultipleDigits & Period & OptionalDigits )**                                 | Ordnet eine Folge von Ziffern, einen Punkt (.) und dann 0 (null) oder mehrere Ziffern zu Im Text kommt kein Punkt vor, weshalb dieses Muster nicht übereinstimmt. | **FALSE** |

### <a name="regular-expressions"></a>Reguläre Ausdrücke

|                                                                              Formel                                                                              |                                                                                                                                  Beschreibung                                                                                                                                   |  Ergebnis   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    **IsMatch( "986", "\d+" )**                                                                    |                                                                                                                    Ordnet eine ganze Zahl größer als 0 (null) zu                                                                                                                     | **TRUE**  |
|                                                               **IsMatch( "1.02", "\d+(\.\d\d)?" )**                                                               |                                        Ordnet einen positiven Währungsbetrag zu Wenn die Eingabe ein Dezimaltrennzeichen enthält, muss die Eingabe auch zwei numerische Zeichen nach dem Dezimaltrennzeichen enthalten. 3,00 ist beispielsweise gültig, aber 3,1 nicht.                                         | **TRUE**  |
|                                                            **IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )**                                                             |                                                        Ordnet einen positiven oder negativen Währungsbetrag zu. Wenn die Eingabe ein Dezimaltrennzeichen enthält, muss die Eingabe auch zwei numerische Zeichen nach dem Dezimaltrennzeichen enthalten.                                                        | **TRUE**  |
|                                                         **IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )**                                                         | Ordnet eine US-Sozialversicherungsnummer zu  Überprüft das Format, den Typ und die Länge des angegebenen Eingabefelds. Die Zeichenfolge, die übereinstimmen soll, muss aus drei numerischen Zeichen gefolgt von einem Bindestrich und dann 2 numerische Zeichen gefolgt von einem Bindestrich und dann 4 numerischen Zeichen bestehen. | **TRUE**  |
|                                                         **IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )**                                                         |                                                                                               Wie im vorherigen Beispiel, aber einer der Bindestriche ist in der Eingabe an der falschen Stelle                                                                                               | **FALSE** |
|                                         **IsMatch( "weakpassword", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )**                                         |                                        Überprüft ein sicheres Kennwort, das 8, 9 oder 10 Zeichen enthalten muss, zusätzlich zu mindestens einer Ziffer und mindestens einem alphabetisches Zeichen. Die Zeichenfolge darf keine Sonderzeichen enthalten.                                        | **FALSE** |
| **IsMatch( "<http://microsoft.com>", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&amp;%\$#_]\*)?" )** |                                                                                                                     Überprüft eine http-, https- oder ftp-URL                                                                                                                      | **TRUE**  |

