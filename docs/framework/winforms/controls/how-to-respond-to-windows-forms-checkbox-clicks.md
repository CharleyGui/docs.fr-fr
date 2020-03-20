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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="e88f9-102">Comment : répondre à un clic du contrôle CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e88f9-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="e88f9-103">Chaque fois qu’un <xref:System.Windows.Forms.CheckBox> utilisateur clique <xref:System.Windows.Forms.Control.Click> sur un contrôle windows Forms, l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="e88f9-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="e88f9-104">Vous pouvez programmer votre demande pour effectuer une action en fonction de l’état de la case à cocher.</span><span class="sxs-lookup"><span data-stu-id="e88f9-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="e88f9-105">Pour répondre aux clics CheckBox</span><span class="sxs-lookup"><span data-stu-id="e88f9-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="e88f9-106">Dans <xref:System.Windows.Forms.Control.Click> l’événement gestionnaire, utilisez la <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété pour déterminer l’état du contrôle, et effectuer toute action nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e88f9-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="e88f9-107">Si l’utilisateur tente de <xref:System.Windows.Forms.CheckBox> cliquer à deux clics sur le contrôle, chaque clic sera traité séparément; c’est-à-dire que le <xref:System.Windows.Forms.CheckBox> contrôle ne prend pas en charge l’événement en double clic.</span><span class="sxs-lookup"><span data-stu-id="e88f9-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e88f9-108">Lorsque <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> la `true` propriété est (la valeur par défaut), elle <xref:System.Windows.Forms.CheckBox> est automatiquement sélectionnée ou effacée lorsqu’elle est cliqué.</span><span class="sxs-lookup"><span data-stu-id="e88f9-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="e88f9-109">Sinon, vous devez régler <xref:System.Windows.Forms.CheckBox.Checked%2A> manuellement <xref:System.Windows.Forms.Control.Click> la propriété lorsque l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="e88f9-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="e88f9-110">Vous pouvez également <xref:System.Windows.Forms.CheckBox> utiliser le contrôle pour déterminer un plan d’action.</span><span class="sxs-lookup"><span data-stu-id="e88f9-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="e88f9-111">Pour déterminer un plan d’action lorsqu’une case à cocher est cliqué</span><span class="sxs-lookup"><span data-stu-id="e88f9-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="e88f9-112">Utilisez une déclaration de cas pour <xref:System.Windows.Forms.CheckBox.CheckState%2A> interroger la valeur de la propriété afin de déterminer un plan d’action.</span><span class="sxs-lookup"><span data-stu-id="e88f9-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="e88f9-113">Lorsque <xref:System.Windows.Forms.CheckBox.ThreeState%2A> la propriété `true`est <xref:System.Windows.Forms.CheckBox.CheckState%2A> réglée, la propriété peut retourner trois valeurs possibles, qui représentent la case en cours de cochée, la boîte étant non contrôlée, ou un troisième état de durée indéterminée dans lequel la boîte est affichée avec une apparence tamisée pour indiquer que l’option n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="e88f9-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="e88f9-114">Lorsque <xref:System.Windows.Forms.CheckBox.ThreeState%2A> la propriété `true`est <xref:System.Windows.Forms.CheckBox.Checked%2A> réglée `true` à <xref:System.Windows.Forms.CheckState.Checked> , <xref:System.Windows.Forms.CheckState.Indeterminate>la propriété revient pour les deux et .</span><span class="sxs-lookup"><span data-stu-id="e88f9-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e88f9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e88f9-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="e88f9-116">Vue d’ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="e88f9-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e88f9-117">Comment : définir des options avec les contrôles CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e88f9-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="e88f9-118">Contrôle De la Case De Contrôle</span><span class="sxs-lookup"><span data-stu-id="e88f9-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
