---
title: 'Comment : Choisissez les imprimantes attachées à l’ordinateur d’un utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 2afbccd02ef42a78d5eac1a01841516fca27c92e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182614"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="268fa-102">Comment : choisir les imprimantes connectées à l'ordinateur d'un utilisateur dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="268fa-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="268fa-103">Souvent, les utilisateurs souhaitent choisir une imprimante autre que l’imprimante par défaut.</span><span class="sxs-lookup"><span data-stu-id="268fa-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="268fa-104">Vous pouvez permettre aux utilisateurs de choisir une imprimante parmi celles installées actuellement à l’aide du composant <xref:System.Windows.Forms.PrintDialog> .</span><span class="sxs-lookup"><span data-stu-id="268fa-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="268fa-105">Par le biais du composant <xref:System.Windows.Forms.PrintDialog> , le <xref:System.Windows.Forms.DialogResult> du composant <xref:System.Windows.Forms.PrintDialog> est capturé et utilisé pour sélectionner l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="268fa-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="268fa-106">Dans la procédure suivante, un fichier texte est sélectionné pour impression vers l’imprimante par défaut.</span><span class="sxs-lookup"><span data-stu-id="268fa-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="268fa-107">La classe <xref:System.Windows.Forms.PrintDialog> est ensuite instanciée.</span><span class="sxs-lookup"><span data-stu-id="268fa-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="268fa-108">Pour choisir une imprimante, puis imprimer un fichier</span><span class="sxs-lookup"><span data-stu-id="268fa-108">To choose a printer and then print a file</span></span>  
  
1. <span data-ttu-id="268fa-109">Sélectionnez l’imprimante à <xref:System.Windows.Forms.PrintDialog> utiliser à l’aide du composant.</span><span class="sxs-lookup"><span data-stu-id="268fa-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="268fa-110">Dans l’exemple de code suivant, deux événements sont gérés.</span><span class="sxs-lookup"><span data-stu-id="268fa-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="268fa-111">Dans le premier, <xref:System.Windows.Forms.Button> un <xref:System.Windows.Forms.Control.Click> événement <xref:System.Windows.Forms.PrintDialog> de contrôle, la classe est instantanée et l’imprimante sélectionnée par l’utilisateur est capturée dans la <xref:System.Windows.Forms.DialogResult> propriété.</span><span class="sxs-lookup"><span data-stu-id="268fa-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="268fa-112">Dans le deuxième <xref:System.Drawing.Printing.PrintDocument.PrintPage> cas, <xref:System.Drawing.Printing.PrintDocument> le cas du composant, un document d’échantillon est imprimé à l’imprimante spécifiée.</span><span class="sxs-lookup"><span data-stu-id="268fa-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="268fa-113">(Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.</span><span class="sxs-lookup"><span data-stu-id="268fa-113">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="268fa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="268fa-114">See also</span></span>

- [<span data-ttu-id="268fa-115">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="268fa-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
