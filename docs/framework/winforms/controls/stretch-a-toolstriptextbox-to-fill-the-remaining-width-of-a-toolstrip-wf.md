---
title: "Comment : étirer un ToolStripTextBox pour remplir la largeur restante d'un ToolStrip"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742842"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="f9775-102">Comment : étirer un ToolStripTextBox pour remplir la largeur restante d'un ToolStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f9775-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="f9775-103">Lorsque vous affectez à la propriété <xref:System.Windows.Forms.ToolStrip.Stretch%2A> d’un contrôle <xref:System.Windows.Forms.ToolStrip> la valeur `true`, le contrôle remplit son conteneur de bout en bout, puis se redimensionne quand son conteneur est redimensionné.</span><span class="sxs-lookup"><span data-stu-id="f9775-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="f9775-104">Dans cette configuration, il peut s’avérer utile d’étirer un élément dans le contrôle, tel qu’un <xref:System.Windows.Forms.ToolStripTextBox>, de remplir l’espace disponible et de le redimensionner lorsque le contrôle est redimensionné.</span><span class="sxs-lookup"><span data-stu-id="f9775-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="f9775-105">Cet étirement est utile, par exemple, si vous souhaitez obtenir une apparence et un comportement similaires à la barre d’adresses dans Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f9775-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9775-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9775-106">Example</span></span>  
 <span data-ttu-id="f9775-107">L’exemple de code suivant fournit une classe dérivée de <xref:System.Windows.Forms.ToolStripTextBox> appelée `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="f9775-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="f9775-108">Cette classe substitue la méthode <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> pour calculer la largeur disponible du contrôle <xref:System.Windows.Forms.ToolStrip> parent après la soustraction de la largeur combinée de tous les autres éléments.</span><span class="sxs-lookup"><span data-stu-id="f9775-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="f9775-109">Cet exemple de code fournit également une classe <xref:System.Windows.Forms.Form> et une classe `Program` pour illustrer le nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="f9775-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f9775-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f9775-110">Compiling the Code</span></span>  
 <span data-ttu-id="f9775-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f9775-111">This example requires:</span></span>  
  
- <span data-ttu-id="f9775-112">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f9775-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9775-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9775-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f9775-114">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f9775-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="f9775-115">Guide pratique pour utiliser la propriété Spring dans un StatusStrip de manière interactive</span><span class="sxs-lookup"><span data-stu-id="f9775-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
