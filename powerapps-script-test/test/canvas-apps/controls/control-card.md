---
title: 'Karten-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Karten-Steuerelement
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: gregli
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cc4338e37b7ecde2e2e2e9ad5c5ac6e96d116b58
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849843"
---
# <a name="card-control-in-powerapps"></a>Karten-Steuerelement in PowerApps
Ermöglicht die Anzeige und Bearbeitung eines einzelnen Felds in einem **[Formular anzeigen](control-form-detail.md)**- oder **[Formular bearbeiten](control-form-detail.md)**-Steuerelement.

## <a name="description"></a>Beschreibung
**[Formular anzeigen](control-form-detail.md)**- und **[Formular bearbeiten](control-form-detail.md)**-Steuerelemente werden als Container für die Anzeige und Bearbeitung vollständiger Datensätze verwendet. Jeder Container kann eine Reihe von **Karten**-Steuerelementen enthalten, in denen einzelne Felder angezeigt oder mit denen diese Felder aktualisiert werden können. Jede Karte besitzt eine **DataField**-Eigenschaft, die angibt, mit welchem Feld des Datensatzes es verknüpft ist.  

Vordefinierte Karten lassen sich für unterschiedliche Datentypen und Funktionen definieren.  Zum Beispiel können Sie eine Karte zum Bearbeiten eines Zahlenfelds mit einem **[Texteingabe](control-text-input.md)**-Steuerelement verwenden, die optimal für Tastatureingaben geeignet ist. Eine andere Karte unterstützt stattdessen etwa das Bearbeiten einer Zahl mit einem **[Schieberegler](control-slider.md)**-Steuerelement. Wenn Sie das Formular-Steuerelement auswählen, können Sie im rechten Bereich ganz einfach eine für ein bestimmtes Feld geeignete Karte auswählen.

Karten enthalten wiederum Steuerelemente. Die Steuerelemente einer Karte bilden die Benutzeroberfläche zum Anzeigen und Bearbeiten eines einzelnen Felds. So kann eine Zahlenkarte beispielsweise aus einem **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) zum Anzeigen des Feldnamens und einem **[Texteingabe](control-text-input.md)**-Steuerelement als Editor für den Wert des Felds bestehen. Außerdem könnte auf der Karte ein **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) vorhanden sein, in dem ggf. Überprüfungsfehler angezeigt werden, sowie ein **[Label](control-text-box.md)**-Steuerelement für das Sternchen, mit dem Pflichtfelder üblicherweise gekennzeichnet sind.

Sie können die Steuerelemente einer vordefinierten Karte anpassen, indem Sie die Größe oder Position ändern, sie ausblenden, weitere Steuerelemente hinzufügen oder sonstige Änderungen vornehmen. Sie können auch eine benutzerdefinierte Karte verwenden, d.h. eine völlig leere Karte, die Sie von Grund auf neu erstellen, indem Sie Steuerelemente hinzufügen.

Vordefinierte Karten sind in der Standardeinstellung *gesperrt*. Bei einer gesperrten Karte können Sie nur bestimmte Eigenschaften der Karte oder der Steuerelemente auf der Karte ändern. Gesperrte Karten können nicht gelöscht werden. Auf der Registerkarte **Anzeigen** der **erweiterten Ansicht** können Sie die Kartensperre einblenden und aufheben. Wenn eine Eigenschaft gesperrt ist und nicht geändert werden kann, wird neben ihrem Namen ein Schlosssymbol angezeigt. Das Entsperren einer Karte ist eher etwas für Fortgeschrittene und sollte Sorgfalt ausgeführt werden, da für die Karte keine automatische Formelgenerierung mehr erfolgt und die Karte nicht wieder gesperrt werden kann.

Im Container des Formulars ist der Datensatz **ThisItem** verfügbar, der alle Felder des Datensatzes enthält.  Beispielsweise ist die **[Default](properties-core.md)**-Eigenschaft der Karte oft auf **ThisItem**.*FieldName* festgelegt.

Mit dem **Parent**-Verweis können Sie ein Steuerelement so konfigurieren, dass es auf die Eigenschaften einer Karte verweist.  Beispielsweise sollte ein Steuerelement den Ausgangszustand des Felds mit **Parent.Default** aus der Datenquelle lesen. Indem Sie **Parent** verwenden, statt direkt auf die gewünschten Informationen zuzugreifen, ist die Karte besser gekapselt und kann in ein anderes Feld umgewandelt werden, ohne Fehler bei den internen Formeln zu verursachen.

Beispiele zum Anpassen, Entsperren und Erstellen von Karten finden Sie unter [Grundlegendes zu Datenkarten](../working-with-cards.md).

## <a name="key-properties"></a>Haupteigenschaften
**DataField** – Der Name des Felds in einem Datensatz, der auf dieser Karte angezeigt wird und bearbeitet werden kann.

* Geben Sie den Namen als eine einzelne statische Zeichenfolge an, die in doppelte Anführungszeichen eingeschlossen ist (z.B. **"Name"**), und nicht als Formel.
* Wenn Sie die **DataField**-Eigenschaft *leer* lassen, wird die Bindung der Karte aufgehoben. Bei nicht gebundenen Karten werden die **Valid**-Eigenschaft und die **Update**-Eigenschaft ignoriert.

