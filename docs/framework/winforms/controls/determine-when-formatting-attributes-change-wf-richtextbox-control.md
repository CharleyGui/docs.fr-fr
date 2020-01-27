---
title: Déterminer quand les attributs de mise en forme changent dans le contrôle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: f9b2a1028f79059ec7d4d6bf3683100455bb5dea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746039"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Comment : déterminer le moment où les attributs de mise en forme changent dans le contrôle RichTextBox Windows Forms
La mise en forme du texte avec des attributs, tels que les options de police ou <xref:System.Windows.Forms.RichTextBox> Windows Forms les styles de paragraphes, est couramment utilisée. Votre application peut être amenée à effectuer le suivi des modifications apportées à la mise en forme du texte dans le but d’afficher une barre d’outils, comme dans de nombreuses applications de traitement de texte.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Pour répondre aux modifications apportées aux attributs de mise en forme  
  
1. Écrivez du code dans le gestionnaire d’événements <xref:System.Windows.Forms.RichTextBox.SelectionChanged> pour exécuter une action appropriée en fonction de la valeur de l’attribut. L’exemple suivant modifie l’apparence d’un bouton de barre d’outils en fonction de la valeur de la propriété <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>. Le bouton de barre d’outils est mis à jour uniquement lorsque le point d’insertion est déplacé dans le contrôle.  
  
     L’exemple ci-dessous suppose un formulaire avec un contrôle <xref:System.Windows.Forms.RichTextBox> et un contrôle <xref:System.Windows.Forms.ToolBar> contenant un bouton de barre d’outils. Pour plus d’informations sur les barres d’outils et les boutons de barre d’outils, consultez Guide pratique [pour ajouter des boutons à un contrôle ToolBar](how-to-add-buttons-to-a-toolbar-control.md).  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
