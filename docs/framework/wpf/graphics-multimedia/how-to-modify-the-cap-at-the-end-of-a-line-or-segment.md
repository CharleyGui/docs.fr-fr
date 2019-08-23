---
title: 'Procédure : Modifier l’extrémité de fin d’une ligne ou d’un segment'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916131"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Procédure : Modifier l’extrémité de fin d’une ligne ou d’un segment
Cet exemple montre comment modifier la forme au début ou à la fin d’un élément <xref:System.Windows.Shapes.Shape> ouvert. Pour modifier l’extrémité au début d’une ouverture <xref:System.Windows.Shapes.Shape>, utilisez sa <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> propriété. Pour modifier l’extrémité à la fin d’une ouverture <xref:System.Windows.Shapes.Shape>, utilisez sa <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> propriété. Pour afficher les embouts de ligne disponibles <xref:System.Windows.Media.PenLineCap> , consultez l’énumération.  
  
> [!NOTE]
> Cette propriété affecte uniquement une forme ouverte, telle qu’un <xref:System.Windows.Shapes.Line>, un <xref:System.Windows.Shapes.Polyline>ou un élément Open <xref:System.Windows.Shapes.Path> .  
  
 L’exemple suivant dessine <xref:System.Windows.Shapes.Polyline> quatre éléments et utilise un ensemble de formes différent à la fin de chaque.  
  
## <a name="example"></a>Exemples  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Cet exemple fait partie d’un exemple plus grand; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
