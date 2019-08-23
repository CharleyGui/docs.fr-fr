---
title: 'Procédure : imprimer un fichier texte de plusieurs pages dans Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931787"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="3febd-102">Procédure : imprimer un fichier texte de plusieurs pages dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3febd-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="3febd-103">Il est très courant que les applications Windows impriment du texte.</span><span class="sxs-lookup"><span data-stu-id="3febd-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="3febd-104">La classe <xref:System.Drawing.Graphics> fournit des méthodes pour dessiner des objets (graphismes ou texte) sur un périphérique, tel qu'un écran ou une imprimante.</span><span class="sxs-lookup"><span data-stu-id="3febd-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3febd-105">Le méthodes <xref:System.Windows.Forms.TextRenderer.DrawText%2A> de <xref:System.Windows.Forms.TextRenderer> ne sont pas prises en charge pour l'impression.</span><span class="sxs-lookup"><span data-stu-id="3febd-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="3febd-106">Vous devez toujours utiliser les méthodes <xref:System.Drawing.Graphics.DrawString%2A> de <xref:System.Drawing.Graphics>, comme illustré dans l'exemple de code suivant, pour dessiner du texte pour l'impression.</span><span class="sxs-lookup"><span data-stu-id="3febd-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="3febd-107">Pour imprimer du texte</span><span class="sxs-lookup"><span data-stu-id="3febd-107">To print text</span></span>  
  
1. <span data-ttu-id="3febd-108">Ajoutez un composant <xref:System.Drawing.Printing.PrintDocument> et une chaîne à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="3febd-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="3febd-109">Si vous imprimez un document, affectez comme valeur de la propriété <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> le document que vous souhaitez imprimer, puis ouvrez et lisez le contenu du document dans la chaîne que vous avez ajoutée précédemment.</span><span class="sxs-lookup"><span data-stu-id="3febd-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="3febd-110">Dans le gestionnaire d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage>, utilisez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs> et le contenu du document pour calculer la longueur de ligne et le nombre de lignes par page.</span><span class="sxs-lookup"><span data-stu-id="3febd-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="3febd-111">Après chaque dessin de page, vérifiez s'il s'agit de la dernière page et définissez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> de <xref:System.Drawing.Printing.PrintPageEventArgs> en conséquence.</span><span class="sxs-lookup"><span data-stu-id="3febd-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="3febd-112">L'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est déclenché jusqu'à ce que <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> soit `false`.</span><span class="sxs-lookup"><span data-stu-id="3febd-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="3febd-113">Assurez-vous aussi que l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est associé à sa méthode de gestion d'événements.</span><span class="sxs-lookup"><span data-stu-id="3febd-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="3febd-114">Dans l'exemple de code suivant, le gestionnaire d'événements est utilisé pour imprimer le contenu du fichier « testPage.txt » avec la même police que celle utilisée sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="3febd-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="3febd-115">Appelez la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour déclencher l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="3febd-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="3febd-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="3febd-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3febd-117">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3febd-117">Compiling the Code</span></span>  
 <span data-ttu-id="3febd-118">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3febd-118">This example requires:</span></span>  
  
- <span data-ttu-id="3febd-119">Un fichier texte nommé testPage.txt contenant le texte à imprimer, situé à la racine du lecteur C:\\.</span><span class="sxs-lookup"><span data-stu-id="3febd-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="3febd-120">Modifiez le code pour imprimer un fichier différent.</span><span class="sxs-lookup"><span data-stu-id="3febd-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="3febd-121">Références aux assemblys System, System.Windows.Forms, System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="3febd-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="3febd-122">Pour plus d’informations sur la création de cet exemple à partir de la C#ligne de commande pour Visual Basic ou visuel, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou génération à partir de la [ligne de commande avec CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3febd-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3febd-123">Vous pouvez également générer cet exemple dans Visual Studio en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="3febd-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3febd-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3febd-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="3febd-125">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3febd-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
