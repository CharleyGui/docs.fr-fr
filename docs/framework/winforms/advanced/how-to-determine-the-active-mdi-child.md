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
# <a name="how-to-determine-the-active-mdi-child"></a>Comment : déterminer l'enfant MDI actif
À l’occasion, vous voudrez fournir une commande qui fonctionne sur le contrôle qui a mis l’accent sur la forme d’enfant actuellement actif. Supposons, par exemple, que vous souhaitez copier du texte sélectionné entre la boîte texte du formulaire enfant et le Clipboard. Vous créeriez une procédure qui copie le <xref:System.Windows.Forms.Control.Click> texte sélectionné au Clipboard en utilisant l’événement de l’élément du menu Copy sur le menu Edit standard.  
  
 Étant donné qu’une application MDI peut présenter de nombreux cas de la même forme d’enfant, la procédure doit savoir quelle forme utiliser. Pour spécifier le <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> formulaire correct, utilisez la propriété, qui renvoie la forme de l’enfant qui a la mise au point ou qui a été plus récemment active.  
  
 Lorsque vous avez plusieurs contrôles sur un formulaire, vous devez également spécifier quel contrôle est actif. Comme <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> la propriété, la <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriété retourne le contrôle en mettant l’accent sur la forme active de l’enfant. La procédure ci-dessous illustre une procédure de copie qui peut être appelée à partir d’un menu de formulaire enfant, un menu sur le formulaire MDI, ou un bouton de barre d’outils.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Déterminer l’enfant MDI actif (pour copier son texte au Clipboard)  
  
1. Dans le cadre d’une méthode, copiez le texte du contrôle actif de la forme active de l’enfant au Clipboard.  
  
    > [!NOTE]
    > Cet exemple suppose qu’il existe`Form1`un formulaire parent MDI ( ) <xref:System.Windows.Forms.RichTextBox> qui a une ou plusieurs fenêtres d’enfant MDI contenant un contrôle. Pour plus d’informations, voir [Créer des formulaires parent MDI](how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Applications d’interface multidocument (MDI, Multiple Document Interface)](multiple-document-interface-mdi-applications.md)
- [Guide pratique pour créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)
- [Comment : créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md)
- [Comment : envoyer des données à l'enfant MDI actif](how-to-send-data-to-the-active-mdi-child.md)
- [Guide pratique pour réorganiser des formulaires MDI enfants](how-to-arrange-mdi-child-forms.md)
