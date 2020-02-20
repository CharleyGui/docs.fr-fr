---
title: 'Comment : créer une courbe de Bézier cubique'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452108"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Comment : créer une courbe de Bézier cubique
Cet exemple montre comment créer une courbe de Bézier cubique. Pour créer une courbe de Bézier cubique, utilisez les classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>et <xref:System.Windows.Media.BezierSegment>.  Pour afficher la géométrie résultante, utilisez un élément <xref:System.Windows.Shapes.Path>, ou utilisez-le avec un <xref:System.Windows.Media.GeometryDrawing> ou un <xref:System.Windows.Media.DrawingContext>. Dans les exemples suivants, une courbe de Bézier cubique est dessinée de (10 100) à (300, 100). La courbe a des points de contrôle de (100, 0) et (200, 200).  
  
## <a name="example"></a>Exemple  
 [xaml]  
  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe abrégée des balises pour décrire un chemin d’accès.  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également dessiner une courbe de Bézier cubique à l’aide de balises d’objet. L'exemple suivant est équivalent à l’exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Voir aussi

- [Créer un arc elliptique](how-to-create-an-elliptical-arc.md)
- [Créer un LineSegment dans une PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [Créer une courbe de Bézier cubique](how-to-create-a-cubic-bezier-curve.md)
- [Créer une courbe de Bézier quadratique](how-to-create-a-quadratic-bezier-curve.md)
