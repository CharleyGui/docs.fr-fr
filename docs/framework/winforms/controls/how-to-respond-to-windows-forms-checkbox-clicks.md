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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="c0951-102">Comment : répondre à un clic du contrôle CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0951-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="c0951-103">Chaque fois qu’un utilisateur clique sur un contrôle Windows Forms <xref:System.Windows.Forms.CheckBox>, l’événement <xref:System.Windows.Forms.Control.Click> se produit.</span><span class="sxs-lookup"><span data-stu-id="c0951-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="c0951-104">Vous pouvez programmer votre application pour effectuer une action en fonction de l’état de la case à cocher.</span><span class="sxs-lookup"><span data-stu-id="c0951-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="c0951-105">Pour répondre aux clics de case</span><span class="sxs-lookup"><span data-stu-id="c0951-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="c0951-106">Dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click>, utilisez la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> pour déterminer l’état du contrôle et effectuez toutes les actions nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c0951-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="c0951-107">Si l’utilisateur tente de double-cliquer sur le contrôle <xref:System.Windows.Forms.CheckBox>, chaque clic est traité séparément. autrement dit, le contrôle <xref:System.Windows.Forms.CheckBox> ne prend pas en charge l’événement de double-clic.</span><span class="sxs-lookup"><span data-stu-id="c0951-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c0951-108">Lorsque la propriété <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> est `true` (valeur par défaut), le <xref:System.Windows.Forms.CheckBox> est automatiquement sélectionné ou effacé lorsqu’un utilisateur clique dessus.</span><span class="sxs-lookup"><span data-stu-id="c0951-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="c0951-109">Dans le cas contraire, vous devez définir manuellement la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> lorsque l’événement <xref:System.Windows.Forms.Control.Click> se produit.</span><span class="sxs-lookup"><span data-stu-id="c0951-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="c0951-110">Vous pouvez également utiliser le contrôle <xref:System.Windows.Forms.CheckBox> pour déterminer un cours d’action.</span><span class="sxs-lookup"><span data-stu-id="c0951-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="c0951-111">Pour déterminer la marche à suivre quand l’utilisateur clique sur une case à cocher</span><span class="sxs-lookup"><span data-stu-id="c0951-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="c0951-112">Utilisez une instruction case pour interroger la valeur de la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> afin de déterminer la marche à suivre.</span><span class="sxs-lookup"><span data-stu-id="c0951-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="c0951-113">Lorsque la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> peut retourner trois valeurs possibles, qui représentent la case cochée, la case désactivée ou un troisième état indéterminé dans lequel la zone est affichée avec une apparence grisée pour indiquer que l’option n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="c0951-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="c0951-114">Lorsque la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> retourne `true` pour <xref:System.Windows.Forms.CheckState.Checked> et <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="c0951-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0951-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0951-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="c0951-116">Vue d'ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="c0951-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="c0951-117">Guide pratique pour définir des options avec les contrôles CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0951-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="c0951-118">CheckBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="c0951-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
