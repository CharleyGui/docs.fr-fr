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
ms.openlocfilehash: 84198eab42aa02b1bb37fa16a3c4247a37f58a10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746762"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Comment : définir des options avec les contrôles CheckBox Windows Forms
Un contrôle Windows Forms <xref:System.Windows.Forms.CheckBox> est utilisé pour fournir aux utilisateurs des options true/false ou Yes/No. Le contrôle affiche une coche lorsqu’il est sélectionné.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Pour définir des options avec les contrôles CheckBox  
  
1. Examinez la valeur de la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> pour déterminer son état et utilisez cette valeur pour définir une option.  
  
     Dans l’exemple de code ci-dessous, lorsque l’événement <xref:System.Windows.Forms.CheckBox.CheckedChanged> du contrôle <xref:System.Windows.Forms.CheckBox> est déclenché, la propriété <xref:System.Windows.Forms.Control.AllowDrop%2A> du formulaire est définie sur `false` si la case à cocher est activée. Cela est utile dans les situations où vous souhaitez limiter l’interaction de l’utilisateur.  
  
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
- [Vue d'ensemble du contrôle CheckBox](checkbox-control-overview-windows-forms.md)
- [Guide pratique pour répondre à un clic du contrôle CheckBox Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox, contrôle](checkbox-control-windows-forms.md)
