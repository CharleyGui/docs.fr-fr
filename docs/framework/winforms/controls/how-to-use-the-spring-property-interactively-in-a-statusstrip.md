---
title: 'Procédure : utiliser la propriété Spring dans un StatusStrip de manière interactive'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: 8750c48d08161260a1dba6ab69098980f25a5d55
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589647"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="2d566-102">Procédure : utiliser la propriété Spring dans un StatusStrip de manière interactive</span><span class="sxs-lookup"><span data-stu-id="2d566-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="2d566-103">Vous pouvez utiliser la propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> pour positionner un contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> dans un contrôle <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2d566-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="2d566-104">La propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> détermine si le contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> remplit automatiquement l'espace disponible sur le contrôle <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2d566-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d566-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d566-105">Example</span></span>  
 <span data-ttu-id="2d566-106">L'exemple de code suivant montre comment utiliser la propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> pour positionner un contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> dans un contrôle <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2d566-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="2d566-107">Le gestionnaire d'événements <xref:System.Windows.Forms.ToolStripItem.Click> exécute une opération « ou exclusif » (XOR) pour faire basculer la valeur de la propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d566-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="2d566-108">Pour utiliser cet exemple de code, compilez et exécutez l’application, puis cliquez sur **Middle (Spring)** sur le <xref:System.Windows.Forms.StatusStrip> contrôle pour faire basculer la valeur de la <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="2d566-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d566-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2d566-109">Compiling the Code</span></span>  
 <span data-ttu-id="2d566-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="2d566-110">This example requires:</span></span>  
  
- <span data-ttu-id="2d566-111">des références aux assemblys System.Design, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2d566-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d566-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d566-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="2d566-113">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2d566-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
