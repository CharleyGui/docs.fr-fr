---
title: 'Procédure : déterminer l’enfant MDI actif'
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
ms.openlocfilehash: 91100b37e4cae9041479b209e40034efe376df5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946220"
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="80a07-102">Procédure : déterminer l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="80a07-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="80a07-103">À l’occasion, vous souhaiterez peut-être fournir une commande qui opère sur le contrôle qui a le focus sur le formulaire enfant actif.</span><span class="sxs-lookup"><span data-stu-id="80a07-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="80a07-104">Par exemple, supposons que vous souhaitiez copier le texte sélectionné de la zone de texte du formulaire enfant vers le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="80a07-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="80a07-105">Vous créez une procédure qui copie le texte sélectionné dans le presse-papiers <xref:System.Windows.Forms.Control.Click> à l’aide de l’événement de l’élément de menu copier du menu Edition standard.</span><span class="sxs-lookup"><span data-stu-id="80a07-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="80a07-106">Étant donné qu’une application MDI peut avoir plusieurs instances du même formulaire enfant, la procédure doit savoir quel formulaire utiliser.</span><span class="sxs-lookup"><span data-stu-id="80a07-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="80a07-107">Pour spécifier la forme appropriée, utilisez la <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriété, qui retourne le formulaire enfant qui a le focus ou qui a été le plus récemment actif.</span><span class="sxs-lookup"><span data-stu-id="80a07-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="80a07-108">Quand vous disposez de plusieurs contrôles sur un formulaire, vous devez également spécifier le contrôle qui est actif.</span><span class="sxs-lookup"><span data-stu-id="80a07-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="80a07-109">À l' <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> instar de <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> la propriété, la propriété retourne le contrôle ayant le focus sur le formulaire enfant actif.</span><span class="sxs-lookup"><span data-stu-id="80a07-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="80a07-110">La procédure suivante illustre une procédure de copie qui peut être appelée à partir d’un menu de formulaire enfant, d’un menu sur le formulaire MDI ou d’un bouton de barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="80a07-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="80a07-111">Pour déterminer l’enfant MDI actif (pour copier son texte dans le presse-papiers)</span><span class="sxs-lookup"><span data-stu-id="80a07-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="80a07-112">Dans une méthode, copiez le texte du contrôle actif du formulaire enfant actif dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="80a07-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="80a07-113">Cet exemple suppose qu’il existe un formulaire MDI parent (`Form1`) avec une ou plusieurs fenêtres enfants MDI contenant un <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="80a07-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="80a07-114">Pour plus d’informations, consultez [création de formulaires MDI parents](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="80a07-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80a07-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80a07-115">See also</span></span>

- [<span data-ttu-id="80a07-116">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="80a07-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="80a07-117">Guide pratique pour Créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="80a07-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="80a07-118">Guide pratique pour Créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="80a07-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="80a07-119">Guide pratique pour Envoyer des données à l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="80a07-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="80a07-120">Guide pratique pour Réorganiser les formulaires enfants MDI</span><span class="sxs-lookup"><span data-stu-id="80a07-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
