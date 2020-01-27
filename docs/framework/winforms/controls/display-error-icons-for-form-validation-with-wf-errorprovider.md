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
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="f5135-102">Comment : afficher des icônes d'erreur pour la validation de formulaire à l'aide du composant ErrorProvider Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5135-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="f5135-103">Vous pouvez utiliser un composant Windows Forms <xref:System.Windows.Forms.ErrorProvider> pour afficher une icône d’erreur lorsque l’utilisateur entre des données non valides.</span><span class="sxs-lookup"><span data-stu-id="f5135-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="f5135-104">Vous devez disposer d’au moins deux contrôles sur le formulaire pour pouvoir les faire passer de l’un à l’autre et, par conséquent, appeler le code de validation.</span><span class="sxs-lookup"><span data-stu-id="f5135-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="f5135-105">Pour afficher une icône d’erreur quand la valeur d’un contrôle n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="f5135-105">To display an error icon when a control's value is invalid</span></span>  
  
1. <span data-ttu-id="f5135-106">Ajoutez deux contrôles, par exemple des zones de texte, à un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="f5135-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2. <span data-ttu-id="f5135-107">Ajoutez un composant <xref:System.Windows.Forms.ErrorProvider> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="f5135-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3. <span data-ttu-id="f5135-108">Sélectionnez le premier contrôle et ajoutez du code à son gestionnaire d’événements <xref:System.Windows.Forms.Control.Validating>.</span><span class="sxs-lookup"><span data-stu-id="f5135-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="f5135-109">Pour que ce code s’exécute correctement, la procédure doit être connectée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="f5135-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="f5135-110">Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f5135-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="f5135-111">Le code suivant teste la validité des données que l’utilisateur a entrées ; Si les données ne sont pas valides, la méthode <xref:System.Windows.Forms.ErrorProvider.SetError%2A> est appelée.</span><span class="sxs-lookup"><span data-stu-id="f5135-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="f5135-112">Le premier argument de la méthode <xref:System.Windows.Forms.ErrorProvider.SetError%2A> spécifie le contrôle qui doit afficher l’icône à côté de.</span><span class="sxs-lookup"><span data-stu-id="f5135-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="f5135-113">Le deuxième argument est le texte d’erreur à afficher.</span><span class="sxs-lookup"><span data-stu-id="f5135-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="f5135-114">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="f5135-114">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. <span data-ttu-id="f5135-115">Exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="f5135-115">Run the project.</span></span> <span data-ttu-id="f5135-116">Tapez des données non valides (dans cet exemple, non numériques) dans le premier contrôle, puis appuyez sur la touche Tab pour la deuxième.</span><span class="sxs-lookup"><span data-stu-id="f5135-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="f5135-117">Lorsque l’icône d’erreur s’affiche, pointez dessus à l’aide du pointeur de la souris pour afficher le texte de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="f5135-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5135-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5135-118">See also</span></span>

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="f5135-119">Vue d’ensemble du composant ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="f5135-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="f5135-120">Guide pratique pour afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5135-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
