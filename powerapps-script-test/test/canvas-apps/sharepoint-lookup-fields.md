---
title: Erstellen einer Beziehung zwischen SharePoint-Listen mithilfe eines Nachschlagefelds in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen Sie in PowerApps mithilfe eines Nachschlagefelds eine Beziehung zwischen SharePoint-Listen in einer Canvas-App.
author: skjerland
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/20/2017
ms.author: sharik
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 88717f9ef894b4082b5881ea8c1f1209ce121e49
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864854"
---
# <a name="how-to-link-sharepoint-lists-using-a-lookup-field-in-powerapps"></a>Verknüpfen von SharePoint-Listen mithilfe von Nachschlagefeldern in PowerApps

In diesem Tutorial erfahren Sie, wie Sie zwei SharePoint-Listen mithilfe eines Nachschlagefelds in einer Canvas-App verknüpfen.

## <a name="overview"></a>Übersicht

SharePoint bietet zwei Arten von Nachschlagefeldern:

* **Nachschlagen**: Verknüpfung mit einer anderen Liste, z.B. kann eine Liste *Bestellungen* über ein Nachschlagefeld verfügen, das mit den Kunden in einer Liste der *Kunden* verknüpft ist.
* **Auswahl**: Durch Klicken oder Tippen auf dieses Feld wird ein kleines Menü mit Elementen angezeigt, aus denen Sie auswählen können.

In diesem Tutorial erstellen Sie eine App, die diese Arten von Nachschlagefeldern verwendet.

### <a name="why-use-a-lookup-field"></a>Gründe für die Verwendung eines Nachschlagefelds

Die Daten in einem Unternehmen sind umfangreich und komplex. Die Daten in einer SharePoint-Liste beziehen sich häufig auf Daten in einer anderen Liste. Nachschlagefelder sind die primäre Methode, um solche Geschäftsdaten zusammenzuführen.

Beispiel: Sie verfügen über eine Liste **Bestellungen**, die ein Nachschlagefeld aufweist, das mit der Liste **Kunden** verknüpft ist. So kann angezeigt werden, welche Kunden die jeweilige Bestellung getätigt haben. Das Nachschlagefeld in der Liste **Bestellungen** ermöglicht es Ihnen, auch Daten aus der Liste **Kunden** abzurufen. Sie könnten außerdem ein Nachschlagefeld verwenden, um die Liste **Bestellungen** mit einer Liste **Produkte** zu verknüpfen und so Informationen zu den bestellten Produkten bereitzustellen, z.B. Produktabbildungen, Spezifikationen, Herstellerdetails usw.

### <a name="what-are-choice-fields-used-for"></a>Wozu werden Auswahlfelder verwendet?
**Auswahlfelder** werden für sehr kurze Listen verwendet. Anstelle jedoch eine separate Liste zu erstellen, schließen Sie die Listenwerte in ein kleines Menü ein, das angezeigt wird, wenn Sie auf das **Auswahlfeld** tippen oder klicken. Anschließend können Sie einen der Werte auswählen.

Beispielsweise können Daten wie Kundenstatuscodes, Produktverfügbarkeit oder Statuscodes für Auswahlfelder verwendet werden – also grundsätzlich jede feste Liste, die relativ kurz ist. Diese Daten könnten natürlich auch als separate Listen implementiert und dann über ein **Nachschlagefeld** verknüpft werden, aber es ist in der Regel einfacher und schneller, sie als **Auswahlfelder** zu implementieren.

## <a name="create-the-lists-in-sharepoint"></a>Erstellen der Listen in SharePoint
In diesem Tutorial verknüpfen Sie zwei benutzerdefinierte SharePoint-Listen: **Assets** und **RepairShop**. Die Liste **Assets** wird verwendet, um Hardwarekomponenten in einem Team nachzuverfolgen. Da es bei Hardwarekomponenten gelegentlich zu einem Defekt kommen kann, werden mit der Liste **RepairShop** die lokalen Werkstätten nachverfolgt, die eine Reparatur durchführen können.

### <a name="the-lookup-fields-used-in-this-example"></a>In diesem Beispiel verwendete Nachschlagefelder
In der Liste **RepairShop** wird das Feld *ContactEmail* verwendet, um die Werkstatt zu identifizieren. Diese Liste wird zuerst definiert, sodass jede Zeile in der Liste **Assets** auf ein Element verweisen kann.

Die Liste **Assets** umfasst zwei Nachschlagefelder:

* Das Feld *RepairShop* ist vom Typ **Nachschlagen** und verwendet E-Mail-Adressen, um auf Einträge in der Liste **RepairShop** zu verweisen.
* Das Feld *AssetType* ist vom Typ **Auswahl** und listet die möglichen Hardwaretypen für die Assets auf.

Je nachdem, welche Informationen Sie nachverfolgen möchten, würden Sie wahrscheinlich weitere Felder definieren.

### <a name="define-the-repairshop-list-and-add-data"></a>Definieren der RepairShop-Liste und Hinzufügen von Daten
Dieser Schritt erfolgt zuerst, damit beim Hinzufügen von Daten zur Liste **Assets** schon Einträge in **RepairShop** verfügbar sind, die aus dem Nachschlagefeld *Assets.RepairShop* ausgewählt werden können.

1. Erstellen Sie auf Ihrer SharePoint-Website eine neue Liste **RepairShop**.

    ![](./media/sharepoint-lookup-fields/new-list.png)

