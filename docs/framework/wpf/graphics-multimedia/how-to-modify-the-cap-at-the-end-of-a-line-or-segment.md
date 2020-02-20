---
title: "Comment : modifier l'embout à la fin d'une ligne ou d'un segment"
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452777"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Comment : modifier l'embout à la fin d'une ligne ou d'un segment
Cet exemple montre comment modifier la forme au début ou à la fin d’un élément <xref:System.Windows.Shapes.Shape> ouvert. Pour modifier l’extrémité au début d’un <xref:System.Windows.Shapes.Shape>ouvert, utilisez sa propriété <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>. Pour modifier l’extrémité à la fin d’un <xref:System.Windows.Shapes.Shape>ouvert, utilisez sa propriété <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>. Pour afficher les embouts de ligne disponibles, consultez l’énumération <xref:System.Windows.Media.PenLineCap>.  
  
> [!NOTE]
> Cette propriété affecte uniquement une forme ouverte, telle qu’une <xref:System.Windows.Shapes.Line>, un <xref:System.Windows.Shapes.Polyline>ou un élément <xref:System.Windows.Shapes.Path> ouvert.  
  
 L’exemple suivant dessine quatre <xref:System.Windows.Shapes.Polyline> éléments et utilise un ensemble de formes différent à la fin de chacune d’elles.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
