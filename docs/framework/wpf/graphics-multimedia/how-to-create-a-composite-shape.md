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
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="b9dbb-102">Comment : créer une forme composite</span><span class="sxs-lookup"><span data-stu-id="b9dbb-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="b9dbb-103">Cet exemple montre comment créer des formes composites à l’aide d’objets <xref:System.Windows.Media.Geometry> et les afficher à l’aide d’un élément <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="b9dbb-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="b9dbb-104">Dans l’exemple suivant, un <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>et un <xref:System.Windows.Media.RectangleGeometry> sont utilisés avec un <xref:System.Windows.Media.GeometryGroup> pour créer une forme composite.</span><span class="sxs-lookup"><span data-stu-id="b9dbb-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="b9dbb-105">Les géométries sont ensuite dessinées à l’aide d’un élément <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="b9dbb-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9dbb-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9dbb-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="b9dbb-107">L’illustration suivante montre la forme créée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="b9dbb-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="b9dbb-108">![Géométrie composite créée à l’aide de GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="b9dbb-108">![A composite geometry created using a GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="b9dbb-109">Géométrie composite</span><span class="sxs-lookup"><span data-stu-id="b9dbb-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="b9dbb-110">Des formes plus complexes, telles que des polygones et des formes avec des segments incurvés, peuvent être créées à l’aide d’un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="b9dbb-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="b9dbb-111">Pour obtenir un exemple illustrant comment créer une forme à l’aide d’un <xref:System.Windows.Media.PathGeometry>, consultez [créer une forme à l’aide d’un PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="b9dbb-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="b9dbb-112">Bien que cet exemple restitue une forme à l’écran à l’aide d’un élément <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Media.Geometry> objets peuvent également être utilisés pour décrire le contenu d’un <xref:System.Windows.Media.GeometryDrawing> ou d’un <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="b9dbb-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="b9dbb-113">Ils peuvent également être utilisés pour le découpage et le test de positionnement.</span><span class="sxs-lookup"><span data-stu-id="b9dbb-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="b9dbb-114">Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="b9dbb-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>
