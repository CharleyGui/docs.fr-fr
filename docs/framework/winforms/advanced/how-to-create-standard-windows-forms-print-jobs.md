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
ms.openlocfilehash: 96122302610d143c34404eac105ca9794b1cb15a
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053671"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="4460c-102">Procédure : créer des travaux d’impression Windows Forms standard</span><span class="sxs-lookup"><span data-stu-id="4460c-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="4460c-103">La base de l’impression dans Windows Forms est la <xref:System.Drawing.Printing.PrintDocument> composant, plus précisément, le <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement.</span><span class="sxs-lookup"><span data-stu-id="4460c-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="4460c-104">En écrivant du code pour gérer le <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement, vous pouvez spécifier les éléments à imprimer et l’imprimer.</span><span class="sxs-lookup"><span data-stu-id="4460c-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="4460c-105">Pour créer un travail d’impression</span><span class="sxs-lookup"><span data-stu-id="4460c-105">To create a print job</span></span>  
  
1. <span data-ttu-id="4460c-106">Ajouter un <xref:System.Drawing.Printing.PrintDocument> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="4460c-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="4460c-107">Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> .</span><span class="sxs-lookup"><span data-stu-id="4460c-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="4460c-108">Vous devrez coder votre propre logique d’impression.</span><span class="sxs-lookup"><span data-stu-id="4460c-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="4460c-109">En outre, vous devez spécifier l’élément à imprimer.</span><span class="sxs-lookup"><span data-stu-id="4460c-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="4460c-110">Dans l’exemple de code suivant, un exemple de graphisme dans la forme d’un rectangle rouge est créé dans le <xref:System.Drawing.Printing.PrintDocument.PrintPage> Gestionnaire d’événements à l’élément à imprimer.</span><span class="sxs-lookup"><span data-stu-id="4460c-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="4460c-111">(Visual C# et Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="4460c-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="4460c-112">Vous souhaiterez également écrire du code pour le <xref:System.Drawing.Printing.PrintDocument.BeginPrint> et <xref:System.Drawing.Printing.PrintDocument.EndPrint> événements, en incluant éventuellement un entier représentant le nombre total de pages à imprimer qui est décrémenté comme imprime chaque page.</span><span class="sxs-lookup"><span data-stu-id="4460c-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4460c-113">Vous pouvez ajouter un <xref:System.Windows.Forms.PrintDialog> à votre formulaire pour fournir une interface propre et efficace de l’utilisateur (IU) à vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4460c-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="4460c-114">Définition de la <xref:System.Windows.Forms.PrintDialog.Document%2A> propriété de la <xref:System.Windows.Forms.PrintDialog> permet de composant vous permet de définir les propriétés relatives à l’impression de document vous travaillez sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="4460c-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="4460c-115">Pour plus d’informations sur la <xref:System.Windows.Forms.PrintDialog> composant, consultez [du composant PrintDialog](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4460c-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="4460c-116">Pour plus d’informations sur les spécificités des Windows Forms les travaux d’impression, y compris la création d’un travail d’impression par programmation, consultez <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="4460c-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4460c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4460c-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="4460c-118">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4460c-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
