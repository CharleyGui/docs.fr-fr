---
title: définir des options avec des contrôles CheckBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 00b467836d8e60aeee51a010a6384abf7dd73c56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141846"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Comment : définir des options avec les contrôles CheckBox Windows Forms
Un contrôle <xref:System.Windows.Forms.CheckBox> des formulaires Windows est utilisé pour donner aux utilisateurs des options True/False ou Yes/No. Le contrôle affiche une marque de contrôle lorsqu’elle est sélectionnée.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Définir des options avec les contrôles CheckBox  
  
1. Examinez la <xref:System.Windows.Forms.CheckBox.Checked%2A> valeur de la propriété pour déterminer son état et utilisez cette valeur pour définir une option.  
  
     Dans l’échantillon de <xref:System.Windows.Forms.CheckBox> code ci-dessous, lorsque l’événement du <xref:System.Windows.Forms.CheckBox.CheckedChanged> contrôleur est soulevé, la propriété du <xref:System.Windows.Forms.Control.AllowDrop%2A> formulaire est définie `false` si la case à cocher est cochée. Ceci est utile pour les situations où vous souhaitez restreindre l’interaction avec l’utilisateur.  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.CheckBox>
- [Vue d’ensemble du contrôle CheckBox](checkbox-control-overview-windows-forms.md)
- [Comment : répondre à un clic du contrôle CheckBox Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Contrôle De la Case De Contrôle](checkbox-control-windows-forms.md)
