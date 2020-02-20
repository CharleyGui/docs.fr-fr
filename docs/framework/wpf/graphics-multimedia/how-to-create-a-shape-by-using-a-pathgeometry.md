---
title: "Comment : créer une forme à l'aide d'un PathGeometry"
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452043"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Comment : créer une forme à l'aide d'un PathGeometry
Cet exemple montre comment créer une forme à l’aide de la classe <xref:System.Windows.Media.PathGeometry>. les objets <xref:System.Windows.Media.PathGeometry> se composent d’un ou plusieurs objets <xref:System.Windows.Media.PathFigure> ; chaque <xref:System.Windows.Media.PathFigure> représente une forme ou un « figure » différent. Chaque <xref:System.Windows.Media.PathFigure> est elle-même composée d’un ou plusieurs objets <xref:System.Windows.Media.PathSegment>, chacun représentant une partie connectée de la figure ou de la forme. Les types de segments incluent <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>et <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une <xref:System.Windows.Media.PathGeometry> pour créer un triangle. Le <xref:System.Windows.Media.PathGeometry> s’affiche à l’aide d’un élément <xref:System.Windows.Shapes.Path>.  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 L’illustration suivante montre la forme créée dans l’exemple précédent.  
  
 ![Une PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
Triangle créé avec un PathGeometry  
  
 L’exemple précédent a montré comment créer une forme relativement simple, un triangle. Un <xref:System.Windows.Media.PathGeometry> peut également être utilisé pour créer des formes plus complexes, y compris des arcs et des courbes. Pour obtenir des exemples, consultez [créer un arc elliptique](how-to-create-an-elliptical-arc.md), [créer une courbe de Bézier cubique](how-to-create-a-cubic-bezier-curve.md)et [créer une courbe de Bézier quadratique](how-to-create-a-quadratic-bezier-curve.md).  
  
 Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Vue d’ensemble de Geometry](geometry-overview.md)
- [Geometry, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
