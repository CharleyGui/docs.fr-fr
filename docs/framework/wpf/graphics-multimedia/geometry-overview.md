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
ms.openlocfilehash: ff42e59edd9d98b0b52dc3bdd3ace0c35df60878
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112373"
---
# <a name="geometry-overview"></a>Vue d'ensemble de Geometry
Cette vue d’ensemble [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> décrit comment utiliser les classes pour décrire les formes. Ce sujet contraste également avec <xref:System.Windows.Media.Geometry> les <xref:System.Windows.Shapes.Shape> différences entre les objets et les éléments.  

<a name="wcpsdk_graphics_geometry_introduction"></a>
## <a name="what-is-a-geometry"></a>Qu’est-ce qu’une géométrie ?  
 La <xref:System.Windows.Media.Geometry> classe et les classes qui <xref:System.Windows.Media.EllipseGeometry>en <xref:System.Windows.Media.PathGeometry>dérivent, telles que , , et <xref:System.Windows.Media.CombinedGeometry>, vous permettent de décrire la géométrie d’une forme 2D. Ces descriptions géométriques ont de nombreuses utilisations, telles que la définition d’une forme à peindre à l’écran ou la définition d’un test de positionnement et de zones de découpage. Vous pouvez également utiliser une géométrie pour définir un tracé d’animation.  
  
 <xref:System.Windows.Media.Geometry>les objets peuvent être simples, tels que des rectangles et des cercles, ou composites, créés à partir de deux objets de géométrie ou plus.  Des géométries plus complexes peuvent <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> être créées en utilisant les et les classes, ce qui vous permet de décrire les arcs et les courbes.  
  
 Parce <xref:System.Windows.Media.Geometry> qu’un <xref:System.Windows.Freezable>est <xref:System.Windows.Media.Geometry> un type de , les objets fournissent plusieurs caractéristiques spéciales: ils peuvent être déclarés comme [des ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, faits en lecture seulement pour améliorer les performances, clonés, et fait thread-safe. Pour plus d’informations sur <xref:System.Windows.Freezable> les différentes fonctionnalités fournies par les objets, voir le [Aperçu des objets freezable](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>
## <a name="geometries-vs-shapes"></a>Géométries vs Formes  
 Les <xref:System.Windows.Media.Geometry> <xref:System.Windows.Shapes.Shape> classes et les classes semblent similaires en <xref:System.Windows.Media.EllipseGeometry> ce <xref:System.Windows.Shapes.Ellipse> qu’elles décrivent toutes les deux des formes 2D (comparer et par exemple), mais il y a des différences importantes.  
  
 D’une <xref:System.Windows.Media.Geometry> part, la <xref:System.Windows.Freezable> classe hérite de la classe tandis que la <xref:System.Windows.Shapes.Shape> classe hérite de <xref:System.Windows.FrameworkElement>. Parce qu’ils <xref:System.Windows.Shapes.Shape> sont des éléments, les objets <xref:System.Windows.Media.Geometry> peuvent se rendre et participer au système de mise en page, tandis que les objets ne peuvent pas.  
  
 Bien <xref:System.Windows.Shapes.Shape> que les objets soient <xref:System.Windows.Media.Geometry> plus <xref:System.Windows.Media.Geometry> facilement utilisables que les objets, les objets sont plus polyvalents. Alors <xref:System.Windows.Shapes.Shape> qu’un objet est utilisé pour <xref:System.Windows.Media.Geometry> rendre des graphiques 2D, un objet peut être utilisé pour définir la région géométrique pour les graphiques 2D, définir une région pour la coupure, ou définir une région pour les tests à succès, par exemple.  
  
### <a name="the-path-shape"></a>La forme Tracé  
 Un <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> la classe, <xref:System.Windows.Media.Geometry> utilise en fait un pour décrire son contenu. En <xref:System.Windows.Shapes.Path.Data%2A> définissant la <xref:System.Windows.Shapes.Path> propriété <xref:System.Windows.Media.Geometry> de <xref:System.Windows.Shapes.Shape.Fill%2A> l’avec un et le réglage de son et <xref:System.Windows.Shapes.Shape.Stroke%2A> ses propriétés, vous pouvez rendre un <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>
## <a name="common-properties-that-take-a-geometry"></a>Propriétés courantes qui acceptent une géométrie  
 Dans les sections précédentes, il était indiqué que les objets géométriques peuvent être utilisés avec d’autres objets pour diverses raisons, telles que le dessin de formes, l’animation et le découpage. Le tableau suivant répertorie plusieurs <xref:System.Windows.Media.Geometry> classes qui ont des propriétés qui prennent un objet.  
  
|Type|Propriété|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>
## <a name="simple-geometry-types"></a>Types de géométrie simples  
 La classe de base pour toutes <xref:System.Windows.Media.Geometry>les géométries est la classe abstraite .  Les classes qui <xref:System.Windows.Media.Geometry> dérivent de la classe peuvent être regroupées à peu près en trois catégories : géométries simples, géométries de chemin et géométries composites.  
  
 Les classes de <xref:System.Windows.Media.LineGeometry>géométrie <xref:System.Windows.Media.RectangleGeometry>simple <xref:System.Windows.Media.EllipseGeometry> incluent, et sont utilisées pour créer des formes géométriques de base, telles que des lignes, des rectangles et des cercles.  
  
- A <xref:System.Windows.Media.LineGeometry> est défini en spécifiant le point de départ de la ligne et le point final.  
  
- A <xref:System.Windows.Media.RectangleGeometry> est défini <xref:System.Windows.Rect> avec une structure qui spécifie sa position relative et sa hauteur et sa largeur. Vous pouvez créer un rectangle <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> arrondi en définissant le et les propriétés.  
  
- Un <xref:System.Windows.Media.EllipseGeometry> est défini par un point central, un rayon x et un y-radius.  Les exemples suivants montrent comment créer des géométries simples pour le rendu et le découpage.  
  
 Ces mêmes formes, ainsi que des formes plus <xref:System.Windows.Media.PathGeometry> complexes, peuvent être créées à l’aide d’un ou en combinant des objets de géométrie ensemble, mais ces classes fournissent un moyen plus simple pour produire ces formes géométriques de base.  
  
 L’exemple suivant montre comment <xref:System.Windows.Media.LineGeometry>créer et rendre un .  Comme indiqué précédemment, un <xref:System.Windows.Media.Geometry> objet est incapable de <xref:System.Windows.Shapes.Path> se dessiner, de sorte que l’exemple utilise une forme pour rendre la ligne.  Étant donné qu’une ligne <xref:System.Windows.Shapes.Shape.Fill%2A> n’a pas de superficie, l’établissement de la propriété de la <xref:System.Windows.Shapes.Path> n’aurait aucun effet; au lieu <xref:System.Windows.Shapes.Shape.Stroke%2A> de <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> cela, seules les propriétés et les propriétés sont spécifiées. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Une LineGeometry tracée de (10,20) à (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 L’exemple suivant montre comment <xref:System.Windows.Media.EllipseGeometry>créer et rendre un .  Les exemples <xref:System.Windows.Media.EllipseGeometry.Center%2A> définit <xref:System.Windows.Media.EllipseGeometry> le de `50,50` l’est réglé au point et le `50`rayon x et le y-radius sont tous deux réglés à , ce qui crée un cercle d’un diamètre de 100.  L’intérieur de l’ellipse est peint en attribuant une valeur <xref:System.Windows.Media.Brushes.Gold%2A>à la propriété Fill de l’élément Path, dans ce cas. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Une EllipseGeometry dessinée à (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 L’exemple suivant montre comment <xref:System.Windows.Media.RectangleGeometry>créer et rendre un .  La position et les dimensions du <xref:System.Windows.Rect> rectangle sont définies par une structure. La position est définie sur `50,50` et la hauteur et la largeur sont définies sur `25`, ce qui crée un carré. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Une RectangleGeometry dessinée à 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 L’exemple suivant montre <xref:System.Windows.Media.EllipseGeometry> comment utiliser une région comme la région clip pour une image.  Un <xref:System.Windows.Controls.Image> objet est <xref:System.Windows.FrameworkElement.Width%2A> défini avec un de <xref:System.Windows.FrameworkElement.Height%2A> 200 et un de 150.  Une <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> valeur de 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> une valeur de 75, et une <xref:System.Windows.Media.EllipseGeometry.Center%2A> valeur de 100,75 est fixé à la <xref:System.Windows.UIElement.Clip%2A> propriété de l’image.  Seule la partie de l’image qui se trouve dans la zone de l’ellipse s’affiche. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une image avec et sans découpage](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Une EllipseGeometry utilisée pour découper une commande Image  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>
## <a name="path-geometries"></a>Géométries de tracés  
 La <xref:System.Windows.Media.PathGeometry> classe et son <xref:System.Windows.Media.StreamGeometry> équivalent léger, la classe, fournissent les moyens de décrire plusieurs figures complexes composées d’arcs, de courbes et de lignes.  
  
 Au cœur <xref:System.Windows.Media.PathGeometry> d’une <xref:System.Windows.Media.PathFigure> collection d’objets, ainsi nommé parce que <xref:System.Windows.Media.PathGeometry>chaque figure décrit une forme discrète dans le . Chacun <xref:System.Windows.Media.PathFigure> est lui-même composé <xref:System.Windows.Media.PathSegment> d’un ou plusieurs objets, dont chacun décrit un segment de la figure.  
  
 Il existe un grand nombre de segments.  
  
|Type de segment|Description|Exemple|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Crée un arc elliptique entre deux points.|[Créez un arc elliptique](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Crée une courbe de Bézier cubique entre deux points.|[Créez une courbe de Bézier Cub .](how-to-create-a-cubic-bezier-curve.md)|  
|<xref:System.Windows.Media.LineSegment>|Crée une ligne entre deux points.|[Créer un LineSegment dans une PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Crée une série de courbes de Bézier cubiques.|Voir <xref:System.Windows.Media.PolyBezierSegment> la page de type.|  
|<xref:System.Windows.Media.PolyLineSegment>|Crée une série de lignes.|Voir <xref:System.Windows.Media.PolyLineSegment> la page de type.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Crée une série de courbes de Bézier quadratiques.|Voir <xref:System.Windows.Media.PolyQuadraticBezierSegment> la page.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Crée une courbe de Bézier quadratique.|[Créez une courbe quadratique de Bézier.](how-to-create-a-quadratic-bezier-curve.md)|  
  
 Les segments <xref:System.Windows.Media.PathFigure> au sein d’un sont combinés en une seule forme géométrique avec le point final de chaque segment étant le point de départ du segment suivant. La <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriété <xref:System.Windows.Media.PathFigure> d’un précise le point à partir duquel le premier segment est dessiné. Chaque segment suivant démarre à l’extrémité du segment précédent. Par exemple, une `10,50` ligne `10,150` verticale de à <xref:System.Windows.Media.PathFigure.StartPoint%2A> partir `10,50` peut <xref:System.Windows.Media.LineSegment> être <xref:System.Windows.Media.LineSegment.Point%2A> définie en `10,150`fixant la propriété à et en créant un avec un cadre de propriété de .  
  
 L’exemple suivant <xref:System.Windows.Media.PathGeometry> crée un simple <xref:System.Windows.Media.PathFigure> composé <xref:System.Windows.Media.LineSegment> d’un <xref:System.Windows.Shapes.Path> single avec un et l’affiche à l’aide d’un élément. L’objet <xref:System.Windows.Media.PathFigure> <xref:System.Windows.Media.PathFigure.StartPoint%2A> est réglé `10,20` et <xref:System.Windows.Media.LineSegment> a est défini `100,130`avec un point final de . L’illustration suivante <xref:System.Windows.Media.PathGeometry> montre la création de cet exemple.  
  
 ![Une LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Une PathGeometry contenant un seul LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Il convient de comparer cet <xref:System.Windows.Media.LineGeometry> exemple avec l’exemple précédent.  La syntaxe <xref:System.Windows.Media.PathGeometry> utilisée pour un est beaucoup plus <xref:System.Windows.Media.LineGeometry>verbeux que celle utilisée <xref:System.Windows.Media.LineGeometry> pour un simple , et il peut <xref:System.Windows.Media.PathGeometry> être plus logique d’utiliser la classe dans ce cas, mais la syntaxe verbeuse de la permet des régions géométriques extrêmement complexes et complexes.  
  
 Des géométries plus complexes peuvent être <xref:System.Windows.Media.PathSegment> créées à l’aide d’une combinaison d’objets.  
  
 L’exemple suivant <xref:System.Windows.Media.BezierSegment>utilise <xref:System.Windows.Media.LineSegment>un <xref:System.Windows.Media.ArcSegment> , un , et un pour créer la forme. L’exemple crée d’abord une courbe cubique de Bézier est en définissant quatre points<xref:System.Windows.Media.BezierSegment.Point3%2A>: un point<xref:System.Windows.Media.BezierSegment.Point1%2A> de <xref:System.Windows.Media.BezierSegment.Point2%2A>départ, qui est le point final du segment précédent, un point final (), et deux points de contrôle (et ).  Les deux points de contrôle d’une courbe de Bézier cubique se comportent comme des aimants qui attirent vers eux des parties de ce qui devrait normalement être une ligne droite, produisant ainsi une courbe. Le premier point <xref:System.Windows.Media.BezierSegment.Point1%2A>de contrôle, , affecte la partie de début de la courbe; le deuxième point <xref:System.Windows.Media.BezierSegment.Point2%2A>de contrôle, , affecte la partie de fin de la courbe.  
  
 L’exemple ajoute <xref:System.Windows.Media.LineSegment>ensuite un , qui est <xref:System.Windows.Media.BezierSegment> dessiné entre le point final <xref:System.Windows.Media.LineSegment> du précédent qui l’a précédé au point spécifié par sa propriété.  
  
 L’exemple ajoute <xref:System.Windows.Media.ArcSegment>ensuite un , qui est <xref:System.Windows.Media.LineSegment> tiré du point <xref:System.Windows.Media.ArcSegment.Point%2A> final de la précédente au point spécifié par sa propriété. L’exemple spécifie également le x et<xref:System.Windows.Media.ArcSegment.Size%2A>le y-radius de l’arc (), un angle de rotation (),<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>un drapeau indiquant la taille de l’angle de l’arc résultant (),<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>et une valeur indiquant dans quelle direction l’arc est dessiné (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). L’illustration suivante montre la forme créée par cet exemple.  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Des géométries encore plus complexes <xref:System.Windows.Media.PathFigure> peuvent être <xref:System.Windows.Media.PathGeometry>créées en utilisant plusieurs objets dans un .  
  
 L’exemple suivant <xref:System.Windows.Media.PathGeometry> crée <xref:System.Windows.Media.PathFigure> un avec deux <xref:System.Windows.Media.PathSegment> objets, dont chacun contient plusieurs objets.  L’exemple <xref:System.Windows.Media.PathFigure> ci-dessus <xref:System.Windows.Media.PathFigure> et <xref:System.Windows.Media.PolyLineSegment> un <xref:System.Windows.Media.QuadraticBezierSegment> avec a et a sont utilisés.  A <xref:System.Windows.Media.PolyLineSegment> est défini avec un <xref:System.Windows.Media.QuadraticBezierSegment> tableau de points et le est défini avec un point de contrôle et un point final. L’illustration suivante montre la forme créée par cet exemple.  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry avec plusieurs figures  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Comme <xref:System.Windows.Media.PathGeometry> la classe, un <xref:System.Windows.Media.StreamGeometry> définit une forme géométrique complexe qui peut contenir des courbes, des arcs et des lignes. Contrairement <xref:System.Windows.Media.PathGeometry>à un , <xref:System.Windows.Media.StreamGeometry> le contenu d’un ne supportent pas la liaison de données, l’animation, ou la modification. Utilisez <xref:System.Windows.Media.StreamGeometry> un lorsque vous avez besoin de décrire une géométrie complexe, mais ne veulent pas les frais généraux de la liaison de données à l’appui, l’animation, ou la modification. En raison de <xref:System.Windows.Media.StreamGeometry> son efficacité, la classe est un bon choix pour décrire les adorateurs.  
  
 Pour obtenir un exemple, consultez [Créer une forme à l’aide d’une StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Syntaxe XAML pour les tracés  
 Les <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> types et [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] les types prennent en charge une syntaxe d’attribut à l’aide d’une série spéciale de commandes de mouvement et de tirage. Pour plus d’informations, consultez [Syntaxe XAML pour les tracés](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>
## <a name="composite-geometries"></a>Géométries composites  
 Des objets de géométrie composite <xref:System.Windows.Media.GeometryGroup>peuvent <xref:System.Windows.Media.CombinedGeometry>être créés à <xref:System.Windows.Media.Geometry> <xref:System.Windows.Media.Geometry.Combine%2A>l’aide d’un , un , ou en appelant la méthode statique .  
  
- L’objet <xref:System.Windows.Media.CombinedGeometry> <xref:System.Windows.Media.Geometry.Combine%2A> et la méthode effectue une opération Boolean pour combiner la zone définie par deux géométries. <xref:System.Windows.Media.Geometry>les objets qui n’ont pas de zone sont jetés. Seuls <xref:System.Windows.Media.Geometry> deux objets peuvent être combinés (bien que ces deux géométries puissent également être des géométries composites).  
  
- La <xref:System.Windows.Media.GeometryGroup> classe crée un <xref:System.Windows.Media.Geometry> amalgame des objets qu’elle contient sans combiner leur zone. N’importe <xref:System.Windows.Media.Geometry> quel nombre d’objets peuvent être ajoutés à un <xref:System.Windows.Media.GeometryGroup>. Pour obtenir un exemple, consultez [Créer une forme composite](how-to-create-a-composite-shape.md).  
  
 Parce qu’ils n’effectuent <xref:System.Windows.Media.GeometryGroup> pas une opération <xref:System.Windows.Media.CombinedGeometry> de <xref:System.Windows.Media.Geometry.Combine%2A> moissonneuse-batteuse, l’utilisation d’objets offre des avantages de performance sur l’utilisation d’objets ou de la méthode.  
  
<a name="combindgeometriessection"></a>
## <a name="combined-geometries"></a>Géométries combinées  
 La section précédente <xref:System.Windows.Media.CombinedGeometry> mentionnait <xref:System.Windows.Media.Geometry.Combine%2A> l’objet et la méthode combine la zone définie par les géométries qu’ils contiennent. L’énumération <xref:System.Windows.Media.GeometryCombineMode> précise comment les géométries sont combinées. Les valeurs possibles <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> pour <xref:System.Windows.Media.GeometryCombineMode.Union>la <xref:System.Windows.Media.GeometryCombineMode.Intersect> <xref:System.Windows.Media.GeometryCombineMode.Exclude>propriété <xref:System.Windows.Media.GeometryCombineMode.Xor>sont: , , , et .  
  
 Dans l’exemple <xref:System.Windows.Media.CombinedGeometry> suivant, un est défini avec un mode de combine de l’Union.  Les <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> deux <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> et les sont définis comme des cercles du même rayon, mais avec des centres décalés par 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Résultats du mode de combinaison Union](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 Dans l’exemple <xref:System.Windows.Media.CombinedGeometry> suivant, un est <xref:System.Windows.Media.GeometryCombineMode.Xor>défini avec un mode de combinaison de .  Les <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> deux <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> et les sont définis comme des cercles du même rayon, mais avec des centres décalés par 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Résultats du mode de combinaison Xor](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Pour obtenir des exemples supplémentaires, consultez [Créer une forme composite](how-to-create-a-composite-shape.md) et [Créer une géométrie combinée](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Fonctionnalités Freezable  
 Parce qu’il <xref:System.Windows.Freezable> hérite <xref:System.Windows.Media.Geometry> de la classe, <xref:System.Windows.Media.Geometry> la classe fournit plusieurs caractéristiques spéciales: les objets peuvent être déclarés comme [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, faits en lecture seulement pour améliorer les performances, cloné, et fait thread-safe. Pour plus d’informations sur <xref:System.Windows.Freezable> les différentes fonctionnalités fournies par les objets, voir le [Aperçu des objets freezable](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>
## <a name="other-geometry-features"></a>Autres fonctionnalités de géométrie  
 La <xref:System.Windows.Media.Geometry> classe fournit également des méthodes d’utilité utiles, telles que les suivantes :  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>- Obtient la <xref:System.Windows.Media.Geometry>zone de la .  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>- Détermine si la géométrie <xref:System.Windows.Media.Geometry>en contient une autre .  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>- Détermine si le <xref:System.Windows.Media.Geometry> trait d’un contient un point spécifié.  
  
 Consultez <xref:System.Windows.Media.Geometry> la classe pour une liste complète de ses méthodes.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Syntaxe XAML pour les tracés](path-markup-syntax.md)
- [Sujets comment se passer](geometries-how-to-topics.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Vue d'ensemble des objets Drawing](drawing-objects-overview.md)
