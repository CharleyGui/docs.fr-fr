---
title: Créer des emplois d’impression standard
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182569"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="f325e-102">Comment : créer des travaux d'impression Windows Forms standard</span><span class="sxs-lookup"><span data-stu-id="f325e-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="f325e-103">La base de l’impression <xref:System.Drawing.Printing.PrintDocument> dans Windows Forms <xref:System.Drawing.Printing.PrintDocument.PrintPage> est le composant, plus précisément, l’événement.</span><span class="sxs-lookup"><span data-stu-id="f325e-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="f325e-104">En écrivant du <xref:System.Drawing.Printing.PrintDocument.PrintPage> code pour gérer l’événement, vous pouvez spécifier ce qu’il faut imprimer et comment l’imprimer.</span><span class="sxs-lookup"><span data-stu-id="f325e-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="f325e-105">Pour créer un travail d’impression</span><span class="sxs-lookup"><span data-stu-id="f325e-105">To create a print job</span></span>  
  
1. <span data-ttu-id="f325e-106">Ajoutez <xref:System.Drawing.Printing.PrintDocument> un composant à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="f325e-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="f325e-107">Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> .</span><span class="sxs-lookup"><span data-stu-id="f325e-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="f325e-108">Vous devrez coder votre propre logique d’impression.</span><span class="sxs-lookup"><span data-stu-id="f325e-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="f325e-109">En outre, vous devrez spécifier le matériel à imprimer.</span><span class="sxs-lookup"><span data-stu-id="f325e-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="f325e-110">Dans l’exemple de code suivant, un graphique d’échantillon <xref:System.Drawing.Printing.PrintDocument.PrintPage> en forme de rectangle rouge est créé dans le gestionnaire d’événements pour agir comme matériel à imprimer.</span><span class="sxs-lookup"><span data-stu-id="f325e-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="f325e-111">(Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.</span><span class="sxs-lookup"><span data-stu-id="f325e-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="f325e-112">Vous pouvez également écrire du <xref:System.Drawing.Printing.PrintDocument.BeginPrint> <xref:System.Drawing.Printing.PrintDocument.EndPrint> code pour les événements et des événements, y compris peut-être un intégrier représentant le nombre total de pages à imprimer qui est décriée au fur et à mesure que chaque page est imprimée.</span><span class="sxs-lookup"><span data-stu-id="f325e-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f325e-113">Vous pouvez <xref:System.Windows.Forms.PrintDialog> ajouter un composant à votre formulaire pour fournir une interface utilisateur propre et efficace (interface utilisateur) à vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f325e-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="f325e-114">La <xref:System.Windows.Forms.PrintDialog.Document%2A> configuration de <xref:System.Windows.Forms.PrintDialog> la propriété du composant vous permet de définir les propriétés liées au document d’impression avec lequel vous travaillez sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="f325e-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="f325e-115">Pour plus d’informations sur le <xref:System.Windows.Forms.PrintDialog> composant, voir [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f325e-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="f325e-116">Pour plus d’informations sur les spécificités des travaux d’impression Windows <xref:System.Drawing.Printing.PrintPageEventArgs>Forms, y compris la façon de créer un emploi d’impression programmatiquement, voir .</span><span class="sxs-lookup"><span data-stu-id="f325e-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f325e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f325e-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="f325e-118">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f325e-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
