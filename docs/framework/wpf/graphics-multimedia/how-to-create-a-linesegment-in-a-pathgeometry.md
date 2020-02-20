---
title: 'Comment : créer un LineSegment dans un PathGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: fc7fbad1e534988a36d85c55c1b6a8249692ad67
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452082"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a><span data-ttu-id="0d393-102">Comment : créer un LineSegment dans un PathGeometry</span><span class="sxs-lookup"><span data-stu-id="0d393-102">How to: Create a LineSegment in a PathGeometry</span></span>

<span data-ttu-id="0d393-103">Cet exemple indique comment créer un segment de ligne.</span><span class="sxs-lookup"><span data-stu-id="0d393-103">This example shows how to create a line segment.</span></span> <span data-ttu-id="0d393-104">Pour créer un segment de ligne, utilisez les classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>et <xref:System.Windows.Media.LineSegment>.</span><span class="sxs-lookup"><span data-stu-id="0d393-104">To create a line segment, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.LineSegment> classes.</span></span>

## <a name="example"></a><span data-ttu-id="0d393-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d393-105">Example</span></span>

<span data-ttu-id="0d393-106">Les exemples suivants dessinent une <xref:System.Windows.Media.LineSegment> de (10, 50) à (200, 70).</span><span class="sxs-lookup"><span data-stu-id="0d393-106">The following examples draw a <xref:System.Windows.Media.LineSegment> from (10, 50) to (200, 70).</span></span> <span data-ttu-id="0d393-107">L’illustration suivante montre les <xref:System.Windows.Media.LineSegment>résultantes ; un arrière-plan de grille a été ajouté pour afficher le système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="0d393-107">The following illustration shows the resulting <xref:System.Windows.Media.LineSegment>; a grid background was added to show the coordinate system.</span></span>

<span data-ttu-id="0d393-108">![LineSegment dans un PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") LineSegment dessiné de (10, 50) à (200, 70)</span><span class="sxs-lookup"><span data-stu-id="0d393-108">![A LineSegment in a PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") A LineSegment drawn from (10,50) to (200,70)</span></span>

<span data-ttu-id="0d393-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="0d393-109">[xaml]</span></span>

<span data-ttu-id="0d393-110">En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe d’attribut pour décrire un tracé.</span><span class="sxs-lookup"><span data-stu-id="0d393-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use attribute syntax to describe a path.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1"
  Data="M 10,50 L 200,70" />
```

<span data-ttu-id="0d393-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="0d393-111">[xaml]</span></span>

<span data-ttu-id="0d393-112">(Notez que cette syntaxe d’attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, une version plus légère d’une <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0d393-112">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="0d393-113">(Pour plus d’informations, consultez la page [Syntaxe XAML pour les tracés](path-markup-syntax.md).)</span><span class="sxs-lookup"><span data-stu-id="0d393-113">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>

<span data-ttu-id="0d393-114">En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également dessiner un segment de ligne en utilisant la syntaxe d’élément objet.</span><span class="sxs-lookup"><span data-stu-id="0d393-114">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a line segment by using object element syntax.</span></span> <span data-ttu-id="0d393-115">L'exemple suivant est équivalent à l’exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.</span><span class="sxs-lookup"><span data-stu-id="0d393-115">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1">
  <Path.Data>
    <PathGeometry>
      <PathFigure StartPoint="10,50">
        <LineSegment Point="200,70" />
      </PathFigure>
    </PathGeometry>
  </Path.Data>
</Path>
```

```csharp
PathFigure myPathFigure = new PathFigure();
myPathFigure.StartPoint = new Point(10, 50);

LineSegment myLineSegment = new LineSegment();
myLineSegment.Point = new Point(200, 70);

PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();
myPathSegmentCollection.Add(myLineSegment);

myPathFigure.Segments = myPathSegmentCollection;

PathFigureCollection myPathFigureCollection = new PathFigureCollection();
myPathFigureCollection.Add(myPathFigure);

PathGeometry myPathGeometry = new PathGeometry();
myPathGeometry.Figures = myPathFigureCollection;

Path myPath = new Path();
myPath.Stroke = Brushes.Black;
myPath.StrokeThickness = 1;
myPath.Data = myPathGeometry;
```

```vb
Dim myPathFigure As New PathFigure()
myPathFigure.StartPoint = New Point(10, 50)

Dim myLineSegment As New LineSegment()
myLineSegment.Point = New Point(200, 70)

Dim myPathSegmentCollection As New PathSegmentCollection()
myPathSegmentCollection.Add(myLineSegment)

myPathFigure.Segments = myPathSegmentCollection

Dim myPathFigureCollection As New PathFigureCollection()
myPathFigureCollection.Add(myPathFigure)

Dim myPathGeometry As New PathGeometry()
myPathGeometry.Figures = myPathFigureCollection

Dim myPath As New Path()
myPath.Stroke = Brushes.Black
myPath.StrokeThickness = 1
myPath.Data = myPathGeometry
```

<span data-ttu-id="0d393-116">Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="0d393-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d393-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d393-117">See also</span></span>

- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [<span data-ttu-id="0d393-118">Vue d’ensemble de Geometry</span><span class="sxs-lookup"><span data-stu-id="0d393-118">Geometry Overview</span></span>](geometry-overview.md)
