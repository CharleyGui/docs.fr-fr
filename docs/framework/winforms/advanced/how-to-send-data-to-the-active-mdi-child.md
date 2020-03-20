---
title: "Comment : envoyer des données à l'enfant MDI actif"
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
ms.openlocfilehash: 563be8494cb84dc74b45985d3ba74e4b6a07eb8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182496"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Comment : envoyer des données à l'enfant MDI actif
Souvent, dans le cadre des [applications d’interface multi-documents (MDI),](multiple-document-interface-mdi-applications.md)vous devrez envoyer des données à la fenêtre active de l’enfant, par exemple lorsque l’utilisateur colle les données du Clipboard dans une application MDI.  
  
> [!NOTE]
> Pour plus d’informations sur la vérification de la fenêtre de l’enfant et l’envoi de son contenu au Clipboard, voir [Déterminer l’enfant actif MDI](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Envoyer des données à la fenêtre active de l’enfant MDI à partir du Clipboard  
  
1. Dans le cadre d’une méthode, copiez le texte sur le Clipboard au contrôle actif de la forme active de l’enfant.  
  
    > [!NOTE]
    > Cet exemple suppose qu’il existe`Form1`un formulaire parent MDI ( ) <xref:System.Windows.Forms.RichTextBox> qui a une ou plusieurs fenêtres d’enfant MDI contenant un contrôle. Pour plus d’informations, voir [Créer des formulaires parent MDI](how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Applications d’interface multidocument (MDI, Multiple Document Interface)](multiple-document-interface-mdi-applications.md)
- [Guide pratique pour créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)
- [Comment : créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md)
- [Comment : déterminer l'enfant MDI actif](how-to-determine-the-active-mdi-child.md)
- [Guide pratique pour réorganiser des formulaires MDI enfants](how-to-arrange-mdi-child-forms.md)
