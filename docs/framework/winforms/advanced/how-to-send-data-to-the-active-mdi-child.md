---
title: 'Procédure : envoyer des données à l’enfant MDI actif'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: 0a7a2475891488d1fdd60f0db4a483c144a73f0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947843"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="735b5-102">Procédure : envoyer des données à l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="735b5-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="735b5-103">Souvent, dans le contexte des [applications d’interface multidocument (MDI, multiple-document interface)](multiple-document-interface-mdi-applications.md), vous devez envoyer des données à la fenêtre enfant active, par exemple lorsque l’utilisateur colle des données du presse-papiers dans une application MDI.</span><span class="sxs-lookup"><span data-stu-id="735b5-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="735b5-104">Pour plus d’informations sur la vérification de la fenêtre enfant qui a le focus et sur l’envoi de son contenu dans le presse-papiers, consultez [détermination de l’enfant MDI actif](how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="735b5-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="735b5-105">Pour envoyer des données à la fenêtre enfant MDI active à partir du presse-papiers</span><span class="sxs-lookup"><span data-stu-id="735b5-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1. <span data-ttu-id="735b5-106">Dans une méthode, copiez le texte dans le presse-papiers vers le contrôle actif du formulaire enfant actif.</span><span class="sxs-lookup"><span data-stu-id="735b5-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="735b5-107">Cet exemple suppose qu’il existe un formulaire MDI parent (`Form1`) avec une ou plusieurs fenêtres enfants MDI contenant un <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="735b5-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="735b5-108">Pour plus d’informations, consultez [création de formulaires MDI parents](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="735b5-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
             }  
          }  
          catch   
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="735b5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="735b5-109">See also</span></span>

- [<span data-ttu-id="735b5-110">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="735b5-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="735b5-111">Guide pratique pour Créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="735b5-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="735b5-112">Guide pratique : Créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="735b5-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="735b5-113">Guide pratique pour Déterminer l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="735b5-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="735b5-114">Guide pratique : Réorganiser les formulaires enfants MDI</span><span class="sxs-lookup"><span data-stu-id="735b5-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
