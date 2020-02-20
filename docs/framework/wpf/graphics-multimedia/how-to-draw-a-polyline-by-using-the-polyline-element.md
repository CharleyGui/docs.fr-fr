---
title: "Comment : dessiner une polyligne à l'aide de l'élément Polyline"
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452959"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="047cd-102">Comment : dessiner une polyligne à l'aide de l'élément Polyline</span><span class="sxs-lookup"><span data-stu-id="047cd-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="047cd-103">Cet exemple montre comment dessiner une polyligne, qui est une série de lignes connectées, à l’aide de l’élément <xref:System.Windows.Shapes.Polyline>.</span><span class="sxs-lookup"><span data-stu-id="047cd-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="047cd-104">Pour dessiner une polyligne, créez un élément <xref:System.Windows.Shapes.Polyline> et utilisez sa propriété <xref:System.Windows.Shapes.Polyline.Points%2A> pour spécifier les sommets de la forme.</span><span class="sxs-lookup"><span data-stu-id="047cd-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="047cd-105">Enfin, utilisez les propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> pour décrire le contour de la polyligne, car une ligne sans trait est invisible.</span><span class="sxs-lookup"><span data-stu-id="047cd-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="047cd-106">Étant donné que l’élément <xref:System.Windows.Shapes.Polyline> n’est pas une forme fermée, la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> n’a aucun effet, même si vous fermez délibérément le contour de la forme.</span><span class="sxs-lookup"><span data-stu-id="047cd-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="047cd-107">Pour créer une forme fermée avec un <xref:System.Windows.Shapes.Shape.Fill%2A>, utilisez un élément <xref:System.Windows.Shapes.Polygon>.</span><span class="sxs-lookup"><span data-stu-id="047cd-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="047cd-108">L’exemple suivant dessine deux éléments <xref:System.Windows.Shapes.Polyline> à l’intérieur d’une <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="047cd-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="047cd-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="047cd-109">Example</span></span>  
 <span data-ttu-id="047cd-110">Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour points est une liste délimitée par des espaces de paires de coordonnées x et y séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="047cd-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="047cd-111">Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les polylignes, vous pouvez utiliser des éléments Polyline (et tous les autres éléments de forme) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="047cd-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="047cd-112">Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="047cd-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047cd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="047cd-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="047cd-114">Élément Shape, exemple</span><span class="sxs-lookup"><span data-stu-id="047cd-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="047cd-115">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="047cd-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
