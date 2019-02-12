---
title: Übersicht über die SQL Server-Verbindung | Microsoft-Dokumentation
description: Schrittweise Anleitung zum Herstellen einer Verbindung mit Azure SQL oder einer lokalen SQL Server-Datenbank
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f001e3da66605db1eb96d74078a3f8b1fdf518f2
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42823844"
---
# <a name="connect-to-sql-server-from-powerapps"></a>Herstellen einer Verbindung mit SQL Server aus PowerApps
![SQL Server-Symbol](./media/connection-azure-sqldatabase/sqlicon.png)

Stellen Sie entweder in Azure oder in einer lokalen Datenbank eine Verbindung mit SQL Server her, sodass Sie darin enthaltene Informationen in PowerApps anzeigen können.

## <a name="prerequisites"></a>Voraussetzungen

* [Registrieren Sie sich](../../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.
* Sammeln Sie die folgenden Informationen für eine Datenbank, die mindestens eine Tabelle mit einem Primärschlüssel enthält:
  
  * den Namen der Datenbank
  * den Namen des Servers, auf dem die Datenbank gehostet wird
  * einen gültigen Benutzernamen und ein Kennwort zum Herstellen der Verbindung mit der Datenbank
  * den Typ der Authentifizierung, die beim Herstellen der Verbindung mit der Datenbank erforderlich ist
    
    Wenn Ihnen diese Informationen nicht bekannt sind, erkundigen Sie sich beim Administrator der Datenbank, die Sie verwenden möchten.
* Geben Sie für eine lokale Datenbank ein [Datengateway](../gateway-management.md) an, das für Sie freigegeben ist (oder erstellen Sie eines).
  
    > [!NOTE]
  > Gateways und lokale Verbindungen können nur in der [Standardumgebung](../working-with-environments.md) des Benutzers erstellt und verwendet werden.

## <a name="generate-an-app-automatically"></a>Eine App automatisch generieren
1. Klicken oder tippen Sie in PowerApps Studio im Menü **Datei** auf die Option **Neu** (am linken Rand).
   
    ![Option „New“ im Menü „File“](./media/connection-azure-sqldatabase/file-new.png)
2. Klicken oder tippen Sie unter **Mit eigenen Daten beginnen** auf den Rechtspfeil am Ende der Zeile mit Connectors.
3. Wenn Sie bereits über eine Verbindung mit der gewünschten Datenbank verfügen, klicken oder tippen Sie darauf, und fahren Sie dann mit Schritt 7 in diesem Verfahren fort.
4. Klicken oder tippen Sie auf **Neue Verbindung**, und klicken oder tippen Sie dann auf **SQL Server**.
   
    ![Hinzufügen einer SQL Server-Verbindung](./media/connection-azure-sqldatabase/add-sql-connection.png)
5. Führen Sie einen der folgenden Schritte aus:
   
   * Geben Sie **Direkte Verbindung (Clouddienste)** an, und geben bzw. fügen Sie den Servernamen, den Datenbanknamen, den Benutzernamen sowie das Kennwort für die zu verwendende Datenbank ein.
     
       ![Herstellen einer Verbindung mit einer Datenbank in Azure](./media/connection-azure-sqldatabase/connect-azure.png)
   * Geben Sie **Verbindung mithilfe eines lokalen Datengateways** an, geben bzw. fügen Sie den Servernamen, den Datenbanknamen, den Benutzernamen und das Kennwort für die zu verwendende Datenbank ein, und geben Sie den Authentifizierungstyp und das Gateway an.
     
       ![Herstellen einer Verbindung mit einer lokalen Datenbank](./media/connection-azure-sqldatabase/connect-onprem.png)
     
       > [!NOTE]
     > Wenn Sie über kein Gateway verfügen, [installieren Sie ein Gateway](../gateway-reference.md), und klicken oder tippen Sie anschließend auf **Gatewayliste aktualisieren**.
6. Klicken oder tippen Sie auf **Verbinden**.
7. Klicken oder tippen Sie auf eine Option unter **Dataset auswählen**, klicken oder tippen Sie auf eine Option unter **Tabelle auswählen**, und klicken oder tippen Sie dann auf **Verbinden**.
   
    In PowerApps wird eine App erstellt, in der Daten auf drei Bildschirmen angezeigt werden. Von einer Heuristik wird vorgeschlagen, welche Art von Daten angezeigt werden sollte, möglicherweise müssen Sie jedoch die Benutzeroberfläche entsprechend den jeweiligen Anforderungen anpassen.
8. Passen Sie die App unter Verwendung von Techniken wie den in [Erstellen einer App aus Excel-Daten](../get-started-create-from-data.md) beschriebenen an; beginnen Sie dabei mit dem Ändern des App-Layouts.

## <a name="build-an-app-from-scratch"></a>Eine App von Grund auf neu erstellen
1. Melden Sie sich bei [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) mit dem Konto an, das sie auch beim Registrieren für PowerApps verwendet haben.
2. Klicken oder tippen Sie in der linken Navigationsleiste auf **Verbindungen**:  
   
    ![Verwalten von Verbindungen](./media/connection-azure-sqldatabase/manage-connections.png)
3. Klicken oder tippen Sie in der oberen rechten Ecke auf **Neue Verbindung**, und klicken oder tippen Sie anschließend auf **SQL Server**.
4. Führen Sie einen der folgenden Schritte aus:
   
   * Geben Sie **Direkte Verbindung (Clouddienste)** an, und geben bzw. fügen Sie den Servernamen, den Datenbanknamen, den Benutzernamen sowie das Kennwort für die zu verwendende Datenbank ein.
     
       ![Herstellen einer Verbindung mit einer Datenbank in Azure](./media/connection-azure-sqldatabase/connect-azure-portal.png)
   * Geben Sie **Verbindung mithilfe eines lokalen Datengateways** an, geben bzw. fügen Sie den Servernamen, den Datenbanknamen, den Benutzernamen und das Kennwort für die zu verwendende Datenbank ein, und geben Sie den Authentifizierungstyp und das Gateway an.
     
       ![Herstellen einer Verbindung mit einer Datenbank in Azure](./media/connection-azure-sqldatabase/connect-onprem-portal.png)
     
       > [!NOTE]
     > Wenn Sie über kein Gateway verfügen, [installieren Sie ein Gateway](../gateway-reference.md), und klicken oder tippen Sie auf das Symbol mit dem im Uhrzeigersinn drehenden Pfeil, um die Liste zu aktualisieren.
5. Klicken oder tippen Sie auf **Erstellen**, um die Verbindung zu erstellen.
6. Erstellen Sie eine App mithilfe von Techniken wie den in [App von Grund auf neu erstellen](../get-started-create-from-blank.md) beschriebenen.

## <a name="update-an-existing-app"></a>Aktualisieren einer vorhandenen App
1. Öffnen Sie in PowerApps Studio die App, die Sie aktualisieren möchten.
2. Klicken oder tippen Sie im Menüband auf der Registerkarte **Ansicht** auf **Datenquellen**.
3. Klicken oder tippen Sie im rechten Bereich auf **Datenquelle hinzufügen**.
   
    ![Datenquelle hinzufügen](./media/connection-azure-sqldatabase/add-data-source.png)
4. Klicken oder tippen Sie auf **Neue Verbindung** und auf **SQL Server**, und klicken oder tippen Sie anschließend auf **Verbinden**.
5. Führen Sie einen der folgenden Schritte aus:
   
   * Geben Sie **Direkte Verbindung (Clouddienste)** an, und geben bzw. fügen Sie den Servernamen, den Datenbanknamen, den Benutzernamen sowie das Kennwort für die zu verwendende Datenbank ein.
     
       ![Herstellen einer Verbindung mit einer Datenbank in Azure](./media/connection-azure-sqldatabase/connect-azure-fromblank.png)
   * Geben Sie **Verbindung mithilfe eines lokalen Datengateways** an, geben bzw. fügen Sie den Servernamen, den Datenbanknamen, den Benutzernamen und das Kennwort für die zu verwendende Datenbank ein, und geben Sie den Authentifizierungstyp und das Gateway an.
     
       ![Herstellen einer Verbindung mit einer Datenbank in Azure](./media/connection-azure-sqldatabase/connect-onprem-fromblank.png)
     
       > [!NOTE]
     > Wenn Sie über kein Gateway verfügen, [installieren Sie ein Gateway](../gateway-reference.md), und klicken oder tippen Sie anschließend auf das Symbol mit dem kreisförmigen Pfeil, um die Liste zu aktualisieren.
6. Klicken oder tippen Sie auf **Verbinden**.
7. Klicken oder tippen Sie unter **Dataset auswählen** auf eine Option.
8. Aktivieren Sie unter **Tabelle auswählen** ein oder mehrere Kontrollkästchen, und klicken oder tippen Sie auf **Verbinden**.

## <a name="next-steps"></a>Nächste Schritte
* Erfahren Sie, wie Sie [Daten aus einer Datenquelle anzeigen](../add-gallery.md).
* Erfahren Sie, wie Sie [Details anzeigen und Datensätze erstellen oder aktualisieren](../add-form.md).
* Hier erhalten Sie Informationen zu anderen Arten von [Datenquellen](../connections-list.md), mit denen Sie eine Verbindung herstellen können.  
* Informieren Sie sich in [Grundlegendes zu Tabellen und Datensätzen](../working-with-tables.md) über tabellarische Datenquellen.

<!--NotAvailableYet
## View the available functions ##
This connection includes the following functions:

| Function Name |  Description |
| --- | --- |
|[GetItems](connection-azure-sqldatabase.md#getitems) | Retrieves rows from a SQL table |
|[PostItem](connection-azure-sqldatabase.md#postitem) | Inserts a new row into a SQL table |
|[GetItem](connection-azure-sqldatabase.md#getitem) | Retrieves a single row from a SQL table |
|[DeleteItem](connection-azure-sqldatabase.md#deleteitem) | Deletes a row from a SQL table |
|[PatchItem](connection-azure-sqldatabase.md#patchitem) | Updates an existing row in a SQL table |
|[GetTables](connection-azure-sqldatabase.md#gettables) | Retrieves tables from a SQL database |

### GetItems
Get rows: Retrieves rows from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|$skip|integer|no|Number of entries to skip (default = 0)|
|$top|integer|no|Maximum number of entries to retrieve (default = 256)|
|$filter|string|no|An ODATA filter query to restrict the number of entries|
|$orderby|string|no|An ODATA orderBy query for specifying the order of entries|

### PostItem
Insert row: Inserts a new row into a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|item| |yes|Row to insert into the specified table in SQL|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | |


### GetItem
Get row: Retrieves a single row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to retrieve|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | |


### DeleteItem
Delete row: Deletes a row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to delete|

#### Output properties
None.

### PatchItem
Update row: Updates an existing row in a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to update|
|item| |yes|Row with updated values|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | &nbsp; |


### GetTables
Get tables: Retrieves tables from a SQL database

#### Input properties
None.

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | Can output the Name and DisplayName properties |

### ExecuteProcedure
Execute stored procedure: Executes a stored procedure in SQL

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|procedure|string|yes|Procedure name|
|parameters| |yes|Input parameters|

#### Output properties
Result of the stored procedure execution.

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|OutputParameters|object|No | Output parameter values |
|ReturnCode|integer|No | Return code of a procedure |
|ResultSets|object|No | Result sets|

-->