2. Fügen Sie ein Feld *ContactEmail* vom Typ **Eine Textzeile** hinzu.

    ![](./media/sharepoint-lookup-fields/add-email-field.png)

3. Fügen Sie nach Bedarf weitere Felder hinzu.

4. Klicken oder tippen Sie auf **+ Neu**, um Beispieldaten in die Liste einzugeben. Fügen Sie mindestens 3 Zeilen mit unterschiedlichen *ContactEmail*-Werten ein. Wenn ein Asset repariert werden muss, wählen Sie eine der Adressen aus.

    ![](./media/sharepoint-lookup-fields/add-repair-shops.png)

### <a name="define-the-assets-list"></a>Definieren der Assetliste
1. Erstellen Sie auf Ihrer SharePoint-Website eine neue Liste **Assets**.

2. Klicken oder tippen Sie auf das Pluszeichen, und wählen Sie **Weitere** aus.

    ![](./media/sharepoint-lookup-fields/choose-more-type.png)

3. Fügen Sie ein Feld *AssetType* vom Typ **Auswahl** hinzu, und geben Sie im Textfeld **Geben Sie jede Auswahl in einer neuen Zeile ein** die Werte ein, die im Auswahlmenü angezeigt werden sollen. Klicken oder tippen Sie dann auf **OK**.

    ![](./media/sharepoint-lookup-fields/define-choice-column.png)

4. Beginnen Sie damit, ein weiteres Feld hinzufügen, und gehen Sie dazu wie in Schritt 2 vor: Klicken oder tippen Sie auf das Pluszeichen, und wählen Sie **Weitere** aus.

5. Fügen Sie ein Feld *RepairShop* vom Typ **Nachschlagen** hinzu, wählen Sie für das Textfeld **Informationen kommen aus** das Feld **RepairShop** aus, und wählen Sie im Textfeld *In dieser Spalte* die Option **ContactEmail** aus. Klicken oder tippen Sie dann auf **OK**.

    ![](./media/sharepoint-lookup-fields/setup-lookup-column.png)

6. Fügen Sie nach Wunsch weitere Felder hinzu.

## <a name="create-an-app-from-the-assets-list"></a>Erstellen einer Apps aus der Assetliste
Sie verwenden diese App, um Daten zur Liste **Assets** hinzuzufügen.

1. [In PowerApps Studio anmelden](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Wenn Sie in PowerApps einsteigen möchten, [können Sie sich kostenlos mit Ihrer Unternehmens-E-Mail-Adresse registrieren](https://powerapps.microsoft.com).

2. Klicken oder tippen Sie im Menü **Datei** auf der linken Seite auf **Neu**, und klicken oder tippen Sie dann auf **SharePoint**.

    ![](./media/sharepoint-lookup-fields/create-app.png)

1. Wählen Sie in der Liste **Zuletzt geöffnete Websites** Ihre SharePoint-Website aus, oder geben Sie die Website-URL direkt in das Textfeld ein. Klicken oder tippen Sie auf **LOS**.

    ![](./media/sharepoint-lookup-fields/choose-sharepoint-site.png)

1. Wählen Sie die Hauptliste aus Ihrer SharePoint-Website aus, in diesem Beispiel **Assets**. Klicken oder tippen Sie rechts unten auf die Schaltfläche **Verbinden**.

    ![](./media/sharepoint-lookup-fields/choose-main-list.png)


## <a name="add-data-to-the-assets-list"></a>Hinzufügen von Daten zur Assetliste
Sie können die App jetzt ausführen und sich ansehen, wie der Bildschirm zur Detailanzeige für die Nachschlagefelder aussieht.

1. Drücken Sie F5, oder wählen Sie die Vorschau (![](./media/sharepoint-lookup-fields/preview.png)) aus.

2. Klicken oder tippen Sie oben rechts auf das Symbol **+**, um einen Eintrag hinzuzufügen.

3. Geben Sie einen **Titel** für das Asset ein.

4. Klicken oder tippen Sie auf den Pfeil der Dropdownliste **AssetType**. Die angezeigten Werte sind diejenigen, die Sie beim Erstellen dieses Felds eingegeben haben. Wählen Sie einen der Einträge.

    ![](./media/sharepoint-lookup-fields/fill-asset-type-3.png)

5. Klicken oder tippen Sie auf den Pfeil der Dropdownliste **RepairShop**. Wählen Sie einen der Einträge.

    ![](./media/sharepoint-lookup-fields/fill-repair-shop-3.png)

6. Klicken oder tippen Sie oben rechts auf das Häkchen, um den neuen Eintrag zu speichern.

7. (Optional) Wiederholen Sie diesen Vorgang, um der Liste weitere Elemente hinzuzufügen.

8. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.

## <a name="for-more-information"></a>Weitere Informationen
* [Neue Unterstützung für Suchvorgänge und eine neue Beispiel-App](https://powerapps.microsoft.com/blog/support-for-lookups/)
* [Leistung, Schaltfläche zum Aktualisieren, ForAll und Suchvorgänge in mehreren Feldern](https://powerapps.microsoft.com/blog/performance-refresh-forall-multiple-field-lookups-531/)
* [Generieren einer App mithilfe einer Common Data Service-Datenbank](data-platform-create-app.md)
* [Neuerstellen einer App mithilfe einer Common Data Service-Datenbank](data-platform-create-app-scratch.md)
