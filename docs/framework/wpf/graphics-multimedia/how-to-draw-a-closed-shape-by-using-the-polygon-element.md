---
title: "Comment : dessiner une forme fermée à l'aide de l'élément Polygon"
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452972"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="f8512-102">Comment : dessiner une forme fermée à l'aide de l'élément Polygon</span><span class="sxs-lookup"><span data-stu-id="f8512-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="f8512-103">Cet exemple montre comment dessiner une forme fermée à l’aide de l’élément <xref:System.Windows.Shapes.Polygon>.</span><span class="sxs-lookup"><span data-stu-id="f8512-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="f8512-104">Pour dessiner une forme fermée, créez un élément <xref:System.Windows.Shapes.Polygon> et utilisez sa propriété <xref:System.Windows.Shapes.Polygon.Points%2A> pour spécifier les vertex d’une forme.</span><span class="sxs-lookup"><span data-stu-id="f8512-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="f8512-105">Une ligne est automatiquement dessinée qui connecte le premier et le dernier point.</span><span class="sxs-lookup"><span data-stu-id="f8512-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="f8512-106">Enfin, spécifiez un <xref:System.Windows.Shapes.Shape.Fill%2A>, un <xref:System.Windows.Shapes.Shape.Stroke%2A>ou les deux.</span><span class="sxs-lookup"><span data-stu-id="f8512-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8512-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8512-107">Example</span></span>  
 <span data-ttu-id="f8512-108">Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour points est une liste délimitée par des espaces de paires de coordonnées x et y séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f8512-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="f8512-109">Bien que l’exemple utilise une <xref:System.Windows.Controls.Canvas> pour contenir les polygones, vous pouvez utiliser des éléments Polygon (et tous les autres éléments Shape) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="f8512-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="f8512-110">Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="f8512-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>
