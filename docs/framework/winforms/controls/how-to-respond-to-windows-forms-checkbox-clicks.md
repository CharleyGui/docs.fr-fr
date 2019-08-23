---
title: 'Procédure : répondre aux clics sur des contrôles Checkbox Windows Forms'
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
ms.openlocfilehash: 7ff6b2aad9ef0775547af57f11af28839e69637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914978"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="5e59d-102">Procédure : répondre aux clics sur des contrôles Checkbox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e59d-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="5e59d-103">Chaque fois qu’un utilisateur clique sur un <xref:System.Windows.Forms.Control.Click> contrôle Windows Forms <xref:System.Windows.Forms.CheckBox> , l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="5e59d-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="5e59d-104">Vous pouvez programmer votre application pour effectuer une action en fonction de l’état de la case à cocher.</span><span class="sxs-lookup"><span data-stu-id="5e59d-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="5e59d-105">Pour répondre aux clics de case</span><span class="sxs-lookup"><span data-stu-id="5e59d-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="5e59d-106">Dans le <xref:System.Windows.Forms.Control.Click> gestionnaire d’événements, utilisez <xref:System.Windows.Forms.CheckBox.Checked%2A> la propriété pour déterminer l’état du contrôle et effectuez toutes les actions nécessaires.</span><span class="sxs-lookup"><span data-stu-id="5e59d-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="5e59d-107">Si l’utilisateur tente de double-cliquer sur <xref:System.Windows.Forms.CheckBox> le contrôle, chaque clic est traité séparément; autrement dit, le <xref:System.Windows.Forms.CheckBox> contrôle ne prend pas en charge l’événement de double-clic.</span><span class="sxs-lookup"><span data-stu-id="5e59d-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5e59d-108">Lorsque la <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> propriété a `true` la valeur (valeur par défaut <xref:System.Windows.Forms.CheckBox> ), l’option est automatiquement sélectionnée ou désactivée lorsque l’utilisateur clique dessus.</span><span class="sxs-lookup"><span data-stu-id="5e59d-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="5e59d-109">Dans le cas contraire, vous devez <xref:System.Windows.Forms.CheckBox.Checked%2A> définir manuellement la <xref:System.Windows.Forms.Control.Click> propriété lorsque l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="5e59d-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="5e59d-110">Vous pouvez également utiliser le <xref:System.Windows.Forms.CheckBox> contrôle pour déterminer un cours d’action.</span><span class="sxs-lookup"><span data-stu-id="5e59d-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="5e59d-111">Pour déterminer la marche à suivre quand l’utilisateur clique sur une case à cocher</span><span class="sxs-lookup"><span data-stu-id="5e59d-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="5e59d-112">Utilisez une instruction case pour interroger la valeur de <xref:System.Windows.Forms.CheckBox.CheckState%2A> la propriété afin de déterminer la marche à suivre.</span><span class="sxs-lookup"><span data-stu-id="5e59d-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="5e59d-113">Lorsque la <xref:System.Windows.Forms.CheckBox.ThreeState%2A> propriété a la `true`valeur, la <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété peut retourner trois valeurs possibles, qui représentent la case cochée, la case désactivée ou un troisième état indéterminé dans lequel la zone est affichée avec un estompé apparence pour indiquer que l’option n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="5e59d-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="5e59d-114">Lorsque la <xref:System.Windows.Forms.CheckBox.ThreeState%2A> propriété a la `true`valeur, <xref:System.Windows.Forms.CheckBox.Checked%2A> `true` lapropriété<xref:System.Windows.Forms.CheckState.Indeterminate>retourne pour et.<xref:System.Windows.Forms.CheckState.Checked></span><span class="sxs-lookup"><span data-stu-id="5e59d-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e59d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e59d-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="5e59d-116">Vue d'ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="5e59d-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="5e59d-117">Guide pratique pour Définir des options avec des contrôles de case à cocher Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e59d-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="5e59d-118">CheckBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="5e59d-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
