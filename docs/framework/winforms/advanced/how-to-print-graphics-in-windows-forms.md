---
title: 'Procédure : imprimer des graphismes dans Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 347c7064c199e953b496c9505f08c9e12c1ae670
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052812"
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="cbf33-102">Procédure : imprimer des graphismes dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbf33-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="cbf33-103">Souvent, vous devez imprimer des graphiques dans votre application basée sur Windows.</span><span class="sxs-lookup"><span data-stu-id="cbf33-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="cbf33-104">Le <xref:System.Drawing.Graphics> classe fournit des méthodes pour dessiner des objets sur un appareil, tel qu’un écran ou une imprimante.</span><span class="sxs-lookup"><span data-stu-id="cbf33-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="cbf33-105">Pour imprimer des graphiques</span><span class="sxs-lookup"><span data-stu-id="cbf33-105">To print graphics</span></span>  
  
1. <span data-ttu-id="cbf33-106">Ajouter un <xref:System.Drawing.Printing.PrintDocument> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="cbf33-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="cbf33-107">Dans le <xref:System.Drawing.Printing.PrintDocument.PrintPage> Gestionnaire d’événements, utilisez le <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriété de la <xref:System.Drawing.Printing.PrintPageEventArgs> classe pour indiquer à l’imprimante sur les types de graphismes à imprimer.</span><span class="sxs-lookup"><span data-stu-id="cbf33-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="cbf33-108">L’exemple de code suivant montre un gestionnaire d’événements utilisé pour créer une ellipse bleue dans un rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="cbf33-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="cbf33-109">Le rectangle a l’emplacement et les dimensions suivantes : début à 100, 150 avec une largeur de 250 et une hauteur de 250.</span><span class="sxs-lookup"><span data-stu-id="cbf33-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     <span data-ttu-id="cbf33-110">(Visual C# et Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="cbf33-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cbf33-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbf33-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="cbf33-112">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbf33-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
