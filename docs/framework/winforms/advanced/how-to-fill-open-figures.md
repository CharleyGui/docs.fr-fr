---
title: 'Procédure : remplir des figures ouvertes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: 6ecea7d3edb0c3e25fb4e69ff12b88019e530021
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506074"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="7c02c-102">Procédure : remplir des figures ouvertes</span><span class="sxs-lookup"><span data-stu-id="7c02c-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="7c02c-103">Vous pouvez remplir un chemin d’accès en passant un <xref:System.Drawing.Drawing2D.GraphicsPath> de l’objet à le <xref:System.Drawing.Graphics.FillPath%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="7c02c-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="7c02c-104">Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage (de substitution ou par balayage) actuellement défini pour le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="7c02c-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="7c02c-105">Si le chemin d’accès comporte des figures ouvertes, le chemin d’accès est rempli comme si ces figures étaient fermées.</span><span class="sxs-lookup"><span data-stu-id="7c02c-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> <span data-ttu-id="7c02c-106">GDI + ferme une figure en dessinant une ligne droite de son point d’arrivée à son point de départ.</span><span class="sxs-lookup"><span data-stu-id="7c02c-106">GDI+ closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c02c-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c02c-107">Example</span></span>  
 <span data-ttu-id="7c02c-108">L’exemple suivant crée un chemin d’accès qui a une figure ouverte (un arc) et une figure fermée (une ellipse).</span><span class="sxs-lookup"><span data-stu-id="7c02c-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="7c02c-109">Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage par défaut, qui est <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="7c02c-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="7c02c-110">L’illustration suivante montre la sortie de l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="7c02c-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="7c02c-111">Notez que le chemin d’accès est rempli (conformément à <xref:System.Drawing.Drawing2D.FillMode.Alternate>) comme si la figure ouverte était fermée par une ligne droite de son point d’arrivée à son point de départ.</span><span class="sxs-lookup"><span data-stu-id="7c02c-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 ![Diagramme qui montre la sortie de la méthode FillPath](./media/how-to-fill-open-figures/fill-path-alternate-mode.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c02c-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7c02c-113">Compiling the Code</span></span>  
 <span data-ttu-id="7c02c-114">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="7c02c-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c02c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c02c-115">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="7c02c-116">Tracés graphiques dans GDI+</span><span class="sxs-lookup"><span data-stu-id="7c02c-116">Graphics Paths in GDI+</span></span>](graphics-paths-in-gdi.md)
