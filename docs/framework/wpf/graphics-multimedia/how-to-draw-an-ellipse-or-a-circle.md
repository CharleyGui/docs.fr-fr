---
title: 'Comment : dessiner une ellipse ou un cercle'
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452920"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="76e4d-102">Comment : dessiner une ellipse ou un cercle</span><span class="sxs-lookup"><span data-stu-id="76e4d-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="76e4d-103">Cet exemple montre comment dessiner des ellipses et des cercles à l’aide de l’élément <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="76e4d-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="76e4d-104">Pour dessiner une ellipse, créez un élément <xref:System.Windows.Shapes.Ellipse> et spécifiez ses <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="76e4d-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="76e4d-105">Utilisez sa propriété <xref:System.Windows.Shapes.Shape.Fill%2A> pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre l’intérieur de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="76e4d-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="76e4d-106">Utilisez sa propriété <xref:System.Windows.Shapes.Shape.Stroke%2A> pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre le contour de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="76e4d-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="76e4d-107">La propriété <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> spécifie l’épaisseur du contour de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="76e4d-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="76e4d-108">Pour dessiner un cercle, rendez le <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de l’élément <xref:System.Windows.Shapes.Ellipse> égal.</span><span class="sxs-lookup"><span data-stu-id="76e4d-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="76e4d-109">L’exemple suivant dessine quatre éléments <xref:System.Windows.Shapes.Ellipse> dans un <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="76e4d-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76e4d-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="76e4d-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="76e4d-111">Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les points de suspension, vous pouvez utiliser des éléments ellipses (et tous les autres éléments de forme) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="76e4d-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="76e4d-112">Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="76e4d-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e4d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76e4d-113">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="76e4d-114">Élément Shape, exemple</span><span class="sxs-lookup"><span data-stu-id="76e4d-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
