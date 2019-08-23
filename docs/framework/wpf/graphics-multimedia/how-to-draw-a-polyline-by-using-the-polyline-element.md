---
title: 'Procédure : Dessiner une polyligne à l’aide de l’élément Polyline'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934965"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="0a78e-102">Procédure : Dessiner une polyligne à l’aide de l’élément Polyline</span><span class="sxs-lookup"><span data-stu-id="0a78e-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="0a78e-103">Cet exemple montre comment dessiner une polyligne, qui est une série de lignes connectées, à l' <xref:System.Windows.Shapes.Polyline> aide de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0a78e-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="0a78e-104">Pour dessiner une polyligne, créez <xref:System.Windows.Shapes.Polyline> un élément et utilisez <xref:System.Windows.Shapes.Polyline.Points%2A> sa propriété pour spécifier les sommets de la forme.</span><span class="sxs-lookup"><span data-stu-id="0a78e-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="0a78e-105">Enfin, utilisez les <xref:System.Windows.Shapes.Shape.Stroke%2A> propriétés <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> et pour décrire le contour de la polyligne, car une ligne sans trait est invisible.</span><span class="sxs-lookup"><span data-stu-id="0a78e-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a78e-106">Étant donné <xref:System.Windows.Shapes.Polyline> que l’élément n’est pas une forme <xref:System.Windows.Shapes.Shape.Fill%2A> fermée, la propriété n’a aucun effet, même si vous fermez délibérément le contour de la forme.</span><span class="sxs-lookup"><span data-stu-id="0a78e-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="0a78e-107">Pour créer une forme fermée avec un <xref:System.Windows.Shapes.Shape.Fill%2A>, utilisez un <xref:System.Windows.Shapes.Polygon> élément.</span><span class="sxs-lookup"><span data-stu-id="0a78e-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="0a78e-108">L’exemple suivant dessine <xref:System.Windows.Shapes.Polyline> deux éléments à <xref:System.Windows.Controls.Canvas>l’intérieur d’un.</span><span class="sxs-lookup"><span data-stu-id="0a78e-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a78e-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a78e-109">Example</span></span>  
 <span data-ttu-id="0a78e-110">Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour points est une liste délimitée par des espaces de paires de coordonnées x et y séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="0a78e-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="0a78e-111">Bien que cet exemple utilise <xref:System.Windows.Controls.Canvas> un pour contenir les polylignes, vous pouvez utiliser des éléments Polyline (et tous les autres éléments Shape <xref:System.Windows.Controls.Panel> ) <xref:System.Windows.Controls.Control> avec n’importe quel élément ou prenant en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="0a78e-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="0a78e-112">Cet exemple fait partie d’un exemple plus grand; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="0a78e-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a78e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a78e-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="0a78e-114">Élément Shape, exemple</span><span class="sxs-lookup"><span data-stu-id="0a78e-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="0a78e-115">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="0a78e-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
