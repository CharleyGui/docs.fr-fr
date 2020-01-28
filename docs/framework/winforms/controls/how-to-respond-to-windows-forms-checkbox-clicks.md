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
ms.openlocfilehash: ba2afb52939a6274978ce725dac19b5622419b99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735663"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Comment : répondre à un clic du contrôle CheckBox Windows Forms
Chaque fois qu’un utilisateur clique sur un contrôle Windows Forms <xref:System.Windows.Forms.CheckBox>, l’événement <xref:System.Windows.Forms.Control.Click> se produit. Vous pouvez programmer votre application pour effectuer une action en fonction de l’état de la case à cocher.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Pour répondre aux clics de case  
  
1. Dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click>, utilisez la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> pour déterminer l’état du contrôle et effectuez toutes les actions nécessaires.  
  
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
    > Si l’utilisateur tente de double-cliquer sur le contrôle <xref:System.Windows.Forms.CheckBox>, chaque clic est traité séparément. autrement dit, le contrôle <xref:System.Windows.Forms.CheckBox> ne prend pas en charge l’événement de double-clic.  
  
    > [!NOTE]
    > Lorsque la propriété <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> est `true` (valeur par défaut), le <xref:System.Windows.Forms.CheckBox> est automatiquement sélectionné ou effacé lorsqu’un utilisateur clique dessus. Dans le cas contraire, vous devez définir manuellement la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> lorsque l’événement <xref:System.Windows.Forms.Control.Click> se produit.  
  
     Vous pouvez également utiliser le contrôle <xref:System.Windows.Forms.CheckBox> pour déterminer un cours d’action.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Pour déterminer la marche à suivre quand l’utilisateur clique sur une case à cocher  
  
1. Utilisez une instruction case pour interroger la valeur de la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> afin de déterminer la marche à suivre. Lorsque la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> peut retourner trois valeurs possibles, qui représentent la case cochée, la case désactivée ou un troisième état indéterminé dans lequel la zone est affichée avec une apparence grisée pour indiquer que l’option n’est pas disponible.  
  
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
    > Lorsque la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> retourne `true` pour <xref:System.Windows.Forms.CheckState.Checked> et <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.CheckBox>
- [Vue d'ensemble du contrôle CheckBox](checkbox-control-overview-windows-forms.md)
- [Guide pratique pour définir des options avec les contrôles CheckBox Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox, contrôle](checkbox-control-windows-forms.md)
