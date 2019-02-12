---
title: Verwenden des Steuerelements „Formularentität“ | Microsoft-Dokumentation
description: Erstellen Sie Apps schneller, indem Sie das Steuerelement „Formularentität“ verwenden, mit dem Sie umfangreiche Formulare für eine Common Data Service-Entität hinzufügen können.
author: aneesmsft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/11/2017
ms.author: aneesa
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ee8573cb9ae4df5ac42deefad4ac67aede3a3502
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836275"
---
# <a name="use-the-entity-form-control"></a>Verwenden des Steuerelements „Formularentität“
Erstellen Sie Apps schneller, indem Sie das Steuerelement **Formularentität** verwenden, mit dem Sie umfangreiche Formulare für eine Common Data Service-Entität hinzufügen können.

Eine Einführung in das Steuerelement **Formularentität** finden Sie in diesem Blogbeitrag: [New entity form control (experimental feature) for Common Data Service (Neues Steuerelement „Formularentität“ (experimentelle Funktion) für Common Data Service)](https://powerapps.microsoft.com/blog/new-entity-form-control-experimental-feature-for-common-data-service/).

> [!IMPORTANT]
> Beachten Sie, dass es sich bei dem Steuerelement **Formularentität** wie im Blogbeitrag beschrieben um eine experimentelle Funktion handelt, und seien Sie zunächst vorsichtig, wenn Sie das Steuerelement **Formularentität** in Produktions-Apps verwenden.

## <a name="key-properties"></a>Haupteigenschaften
Hier sind die wichtigsten Eigenschaften des Steuerelements **Formularentität**.

**DataSource**: Gibt die Datenquelle an, die den Datensatz (die Datensätze) enthält, den (die) Sie anzeigen möchten.   
> [!NOTE]
> Derzeit werden nur Entitäten in Common Data Service als Datenquellen für das Steuerelement **Formularentität** unterstützt.  

**Pattern**: Gibt die Formatvorlage des Formulars an, das im Steuerelement **Formularentität** angezeigt werden soll. Legen Sie diese Eigenschaft mithilfe der **FormPattern**-Enumeration fest.

* **FormPattern.List**: Zeigt eine tabellarische Liste von Datensätzen an.
* **FormPattern.CardList**: Zeigt eine Kartenliste von Datensätzen an.
* **FormPattern.Details**: Zeigt ein Formular zum Anzeigen oder Bearbeiten der Details eines einzelnen Datensatzes an.
* **FormPattern.None**: Es wurde keine Formatvorlage explizit angegeben. Verwendet standardmäßig **List** für Tablet-Apps und **CardList** für Phone-Apps.

**Item**: Gibt den Datensatz in der Datenquelle an, den das Steuerelement **Formularentität** anzeigen soll. Diese Eigenschaft wird nur verwendet, wenn **Pattern** auf **FormPattern.Details** festgelegt ist.

**Selected**: Ruft den Datensatz ab, der gerade ausgewählt ist.  
Beispiel: Wenn das Steuerelement **Formularentität** eine Liste mit Verkaufsauftrag-Datensätzen anzeigt, gibt die **Selected**-Eigenschaft den Datensatz an, der gerade ausgewählt ist. Sie können auch auf ein Feld in einem Datensatz zugreifen. (Geben Sie z.B. für den Wert des **Account**-Felds (Konto) des ausgewählten Datensatzes **Selected.Account** an.)

**SelectableFields**: Gibt an, welche Felder als Links angezeigt werden sollen. Legen Sie den Wert dieser Eigenschaft mithilfe der folgenden Syntax fest:  
**{Field1Name : true, Field2Name : true}**  
Beispiel: Wenn Sie möchten, dass die Felder **SalesOrderId** und **Account** in einem Formular als Links angezeigt werden, müssen Sie die **SelectableFields**-Eigenschaft dieses Formulars auf diesen Wert festlegen:  
**{SalesOrderId : true, Account : true}**

**SelectedField**: Bestimmt, welches Feld angeklickt oder angetippt wurde. Dies gilt nur für die Felder, die als **SelectableFields** angegeben werden.  
Beispiel: Wenn Sie die **SelectableFields**-Eigenschaft auf **{SalesOrderId : true, Account : true}** festlegen und der Benutzer auf das **Account**-Feld klickt oder tippt, wird **SelectedField.Account** auf TRUE festgelegt.

**OnFieldSelect**: Gibt an, wie eine App reagiert, wenn der Benutzer auf ein Feld klickt oder tippt. Dies gilt nur für die Felder, die als **SelectableFields** angegeben werden.

**Mode**: Bestimmt den Modus des Formulars. Verwenden Sie zum Ändern des Modus die Funktion **ViewForm**, **EditForm** oder **NewForm**. Diese Funktionen funktionieren nur, wenn die **Pattern**-Eigenschaft auf **FormPattern.Details** festgelegt ist. Legen Sie den Wert der **Mode**-Eigenschaft auf den Wert der **FormMode**-Enumeration fest.

* **FormMode.View**: Ermöglicht Benutzern das Anzeigen, aber nicht das Bearbeiten oder Hinzufügen eines Datensatzes.
* **FormMode.Edit**: Ermöglicht Benutzern das Bearbeiten eines Datensatzes.
* **FormMode.New**: Ermöglicht Benutzern das Hinzufügen eines Datensatzes.

**OnSuccess**: Gibt an, wie eine App reagiert, wenn ein Datenvorgang erfolgreich ausgeführt wurde.

**OnFailure**: Gibt an, wie eine App reagiert, wenn ein Datenvorgang nicht erfolgreich ausgeführt wurde.

**Unsaved**: Gibt an, ob ein Datensatz, den ein Benutzer bearbeitet, über nicht gespeicherte Änderungen verfügt.

## <a name="related-functions"></a>Verwandte Funktionen
Sie können diese freigegebenen Funktionen entweder mit dem Steuerelement **Formularentität** oder mit dem Steuerelement [Formular bearbeiten](functions/function-form.md) verwenden. Diese Funktionen arbeiten nur mit dem Steuerelement **Formularentität**, wenn dessen **Pattern**-Eigenschaft auf **FormPattern.Details** festgelegt ist.

**ViewForm**: Legt die **Mode**-Eigenschaft eines Steuerelements **Formularentität** auf **FormMode.View** fest.

**EditForm**: Legt die **Mode**-Eigenschaft eines Steuerelements **Formularentität** auf **FormMode.Edit** fest.

**NewForm**: Legt die **Mode**-Eigenschaft eines Steuerelements **Formularentität** auf **FormMode.New** fest.

**SubmitForm**: Speichert Änderungen, wenn ein Benutzer einen Datensatz in einem Steuerelement **Formularentität** bearbeitet.

**ResetForm**: Verwirft nicht gespeicherte Änderungen, wenn ein Benutzer einen Datensatz in einem Steuerelement **Formularentität** bearbeitet.

Nun haben Sie einen Überblick über die verschiedenen Eigenschaften und Funktionen erhalten, und als Nächstes sehen wir sie uns in Aktion an.

> [!NOTE]
> Wenn Sie keinen Zugriff auf eine Common Data Service-Datenbank haben, erstellen Sie eine, bevor Sie die folgenden Schritte ausführen.

## <a name="display-a-list-of-records"></a>Anzeigen einer Liste von Datensätzen
Die folgenden fünf Vorgehensweisen bieten ein einzelnes, umfassendes Beispiel zur Verwendung von **Formularentität**-Steuerelementen. Fügen Sie in dieser Vorgehensweise ein Formular hinzu, das eine Liste mit Verkaufsaufträgen anzeigt.  

1. Erstellen Sie eine leere Tablet-App.
   
    ![](media/entity-form-control/entityform-tutorial-01-01.png)
2. Benennen Sie den ersten Bildschirm in **SalesOrderListScreen** um.
   
    ![](media/entity-form-control/entityform-tutorial-01-02.png)
3. Klicken oder tippen Sie auf der Registerkarte **Insert** (Einfügen) auf **Forms** (Formulare) und dann auf **Entity form (experimental)** (Formularentität (experimentell)).  
   
    Ein **Formularentität**-Steuerelement wird dem Bildschirm hinzugefügt.  
   
    ![](media/entity-form-control/entityform-tutorial-01-03.png)
4. Benennen Sie das Steuerelement **Formularentität** in **SalesOrderListForm** um, und ändern Sie seine Größe so, dass es den gesamten Bildschirm abdeckt.
5. Klicken oder tippen Sie im rechten Bereich auf das Datenbanksymbol neben dem Text **No data source selected** (Es ist keine Datenquelle ausgewählt) und dann auf **Add a data source** (Datenquelle hinzufügen).  
   
    ![](media/entity-form-control/entityform-tutorial-01-04.png)
6. Klicken oder tippen Sie in der Liste der Verbindungen auf die Verbindung für die Datenbank.  
   
    ![](media/entity-form-control/entityform-tutorial-01-05.png)
7. Klicken oder tippen Sie in der Liste der Entitäten auf **Sales order** (Verkaufsauftrag) und dann auf **Connect** (Verbinden).  
   
    Eine Datenquelle für die **Sales order**-Entität wird erstellt, und die **DataSource**-Eigenschaft von **SalesOrderListForm** wird auf diese Datenquelle festgelegt.
   
    ![](media/entity-form-control/entityform-tutorial-01-06.png)  
   
    Das Steuerelement **Formularentität** zeigt eine Liste mit Verkaufsaufträgen an. Mithilfe des Steuerelements **Formularentität** haben Sie schnell ein Listenformular angezeigt, ohne dass Sie es manuell erstellen mussten.
   
    ![](media/entity-form-control/entityform-tutorial-01-07.png)  
   
    Da Sie die **Pattern**-Eigenschaft für das Steuerelement **Formularentität** nicht festgelegt haben, wird es standardmäßig auf das **List**-Muster festgelegt. Darüber hinaus wird die **DefaultList**-Feldgruppe der **Sales order**-Entität verwendet, um das Listenformular anzuzeigen. Das Formular ist auch dynamisch, und jede Änderung in der Feldgruppe wird automatisch darauf angewendet.


## <a name="display-the-details-of-a-record"></a>Anzeigen der Details eines Datensatzes
Fügen Sie ein weiteres **Formularentität**-Steuerelement hinzu, um die Details des Verkaufsauftrags anzuzeigen, der in der zuvor erstellten Liste ausgewählt ist.  

1. Ändern Sie die Größe von **SalesOrderListForm** auf die halbe Bildschirmgröße, und fügen Sie ein zweites **Formularentität**-Steuerelement hinzu, um die andere Hälfte des Bildschirms abzudecken.  
   <br>![](media/entity-form-control/entityform-tutorial-01-09.png)
2. Benennen Sie das zweite **Formularentität**-Steuerelement in **SalesOrderDetailsForm** um, und verbinden Sie es mit der zuvor erstellten Datenquelle **Sales order** (Verkaufsauftrag).  
   <br>![](media/entity-form-control/entityform-tutorial-01-10.png)
3. Legen Sie die **Pattern**-Eigenschaft von **SalesOrderDetailsForm** auf **FormPattern.Details** fest.  
   
    **SalesOrderDetailsForm** verwendet die Feldgruppe **DefaultDetails** der **Sales order**-Entität, um das Formular anzuzeigen. Wie bei **SalesOrderListForm** können Sie schnell Details des Datensatzes anzeigen, ohne manuell ein Formular erstellen zu müssen.  
   
    ![](media/entity-form-control/entityform-tutorial-01-11.png)
4. Legen Sie die **Item**-Eigenschaft von **SalesOrderDetailsForm** auf **SalesOrderListForm.Selected** fest.
   
    **SalesOrderDetailsForm** zeigt die Details des Datensatzes an, auf den der Benutzer in **SalesOrderListForm** klickt oder tippt.
   
    ![](media/entity-form-control/entityform-tutorial-01-12.png)
5. Zeigen Sie eine Vorschau der App durch Drücken von F5 an, und klicken oder tippen Sie dann in der Liste auf der linken Seite auf einen Verkaufsauftrag.  
   
    Die Details der Bestellung, die Sie ausgewählt haben, werden auf der rechten Seite angezeigt.  
   
    ![](media/entity-form-control/entityform-tutorial-01-13.png)  

## <a name="configure-a-field-to-navigate-to-another-screen"></a>Konfigurieren eines Felds zum Navigieren zu einem anderen Bildschirm
Als Nächstes fügen wir der App weitere Bildschirme hinzu, und konfigurieren dann Felder in einem **Formularentität**-Steuerelement, um zu einem anderen Bildschirm in der App zu navigieren, wenn der Benutzer auf ein Feld klickt oder tippt.  

1. Fügen Sie der App einen zweiten Bildschirm hinzu, und benennen Sie den Bildschirm in **SalesOrderDetailsScreen** um.
2. Schneiden Sie **SalesOrderDetailsForm** aus, fügen Sie es auf **SalesOrderDetailsScreen** ein, und ändern Sie die Größe des Formulars, sodass es fast den ganzen Bildschirm abdeckt und am oberen Rand genügend Platz für ein Symbol bleibt.
3. Fügen Sie ein Rückwärtspfeil-Symbol in der oberen linken Ecke von **SalesOrderDetailsScreen** hinzu.
4. Legen Sie die **OnSelect**-Eigenschaft des Rückwärtspfeil-Symbols auf die [**Back**](functions/function-navigate.md)-Funktion fest.  
   
    ![](media/entity-form-control/entityform-tutorial-01-14.png)
5. Ändern Sie auf **SalesOrderListScreen** die Größe von **SalesOrderListForm** so, dass es den gesamten Bildschirm abdeckt.
6. Klicken oder tippen Sie auf **SalesOrderListForm**, um es auszuwählen.
7. Legen Sie im rechten Bereich unter **Fields** (Felder) **SalesOrderId** so fest, dass es zu **SalesOrderDetailsScreen** navigiert.  
   
    ![](media/entity-form-control/entityform-tutorial-01-15.png)
   
    Das Steuerelement **Formularentität** zeigt die Werte im **SalesOrderId**-Feld (erste Spalte in der Liste) als Links an.
   
    ![](media/entity-form-control/entityform-tutorial-01-16.png)  
8. Zeigen Sie eine Vorschau der App durch Drücken von F5 an, und klicken oder tippen Sie dann in der Liste der Verkaufsaufträge auf einen Link.
   
    ![](media/entity-form-control/entityform-tutorial-01-17.png)  
   
    Der zweite Bildschirm wird geöffnet und zeigt die Details zum angegebenen Verkaufsauftrag an.
   
    ![](media/entity-form-control/entityform-tutorial-01-18.png)  
   
    Klicken oder tippen Sie zum Anzeigen der Details zu einem anderen Verkaufsauftrag auf den Rückwärtspfeil, um zurück zur Liste zu navigieren, und klicken oder tippen Sie dann auf den Link des Verkaufsauftrags, für den Sie Details anzeigen möchten.

## <a name="navigate-with-a-context-variable"></a>Navigieren mit einer Kontextvariablen
Die **Item**-Eigenschaft von **SalesOrderDetailsForm** ist auf **SalesOrderListForm.Selected** festgelegt, sodass **SalesOrderDetailsForm** Details zu dem Datensatz anzeigt, den der Benutzer in **SalesOrderListForm** auswählt. Sie können den Kontext des ausgewählten Datensatzes auch mithilfe der Kontextvariablen **NavigationContext** abrufen, die automatisch erstellt wird, wenn Sie den Bereich für die Anpassung von Formularen verwenden, um ein Feld zum Navigieren zu konfigurieren.  

1. Legen Sie die **Item**-Eigenschaft von **SalesOrderDetailsForm** auf **NavigationContext** fest.
   
    ![](media/entity-form-control/entityform-tutorial-01-19.png)
2. Zeigen Sie eine Vorschau der App durch Drücken von F5 an, und klicken oder tippen Sie dann in der Liste der Verkaufsaufträge auf einen Link.
   
    Die App öffnet **SalesOrderDetailsScreen** und zeigt die Details des angegebenen Verkaufsauftrags an.

Befassen wir uns nun näher damit, wie der Bereich für die Anpassung von Formularen für uns Navigation und Kontext einrichtet.  

Die **SelectableFields**-Eigenschaft von **SalesOrderListForm** legt **SalesOrderId** als auswählbares Feld fest.

![](media/entity-form-control/entityform-tutorial-01-20.png)  

Dies wurde automatisch eingerichtet, als wir den Bereich für die Anpassung von Formularen verwendet haben, um das **SalesOrderId**-Feld für die Navigation zu **SalesOrderDetailsScreen** einzurichten. Aus diesem Grund werden die Werte im **SalesOrderId**-Feld als Links angezeigt.

Die **OnFieldSelect**-Eigenschaft von **SalesOrderListForm** ist auf eine [**If**](functions/function-if.md)-Funktion festgelegt, die bestimmt, ob der Benutzer auf das **SalesOrderId**-Feld klickt oder tippt: **SalesOrderListForm.SelectedField.SalesOrderId = true**.  

Wenn die Funktion als TRUE ausgewertet wird, öffnet sich **SalesOrderDetailsScreen** mit der zuvor verwendeten Kontextvariablen **NavigationContext**.  

All dies wurde ebenfalls automatisch eingerichtet, als wir den Bereich für die Anpassung von Formularen verwendet haben, um das **SalesOrderId**-Feld für die Navigation zu **SalesOrderDetailsScreen** einzurichten.  

Wenn der Benutzer auf das SalesOrderId-Feld klickt oder tippt, wird deshalb die [**If**](functions/function-if.md)-Funktion zu TRUE ausgewertet, und die [**Navigate**](functions/function-navigate.md)-Funktion wird mit dem entsprechenden Kontext aufgerufen, sodass sich die Detailansicht öffnet.  

![](media/entity-form-control/entityform-tutorial-01-21.png)  

> [!NOTE]
> Wenn Sie den Bereich für die Anpassung von Formularen verwenden, wird **NavigationContext** für Sie intelligent bestimmt. Wenn der Benutzer auf **SalesOrderId** klickt oder tippt, wird **NavigationContext** auf **SalesOrderListForm.Selected** festgelegt, wie in der früheren Formel dargestellt. Wenn wir stattdessen das **Account**-Feld für die Navigation angegeben hätten, wäre **NavigationContext** auf **SalesOrderListForm.Selected.Account** festgelegt worden, um sicherzustellen, dass der richtige Kontext übergeben wird. Allerdings würden Sie für die Nutzung dieses Kontexts ein **Formularentität**-Steuerelement benötigen, das mit der **Account**-Entität in Common Data Service verbunden ist.

## <a name="edit-and-save-a-record"></a>Bearbeiten und Speichern eines Datensatzes
Abschließend sehen wir uns an, wie wir einen Datensatz in einem **Formularentität**-Steuerelement bearbeiten und speichern können.  

1. Fügen Sie auf **SalesOrderDetailsScreen** ein Bearbeitungssymbol hinzu, und legen Sie dann dessen **OnSelect**-Eigenschaft auf diese Formel fest:  
   **EditForm(SalesOrderDetailsForm)**
   
    ![](media/entity-form-control/entityform-tutorial-01-22.png)
2. Fügen Sie neben dem Bearbeitungssymbol ein Häkchen hinzu, und legen Sie dann die **OnSelect**-Eigenschaft des Häkchens auf diese Formel fest:  
   **SubmitForm(SalesOrderDetailsForm)**  
   
    ![](media/entity-form-control/entityform-tutorial-01-23.png)
3. Zeigen Sie eine Vorschau der App durch Drücken von F5 an, klicken oder tippen Sie auf einen **SalesOrderId**-Link, um die Details eines Verkaufsauftrags anzuzeigen, und klicken oder tippen Sie dann auf das Bearbeitungssymbol.  
   
    Die **Mode**-Eigenschaft des Steuerelements **Formularentität** ist auf **FormMode.Edit** festgelegt, sodass Sie den Datensatz bearbeiten können.
4. Aktualisieren Sie **Order status** (Auftragsstatus) auf **Invoice** (Rechnung).  
   
    ![](media/entity-form-control/entityform-tutorial-01-24.png)
5. Aktualisieren Sie **Sales person** (Vertriebsmitarbeiter) auf **WRK014**.
   
    Um Ihnen bei der Auswahl von **Sales person** (Vertriebsmitarbeiter) zu helfen, rendert das Steuerelement **Formularentität** automatisch eine ausführliche Suche. Zum Generieren und Anzeigen dieser Suche verwendet das Steuerelement die **DefaultLookup**-Feldgruppe der **Worker**-Entität in Common Data Service. Die **Worker**-Entität wird verwendet, weil das **Sales person**-Feld vom Typ **Worker** ist.
   
    ![](media/entity-form-control/entityform-tutorial-01-25.png)
6. Klicken oder tippen Sie auf das Häkchen, um die Änderungen zu speichern.

Mit diesem Schritt kommen wir zum Ende des Artikels über die Verwendung des Steuerelements **Formularentität** in Ihren Apps. Wir hoffen, dass die hier behandelten Informationen für Sie bei den ersten Schritten mit dem Steuerelement **Formularentität** nützlich waren. Wir freuen uns auf Ihre Meinung zum Steuerelement **Formularentität** und zu unserem allgemeinen Ansatz, Ihnen dabei zu helfen, schnell umfangreiche Formulare zu Ihren Apps hinzuzufügen.

