---
title: 'Comment : dessiner une ligne'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452946"
---
# <a name="how-to-draw-a-line"></a>Comment : dessiner une ligne
Cet exemple montre comment dessiner des lignes à l’aide de l’élément <xref:System.Windows.Shapes.Line>.  
  
 Pour dessiner une ligne, créez un élément <xref:System.Windows.Shapes.Line>. Utilisez ses propriétés <xref:System.Windows.Shapes.Line.X1%2A> et <xref:System.Windows.Shapes.Line.Y1%2A> pour définir son point de départ. et utilisent ses propriétés <xref:System.Windows.Shapes.Line.X2%2A> et <xref:System.Windows.Shapes.Line.Y2%2A> pour définir son point de terminaison. Enfin, définissez ses <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>, car une ligne sans trait est invisible.  
  
 La définition de l’élément <xref:System.Windows.Shapes.Shape.Fill%2A> pour une ligne n’a aucun effet, car une ligne n’a pas d’intérieur.  
  
 L’exemple suivant dessine trois lignes à l’intérieur d’un élément <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Line>
- [Élément Shape, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
