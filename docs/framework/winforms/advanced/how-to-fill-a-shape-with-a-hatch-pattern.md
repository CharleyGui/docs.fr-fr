---
title: 'Comment : remplir une forme avec un motif hachuré'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320055"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="9dd28-102">Comment : remplir une forme avec un motif hachuré</span><span class="sxs-lookup"><span data-stu-id="9dd28-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="9dd28-103">Un motif hachuré est constitué de deux couleurs : une pour l’arrière-plan et une pour les lignes qui forment le modèle sur l’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9dd28-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="9dd28-104">Pour remplir une forme fermée avec un motif hachuré, utilisez un objet <xref:System.Drawing.Drawing2D.HatchBrush>.</span><span class="sxs-lookup"><span data-stu-id="9dd28-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="9dd28-105">L’exemple suivant montre comment remplir une ellipse avec un modèle de hachurage :</span><span class="sxs-lookup"><span data-stu-id="9dd28-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dd28-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="9dd28-106">Example</span></span>  
 <span data-ttu-id="9dd28-107">Le constructeur <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> accepte trois arguments : le style de hachurage, la couleur de la ligne hachurée et la couleur de l’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9dd28-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="9dd28-108">L’argument de style de hachurage peut être n’importe quelle valeur de l’énumération <xref:System.Drawing.Drawing2D.HatchStyle>.</span><span class="sxs-lookup"><span data-stu-id="9dd28-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="9dd28-109">Il y a plus de 50 éléments dans l’énumération <xref:System.Drawing.Drawing2D.HatchStyle> ; quelques-uns de ces éléments sont affichés dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="9dd28-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="9dd28-110">L’illustration suivante montre l’Ellipse remplie.</span><span class="sxs-lookup"><span data-stu-id="9dd28-110">The following illustration shows the filled ellipse.</span></span>  
  
  <span data-ttu-id="9dd28-111">![Capture d’écran de l’apparence d’une Ellipse remplie avec un hachurage.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="9dd28-111">![Screenshot of what an ellipse filled with a hatch pattern looks like.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")</span></span>
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9dd28-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9dd28-112">Compiling the Code</span></span>  
 <span data-ttu-id="9dd28-113">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="9dd28-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd28-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dd28-114">See also</span></span>

- [<span data-ttu-id="9dd28-115">Utilisation d'un pinceau pour remplir des formes</span><span class="sxs-lookup"><span data-stu-id="9dd28-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
