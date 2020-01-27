---
title: Afficher les icônes d’erreur pour la validation de formulaire avec le composant ErrorProvider
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
ms.openlocfilehash: a1e346e332db489351f59c9a0c03ae731baf3dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745912"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Comment : afficher des icônes d'erreur pour la validation de formulaire à l'aide du composant ErrorProvider Windows Forms
Vous pouvez utiliser un composant Windows Forms <xref:System.Windows.Forms.ErrorProvider> pour afficher une icône d’erreur lorsque l’utilisateur entre des données non valides. Vous devez disposer d’au moins deux contrôles sur le formulaire pour pouvoir les faire passer de l’un à l’autre et, par conséquent, appeler le code de validation.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Pour afficher une icône d’erreur quand la valeur d’un contrôle n’est pas valide  
  
1. Ajoutez deux contrôles, par exemple des zones de texte, à un Windows Form.  
  
2. Ajoutez un composant <xref:System.Windows.Forms.ErrorProvider> au formulaire.  
  
3. Sélectionnez le premier contrôle et ajoutez du code à son gestionnaire d’événements <xref:System.Windows.Forms.Control.Validating>. Pour que ce code s’exécute correctement, la procédure doit être connectée à l’événement. Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Le code suivant teste la validité des données que l’utilisateur a entrées ; Si les données ne sont pas valides, la méthode <xref:System.Windows.Forms.ErrorProvider.SetError%2A> est appelée. Le premier argument de la méthode <xref:System.Windows.Forms.ErrorProvider.SetError%2A> spécifie le contrôle qui doit afficher l’icône à côté de. Le deuxième argument est le texte d’erreur à afficher.  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Exécuter le projet. Tapez des données non valides (dans cet exemple, non numériques) dans le premier contrôle, puis appuyez sur la touche Tab pour la deuxième. Lorsque l’icône d’erreur s’affiche, pointez dessus à l’aide du pointeur de la souris pour afficher le texte de l’erreur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [Vue d’ensemble du composant ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Guide pratique pour afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
