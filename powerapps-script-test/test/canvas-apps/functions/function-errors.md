---
title: Funktion „Errors“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Errors“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 886479b4cd2f7e04e9949c99ba05e6219e92b2b3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42859984"
---
# <a name="errors-function-in-powerapps"></a>Funktion „Errors“ in PowerApps
Enthält Fehlerinformationen zu vorherigen Änderungen an einer [Datenquelle](../working-with-data-sources.md).

## <a name="overview"></a>Übersicht
Es kann zu Fehlern kommen, wenn der [Datensatz](../working-with-tables.md#records) einer Quelle geändert wird.  Dafür gibt viele Ursachen, wie z.B. einen Netzwerkausfall, unzureichende Berechtigungen oder Bearbeitungskonflikte.  

Die **[Patch](function-patch.md)**-Funktion und andere Datenfunktionen geben Fehler nicht direkt zurück. Stattdessen geben sie das Ergebnis des Vorgangs zurück. Nachdem eine Datenfunktion ausgeführt wurde, können Sie mithilfe der **Errors**-Funktion die Details der Fehler abrufen.  Suchen Sie über die **[IsEmpty]**-Funktion in der Formel **IsEmpty ( Errors (...))**  nach Fehlern.

Sie können einige Fehler im Vorfeld vermeiden, wenn Sie die **[Validate](function-validate.md)** und die **[DataSourceInfo](function-datasourceinfo.md)**-Funktionen nutzen.  Weitere Informationen dazu, wie Sie mit Fehler umgehen oder sie vermeiden können, finden Sie unter [Working with data sources (Arbeiten mit Datenquellen)](../working-with-data-sources.md).

## <a name="description"></a>Beschreibung
Die **Errors**-Funktion gibt eine [Tabelle](../working-with-tables.md) von Fehlern mit den folgenden [Spalten](../working-with-tables.md#columns) zurück:

* **Record**.  Der Datensatz in der Datenquelle, die den Fehler enthält.  Wenn der Fehler während der Erstellung eines Datensatzes aufgetreten ist, hat diese Spalte den Wert *blank*.
* **Column**.  Die Spalte, die den Fehler verursacht hat, wenn der Fehler auf eine einzelne Spalte zurückverfolgt werden kann. Andernfalls hat die Spalte den Wert *leer*.
* **Message**.  Eine Beschreibung des Fehlers.  Diese Fehlerzeichenfolge kann für den Endbenutzer angezeigt werden.  Denken Sie daran, dass diese Meldung vielleicht von der Datenquelle generiert wird. Sie kann lang sein und unformatierte Spaltennamen enthalten, die möglicherweise keine Bedeutung für den Benutzer haben.
* **Error**.  Ein Fehlercode, der in Formeln verwendet werden kann, um den Fehler zu beheben:

| ErrorKind | Beschreibung |
| --- | --- |
| ErrorKind.Conflict |Am selben Datensatz wurde eine andere Änderung vorgenommen, die zu einem Änderungskonflikt geführt hat.  Verwenden Sie die **[Refresh](function-refresh.md)**-Funktion, um den Datensatz zu laden, und wiederholen Sie die Änderung. |
| ErrorKind.ConstraintViolation |Mindestens eine Einschränkung wurde verletzt. |
| ErrorKind.CreatePermission |Es wurde versucht, einen Datensatz zu erstellen, und der aktuelle Benutzer verfügt nicht über die Berechtigung zum Erstellen von Datensätzen. |
| ErrorKind.DeletePermission |Es wurde versucht, einen Datensatz zu löschen, und der aktuelle Benutzer verfügt nicht über die Berechtigung zum Löschen von Datensätzen. |
| ErrorKind.EditPermission |Es wurde versucht, einen Datensatz zu bearbeiten, und der aktuelle Benutzer verfügt nicht über die Berechtigung zum Bearbeiten von Datensätzen. |
| ErrorKind.GeneratedValue |Es wurde versucht, eine Spalte zu ändern, die die Datenquelle automatisch generiert. |
| ErrorKind.MissingRequired |Der Wert für eine erforderliche Spalte fehlt im Datensatz. |
| ErrorKind.None |Es liegt kein Fehler vor. |
| ErrorKind.NotFound |Es wurde versucht, einen Datensatz zu bearbeiten oder zu löschen, aber der Datensatz konnte nicht gefunden werden.  Ein anderer Benutzer hat den Datensatz möglicherweise geändert. |
| ErrorKind.ReadOnlyValue |Es wurde versucht, eine Spalte zu ändern, die schreibgeschützt ist. |
| ErrorKind.Sync |Von der Datenquelle wurde ein Fehler gemeldet.  Überprüfen Sie die Meldungsspalte auf weitere Informationen. |
| ErrorKind.Unknown |Es ist ein Fehler aufgetreten, der jedoch unbekannt ist. |
| ErrorKind.Validation |Es wurde ein allgemeines Validierungsproblem erkannt, das keinem anderen entspricht. |

Fehler können für die gesamte Datenquelle oder nur für eine ausgewählte Zeile durch die Bereitstellung des *Record*-Arguments für die Funktion zurückgegeben werden.  

**[Patch](function-patch.md)** oder eine andere Datenfunktion können einen Wert *blank* zurückgeben, wenn z.B. ein Datensatz nicht erstellt werden konnte. Sie können den Wert *Blank* an **Errors** übergeben, und es werden entsprechende Fehlerinformationen in diesen Fällen zurückgeben.  Bei einer späteren Verwendung der Datenfunktionen auf der gleichen Datenquelle werden diese Fehlerinformationen gelöscht.

Wenn keine Fehler vorliegen, ist die Tabelle, die **Errors** zurückgibt, [leer](function-isblank-isempty.md) und kann mit der **[IsEmpty](function-isblank-isempty.md)**-Funktion getestet werden.

## <a name="syntax"></a>Syntax
**Errors**( *DataSource* [, *Record* ] )

* *DataSource*: erforderlich. Die Datenquelle, für die Fehler zurückgegeben werden sollen.
* *Record*: optional.  Ein bestimmter Datensatz, für den Fehler zurückgegeben werden sollen. Wenn Sie dieses Argument nicht angeben, gibt die Funktion für die gesamte Datenquelle Fehler zurück.

## <a name="examples"></a>Beispiele
### <a name="step-by-step"></a>Schritt für Schritt
In diesem Beispiel arbeiten wir mit der Datenquelle **IceCream**:

![](media/function-errors/icecream.png)

Über die App lädt ein Benutzer den Schokoladendatensatz in ein Dateneingabeformular und ändert anschließend den Wert für **Quantity** auf 90.  Der Datensatz, mit dem gearbeitet wird, befindet sich in der [Kontextvariablen](../working-with-variables.md#create-a-context-variable) **EditRecord**:

* **UpdateContext( { EditRecord: First( Filter( IceCream, Flavor = "Chocolate" ) ) } )**

Für diese Änderung in der Datenquelle wird die **[Patch](function-patch.md)**-Funktion verwendet:

* **Patch( IceCream, EditRecord, Gallery.Updates )**

wobei **Gallery.Updates** den Wert **{Quantity: 90}** ergibt, da nur die **Quantity**-Eigenschaft geändert wurde.

Leider hat eine andere Person kurz vor dem Aufrufen der **[Patch](function-patch.md)**-Funktion den Wert für **Quantity** für Schokolade auf 80 geändert.  PowerApps erkennt dies und verhindert einen Änderungskonflikt.  Sie können dies anhand der folgenden Formel überprüfen:

* **IsEmpty( Errors( IceCream, EditRecord ) )**

Diese gibt **FALSE** zurück, da die **Errors**-Funktion die folgende Tabelle zurückgegeben hat:

| Datensatz | Spalte | Nachricht | Fehler |
| --- | --- | --- | --- |
| { Flavor: "Chocolate", Quantity: 100 } |*blank* |„Another user has modified the record that you're trying to modify. (Ein anderer Benutzer hat den Datensatz geändert, den Sie gerade ändern möchten.“) Please reload the record and try again.“ (Laden Sie den Datensatz neu, und versuchen Sie es erneut.) |ErrorKind.Conflict |

Sie können eine Bezeichnung auf dem Formular platzieren, um dem Benutzer diesen Fehler anzeigen.

* Um den Fehler anzuzeigen, legen Sie die Bezeichnung der  **[Text](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
  **Label.Text = First(Errors( IceCream, EditRecord )).Message**

Sie können auch eine **Reload**-Schaltfläche zum erneuten Laden im Formular hinzufügen, damit der Benutzer den Konflikt effizient beheben kann.

* Um die Schaltfläche nur dann anzuzeigen, wenn ein Konflikt aufgetreten ist, legen Sie die **[Visible](../controls/properties-core.md)**-Eigenschaft der Schaltfläche auf diese Formel fest:<br>
    **!IsEmpty( Lookup( Errors( IceCream, EditRecord ), Error = ErrorKind.Conflict ) )**
* Sie können die Änderung rückgängig machen, für die der Benutzer die Schaltfläche auswählt, indem Sie die **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel festlegen:<br>
    **ReloadButton.OnSelect = Revert( IceCream, EditRecord )**

