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
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Procédure : Dessiner une polyligne à l’aide de l’élément Polyline
Cet exemple montre comment dessiner une polyligne, qui est une série de lignes connectées, à l' <xref:System.Windows.Shapes.Polyline> aide de l’élément.  
  
 Pour dessiner une polyligne, créez <xref:System.Windows.Shapes.Polyline> un élément et utilisez <xref:System.Windows.Shapes.Polyline.Points%2A> sa propriété pour spécifier les sommets de la forme. Enfin, utilisez les <xref:System.Windows.Shapes.Shape.Stroke%2A> propriétés <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> et pour décrire le contour de la polyligne, car une ligne sans trait est invisible.  
  
> [!NOTE]
> Étant donné <xref:System.Windows.Shapes.Polyline> que l’élément n’est pas une forme <xref:System.Windows.Shapes.Shape.Fill%2A> fermée, la propriété n’a aucun effet, même si vous fermez délibérément le contour de la forme. Pour créer une forme fermée avec un <xref:System.Windows.Shapes.Shape.Fill%2A>, utilisez un <xref:System.Windows.Shapes.Polygon> élément.  
  
 L’exemple suivant dessine <xref:System.Windows.Shapes.Polyline> deux éléments à <xref:System.Windows.Controls.Canvas>l’intérieur d’un.  
  
## <a name="example"></a>Exemple  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour points est une liste délimitée par des espaces de paires de coordonnées x et y séparées par des virgules.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Bien que cet exemple utilise <xref:System.Windows.Controls.Canvas> un pour contenir les polylignes, vous pouvez utiliser des éléments Polyline (et tous les autres éléments Shape <xref:System.Windows.Controls.Panel> ) <xref:System.Windows.Controls.Control> avec n’importe quel élément ou prenant en charge le contenu non textuel.  
  
 Cet exemple fait partie d’un exemple plus grand; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Élément Shape, exemple](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
