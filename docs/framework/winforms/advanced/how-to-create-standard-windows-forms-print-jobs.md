---
title: 'Procédure : créer des travaux d’impression Windows Forms standard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938243"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="3f82c-102">Procédure : créer des travaux d’impression Windows Forms standard</span><span class="sxs-lookup"><span data-stu-id="3f82c-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="3f82c-103">La base de l’impression dans Windows Forms est <xref:System.Drawing.Printing.PrintDocument> le composant, plus particulièrement l' <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement.</span><span class="sxs-lookup"><span data-stu-id="3f82c-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="3f82c-104">En écrivant du code pour <xref:System.Drawing.Printing.PrintDocument.PrintPage> gérer l’événement, vous pouvez spécifier ce qui doit être imprimé et comment l’imprimer.</span><span class="sxs-lookup"><span data-stu-id="3f82c-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="3f82c-105">Pour créer un travail d’impression</span><span class="sxs-lookup"><span data-stu-id="3f82c-105">To create a print job</span></span>  
  
1. <span data-ttu-id="3f82c-106">Ajoutez un <xref:System.Drawing.Printing.PrintDocument> composant à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="3f82c-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="3f82c-107">Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> .</span><span class="sxs-lookup"><span data-stu-id="3f82c-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="3f82c-108">Vous devrez coder votre propre logique d’impression.</span><span class="sxs-lookup"><span data-stu-id="3f82c-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="3f82c-109">En outre, vous devrez spécifier le matériel à imprimer.</span><span class="sxs-lookup"><span data-stu-id="3f82c-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="3f82c-110">Dans l’exemple de code suivant, un exemple de graphique dans la forme d’un rectangle rouge est créé <xref:System.Drawing.Printing.PrintDocument.PrintPage> dans le gestionnaire d’événements pour agir en tant que matériau à imprimer.</span><span class="sxs-lookup"><span data-stu-id="3f82c-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="3f82c-111">(Visuel C# et visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="3f82c-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     <span data-ttu-id="3f82c-112">Vous pouvez également écrire du code pour les <xref:System.Drawing.Printing.PrintDocument.BeginPrint> événements et <xref:System.Drawing.Printing.PrintDocument.EndPrint> , en incluant éventuellement un entier représentant le nombre total de pages à imprimer qui est décrémenté à mesure que chaque page s’imprime.</span><span class="sxs-lookup"><span data-stu-id="3f82c-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3f82c-113">Vous pouvez ajouter un <xref:System.Windows.Forms.PrintDialog> composant à votre formulaire pour fournir une interface utilisateur propre et efficace à vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="3f82c-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="3f82c-114">La définition <xref:System.Windows.Forms.PrintDialog.Document%2A> <xref:System.Windows.Forms.PrintDialog> de la propriété du composant vous permet de définir les propriétés relatives à l’impression du document que vous utilisez dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="3f82c-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="3f82c-115">Pour plus d’informations sur <xref:System.Windows.Forms.PrintDialog> le composant, consultez [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3f82c-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="3f82c-116">Pour plus d’informations sur les spécificités de Windows Forms travaux d’impression, notamment sur la création d’un travail d’impression par <xref:System.Drawing.Printing.PrintPageEventArgs>programme, consultez.</span><span class="sxs-lookup"><span data-stu-id="3f82c-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f82c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f82c-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="3f82c-118">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f82c-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
