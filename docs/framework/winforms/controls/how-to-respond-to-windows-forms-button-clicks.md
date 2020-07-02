---
title: répondre aux clics de bouton
description: Découvrez comment répondre à Windows Forms clics de bouton. L’utilisation la plus simple d’un contrôle de bouton de Windows Forms consiste à exécuter du code suite à un clic sur le bouton.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: 5c458d56dbd6f1cab8e88bdbb86ede958367e5c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619726"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Comment : répondre à un clic du contrôle Button Windows Forms
L’utilisation la plus simple d’un <xref:System.Windows.Forms.Button> contrôle Windows Forms consiste à exécuter du code suite à un clic sur le bouton.  
  
 En cliquant sur un <xref:System.Windows.Forms.Button> contrôle, vous générez également un certain nombre d’autres événements, tels que les <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseDown> événements, et <xref:System.Windows.Forms.Control.MouseUp> . Si vous envisagez d’attacher des gestionnaires d’événements pour ces événements connexes, assurez-vous que leurs actions ne sont pas en conflit. Par exemple, si le fait de cliquer sur le bouton efface les informations que l’utilisateur a tapées dans une zone de texte, la suspension du pointeur de la souris sur le bouton ne doit pas afficher d’info-bulle avec des informations qui sont maintenant inexistantes.  
  
 Si l’utilisateur tente de double-cliquer sur le <xref:System.Windows.Forms.Button> contrôle, chaque clic est traité séparément ; autrement dit, le contrôle ne prend pas en charge l’événement de double-clic.  
  
### <a name="to-respond-to-a-button-click"></a>Pour répondre à un clic sur un bouton  
  
- Dans le bouton, `Click` <xref:System.EventHandler> écrivez le code à exécuter. `Button1_Click`doit être lié au contrôle. Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Button, contrôle](button-control-windows-forms.md)
