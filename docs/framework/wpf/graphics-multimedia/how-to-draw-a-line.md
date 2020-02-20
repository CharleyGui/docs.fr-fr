---
title: 'Comment : dessiner une ligne'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452946"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="d6fb3-102">Comment : dessiner une ligne</span><span class="sxs-lookup"><span data-stu-id="d6fb3-102">How to: Draw a Line</span></span>
<span data-ttu-id="d6fb3-103">Cet exemple montre comment dessiner des lignes à l’aide de l’élément <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="d6fb3-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="d6fb3-104">Pour dessiner une ligne, créez un élément <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="d6fb3-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="d6fb3-105">Utilisez ses propriétés <xref:System.Windows.Shapes.Line.X1%2A> et <xref:System.Windows.Shapes.Line.Y1%2A> pour définir son point de départ. et utilisent ses propriétés <xref:System.Windows.Shapes.Line.X2%2A> et <xref:System.Windows.Shapes.Line.Y2%2A> pour définir son point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d6fb3-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="d6fb3-106">Enfin, définissez ses <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>, car une ligne sans trait est invisible.</span><span class="sxs-lookup"><span data-stu-id="d6fb3-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="d6fb3-107">La définition de l’élément <xref:System.Windows.Shapes.Shape.Fill%2A> pour une ligne n’a aucun effet, car une ligne n’a pas d’intérieur.</span><span class="sxs-lookup"><span data-stu-id="d6fb3-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="d6fb3-108">L’exemple suivant dessine trois lignes à l’intérieur d’un élément <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="d6fb3-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6fb3-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="d6fb3-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="d6fb3-110">Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="d6fb3-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fb3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6fb3-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="d6fb3-112">Élément Shape, exemple</span><span class="sxs-lookup"><span data-stu-id="d6fb3-112">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
