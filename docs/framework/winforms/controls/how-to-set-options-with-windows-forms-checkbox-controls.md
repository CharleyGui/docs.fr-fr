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
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="68976-102">Comment : définir des options avec les contrôles CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68976-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="68976-103">Un contrôle Windows Forms <xref:System.Windows.Forms.CheckBox> est utilisé pour fournir aux utilisateurs des options true/false ou Yes/No.</span><span class="sxs-lookup"><span data-stu-id="68976-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="68976-104">Le contrôle affiche une coche lorsqu’il est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="68976-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="68976-105">Pour définir des options avec les contrôles CheckBox</span><span class="sxs-lookup"><span data-stu-id="68976-105">To set options with CheckBox controls</span></span>  
  
1. <span data-ttu-id="68976-106">Examinez la valeur de la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> pour déterminer son état et utilisez cette valeur pour définir une option.</span><span class="sxs-lookup"><span data-stu-id="68976-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="68976-107">Dans l’exemple de code ci-dessous, lorsque l’événement <xref:System.Windows.Forms.CheckBox.CheckedChanged> du contrôle <xref:System.Windows.Forms.CheckBox> est déclenché, la propriété <xref:System.Windows.Forms.Control.AllowDrop%2A> du formulaire est définie sur `false` si la case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="68976-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="68976-108">Cela est utile dans les situations où vous souhaitez limiter l’interaction de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="68976-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68976-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68976-109">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="68976-110">Vue d'ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="68976-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="68976-111">Guide pratique pour répondre à un clic du contrôle CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68976-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="68976-112">CheckBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="68976-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
