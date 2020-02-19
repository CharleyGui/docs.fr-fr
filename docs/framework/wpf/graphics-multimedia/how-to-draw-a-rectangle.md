---
title: 'Comment : dessiner un rectangle'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452933"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="c1ed3-102">Comment : dessiner un rectangle</span><span class="sxs-lookup"><span data-stu-id="c1ed3-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="c1ed3-103">Cet exemple montre comment dessiner un rectangle à l’aide de l’élément <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="c1ed3-104">Pour dessiner un rectangle, créez un élément <xref:System.Windows.Shapes.Rectangle> et spécifiez ses <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="c1ed3-105">Pour peindre l’intérieur du rectangle, définissez son <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="c1ed3-106">Pour attribuer un contour au rectangle, utilisez ses propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="c1ed3-107">Pour affecter des angles arrondis au rectangle, spécifiez les propriétés facultatives <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="c1ed3-108">Les propriétés <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> définissent les rayons axe x et axe y de l’ellipse utilisée pour arrondir les angles du rectangle.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="c1ed3-109">Dans l’exemple suivant, deux éléments <xref:System.Windows.Shapes.Rectangle> sont dessinés dans une <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="c1ed3-110">Le premier rectangle a une <xref:System.Windows.Media.Brushes.Blue%2A> intérieur.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="c1ed3-111">Le deuxième rectangle a une <xref:System.Windows.Media.Brushes.Blue%2A> intérieur, un contour de <xref:System.Windows.Media.Brushes.Black%2A> et des angles arrondis.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1ed3-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1ed3-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="c1ed3-113">Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les rectangles, vous pouvez utiliser des éléments rectangle (et tous les autres éléments Shape) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="c1ed3-114">En fait, les rectangles sont particulièrement utiles pour fournir des arrière-plans à des portions de panneaux <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c1ed3-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="c1ed3-115">Pour obtenir un exemple, consultez la [vue d’ensemble du tableau](../advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c1ed3-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="c1ed3-116">Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="c1ed3-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ed3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1ed3-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="c1ed3-118">Élément Shape, exemple</span><span class="sxs-lookup"><span data-stu-id="c1ed3-118">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="c1ed3-119">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="c1ed3-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="c1ed3-120">Vue d’ensemble des tables</span><span class="sxs-lookup"><span data-stu-id="c1ed3-120">Table Overview</span></span>](../advanced/table-overview.md)