**[Default](properties-core.md)** – Der Anfangswert eines Steuerelements, bevor es vom Benutzer geändert wird.

* Legen Sie diese Eigenschaft bei allen Steuerelementen einer Karte auf **Parent.Default** fest, um auf den Standardwert des Felds aus der Datenquelle zu verweisen. Legen Sie beispielsweise die **[Default](properties-core.md)**-Eigenschaft eines Schiebereglers auf **Parent.Default** fest, um sicherzustellen, dass dem Benutzer zunächst der Basiswert dieses Schiebereglers angezeigt wird.

**DisplayMode**: Mögliche Werte sind **Edit, View** und **Disabled** (Bearbeiten, Anzeigen und Deaktiviert). Legt fest, ob das Steuerelement in der Karte Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).  

* Ermöglicht die Verwendung einer einzelnen Karte in Bearbeitungs- und Anzeigeformularen; hierfür wird diese Eigenschaft konfiguriert, die standardmäßig an das Verhalten des Formulars gebunden ist.
* Im Modus **View** (Anzeigen) zeigen untergeordnete Steuerelemente wie **[Texteingabe](control-text-input.md)**, **[Dropdown](control-drop-down.md)** und **[Datumsauswahl](control-date-picker.md)** lediglich den Textwert an, und es werden keine interaktiven Elemente oder Dekorationen gerendert.

**DisplayName** – Der benutzerfreundliche Name für ein Feld in einer Datenquelle.

* Die **[DataSourceInfo](../functions/function-datasourceinfo.md)**-Funktion ruft diese Metadaten aus der Datenquelle ab.
* Steuerelemente auf der Karte sollten mit **Parent.DisplayName** auf den Namen des Felds verweisen.

**Error** – Die benutzerfreundliche Fehlermeldung, die bei einem Überprüfungsfehler für dieses Feld angezeigt werden soll.

* Diese Eigenschaft wird bei einem Aufruf von **SubmitForm** festgelegt.  
* In der Meldung werden Probleme bei der Überprüfung auf Grundlage der Metadaten der Datenquelle und der **Required**-Eigenschaft erläutert.

**Required** – Gibt an, ob eine Karte zum Bearbeiten des Felds einer Datenquelle einen Wert enthalten muss.

* Die **[DataSourceInfo](../functions/function-datasourceinfo.md)**-Funktion ruft die erforderlichen Metadaten aus der Datenquelle ab.
* Steuerelemente auf der Karte sollten **Parent.Required** verwenden, um zu ermitteln, ob das Feld der Karte erforderlich ist.

**Update** – Der Wert, der für ein Feld in die Datenquelle geschrieben werden soll.

* Mit der Formel dieser Eigenschaft können Sie die Werte aus den Bearbeitungssteuerelementen der Karte abrufen, um sie wieder in die Datenquelle zu schreiben. Legen Sie beispielsweise die **Update**-Eigenschaft einer Karte auf **Slider.Value** fest, um die Datenquelle mit dem Wert des Schiebereglers auf dieser Karte zu aktualisieren.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[WidthFit](properties-size-location.md)** – Gibt an, ob ein Steuerelement automatisch horizontal vergrößert wird, um leeren Raum in einem Containersteuerelement wie z. B. einem **[Formularbearbeitung](control-form-detail.md)**-Steuerelement auszufüllen. Wenn bei mehreren Karten diese Eigenschaft auf **TRUE** festgelegt ist, teilen sie sich den Raum. Weitere Informationen finden Sie unter [Grundlegendes zum Layout von Datenformularen](../working-with-form-layout.md).

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**Valid** – Gibt an, ob das **Karten**- oder **[Formular bearbeiten](control-form-detail.md)**-Steuerelement gültige Einträge enthält, die an die Datenquelle gesendet werden können.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist). Für ein **[Karten](control-card.md)**-Steuerelement in einem Container mit mehreren Spalten bestimmt diese Eigenschaft die Spalte, in der die Karte angezeigt wird.

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist). Für ein **[Karten](control-card.md)**-Steuerelement in einem Container mit mehreren Zeilen bestimmt diese Eigenschaft die Zeile, in der die Karte angezeigt wird.

## <a name="examples"></a>Beispiele
Beispiele finden Sie unter [Grundlegendes zu Datenkarten](../working-with-cards.md) und [Grundlegendes zum Layout von Datenformularen](../working-with-form-layout.md).


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **[Fill](properties-color-border.md)**-Steuerelement und beliebige untergeordnete Steuerelemente. Wenn beispielsweise eine Karte eine **[Bezeichnung](control-text-box.md)** enthält und die **[Füllung](properties-color-border.md)** der Karte durchsichtig ist, wird diese Füllung als Hintergrundfarbe für die Bezeichnung verwendet. Dadurch sollte ein angemessenes Maß an Kontrast zwischen der **[Füllung](properties-color-border.md)** der Karte und der **[Farbe](properties-color-border.md)** der Bezeichnung entstehen.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **DisplayName** muss vorhanden sein.
