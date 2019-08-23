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
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Procédure : envoyer des données à l’enfant MDI actif
Souvent, dans le contexte des [applications d’interface multidocument (MDI, multiple-document interface)](multiple-document-interface-mdi-applications.md), vous devez envoyer des données à la fenêtre enfant active, par exemple lorsque l’utilisateur colle des données du presse-papiers dans une application MDI.  
  
> [!NOTE]
> Pour plus d’informations sur la vérification de la fenêtre enfant qui a le focus et sur l’envoi de son contenu dans le presse-papiers, consultez [détermination de l’enfant MDI actif](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Pour envoyer des données à la fenêtre enfant MDI active à partir du presse-papiers  
  
1. Dans une méthode, copiez le texte dans le presse-papiers vers le contrôle actif du formulaire enfant actif.  
  
    > [!NOTE]
    > Cet exemple suppose qu’il existe un formulaire MDI parent (`Form1`) avec une ou plusieurs fenêtres enfants MDI contenant un <xref:System.Windows.Forms.RichTextBox> contrôle. Pour plus d’informations, consultez [création de formulaires MDI parents](how-to-create-mdi-parent-forms.md).  
  
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
- [Guide pratique pour Créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)
- [Guide pratique : Créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md)
- [Guide pratique pour Déterminer l’enfant MDI actif](how-to-determine-the-active-mdi-child.md)
- [Guide pratique : Réorganiser les formulaires enfants MDI](how-to-arrange-mdi-child-forms.md)
