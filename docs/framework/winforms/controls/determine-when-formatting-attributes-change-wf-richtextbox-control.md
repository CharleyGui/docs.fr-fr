---
title: Déterminer quand les attributs de formatage changent dans le contrôle de RichTextBox
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
ms.openlocfilehash: a190c3479b58464763e0eefdd32d14e88a1f05e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142262"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Comment : déterminer le moment où les attributs de mise en forme changent dans le contrôle RichTextBox Windows Forms
Une utilisation courante du <xref:System.Windows.Forms.RichTextBox> contrôle des formulaires Windows consiste à formater le texte avec des attributs tels que les options de police ou les styles de paragraphes. Votre application peut avoir besoin de garder une trace de toute modification du formatage de texte dans le but d’afficher une barre d’outils, comme dans de nombreuses applications de traitement de texte.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Pour répondre aux changements dans les attributs de formatage  
  
1. Écrivez du <xref:System.Windows.Forms.RichTextBox.SelectionChanged> code dans le gestionnaire d’événements pour effectuer une action appropriée en fonction de la valeur de l’attribut. L’exemple suivant modifie l’apparence d’un bouton <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> de barre d’outils en fonction de la valeur de la propriété. Le bouton de la barre d’outils ne sera mis à jour que lorsque le point d’insertion est déplacé dans le contrôle.  
  
     L’exemple ci-dessous suppose <xref:System.Windows.Forms.RichTextBox> un <xref:System.Windows.Forms.ToolBar> formulaire avec un contrôle et un contrôle qui contient un bouton de barre d’outils. Pour plus d’informations sur les barres d’outils et les boutons de la barre d’outils, voir [Comment : Ajouter des boutons à un contrôle ToolBar](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
- [Contrôles à utiliser sur les formulaires Windows](controls-to-use-on-windows-forms.md)
