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
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="18eaa-102">Comment : définir des options avec les contrôles CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18eaa-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="18eaa-103">Un contrôle <xref:System.Windows.Forms.CheckBox> des formulaires Windows est utilisé pour donner aux utilisateurs des options True/False ou Yes/No.</span><span class="sxs-lookup"><span data-stu-id="18eaa-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="18eaa-104">Le contrôle affiche une marque de contrôle lorsqu’elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18eaa-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="18eaa-105">Définir des options avec les contrôles CheckBox</span><span class="sxs-lookup"><span data-stu-id="18eaa-105">To set options with CheckBox controls</span></span>  
  
1. <span data-ttu-id="18eaa-106">Examinez la <xref:System.Windows.Forms.CheckBox.Checked%2A> valeur de la propriété pour déterminer son état et utilisez cette valeur pour définir une option.</span><span class="sxs-lookup"><span data-stu-id="18eaa-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="18eaa-107">Dans l’échantillon de <xref:System.Windows.Forms.CheckBox> code ci-dessous, lorsque l’événement du <xref:System.Windows.Forms.CheckBox.CheckedChanged> contrôleur est soulevé, la propriété du <xref:System.Windows.Forms.Control.AllowDrop%2A> formulaire est définie `false` si la case à cocher est cochée.</span><span class="sxs-lookup"><span data-stu-id="18eaa-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="18eaa-108">Ceci est utile pour les situations où vous souhaitez restreindre l’interaction avec l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="18eaa-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18eaa-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18eaa-109">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="18eaa-110">Vue d’ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="18eaa-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="18eaa-111">Comment : répondre à un clic du contrôle CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18eaa-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="18eaa-112">Contrôle De la Case De Contrôle</span><span class="sxs-lookup"><span data-stu-id="18eaa-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
