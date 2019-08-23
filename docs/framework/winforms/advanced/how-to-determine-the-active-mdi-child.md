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
# <a name="how-to-determine-the-active-mdi-child"></a>Procédure : déterminer l’enfant MDI actif
À l’occasion, vous souhaiterez peut-être fournir une commande qui opère sur le contrôle qui a le focus sur le formulaire enfant actif. Par exemple, supposons que vous souhaitiez copier le texte sélectionné de la zone de texte du formulaire enfant vers le presse-papiers. Vous créez une procédure qui copie le texte sélectionné dans le presse-papiers <xref:System.Windows.Forms.Control.Click> à l’aide de l’événement de l’élément de menu copier du menu Edition standard.  
  
 Étant donné qu’une application MDI peut avoir plusieurs instances du même formulaire enfant, la procédure doit savoir quel formulaire utiliser. Pour spécifier la forme appropriée, utilisez la <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriété, qui retourne le formulaire enfant qui a le focus ou qui a été le plus récemment actif.  
  
 Quand vous disposez de plusieurs contrôles sur un formulaire, vous devez également spécifier le contrôle qui est actif. À l' <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> instar de <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> la propriété, la propriété retourne le contrôle ayant le focus sur le formulaire enfant actif. La procédure suivante illustre une procédure de copie qui peut être appelée à partir d’un menu de formulaire enfant, d’un menu sur le formulaire MDI ou d’un bouton de barre d’outils.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Pour déterminer l’enfant MDI actif (pour copier son texte dans le presse-papiers)  
  
1. Dans une méthode, copiez le texte du contrôle actif du formulaire enfant actif dans le presse-papiers.  
  
    > [!NOTE]
    > Cet exemple suppose qu’il existe un formulaire MDI parent (`Form1`) avec une ou plusieurs fenêtres enfants MDI contenant un <xref:System.Windows.Forms.RichTextBox> contrôle. Pour plus d’informations, consultez [création de formulaires MDI parents](how-to-create-mdi-parent-forms.md).  
  
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
- [Guide pratique pour Créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)
- [Guide pratique pour Créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md)
- [Guide pratique pour Envoyer des données à l’enfant MDI actif](how-to-send-data-to-the-active-mdi-child.md)
- [Guide pratique pour Réorganiser les formulaires enfants MDI](how-to-arrange-mdi-child-forms.md)
