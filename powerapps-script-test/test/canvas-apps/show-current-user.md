---
title: Anzeigen von Details zum aktuellen Benutzer in einer Canvas-App | Microsoft-Dokumentation
description: Anzeigen des Namens und der E-Mail-Adresse des angemeldeten Benutzers in einer Canvas-App in PowerApps
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/16/2016
ms.author: lonu
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ef38ef00ed72eb59b459d3e9b71a6efbb6568d6b
ms.sourcegitcommit: c1f58a16f8dcd309a1d5fc4658ca16d82c615994
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2018
ms.locfileid: "42833971"
---
# <a name="show-information-about-a-powerapps-user-in-a-canvas-app"></a>Anzeigen von Informationen zu einem PowerApps-Benutzer in einer Canvas-App

Zeigen Sie den vollständigen Namen, die E-Mail-Adresse und das zugeordnete Bild des Benutzers, der bei einer Canvas-App angemeldet ist, in PowerApps an. Sie können diese Informationen verwenden, um beispielsweise ein Formular automatisch auszufüllen.

Beispielsweise können Sie dieses Feature folgendermaßen einsetzen:

* Erstellen Sie für die Benutzer ein „Anmeldeformular“ zur Teilnahme an Trainings und Events, zum Einchecken bei einem Kioskcomputer usw.
* Zeigen Sie den vollständigen Namen in einer Personalverwaltungs-App an.
* Fügen Sie automatisch eine E-Mail-Adresse ein, wenn Sie sich an Ihren Helpdesk wenden.

Grundsätzlich können Sie diese Funktion immer dann einsetzen, wenn Benutzer davon profitieren, dass Formulare oder Bezeichnungen automatisch ausgefüllt werden.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>Anzeigen von Benutzerdetails

1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Medien** und anschließend auf **Bild**.
   
   ![][2]
2. Legen Sie die Eigenschaft **[Image](controls/properties-visual.md)** auf die folgende Formel fest:
   <br>**User().Image**
   
    ![][3]
3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Text** und anschließend auf **Bezeichnung**:  
   
    ![][4]
4. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**User().FullName**
   
   ![][6]
   
   Wenn Sie dies tun, wird die Bezeichnung automatisch mit Ihrem vollständigen Namen aufgefüllt. Verschieben Sie die Bezeichnung, sodass sie sich unterhalb des Bildsteuerelements befindet, ähnlich wie hier gezeigt:
   
   ![][5]
5. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](controls/properties-core.md)** auf diese Funktion fest:
   <br>**User().Email**  
   
    ![][8]
   
    Hierdurch wird die Bezeichnung automatisch mit Ihrer E-Mail-Adresse aufgefüllt. Verschieben Sie die Bezeichnung, sodass sie unterhalb der ersten Bezeichnung angezeigt wird, ähnlich wie hier dargestellt:  
   
    ![][7]

[2]: ./media/show-current-user/add-image.png
[3]: ./media/show-current-user/imageproperty.png
[4]: ./media/show-current-user/insertlabel.png
[5]: ./media/show-current-user/label.png
[6]: ./media/show-current-user/textproperty.png
[7]: ./media/show-current-user/secondlabel.png
[8]: ./media/show-current-user/email.png
[9]: ./media/show-current-user/preview.png
