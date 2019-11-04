---
title: Vue d'ensemble de Geometry
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
ms.openlocfilehash: f45c13e1af9bc2d1f75da11b13a2c03936b136c1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455009"
---
# <a name="geometry-overview"></a>Vue d'ensemble de Geometry
Cette vue d’ensemble explique comment utiliser les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> pour décrire les formes. Cette rubrique compare également les différences entre les objets <xref:System.Windows.Media.Geometry> et les éléments <xref:System.Windows.Shapes.Shape>.  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Qu’est-ce qu’une géométrie ?  
 La classe <xref:System.Windows.Media.Geometry> et les classes qui en dérivent, telles que <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>et <xref:System.Windows.Media.CombinedGeometry>, vous permettent de décrire la géométrie d’une forme 2D. Ces descriptions géométriques ont de nombreuses utilisations, telles que la définition d’une forme à peindre à l’écran ou la définition d’un test de positionnement et de zones de découpage. Vous pouvez également utiliser une géométrie pour définir un tracé d’animation.  
  
 les objets <xref:System.Windows.Media.Geometry> peuvent être simples, tels que des rectangles et des cercles, ou composites, créés à partir de deux objets géométriques ou plus.  Vous pouvez créer des géométries plus complexes à l’aide des classes <xref:System.Windows.Media.PathGeometry> et <xref:System.Windows.Media.StreamGeometry>, qui vous permettent de décrire des arcs et des courbes.  
  
 Étant donné qu’un <xref:System.Windows.Media.Geometry> est un type de <xref:System.Windows.Freezable>, les objets <xref:System.Windows.Media.Geometry> fournissent plusieurs fonctionnalités spéciales : ils peuvent être déclarés en tant que [ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, mis en lecture seule pour améliorer les performances, clonés et rendus thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Géométries et formes  
 Les classes <xref:System.Windows.Media.Geometry> et <xref:System.Windows.Shapes.Shape> semblent similaires en ce sens qu’elles décrivent toutes les deux des formes 2D (comparer <xref:System.Windows.Media.EllipseGeometry> et <xref:System.Windows.Shapes.Ellipse> par exemple), mais il existe des différences importantes.  
  
 Pour un, la classe <xref:System.Windows.Media.Geometry> hérite de la classe <xref:System.Windows.Freezable>, tandis que la classe <xref:System.Windows.Shapes.Shape> hérite de <xref:System.Windows.FrameworkElement>. Étant donné qu’il s’agit d’éléments, <xref:System.Windows.Shapes.Shape> objets peuvent s’afficher et participer au système de disposition, contrairement aux objets <xref:System.Windows.Media.Geometry>.  
  
 Bien que les objets <xref:System.Windows.Shapes.Shape> soient plus facilement utilisables que les objets <xref:System.Windows.Media.Geometry>, les objets <xref:System.Windows.Media.Geometry> sont plus polyvalents. Lorsqu’un objet <xref:System.Windows.Shapes.Shape> est utilisé pour restituer des graphiques 2D, un objet <xref:System.Windows.Media.Geometry> peut être utilisé pour définir la région géométrique pour les graphiques 2D, définir une région pour le découpage ou définir une région pour le test de positionnement, par exemple.  
  
### <a name="the-path-shape"></a>La forme Tracé  
 L’une <xref:System.Windows.Shapes.Shape>, la classe <xref:System.Windows.Shapes.Path>, utilise en fait un <xref:System.Windows.Media.Geometry> pour décrire son contenu. En définissant la propriété <xref:System.Windows.Shapes.Path.Data%2A> du <xref:System.Windows.Shapes.Path> avec un <xref:System.Windows.Media.Geometry> et en définissant ses propriétés <xref:System.Windows.Shapes.Shape.Fill%2A> et <xref:System.Windows.Shapes.Shape.Stroke%2A>, vous pouvez restituer une <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Propriétés courantes qui acceptent une géométrie  
 Dans les sections précédentes, il était indiqué que les objets géométriques peuvent être utilisés avec d’autres objets pour diverses raisons, telles que le dessin de formes, l’animation et le découpage. Le tableau suivant répertorie plusieurs classes qui ont des propriétés qui acceptent un objet <xref:System.Windows.Media.Geometry>.  
  
|Tapez|Property|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Types de géométrie simples  
 La classe de base pour toutes les géométries est la classe abstraite <xref:System.Windows.Media.Geometry>.  Les classes qui dérivent de la classe <xref:System.Windows.Media.Geometry> peuvent être regroupées en trois catégories : géométries simples, géométries de tracés et géométries composites.  
  
 Les classes Geometry simples incluent <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>et <xref:System.Windows.Media.EllipseGeometry> et sont utilisées pour créer des formes géométriques de base, telles que des lignes, des rectangles et des cercles.  
  
- Une <xref:System.Windows.Media.LineGeometry> est définie en spécifiant le point de départ de la ligne et le point de terminaison.  
  
- Une <xref:System.Windows.Media.RectangleGeometry> est définie avec une structure <xref:System.Windows.Rect> qui spécifie sa position relative et sa hauteur et sa largeur. Vous pouvez créer un rectangle arrondi en définissant les propriétés <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> et <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>.  
  
- Un <xref:System.Windows.Media.EllipseGeometry> est défini par un point central, un rayon x et un rayon y.  Les exemples suivants montrent comment créer des géométries simples pour le rendu et le découpage.  
  
 Ces mêmes formes, ainsi que des formes plus complexes, peuvent être créées à l’aide d’un <xref:System.Windows.Media.PathGeometry> ou en combinant des objets Geometry, mais ces classes fournissent un moyen plus simple de produire ces formes géométriques de base.  
  
 L’exemple suivant montre comment créer et restituer un <xref:System.Windows.Media.LineGeometry>.  Comme indiqué précédemment, un objet <xref:System.Windows.Media.Geometry> ne peut pas se dessiner lui-même. l’exemple utilise donc une forme <xref:System.Windows.Shapes.Path> pour effectuer le rendu de la ligne.  Comme une ligne n’a pas de zone, la définition de la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de l' <xref:System.Windows.Shapes.Path> n’aurait aucun effet. au lieu de cela, seules les propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> sont spécifiées. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Une LineGeometry tracée de (10,20) à (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 L’exemple suivant montre comment créer et restituer un <xref:System.Windows.Media.EllipseGeometry>.  Les exemples définissent la <xref:System.Windows.Media.EllipseGeometry.Center%2A> du <xref:System.Windows.Media.EllipseGeometry> est défini sur le point `50,50` et le rayon x et le rayon y sont tous deux définis sur `50`, ce qui crée un cercle avec un diamètre de 100.  L’intérieur de l’ellipse est peint en affectant une valeur à la propriété Fill de l’élément Path, dans ce cas <xref:System.Windows.Media.Brushes.Gold%2A>. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Une EllipseGeometry dessinée à (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 L’exemple suivant montre comment créer et restituer un <xref:System.Windows.Media.RectangleGeometry>.  La position et les dimensions du rectangle sont définies par une structure <xref:System.Windows.Rect>. La position est définie sur `50,50` et la hauteur et la largeur sont définies sur `25`, ce qui crée un carré. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Une RectangleGeometry dessinée à 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 L’exemple suivant montre comment utiliser un <xref:System.Windows.Media.EllipseGeometry> comme zone de découpage pour une image.  Un objet <xref:System.Windows.Controls.Image> est défini avec un <xref:System.Windows.FrameworkElement.Width%2A> de 200 et un <xref:System.Windows.FrameworkElement.Height%2A> de 150.  Une <xref:System.Windows.Media.EllipseGeometry> avec une valeur <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> de 100, une valeur <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> de 75 et une valeur <xref:System.Windows.Media.EllipseGeometry.Center%2A> de 100, 75 est définie sur la propriété <xref:System.Windows.UIElement.Clip%2A> de l’image.  Seule la partie de l’image qui se trouve dans la zone de l’ellipse s’affiche. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une image avec et sans découpage](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Une EllipseGeometry utilisée pour découper une commande Image  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Géométries de tracés  
 La classe <xref:System.Windows.Media.PathGeometry> et son équivalent léger, la classe <xref:System.Windows.Media.StreamGeometry>, fournissent les moyens de décrire plusieurs figures complexes composées d’arcs, de courbes et de lignes.  
  
 Au cœur d’un <xref:System.Windows.Media.PathGeometry> est une collection d’objets <xref:System.Windows.Media.PathFigure>, donc nommés, car chaque figure décrit une forme discrète dans le <xref:System.Windows.Media.PathGeometry>. Chaque <xref:System.Windows.Media.PathFigure> est constituée d’un ou plusieurs objets <xref:System.Windows.Media.PathSegment>, chacun d’eux décrivant un segment de la figure.  
  
 Il existe un grand nombre de segments.  
  
|Type de segment|Description|Exemple|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Crée un arc elliptique entre deux points.|[Créer un arc elliptique](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Crée une courbe de Bézier cubique entre deux points.|[Créer une courbe de Bézier cubique](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Crée une ligne entre deux points.|[Créer un LineSegment dans une PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Crée une série de courbes de Bézier cubiques.|Consultez la page type de <xref:System.Windows.Media.PolyBezierSegment>.|  
|<xref:System.Windows.Media.PolyLineSegment>|Crée une série de lignes.|Consultez la page type de <xref:System.Windows.Media.PolyLineSegment>.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Crée une série de courbes de Bézier quadratiques.|Consultez la page <xref:System.Windows.Media.PolyQuadraticBezierSegment>.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Crée une courbe de Bézier quadratique.|[Créer une courbe de Bézier quadratique](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Les segments d’un <xref:System.Windows.Media.PathFigure> sont combinés en une seule forme géométrique, le point de terminaison de chaque segment étant le point de départ du segment suivant. La propriété <xref:System.Windows.Media.PathFigure.StartPoint%2A> d’un <xref:System.Windows.Media.PathFigure> spécifie le point à partir duquel le premier segment est dessiné. Chaque segment suivant démarre au point de fin du segment précédent. Par exemple, une ligne verticale de `10,50` à `10,150` peut être définie en affectant à la propriété <xref:System.Windows.Media.PathFigure.StartPoint%2A> la valeur `10,50` et en créant un <xref:System.Windows.Media.LineSegment> avec un paramètre de propriété <xref:System.Windows.Media.LineSegment.Point%2A> de `10,150`.  
  
 L’exemple suivant crée une <xref:System.Windows.Media.PathGeometry> simple composée d’une <xref:System.Windows.Media.PathFigure> unique avec un <xref:System.Windows.Media.LineSegment> et l’affiche à l’aide d’un élément <xref:System.Windows.Shapes.Path>. Le <xref:System.Windows.Media.PathFigure.StartPoint%2A> de l’objet <xref:System.Windows.Media.PathFigure> est défini sur `10,20` et une <xref:System.Windows.Media.LineSegment> est définie avec un point de terminaison de `100,130`. L’illustration suivante montre les <xref:System.Windows.Media.PathGeometry> créés par cet exemple.  
  
 ![Une LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Une PathGeometry contenant un seul LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Il est intéressant de comparer cet exemple avec l’exemple de <xref:System.Windows.Media.LineGeometry> précédent.  La syntaxe utilisée pour un <xref:System.Windows.Media.PathGeometry> est beaucoup plus détaillée que celle utilisée pour un <xref:System.Windows.Media.LineGeometry>simple, et il peut être plus judicieux d’utiliser la classe <xref:System.Windows.Media.LineGeometry> dans ce cas, mais la syntaxe détaillée de la <xref:System.Windows.Media.PathGeometry> autorise des régions géométriques extrêmement compliquées et complexes.  
  
 Il est possible de créer des géométries plus complexes à l’aide d’une combinaison d’objets <xref:System.Windows.Media.PathSegment>.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.BezierSegment>, un <xref:System.Windows.Media.LineSegment>et un <xref:System.Windows.Media.ArcSegment> pour créer une forme. L’exemple crée d’abord une courbe de Bézier cubique en définissant quatre points : un point de départ, qui est le point de terminaison du segment précédent, un point de terminaison (<xref:System.Windows.Media.BezierSegment.Point3%2A>) et deux points de contrôle (<xref:System.Windows.Media.BezierSegment.Point1%2A> et <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Les deux points de contrôle d’une courbe de Bézier cubique se comportent comme des aimants qui attirent vers eux des parties de ce qui devrait normalement être une ligne droite, produisant ainsi une courbe. Le premier point de contrôle, <xref:System.Windows.Media.BezierSegment.Point1%2A>, affecte la partie de début de la courbe ; le deuxième point de contrôle, <xref:System.Windows.Media.BezierSegment.Point2%2A>, affecte la partie de fin de la courbe.  
  
 L’exemple ajoute ensuite un <xref:System.Windows.Media.LineSegment>, qui est dessiné entre le point de terminaison de la <xref:System.Windows.Media.BezierSegment> précédente qui l’a précédé jusqu’au point spécifié par sa propriété <xref:System.Windows.Media.LineSegment>.  
  
 L’exemple ajoute ensuite un <xref:System.Windows.Media.ArcSegment>, qui est dessiné à partir du point de terminaison du <xref:System.Windows.Media.LineSegment> précédent jusqu’au point spécifié par sa propriété <xref:System.Windows.Media.ArcSegment.Point%2A>. L’exemple spécifie également les rayons x et y de l’arc (<xref:System.Windows.Media.ArcSegment.Size%2A>), un angle de rotation (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), un indicateur qui spécifie la taille de l’angle de l’arc résultant (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) et une valeur indiquant la direction dans laquelle l’arc est dessiné (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). L’illustration suivante montre la forme créée par cet exemple.  
  
 ![Une PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Vous pouvez créer des géométries encore plus complexes à l’aide de plusieurs objets <xref:System.Windows.Media.PathFigure> au sein d’un <xref:System.Windows.Media.PathGeometry>.  
  
 L’exemple suivant crée une <xref:System.Windows.Media.PathGeometry> avec deux objets <xref:System.Windows.Media.PathFigure>, chacun contenant plusieurs objets <xref:System.Windows.Media.PathSegment>.  Le <xref:System.Windows.Media.PathFigure> de l’exemple ci-dessus et un <xref:System.Windows.Media.PathFigure> avec un <xref:System.Windows.Media.PolyLineSegment> et un <xref:System.Windows.Media.QuadraticBezierSegment> sont utilisés.  Une <xref:System.Windows.Media.PolyLineSegment> est définie avec un tableau de points et la <xref:System.Windows.Media.QuadraticBezierSegment> est définie avec un point de contrôle et un point de terminaison. L’illustration suivante montre la forme créée par cet exemple.  
  
 ![Une PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry avec plusieurs figures  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 À l’instar de la classe <xref:System.Windows.Media.PathGeometry>, un <xref:System.Windows.Media.StreamGeometry> définit une forme géométrique complexe qui peut contenir des courbes, des arcs et des lignes. Contrairement à un <xref:System.Windows.Media.PathGeometry>, le contenu d’un <xref:System.Windows.Media.StreamGeometry> ne prend pas en charge la liaison de données, l’animation ou la modification. Utilisez une <xref:System.Windows.Media.StreamGeometry> lorsque vous devez décrire une géométrie complexe, mais ne souhaitez pas la surcharge liée à la prise en charge de la liaison de données, de l’animation ou de la modification. En raison de son efficacité, la classe <xref:System.Windows.Media.StreamGeometry> est un bon choix pour décrire les ornements.  
  
 Pour obtenir un exemple, consultez [Créer une forme à l’aide d’une StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Syntaxe XAML pour les tracés  
 Les types <xref:System.Windows.Media.PathGeometry> et <xref:System.Windows.Media.StreamGeometry> prennent en charge une syntaxe d’attribut [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] à l’aide d’une série spéciale de commandes Move et Draw. Pour plus d’informations, consultez [Syntaxe XAML pour les tracés](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Géométries composites  
 Les objets Geometry composites peuvent être créés à l’aide d’un <xref:System.Windows.Media.GeometryGroup>, d’un <xref:System.Windows.Media.CombinedGeometry>ou d’un appel de la méthode <xref:System.Windows.Media.Geometry> statique <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
- L’objet <xref:System.Windows.Media.CombinedGeometry> et la méthode <xref:System.Windows.Media.Geometry.Combine%2A> exécutent une opération booléenne pour combiner la zone définie par deux géométries. <xref:System.Windows.Media.Geometry> objets qui n’ont pas de zone sont ignorés. Seuls deux objets <xref:System.Windows.Media.Geometry> peuvent être combinés (bien que ces deux géométries puissent également être des géométries composites).  
  
- La classe <xref:System.Windows.Media.GeometryGroup> crée un amalgame des objets <xref:System.Windows.Media.Geometry> qu’elle contient sans combiner leur zone. Un nombre quelconque d’objets <xref:System.Windows.Media.Geometry> peuvent être ajoutés à une <xref:System.Windows.Media.GeometryGroup>. Pour obtenir un exemple, consultez [Créer une forme composite](how-to-create-a-composite-shape.md).  
  
 Étant donné qu’ils n’effectuent pas d’opération de combinaison, l’utilisation d’objets <xref:System.Windows.Media.GeometryGroup> offre des avantages en matière de performances par rapport à l’utilisation d’objets <xref:System.Windows.Media.CombinedGeometry> ou de la méthode <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Géométries combinées  
 La section précédente a mentionné que l’objet <xref:System.Windows.Media.CombinedGeometry> et la méthode <xref:System.Windows.Media.Geometry.Combine%2A> associent la zone définie par les géométries qu’elles contiennent. L’énumération <xref:System.Windows.Media.GeometryCombineMode> spécifie la manière dont les géométries sont combinées. Les valeurs possibles pour la propriété <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> sont les suivantes : <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>et <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 Dans l’exemple suivant, une <xref:System.Windows.Media.CombinedGeometry> est définie avec le mode combiné Union.  Les <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et les <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définis comme des cercles du même rayon, mais avec les centres décalés de 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Résultats du mode de combinaison Union](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 Dans l’exemple suivant, une <xref:System.Windows.Media.CombinedGeometry> est définie avec un mode combiné de <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Les <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et les <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définis comme des cercles du même rayon, mais avec les centres décalés de 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Résultats du mode de combinaison XOR](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Pour obtenir des exemples supplémentaires, consultez [Créer une forme composite](how-to-create-a-composite-shape.md) et [Créer une géométrie combinée](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Fonctionnalités Freezable  
 Comme elle hérite de la classe <xref:System.Windows.Freezable>, la classe <xref:System.Windows.Media.Geometry> fournit plusieurs fonctionnalités spéciales : les objets <xref:System.Windows.Media.Geometry> peuvent être déclarés en tant que [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, mis en lecture seule pour améliorer les performances, clonés et créés thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Autres fonctionnalités de géométrie  
 La classe <xref:System.Windows.Media.Geometry> fournit également des méthodes utilitaires utiles, telles que les suivantes :  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A> : obtient la zone du <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A> : détermine si la géométrie contient une autre <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A> : détermine si le trait d’un <xref:System.Windows.Media.Geometry> contient un point spécifié.  
  
 Consultez la classe <xref:System.Windows.Media.Geometry> pour obtenir la liste complète de ses méthodes.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Graphiques 2D et acquisition d'images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Syntaxe XAML pour les tracés](path-markup-syntax.md)
- [Rubriques de guide pratique](geometries-how-to-topics.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Vue d’ensemble des objets de dessin](drawing-objects-overview.md)
