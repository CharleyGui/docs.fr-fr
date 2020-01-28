---
title: Terminer les travaux d’impression
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746492"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="2d745-102">Comment : terminer des travaux d'impression Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d745-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="2d745-103">Souvent, les traitements de texte et d’autres applications qui impliquent l’impression offrent la possibilité d’afficher un message aux utilisateurs qu’un travail d’impression est terminé.</span><span class="sxs-lookup"><span data-stu-id="2d745-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="2d745-104">Vous pouvez fournir cette fonctionnalité dans votre Windows Forms en gérant l’événement <xref:System.Drawing.Printing.PrintDocument.EndPrint> du composant <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="2d745-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="2d745-105">La procédure suivante nécessite que vous ayez créé une application Windows avec un composant <xref:System.Drawing.Printing.PrintDocument>, qui est la méthode standard d’activation de l’impression à partir d’une application Windows.</span><span class="sxs-lookup"><span data-stu-id="2d745-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="2d745-106">Pour plus d’informations sur l’impression à partir de Windows Forms à l’aide du composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : créer des travaux d’impression Windows Forms standard](how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2d745-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="2d745-107">Pour terminer un travail d’impression</span><span class="sxs-lookup"><span data-stu-id="2d745-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="2d745-108">Définissez la propriété <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> du composant <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="2d745-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="2d745-109">Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.EndPrint> .</span><span class="sxs-lookup"><span data-stu-id="2d745-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="2d745-110">Dans l’exemple de code suivant, une boîte de message s’affiche, indiquant que l’impression du document est terminée.</span><span class="sxs-lookup"><span data-stu-id="2d745-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     <span data-ttu-id="2d745-111">(Visuel C# et visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="2d745-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d745-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d745-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="2d745-113">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d745-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
