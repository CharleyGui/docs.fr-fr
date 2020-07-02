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
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Comment : dessiner une ellipse ou un cercle
Cet exemple montre comment dessiner des ellipses et des cercles à l’aide de l' <xref:System.Windows.Shapes.Ellipse> élément. Pour dessiner une ellipse, créez un <xref:System.Windows.Shapes.Ellipse> élément et spécifiez son <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> . Utilisez sa <xref:System.Windows.Shapes.Shape.Fill%2A> propriété pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre l’intérieur de l’ellipse. Utilisez sa <xref:System.Windows.Shapes.Shape.Stroke%2A> propriété pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre le contour de l’ellipse. La <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriété spécifie l’épaisseur du contour de l’ellipse.  
  
 Pour dessiner un cercle, faites en sorte que les <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de l' <xref:System.Windows.Shapes.Ellipse> élément soient égaux.  
  
 L’exemple suivant dessine quatre <xref:System.Windows.Shapes.Ellipse> éléments dans un <xref:System.Windows.Controls.Canvas> .  
  
## <a name="example"></a>Exemple  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les points de suspension, vous pouvez utiliser des éléments ellipse (et tous les autres éléments de forme) avec n’importe quel élément <xref:System.Windows.Controls.Panel> ou prenant <xref:System.Windows.Controls.Control> en charge le contenu non textuel.  
  
 Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Élément Shape, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
