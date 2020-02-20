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
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="34d35-102">Comment : créer une forme à l'aide d'un PathGeometry</span><span class="sxs-lookup"><span data-stu-id="34d35-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="34d35-103">Cet exemple montre comment créer une forme à l’aide de la classe <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="34d35-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="34d35-104">les objets <xref:System.Windows.Media.PathGeometry> se composent d’un ou plusieurs objets <xref:System.Windows.Media.PathFigure> ; chaque <xref:System.Windows.Media.PathFigure> représente une forme ou un « figure » différent.</span><span class="sxs-lookup"><span data-stu-id="34d35-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="34d35-105">Chaque <xref:System.Windows.Media.PathFigure> est elle-même composée d’un ou plusieurs objets <xref:System.Windows.Media.PathSegment>, chacun représentant une partie connectée de la figure ou de la forme.</span><span class="sxs-lookup"><span data-stu-id="34d35-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="34d35-106">Les types de segments incluent <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>et <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="34d35-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d35-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="34d35-107">Example</span></span>  
 <span data-ttu-id="34d35-108">L’exemple suivant utilise une <xref:System.Windows.Media.PathGeometry> pour créer un triangle.</span><span class="sxs-lookup"><span data-stu-id="34d35-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="34d35-109">Le <xref:System.Windows.Media.PathGeometry> s’affiche à l’aide d’un élément <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="34d35-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="34d35-110">L’illustration suivante montre la forme créée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="34d35-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="34d35-111">![Une PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="34d35-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="34d35-112">Triangle créé avec un PathGeometry</span><span class="sxs-lookup"><span data-stu-id="34d35-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="34d35-113">L’exemple précédent a montré comment créer une forme relativement simple, un triangle.</span><span class="sxs-lookup"><span data-stu-id="34d35-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="34d35-114">Un <xref:System.Windows.Media.PathGeometry> peut également être utilisé pour créer des formes plus complexes, y compris des arcs et des courbes.</span><span class="sxs-lookup"><span data-stu-id="34d35-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="34d35-115">Pour obtenir des exemples, consultez [créer un arc elliptique](how-to-create-an-elliptical-arc.md), [créer une courbe de Bézier cubique](how-to-create-a-cubic-bezier-curve.md)et [créer une courbe de Bézier quadratique](how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="34d35-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="34d35-116">Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="34d35-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d35-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34d35-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="34d35-118">Vue d’ensemble de Geometry</span><span class="sxs-lookup"><span data-stu-id="34d35-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="34d35-119">Geometry, exemple</span><span class="sxs-lookup"><span data-stu-id="34d35-119">Geometries Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
