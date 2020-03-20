---
title: "Comment : déterminer l'enfant MDI actif"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182545"
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="6f2bc-102">Comment : déterminer l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="6f2bc-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="6f2bc-103">À l’occasion, vous voudrez fournir une commande qui fonctionne sur le contrôle qui a mis l’accent sur la forme d’enfant actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="6f2bc-104">Supposons, par exemple, que vous souhaitez copier du texte sélectionné entre la boîte texte du formulaire enfant et le Clipboard.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="6f2bc-105">Vous créeriez une procédure qui copie le <xref:System.Windows.Forms.Control.Click> texte sélectionné au Clipboard en utilisant l’événement de l’élément du menu Copy sur le menu Edit standard.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="6f2bc-106">Étant donné qu’une application MDI peut présenter de nombreux cas de la même forme d’enfant, la procédure doit savoir quelle forme utiliser.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="6f2bc-107">Pour spécifier le <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> formulaire correct, utilisez la propriété, qui renvoie la forme de l’enfant qui a la mise au point ou qui a été plus récemment active.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="6f2bc-108">Lorsque vous avez plusieurs contrôles sur un formulaire, vous devez également spécifier quel contrôle est actif.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="6f2bc-109">Comme <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> la propriété, la <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriété retourne le contrôle en mettant l’accent sur la forme active de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="6f2bc-110">La procédure ci-dessous illustre une procédure de copie qui peut être appelée à partir d’un menu de formulaire enfant, un menu sur le formulaire MDI, ou un bouton de barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="6f2bc-111">Déterminer l’enfant MDI actif (pour copier son texte au Clipboard)</span><span class="sxs-lookup"><span data-stu-id="6f2bc-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="6f2bc-112">Dans le cadre d’une méthode, copiez le texte du contrôle actif de la forme active de l’enfant au Clipboard.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6f2bc-113">Cet exemple suppose qu’il existe`Form1`un formulaire parent MDI ( ) <xref:System.Windows.Forms.RichTextBox> qui a une ou plusieurs fenêtres d’enfant MDI contenant un contrôle.</span><span class="sxs-lookup"><span data-stu-id="6f2bc-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="6f2bc-114">Pour plus d’informations, voir [Créer des formulaires parent MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6f2bc-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6f2bc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f2bc-115">See also</span></span>

- [<span data-ttu-id="6f2bc-116">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="6f2bc-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="6f2bc-117">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="6f2bc-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="6f2bc-118">Comment : créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="6f2bc-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="6f2bc-119">Comment : envoyer des données à l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="6f2bc-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="6f2bc-120">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="6f2bc-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
