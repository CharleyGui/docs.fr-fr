---
title: 'Comment : créer des gestionnaires d’événements au moment de l’exécution'
description: Découvrez comment créer un gestionnaire d’événements au moment de l’exécution avec le Concepteur Windows Forms dans Visual Studio. Cette action vous permet de connecter des gestionnaires d’événements au moment de l’exécution.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325806"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Procédure : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms

En plus de créer des événements à l’aide de l’Concepteur Windows Forms dans Visual Studio, vous pouvez également créer un gestionnaire d’événements au moment de l’exécution. Cette action vous permet de connecter des gestionnaires d’événements en fonction de conditions spécifiées dans le code lors de l’exécution au lieu de les connecter au premier démarrage du programme.

## <a name="create-an-event-handler-at-run-time"></a>Créer un gestionnaire d’événements au moment de l’exécution

1. Ouvrez le formulaire auquel vous souhaitez ajouter un gestionnaire d’événements.

2. Ajoutez une méthode à votre formulaire avec la signature de méthode pour l’événement que vous souhaitez gérer.

     Par exemple, si vous gérez l' <xref:System.Windows.Forms.Control.Click> événement d’un <xref:System.Windows.Forms.Button> contrôle, vous devez créer une méthode telle que la suivante :

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. Ajoutez le code au gestionnaire d’événements en fonction de votre application.

4. Déterminez le formulaire ou le contrôle pour lequel vous souhaitez créer un gestionnaire d’événements.

5. Dans une méthode de classe de votre formulaire, ajoutez le code qui spécifie au gestionnaire d’événements de gérer l’événement. Par exemple, le code suivant spécifie que le gestionnaire `button1_Click` d’événements gère l' <xref:System.Windows.Forms.Control.Click> événement d’un <xref:System.Windows.Forms.Button> contrôle :

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     La <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> méthode illustrée dans le code Visual Basic ci-dessus établit un gestionnaire d’événements Click pour le bouton.

## <a name="see-also"></a>Voir aussi

- [Création de gestionnaires d'événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Vue d’ensemble des gestionnaires d’événements](event-handlers-overview-windows-forms.md)
- [Dépannage des gestionnaires d'événements hérités dans Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
