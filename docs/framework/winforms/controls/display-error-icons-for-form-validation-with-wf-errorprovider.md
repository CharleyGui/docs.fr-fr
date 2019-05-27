---
title: 'Procédure : afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms'
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
ms.openlocfilehash: 2af8d3b9ea97b678c493de8a58d439b62f448387
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053713"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Procédure : afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms
Vous pouvez utiliser un formulaire Windows <xref:System.Windows.Forms.ErrorProvider> composant pour afficher une icône d’erreur lorsque l’utilisateur entre des données non valides. Vous devez disposer d’au moins deux contrôles du formulaire afin d’onglet entre eux et ainsi appeler le code de validation.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Pour afficher une icône d’erreur lors de la valeur d’un contrôle n’est pas valide  
  
1. Ajoutez deux contrôles, par exemple, les zones de texte, à un formulaire Windows.  
  
2. Ajouter un <xref:System.Windows.Forms.ErrorProvider> composant au formulaire.  
  
3. Sélectionnez le premier contrôle et ajoutez du code à son <xref:System.Windows.Forms.Control.Validating> Gestionnaire d’événements. Dans l’ordre pour que ce code s’exécute correctement, la procédure doit être connectée à l’événement. Pour plus d'informations, voir [Procédure : Créer des gestionnaires d’événements en cours d’exécution pour les Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Le code suivant teste la validité des données entrées par l’utilisateur ; Si les données ne sont pas valides, le <xref:System.Windows.Forms.ErrorProvider.SetError%2A> méthode est appelée. Le premier argument de la <xref:System.Windows.Forms.ErrorProvider.SetError%2A> méthode spécifie le contrôle à afficher à côté de l’icône. Le deuxième argument est le texte d’erreur à afficher.  
  
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
  
     (Visual C#, Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Exécuter le projet. Tapez les données non valides (dans cet exemple, non numérique) dans le premier contrôle, puis onglet à la seconde. Lorsque l’icône d’erreur s’affiche, placez le pointeur de la souris pour afficher le texte d’erreur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [Vue d’ensemble du composant ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Guide pratique pour Afficher les erreurs au sein d’un jeu de données avec l’aide du composant ErrorProvider Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
