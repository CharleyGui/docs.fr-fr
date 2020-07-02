---
title: 'Comment : dessiner une ellipse ou un cercle'
description: Découvrez comment dessiner une ellipse ou un cercle avec des choix pour l’épaisseur du contour et la couleur intérieure dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853569"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="f3e88-103">Comment : dessiner une ellipse ou un cercle</span><span class="sxs-lookup"><span data-stu-id="f3e88-103">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="f3e88-104">Cet exemple montre comment dessiner des ellipses et des cercles à l’aide de l' <xref:System.Windows.Shapes.Ellipse> élément.</span><span class="sxs-lookup"><span data-stu-id="f3e88-104">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="f3e88-105">Pour dessiner une ellipse, créez un <xref:System.Windows.Shapes.Ellipse> élément et spécifiez son <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="f3e88-105">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="f3e88-106">Utilisez sa <xref:System.Windows.Shapes.Shape.Fill%2A> propriété pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre l’intérieur de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="f3e88-106">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="f3e88-107">Utilisez sa <xref:System.Windows.Shapes.Shape.Stroke%2A> propriété pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre le contour de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="f3e88-107">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="f3e88-108">La <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriété spécifie l’épaisseur du contour de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="f3e88-108">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="f3e88-109">Pour dessiner un cercle, faites en sorte que les <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de l' <xref:System.Windows.Shapes.Ellipse> élément soient égaux.</span><span class="sxs-lookup"><span data-stu-id="f3e88-109">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="f3e88-110">L’exemple suivant dessine quatre <xref:System.Windows.Shapes.Ellipse> éléments dans un <xref:System.Windows.Controls.Canvas> .</span><span class="sxs-lookup"><span data-stu-id="f3e88-110">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e88-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3e88-111">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="f3e88-112">Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les points de suspension, vous pouvez utiliser des éléments ellipse (et tous les autres éléments de forme) avec n’importe quel élément <xref:System.Windows.Controls.Panel> ou prenant <xref:System.Windows.Controls.Control> en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="f3e88-112">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="f3e88-113">Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="f3e88-113">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e88-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3e88-114">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="f3e88-115">Élément Shape, exemple</span><span class="sxs-lookup"><span data-stu-id="f3e88-115">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
