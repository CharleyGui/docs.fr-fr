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
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Comment : dessiner une ellipse ou un cercle
Cet exemple montre comment dessiner des ellipses et des cercles à l’aide de l’élément <xref:System.Windows.Shapes.Ellipse>. Pour dessiner une ellipse, créez un élément <xref:System.Windows.Shapes.Ellipse> et spécifiez ses <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>. Utilisez sa propriété <xref:System.Windows.Shapes.Shape.Fill%2A> pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre l’intérieur de l’ellipse. Utilisez sa propriété <xref:System.Windows.Shapes.Shape.Stroke%2A> pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre le contour de l’ellipse. La propriété <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> spécifie l’épaisseur du contour de l’ellipse.  
  
 Pour dessiner un cercle, rendez le <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de l’élément <xref:System.Windows.Shapes.Ellipse> égal.  
  
 L’exemple suivant dessine quatre éléments <xref:System.Windows.Shapes.Ellipse> dans un <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les points de suspension, vous pouvez utiliser des éléments ellipses (et tous les autres éléments de forme) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.  
  
 Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Élément Shape, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
