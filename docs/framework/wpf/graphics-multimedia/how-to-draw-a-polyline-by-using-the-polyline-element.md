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
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Comment : dessiner une polyligne à l'aide de l'élément Polyline
Cet exemple montre comment dessiner une polyligne, qui est une série de lignes connectées, à l’aide de l’élément <xref:System.Windows.Shapes.Polyline>.  
  
 Pour dessiner une polyligne, créez un élément <xref:System.Windows.Shapes.Polyline> et utilisez sa propriété <xref:System.Windows.Shapes.Polyline.Points%2A> pour spécifier les sommets de la forme. Enfin, utilisez les propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> pour décrire le contour de la polyligne, car une ligne sans trait est invisible.  
  
> [!NOTE]
> Étant donné que l’élément <xref:System.Windows.Shapes.Polyline> n’est pas une forme fermée, la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> n’a aucun effet, même si vous fermez délibérément le contour de la forme. Pour créer une forme fermée avec un <xref:System.Windows.Shapes.Shape.Fill%2A>, utilisez un élément <xref:System.Windows.Shapes.Polygon>.  
  
 L’exemple suivant dessine deux éléments <xref:System.Windows.Shapes.Polyline> à l’intérieur d’une <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemple  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour points est une liste délimitée par des espaces de paires de coordonnées x et y séparées par des virgules.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les polylignes, vous pouvez utiliser des éléments Polyline (et tous les autres éléments de forme) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.  
  
 Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Élément Shape, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
