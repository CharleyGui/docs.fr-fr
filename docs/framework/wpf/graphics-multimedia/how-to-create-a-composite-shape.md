---
title: 'Comment : créer une forme composite'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452095"
---
# <a name="how-to-create-a-composite-shape"></a>Comment : créer une forme composite
Cet exemple montre comment créer des formes composites à l’aide d’objets <xref:System.Windows.Media.Geometry> et les afficher à l’aide d’un élément <xref:System.Windows.Shapes.Path>. Dans l’exemple suivant, un <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>et un <xref:System.Windows.Media.RectangleGeometry> sont utilisés avec un <xref:System.Windows.Media.GeometryGroup> pour créer une forme composite. Les géométries sont ensuite dessinées à l’aide d’un élément <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 L’illustration suivante montre la forme créée dans l’exemple précédent.  
  
 ![Géométrie composite créée à l’aide de GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Géométrie composite  
  
 Des formes plus complexes, telles que des polygones et des formes avec des segments incurvés, peuvent être créées à l’aide d’un <xref:System.Windows.Media.PathGeometry>. Pour obtenir un exemple illustrant comment créer une forme à l’aide d’un <xref:System.Windows.Media.PathGeometry>, consultez [créer une forme à l’aide d’un PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  Bien que cet exemple restitue une forme à l’écran à l’aide d’un élément <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Media.Geometry> objets peuvent également être utilisés pour décrire le contenu d’un <xref:System.Windows.Media.GeometryDrawing> ou d’un <xref:System.Windows.Media.DrawingContext>. Ils peuvent également être utilisés pour le découpage et le test de positionnement.  
  
 Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).
