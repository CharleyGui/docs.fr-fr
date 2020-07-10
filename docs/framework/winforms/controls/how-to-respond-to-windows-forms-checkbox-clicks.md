---
title: répondre aux clics de case à cocher
description: Découvrez comment programmer votre application Windows Forms pour effectuer une action en fonction de l’état de la case à cocher.
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
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174495"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="71397-103">Comment : répondre à un clic du contrôle CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71397-103">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="71397-104">Chaque fois qu’un utilisateur clique sur un <xref:System.Windows.Forms.CheckBox> contrôle Windows Forms, l' <xref:System.Windows.Forms.Control.Click> événement se produit.</span><span class="sxs-lookup"><span data-stu-id="71397-104">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="71397-105">Vous pouvez programmer votre application pour effectuer une action en fonction de l’état de la case à cocher.</span><span class="sxs-lookup"><span data-stu-id="71397-105">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="71397-106">Pour répondre aux clics de case</span><span class="sxs-lookup"><span data-stu-id="71397-106">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="71397-107">Dans le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements, utilisez la <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété pour déterminer l’état du contrôle et effectuez toutes les actions nécessaires.</span><span class="sxs-lookup"><span data-stu-id="71397-107">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="71397-108">Si l’utilisateur tente de double-cliquer sur le <xref:System.Windows.Forms.CheckBox> contrôle, chaque clic est traité séparément ; autrement dit, le <xref:System.Windows.Forms.CheckBox> contrôle ne prend pas en charge l’événement de double-clic.</span><span class="sxs-lookup"><span data-stu-id="71397-108">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="71397-109">Lorsque la <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> propriété a la `true` valeur (valeur par défaut), l' <xref:System.Windows.Forms.CheckBox> option est automatiquement sélectionnée ou désactivée lorsque l’utilisateur clique dessus.</span><span class="sxs-lookup"><span data-stu-id="71397-109">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="71397-110">Dans le cas contraire, vous devez définir manuellement la <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété lorsque l' <xref:System.Windows.Forms.Control.Click> événement se produit.</span><span class="sxs-lookup"><span data-stu-id="71397-110">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="71397-111">Vous pouvez également utiliser le <xref:System.Windows.Forms.CheckBox> contrôle pour déterminer un cours d’action.</span><span class="sxs-lookup"><span data-stu-id="71397-111">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="71397-112">Pour déterminer la marche à suivre quand l’utilisateur clique sur une case à cocher</span><span class="sxs-lookup"><span data-stu-id="71397-112">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="71397-113">Utilisez une instruction case pour interroger la valeur de la <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété afin de déterminer la marche à suivre.</span><span class="sxs-lookup"><span data-stu-id="71397-113">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="71397-114">Lorsque la <xref:System.Windows.Forms.CheckBox.ThreeState%2A> propriété a la valeur `true` , la <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété peut retourner trois valeurs possibles, qui représentent la case cochée, la case désactivée ou un troisième état indéterminé dans lequel la zone est affichée avec une apparence grisée pour indiquer que l’option n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="71397-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="71397-115">Lorsque la <xref:System.Windows.Forms.CheckBox.ThreeState%2A> propriété a la valeur `true` , la <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété retourne `true` pour <xref:System.Windows.Forms.CheckState.Checked> et <xref:System.Windows.Forms.CheckState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="71397-115">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71397-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71397-116">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="71397-117">Vue d’ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="71397-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="71397-118">Comment : définir des options avec les contrôles CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71397-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="71397-119">CheckBox (contrôle)</span><span class="sxs-lookup"><span data-stu-id="71397-119">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
