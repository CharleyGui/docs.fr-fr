---
title: répondre aux clics de case à cocher
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141924"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Comment : répondre à un clic du contrôle CheckBox Windows Forms
Chaque fois qu’un <xref:System.Windows.Forms.CheckBox> utilisateur clique <xref:System.Windows.Forms.Control.Click> sur un contrôle windows Forms, l’événement se produit. Vous pouvez programmer votre demande pour effectuer une action en fonction de l’état de la case à cocher.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Pour répondre aux clics CheckBox  
  
1. Dans <xref:System.Windows.Forms.Control.Click> l’événement gestionnaire, utilisez la <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété pour déterminer l’état du contrôle, et effectuer toute action nécessaire.  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > Si l’utilisateur tente de <xref:System.Windows.Forms.CheckBox> cliquer à deux clics sur le contrôle, chaque clic sera traité séparément; c’est-à-dire que le <xref:System.Windows.Forms.CheckBox> contrôle ne prend pas en charge l’événement en double clic.  
  
    > [!NOTE]
    > Lorsque <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> la `true` propriété est (la valeur par défaut), elle <xref:System.Windows.Forms.CheckBox> est automatiquement sélectionnée ou effacée lorsqu’elle est cliqué. Sinon, vous devez régler <xref:System.Windows.Forms.CheckBox.Checked%2A> manuellement <xref:System.Windows.Forms.Control.Click> la propriété lorsque l’événement se produit.  
  
     Vous pouvez également <xref:System.Windows.Forms.CheckBox> utiliser le contrôle pour déterminer un plan d’action.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Pour déterminer un plan d’action lorsqu’une case à cocher est cliqué  
  
1. Utilisez une déclaration de cas pour <xref:System.Windows.Forms.CheckBox.CheckState%2A> interroger la valeur de la propriété afin de déterminer un plan d’action. Lorsque <xref:System.Windows.Forms.CheckBox.ThreeState%2A> la propriété `true`est <xref:System.Windows.Forms.CheckBox.CheckState%2A> réglée, la propriété peut retourner trois valeurs possibles, qui représentent la case en cours de cochée, la boîte étant non contrôlée, ou un troisième état de durée indéterminée dans lequel la boîte est affichée avec une apparence tamisée pour indiquer que l’option n’est pas disponible.  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > Lorsque <xref:System.Windows.Forms.CheckBox.ThreeState%2A> la propriété `true`est <xref:System.Windows.Forms.CheckBox.Checked%2A> réglée `true` à <xref:System.Windows.Forms.CheckState.Checked> , <xref:System.Windows.Forms.CheckState.Indeterminate>la propriété revient pour les deux et .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.CheckBox>
- [Vue d’ensemble du contrôle CheckBox](checkbox-control-overview-windows-forms.md)
- [Comment : définir des options avec les contrôles CheckBox Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Contrôle De la Case De Contrôle](checkbox-control-windows-forms.md)
