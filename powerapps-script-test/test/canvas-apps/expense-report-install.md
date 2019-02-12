---
title: Installieren und Konfigurieren des Beispiels „Expense Report“ für Canvas-Apps | Microsoft-Dokumentation
description: Exemplarische Vorgehensweise zum Installieren und Konfigurieren des Beispiels „Expense Report“ für Canvas-Apps in PowerApps
author: caburk
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/08/2018
ms.author: caburk
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 43d1dc6ef2d264dd60b6a9f3de0f5c0fed633283
ms.sourcegitcommit: d3d665500b9c49c14657d044b084bdd64c52c5a3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44124473"
---
# <a name="install-and-configure-the-expense-report-sample-for-canvas-apps-in-powerapps"></a>Installieren und Konfigurieren des Beispiels „Expense Report“ für Canvas-Apps in PowerApps

Ausführliche Anleitung zum Installieren und Konfigurieren der Beispiel-App „Expense Report“ [Hier](https://aka.ms/previewmyexpenses) können Sie auch eine Vorschau der Beispiel-App anzeigen.

Geschätzte Dauer: **10–15 Minuten**.

> [!TIP]
> Sehen Sie sich [in diesem Video](https://youtu.be/kJXZPILfbwU) eine Demonstration zur Verwendung der Beispiel-App „Expense Report“ an. 

Verfolgen Sie Ausgabenberichte nach – von der Einreichung bis zur Genehmigung. Buchen Sie Positionen als individuellen Ausgabenzuwachs, und senden Sie die Berichte zur Genehmigung, wenn sie fertig sind. Diese App erfordert ein geringes Maß an Einrichtung, um sie an Ihre Anforderungen anzupassen.

![Startbildschirm der PowerApp „Expense Report“](./media/expense-report-install/expense-report-powerapp.png)

> [!TIP]
> Sehen Sie sich [dieses Video](https://youtu.be/h6E9cdrOvMU) an, um mehr über die Verwendung der PowerApps-Beispiel-App „Expense Report“ zu erfahren.

## <a name="prerequisites"></a>Voraussetzungen

- [Registrieren Sie sich](../signup-for-powerapps.md) bei PowerApps.

## <a name="create-the-expenses-sharepoint-list"></a>Erstellen der SharePoint-Liste „Ausgaben“

In dieser Liste werden die Ausgabenbereich gespeichert.

1. Öffnen Sie einen Webbrowser, und navigieren Sie zu https://portal.office.com.
2. Melden Sie sich mit einem Konto an, das über die Berechtigung zum Erstellen von Listen verfügt.
3. Navigieren Sie zur Websitesammlung, in der Sie die Ausgabenliste erstellen möchten.
4. Klicken Sie auf das **Zahnradsymbol** oben rechts auf der Webseite.
5. Klicken Sie auf **Add an App** (Eine App hinzufügen).
6. Geben Sie im Textfeld **Eine App suchen** **Benutzerdefiniert** ein.
7. Klicken Sie auf das **Lupensymbol**.
8. Klicken Sie auf die App **Benutzerdefinierte Liste**.
9. Geben Sie im Textfeld **Name** **Ausgaben** ein.

    > [!IMPORTANT]
    > Wenn Sie einen anderen Namen für die Liste eingeben, schreiben Sie sich diesen auf, da Sie ihn während der Installation und Konfiguration überall dort eingeben müssen, wo hier „Ausgaben“ verwendet wird.

10. Klicken Sie auf **Erstellen**.

### <a name="create-cost-center-column"></a>Erstellen der Spalte „Kostenstelle“

1. Klicken Sie auf die Liste **Ausgaben**.
2. Klicken Sie auf das **Zahnradsymbol** oben rechts auf der Webseite.
3. Klicken Sie auf **Listeneinstellungen**.
4. Klicken Sie auf **Spalte erstellen**.
5. Geben Sie im Textfeld **Spaltenname** **Kostenstelle** ein.
6. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Auswahl**.
7. Geben Sie im Textfeld **Geben Sie jede Auswahl in einer neuen Zeile ein** die folgenden Werte jeweils in einer neuen Zeile ein: 
    - Microsoft
    - Contoso
8. Geben Sie im Textfeld **Standardwert** **Microsoft** ein.
9. Klicken Sie auf **OK**.

### <a name="create-comments-column"></a>Erstellen der Spalte „Kommentare“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **Kommentare** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Mehrere Textzeilen**.
4. Klicken Sie auf **OK**.

### <a name="create-status-column"></a>Erstellen der Spalte „Status“

1. Klicken Sie auf die Liste **Ausgaben**.
2. Klicken Sie auf das **Zahnradsymbol** oben rechts auf der Webseite.
3. Klicken Sie auf **Listeneinstellungen**.
4. Klicken Sie auf **Spalte erstellen**.
5. Geben Sie im Textfeld **Spaltenname** **Status** ein.
6. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Auswahl**.
7. Geben Sie im Textfeld **Geben Sie jede Auswahl in einer neuen Zeile ein** die folgenden Werte jeweils in einer neuen Zeile ein: 
    - Offen
    - Ausstehend
    - Approved (Genehmigt)
8. Geben Sie im Textfeld **Standardwert** **Öffnen** ein.
9. Klicken Sie auf **OK**.

### <a name="create-approvername-column"></a>Erstellen der Spalte „NameDesGenehmigers“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **NameDesGenehmigers** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Person or Group** (Person oder Gruppe).
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Klicken Sie auf **OK**.

### <a name="create-datesubmitted-column"></a>Erstellen der Spalte „DatumDerÜbermittlung“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **DatumDerÜbermittlung** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Datum und Uhrzeit**.
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Klicken Sie auf **OK**.

### <a name="create-startdate-column"></a>Erstellen der Spalte „Startdatum“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **Startdatum** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Datum und Uhrzeit**.
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Klicken Sie auf **OK**.

### <a name="create-enddate-column"></a>Erstellen der Spalte „Enddatum“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **Enddatum** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Datum und Uhrzeit**.
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Klicken Sie auf **OK**.

## <a name="create-the-line-items-sharepoint-list"></a>Erstellen der SharePoint-Liste mit separaten Positionen

In dieser Liste werden die Positionen der Ausgabenberichte gespeichert.

1. Navigieren Sie zur gleichen Websitesammlung, in der Sie die Ausgabenliste erstellt haben.
2. Klicken Sie auf das **Zahnradsymbol** oben rechts auf der Webseite.
3. Klicken Sie auf **Add an App** (Eine App hinzufügen).
4. Geben Sie im Textfeld **Eine App suchen** **Benutzerdefiniert** ein.
5. Klicken Sie auf das **Lupensymbol**.
6. Klicken Sie auf die App **Benutzerdefinierte Liste**.
7. Geben Sie im Textfeld **Name** **Positionen** ein.

    > [!IMPORTANT] 
    > Wenn Sie einen anderen Namen für die Liste eingeben, schreiben Sie sich diesen auf, da Sie ihn während der Installation und Konfiguration überall dort eingeben müssen, wo hier „Ausgaben“ verwendet wird.

8. Klicken Sie auf **Erstellen**.
 
### <a name="create-category-column"></a>Erstellen der Spalte „Kategorie“

1. Klicken Sie auf die Liste **Positionen**.
2. Klicken Sie auf das **Zahnradsymbol** oben rechts auf der Webseite.
3. Klicken Sie auf **Listeneinstellungen**.
4. Klicken Sie auf **Spalte erstellen**.
5. Geben Sie im Textfeld **Spaltenname** das Wort **Kategorie** ein.
6. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Auswahl**.
7. Geben Sie im Textfeld **Geben Sie jede Auswahl in einer neuen Zeile ein** die folgenden Werte jeweils in einer neuen Zeile ein: 
    - Essen & Trinken
    - Transport und Verkehr
    - Geschäftsanforderungen
8. Geben Sie im Textfeld **Standardwert** **Essen & Trinken** ein.
9. Klicken Sie auf **OK**.

### <a name="create-cost-column"></a>Erstellen der Spalte „Kosten“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **Kosten** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Number (1, 10, 100)** (Zahl (1, 10, 100)).
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Klicken Sie auf **OK**.

### <a name="create-date-column"></a>Erstellen der Spalte „Datum“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **Datum** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Datum und Uhrzeit**.
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Klicken Sie auf **OK**.

### <a name="create-description-column"></a>Erstellen der Spalte „Beschreibung“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** das Wort **Beschreibung** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Mehrere Textzeilen**.
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Wählen Sie in der Optionsfeldliste **Specify the type of text to allow** (Zu erlaubender Textyp auswählen) **Nur-Text** aus.
6. Klicken Sie auf **OK**.

### <a name="create-reportid-column"></a>Erstellen der Spalte „BerichtsID“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** **BerichtsID** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Lookup (information already on this site)** (Suchen (Informationen, die sich bereits auf dieser Website befinden)).
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
5. Klicken Sie in der Dropdownliste **Get information from** (Informationen abrufen von) auf die Liste **Ausgabe**, die Sie erstellt haben.
6. Klicken Sie in der Dropdownliste **In this column** (In dieser Spalte) auf **ID**.
7. Klicken Sie auf **OK**.

### <a name="edit-title-column"></a>Bearbeiten der Spalte „Titel“

1. Klicken Sie auf den Link zur Spalte **Titel**.
2. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Nein**.
3. Klicken Sie auf **OK**.

## <a name="download-the-expense-report-powerapp"></a>Herunterladen der PowerApp „Expense Report“

1.  Navigieren Sie in einem Webbrowser zu folgendem Link:

    [http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip](http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip).

2.  Laden Sie das PowerApps-Beispielpaket „Expense Report“ herunter, und speichern Sie es auf Ihrem Computer.

## <a name="create-connections"></a>Erstellen von Verbindungen

1.  Navigieren Sie in einem Webbrowser zu [web.powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2.  Melden Sie sich mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.
3.  Wählen Sie im Menü auf der linken Seite **Verbindungen** aus.

### <a name="create-approvals-connection"></a>Erstellen der Verbindung „Approvals“ (Genehmigungen)

1.  Klicken Sie auf **+ Neue Verbindung**.
2.  Geben Sie in das **Suchfeld** **Approvals** (Genehmigungen) ein.
3.  Klicken Sie in der Liste auf **Approvals**.
4.  Klicken Sie auf **Erstellen**.
    
### <a name="create-office-365-outlook-connection"></a>Erstellen einer Office 365 Outlook-Verbindung

1.  Klicken Sie auf **+ Neue Verbindung**.
2.  Geben Sie im **Suchfeld** die Verbindung **Office 365 Outlook** ein.
3.  Klicken Sie in der Liste auf **Office 365 Outlook**.
4.  Klicken Sie auf **Erstellen**.
5.  Wählen Sie im Popupfenster das Konto aus, mit dem Sie sich angemeldet haben.

### <a name="create-sharepoint-connection"></a>Erstellen einer SharePoint-Verbindung

1.  Klicken Sie auf **+ Neue Verbindung**.
2.  Geben Sie in das **Suchfeld** die Verbindung **SharePoint** ein.
3.  Klicken Sie in der Liste auf **SharePoint**.
4.  Klicken Sie auf **Erstellen**.
5.  Wählen Sie im Popupfenster das Konto aus, mit dem Sie sich angemeldet haben.

## <a name="import-the-expense-report-powerapp"></a>Importieren der PowerApp „Expense Report“

1. Navigieren Sie in einem Webbrowser zu https://web.powerapps.com.
2. Melden Sie sich mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.
3. Wählen Sie im Menü auf der linken Seite **Apps** aus. 
4. Klicken Sie auf **Paket importieren (Vorschau)**.
    
   ![Anzeige „Paket importieren“](./media/expense-report-install/import-package.png)

5. Klicken Sie auf **Hochladen**, und wählen Sie das PowerApps-Paket aus, das Sie in den vorherigen Schritten heruntergeladen haben.
6. Legen Sie für die Ressourcentypen **App** und **Flow** für **IMPORTEINRICHTUNG** die Option **Als neu erstellen** fest.
7. Legen Sie für die Verbindungen **SharePoint** und **Outlook** für **IMPORTEINRICHTUNG** die Option **Beim Import auswählen** fest.
    
   ![Anzeige „Importeinstellungen“](./media/expense-report-install/import-settings.png)

8. Klicken Sie auf das **rote Symbol** für die **SharePoint-Verbindung**.
9. Klicken Sie in der Verbindungsliste auf das Element mit ihrem Benutzernamen.

   ![Anzeige „Importeinstellungen“](./media/expense-report-install/import-settings-sharepoint.png)

10. Klicken Sie auf **Speichern**.
11. Klicken Sie auf das **rote Symbol** für die **Genehmigungsverbindung**.
12. Klicken Sie in der Verbindungsliste auf das Element mit ihrem Benutzernamen.

    ![Anzeige „Importeinstellungen“](./media/expense-report-install/import-settings-approvals.png)

13. Klicken Sie auf **Speichern**.
14. Klicken Sie auf das **rote Symbol** für die **Office 365 Outlook-Verbindung**.
15. Klicken Sie in der Verbindungsliste auf das Element mit ihrem Benutzernamen.

    ![Anzeige „Importeinstellungen“](./media/expense-report-install/import-settings-office365outlook.png)

16. Klicken Sie auf **Speichern**.

    > [!TIP] 
    > Anschließend wird Folgendes auf dem Bildschirm angezeigt:

    ![Anzeige „Importeinstellungen“](./media/expense-report-install/import-settings-done.png)

17. Klicken Sie auf **Importieren**, und warten Sie, bis der Vorgang abgeschlossen ist.

    ![Anzeige „Importeinstellungen“](./media/expense-report-install/import-done.png)

## <a name="configure-the-powerapp-to-use-the-sharepoint-lists"></a>Konfigurieren der PowerApps-App, sodass sie die SharePoint-Liste verwendet

1. Klicken Sie im Webbrowser auf **Apps**.
2. Klicken Sie auf die **Auslassungspunkte** neben der Expense Report-PowerApp.
3. Klicken Sie auf **Im Web bearbeiten**.
4. Klicken Sie auf **Allow** (Zulassen).

### <a name="delete-connections"></a>Löschen von Verbindungen
1. Klicken Sie auf **Ansicht**.
2. Klicken Sie auf **Datenquellen**.
3. Klicken Sie im Bereich **Daten** auf die **Auslassungspunkte** neben **Ausgaben**.
4. Klicken Sie auf **Entfernen**.
5. Klicken Sie im Bereich **Daten** auf die **Auslassungspunkte** neben **Positionen**.
6. Klicken Sie auf **Entfernen**.

### <a name="expenses-list"></a>Ausgabenliste

1. Klicken Sie auf **Ansicht**.
2. Klicken Sie auf **Datenquellen**.
3. Klicken Sie im Bereich **Daten** auf **Datenquelle hinzufügen**.
4. Klicken Sie auf **+ Neue Verbindung**.
5. Wählen Sie **SharePoint** aus.
6. Klicken Sie auf **Erstellen**.
7. Wählen Sie in der Liste **Zuletzt geöffnete Websites** die SharePoint-Website aus, auf der Sie die Ausgabenliste erstellt haben.

    > [!TIP] 
    > Wenn die Website nicht in der Liste angezeigt wird, geben Sie die URL der SharePoint-Website im Testfeld ein, und klicken Sie auf **Los**.

8. Geben Sie im **Suchfeld** über der Liste **Ausgaben** ein.
9. Aktivieren Sie das Kontrollkästchen neben der **Ausgabenliste**.
10. Klicken Sie auf **Verbinden**.

### <a name="lineitems-list"></a>Liste „Positionen“

1. Klicken Sie auf **Ansicht**.
2. Klicken Sie auf **Datenquellen**.
3. Klicken Sie im Bereich **Daten** auf **Datenquelle hinzufügen**.
4. Klicken Sie auf **+ Neue Verbindung**.
5. Wählen Sie **SharePoint** aus.
6. Klicken Sie auf **Erstellen**.
7. Wählen Sie in der Liste **Zuletzt geöffnete Websites** die SharePoint-Website aus, auf der Sie die Liste „Positionen“ erstellt haben.

    > [!TIP] 
    > Wenn die Website nicht in der Liste angezeigt wird, geben Sie die URL der SharePoint-Website im Testfeld ein, und klicken Sie auf **Los**.

8. Geben Sie im **Suchfeld** über der Liste **Postionen** ein.
9. Aktivieren Sie das Kontrollkästchen neben der Liste **Positionen**.
10. Klicken Sie auf **Verbinden**.
11. Klicken Sie auf **Datei**.
12. Klicken Sie auf **Speichern**.
13. Klicken Sie auf **Veröffentlichen**.
14. Klicken Sie auf **Diese Version veröffentlichen**.

## <a name="modify-the-flow"></a>Ändern des Flows

1.  Klicken Sie links im Menü auf **Flows**.
2.  Wenn Sie dazu aufgefordert werden, melden Sie sich mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.
3.  Wählen Sie im oberen Menü **Meine Flows** aus.
4.  Klicken Sie neben dem Flow **ApproveExpense** (AusgabeGenehmigen) auf das **Stiftsymbol**.
 
    ![Anzeige „Flow bearbeiten“](./media/expense-report-install/edit-flow.png)

5.  Erweitern Sie die Aktion **Elemente abrufen**. 
6.  Passen Sie die **Websiteadresse** und den **Listennamen** so an, dass sie der Expense SharePoint-Liste entsprechen, die Sie erstellt haben.
    
    ![Anzeige „Flow bearbeiten“](./media/expense-report-install/edit-flow-getitems.png)

    > [!TIP] 
    > Sie müssen keine manuelle Angabe machen, sondern können in der Dropdownliste eine Auswahl treffen.

7.  Erweitern Sie die **Bedingung**.
8.  Erweitern Sie den Bereich **Wenn ja**.
9.  Erweitern Sie die Aktion **Change item status to Approved** (Elementstatus in Genehmigt ändern).
10. Passen Sie die **Websiteadresse** und den **Listennamen** so an, dass sie der Expense SharePoint-Liste entsprechen, die Sie erstellt haben.

    ![Anzeige „Flow bearbeiten“](./media/expense-report-install/edit-flow-condition-ifyes.png) 

    > [!TIP] 
    > Sie müssen keine manuelle Angabe machen, sondern können in der Dropdownliste eine Auswahl treffen.

11. Erweitern Sie den Bereich **Wenn nein**.
12. Erweitern Sie die Aktion **Change item status to Open** (Elementstatus in „Offen“ ändern).
13. Passen Sie die **Websiteadresse** und den **Listennamen** so an, dass sie der Expense SharePoint-Liste entsprechen, die Sie erstellt haben. 

    ![Anzeige „Flow bearbeiten“](./media/expense-report-install/edit-flow-condition-ifno.png)

    > [!TIP] 
    > Sie müssen keine manuelle Angabe machen, sondern können in der Dropdownliste eine Auswahl treffen.

14. Klicken Sie auf **Flow aktualisieren**.

## <a name="play-the-powerapp"></a>Wiedergeben der PowerApps-App

1. Klicken Sie im Webbrowser auf **Apps**.
2. Klicken Sie auf die **Auslassungspunkte** neben der Expense Report-PowerApp.
3. Klicken Sie auf **Öffnen**.


## <a name="next-steps"></a>Nächste Schritte
- [Anpassen eines SharePoint-Listenformulars mit PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [Hinzufügen und Konfigurieren eines Steuerelements in PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [Bearbeiten und Verwalten von Berechtigungen für eine SharePoint-Liste oder -Bibliothek](https://support.office.com/en-us/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)



