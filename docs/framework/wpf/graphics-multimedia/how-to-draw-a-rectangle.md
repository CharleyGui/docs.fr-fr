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
# <a name="how-to-draw-a-rectangle"></a>Comment : dessiner un rectangle
Cet exemple montre comment dessiner un rectangle à l’aide de l’élément <xref:System.Windows.Shapes.Rectangle>.  
  
 Pour dessiner un rectangle, créez un élément <xref:System.Windows.Shapes.Rectangle> et spécifiez ses <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>. Pour peindre l’intérieur du rectangle, définissez son <xref:System.Windows.Shapes.Shape.Fill%2A>. Pour attribuer un contour au rectangle, utilisez ses propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.  
  
 Pour affecter des angles arrondis au rectangle, spécifiez les propriétés facultatives <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>. Les propriétés <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> définissent les rayons axe x et axe y de l’ellipse utilisée pour arrondir les angles du rectangle.  
  
 Dans l’exemple suivant, deux éléments <xref:System.Windows.Shapes.Rectangle> sont dessinés dans une <xref:System.Windows.Controls.Canvas>. Le premier rectangle a une <xref:System.Windows.Media.Brushes.Blue%2A> intérieur. Le deuxième rectangle a une <xref:System.Windows.Media.Brushes.Blue%2A> intérieur, un contour de <xref:System.Windows.Media.Brushes.Black%2A> et des angles arrondis.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les rectangles, vous pouvez utiliser des éléments rectangle (et tous les autres éléments Shape) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel. En fait, les rectangles sont particulièrement utiles pour fournir des arrière-plans à des portions de panneaux <xref:System.Windows.Controls.Grid>. Pour obtenir un exemple, consultez la [vue d’ensemble du tableau](../advanced/table-overview.md).  
  
 Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Rectangle>
- [Élément Shape, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Vue d’ensemble des tables](../advanced/table-overview.md)
