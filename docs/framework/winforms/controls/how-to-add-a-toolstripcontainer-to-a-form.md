---
title: 'Procédure : ajouter un ToolStripContainer à un formulaire'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 6b35baac09ac47a25cc55877b2c94628f1b57111
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624070"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="d8585-102">Procédure : ajouter un ToolStripContainer à un formulaire</span><span class="sxs-lookup"><span data-stu-id="d8585-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="d8585-103">Vous pouvez ajouter par programmation un <xref:System.Windows.Forms.ToolStripContainer> à un Windows Form et le remplir avec des contrôles.</span><span class="sxs-lookup"><span data-stu-id="d8585-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8585-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8585-104">Example</span></span>  
 <span data-ttu-id="d8585-105">L'exemple de code suivant montre comment ajouter un <xref:System.Windows.Forms.ToolStripContainer> et un <xref:System.Windows.Forms.ToolStrip> à un Windows Forms, comment ajouter des éléments au <xref:System.Windows.Forms.ToolStrip> et comment ajouter le <xref:System.Windows.Forms.ToolStrip> au <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> du <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d8585-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8585-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d8585-106">Compiling the Code</span></span>  
 <span data-ttu-id="d8585-107">Cet exemple de code nécessite :</span><span class="sxs-lookup"><span data-stu-id="d8585-107">This code example requires:</span></span>  
  
- <span data-ttu-id="d8585-108">Références aux assemblys System.Drawing, System.Text et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d8585-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d8585-109">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d8585-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d8585-110">Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="d8585-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d8585-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8585-111">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="d8585-112">ToolStripContainer, contrôle</span><span class="sxs-lookup"><span data-stu-id="d8585-112">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="d8585-113">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d8585-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
