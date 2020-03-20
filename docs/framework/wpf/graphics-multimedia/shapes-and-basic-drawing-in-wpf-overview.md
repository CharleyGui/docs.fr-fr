---
title: Formes et aperçu de dessin de base
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: 44104bec478f1fbb10acc0e591af43ea95fecdc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141326"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Vue d'ensemble des formes et dessins de base dans WPF
Ce sujet donne un aperçu <xref:System.Windows.Shapes.Shape> de la façon de dessiner avec des objets. A <xref:System.Windows.Shapes.Shape> est un <xref:System.Windows.UIElement> type qui vous permet de dessiner une forme à l’écran. Parce qu’ils sont <xref:System.Windows.Shapes.Shape> des éléments <xref:System.Windows.Controls.Panel> d’interface utilisateur, les objets peuvent être utilisés à l’intérieur des éléments et la plupart des contrôles.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre plusieurs couches d’accès aux services graphiques et de rendu. À la couche <xref:System.Windows.Shapes.Shape> supérieure, les objets sont faciles à utiliser et [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournissent de nombreuses fonctionnalités utiles, telles que la mise en page et la participation au système d’événements.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Objets Shape  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un certain nombre d’objets prêts à l’emploi. <xref:System.Windows.Shapes.Shape>  Tous les objets <xref:System.Windows.Shapes.Shape> de forme héritent de la classe. Les objets <xref:System.Windows.Shapes.Ellipse>de <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>forme <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>disponibles <xref:System.Windows.Shapes.Rectangle>incluent , , , , et . <xref:System.Windows.Shapes.Shape>les objets partagent les propriétés communes suivantes.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Décrit comment le contour de la forme est peint.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Décrit l’épaisseur du contour de la forme.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Décrit comment l’intérieur de la forme est peint.  
  
- Des propriétés de données pour spécifier des coordonnées et des sommets, mesurés en dip (device independent pixel).  
  
 Parce qu’ils dérivent de , les objets de <xref:System.Windows.UIElement>forme peuvent être utilisés à l’intérieur des panneaux et la plupart des contrôles. Le <xref:System.Windows.Controls.Canvas> panneau est un choix particulièrement bon pour créer des dessins complexes car il soutient le positionnement absolu de ses objets pour enfants.  
  
 La <xref:System.Windows.Shapes.Line> classe vous permet de tracer une ligne entre deux points. L’exemple suivant montre plusieurs façons de spécifier les propriétés du trait et les coordonnées de la ligne.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 L’image suivante montre <xref:System.Windows.Shapes.Line>le rendu .  
  
 ![Illustration d'une ligne](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Bien <xref:System.Windows.Shapes.Line> que la <xref:System.Windows.Shapes.Shape.Fill%2A> classe ne fournissent une propriété, la mise n’a aucun effet parce qu’un <xref:System.Windows.Shapes.Line> n’a pas de zone.  
  
 Une autre forme <xref:System.Windows.Shapes.Ellipse>commune est le .  Créez <xref:System.Windows.Shapes.Ellipse> un en définissant <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> la forme et les propriétés. Pour dessiner un cercle, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> spécifiez un <xref:System.Windows.Shapes.Ellipse> dont et les valeurs sont égales.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 L’image suivante montre un <xref:System.Windows.Shapes.Ellipse>exemple d’un rendu .  
  
 ![Illustration d'une ellipse](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Utilisation des tracés et des géométries  
 La <xref:System.Windows.Shapes.Path> classe vous permet de dessiner des courbes et des formes complexes. Ces courbes et formes <xref:System.Windows.Media.Geometry> sont décrites à l’aide d’objets. Pour utiliser <xref:System.Windows.Shapes.Path>un , <xref:System.Windows.Media.Geometry> vous créez un <xref:System.Windows.Shapes.Path> et <xref:System.Windows.Shapes.Path.Data%2A> l’utilisez pour définir la propriété de l’objet.  
  
 Il ya une <xref:System.Windows.Media.Geometry> variété d’objets à choisir. Les <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>classes <xref:System.Windows.Media.EllipseGeometry> , et décrire des formes relativement simples. Pour créer des formes plus complexes <xref:System.Windows.Media.PathGeometry>ou créer des courbes, utilisez un .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>Éléments PathGeometry et PathSegments  
 <xref:System.Windows.Media.PathGeometry>les objets sont composés <xref:System.Windows.Media.PathFigure> d’un ou plusieurs objets; chacun <xref:System.Windows.Media.PathFigure> représente une « figure » ou une forme différente. Chacun <xref:System.Windows.Media.PathFigure> est lui-même composé <xref:System.Windows.Media.PathSegment> d’un ou plusieurs objets, chacun représentant une partie connectée de la figure ou de la forme. Les types de <xref:System.Windows.Media.LineSegment>segment <xref:System.Windows.Media.BezierSegment>incluent <xref:System.Windows.Media.ArcSegment>ce qui suit : , , et .  
  
 Dans l’exemple <xref:System.Windows.Shapes.Path> suivant, un est utilisé pour dessiner une courbe quadratique bézier.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 L’illustration suivante montre le rendu de la forme.  
  
 ![Illustration d’un chemin d’accès](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Pour plus <xref:System.Windows.Media.PathGeometry> d’informations <xref:System.Windows.Media.Geometry> sur et les autres classes, voir la [vue d’ensemble de](geometry-overview.md)géométrie .  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Syntaxe XAML abrégée  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez également utiliser une syntaxe <xref:System.Windows.Shapes.Path>abrégée spéciale pour décrire un . Dans l’exemple suivant, la syntaxe abrégée est utilisée pour dessiner une forme complexe.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 L’image suivante montre <xref:System.Windows.Shapes.Path>un rendu .  
  
 ![Illustration d’un chemin d’accès](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 La <xref:System.Windows.Shapes.Path.Data%2A> chaîne d’attribut commence par la commande "moveto", indiquée par M, qui <xref:System.Windows.Controls.Canvas>établit un point de départ pour le chemin dans le système de coordonnées du . <xref:System.Windows.Shapes.Path>les paramètres de données sont sensibles aux cas. La capitale M indique un emplacement absolu pour le nouveau point actuel. Un m minuscule indiquerait des coordonnées relatives. Le premier segment est une courbe de Bézier cubique commençant à (100,200) et se terminant à (400,175), tracée en utilisant les deux points de contrôle (100,25) et (400,350). Ce segment est indiqué par <xref:System.Windows.Shapes.Path.Data%2A> la commande C dans la chaîne d’attribut. Là encore, le C majuscule indique un tracé absolu ; le c minuscule indiquerait un tracé relatif.  
  
 Le deuxième segment commence par une commande H « lineto » horizontale absolue, qui indique une ligne tracée à partir du point de fin du sous-tracé précédent (400,175) vers un nouveau point de fin (280,175). Étant donné qu’il s’agit d’une commande horizontale de « lineto », la valeur spécifiée est *une*x-coordonnées.  
  
 Pour la syntaxe complète <xref:System.Windows.Shapes.Path.Data%2A> du chemin, voir la référence et [créer une forme en utilisant un PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Peindre des formes  
 <xref:System.Windows.Media.Brush>objets sont utilisés pour peindre <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Shapes.Shape.Fill%2A>une forme et . Dans l’exemple suivant, l’AVC et le remplissage d’un <xref:System.Windows.Shapes.Ellipse> sont spécifiés. Notez que les entrées valides pour les propriétés de pinceau peuvent être une valeur de couleur hexadécimale ou un mot clé de couleur. Pour plus d’informations sur les mots <xref:System.Windows.Media.Colors> clés <xref:System.Windows.Media> de couleur disponibles, voir les propriétés de la classe dans l’espace de nom.  
  
```xaml
<Canvas Background="LightGray">
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 L’image suivante montre <xref:System.Windows.Shapes.Ellipse>le rendu .  
  
 ![Ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternativement, vous pouvez utiliser la syntaxe d’élément de propriété pour créer explicitement un <xref:System.Windows.Media.SolidColorBrush> objet pour peindre la forme avec une couleur solide.  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 L’illustration suivante montre le rendu de la forme.  
  
 ![Illustration de SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Vous pouvez également peindre le trait ou le remplissage d’une forme avec des dégradés, des images, des motifs, etc. Pour plus d’informations, voir la [peinture avec des couleurs solides et Gradients Aperçu](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Formes étirables  
 Le <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> , et <xref:System.Windows.Shapes.Shape.Stretch%2A> les classes ont tous une propriété. Cette propriété détermine <xref:System.Windows.Shapes.Shape> comment le contenu d’un objet (la forme <xref:System.Windows.Shapes.Shape> à dessiner) est étiré pour remplir l’espace de disposition de l’objet. L’espace de mise en page <xref:System.Windows.Shapes.Shape> <xref:System.Windows.Shapes.Shape> d’un objet est la quantité d’espace allouée par le système de mise en page, en raison d’un réglage explicite <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de réglage ou en raison de son <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> de ses paramètres. Pour plus d’informations sur la mise en page de Windows Presentation Foundation, consultez [l’aperçu de la mise en page.](../advanced/layout.md)  
  
 La propriété Stretch peut prendre les valeurs suivantes :  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet n’est pas étiré.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet est étiré pour remplir son espace de mise en page.  Les proportions ne sont pas conservées.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet est étiré autant que possible pour remplir son espace de mise en page tout en préservant son rapport d’aspect d’origine.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet est étiré pour remplir complètement son espace de mise en page tout en préservant son rapport d’aspect d’origine.  
  
 Notez que, <xref:System.Windows.Shapes.Shape> lorsque le contenu d’un objet est étiré, le contour de l’objet <xref:System.Windows.Shapes.Shape> est peint après l’étirement.  
  
 Dans l’exemple <xref:System.Windows.Shapes.Polygon> suivant, a est utilisé pour dessiner un très petit triangle de (0,0) à (0,1) à (1,1). L’objet <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> sont réglés à 100, et sa propriété extensible est réglé pour remplir. En conséquence, <xref:System.Windows.Shapes.Polygon> le contenu de l’objet (le triangle) est étiré pour remplir l’espace plus grand.  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>
## <a name="transforming-shapes"></a>Transformer des formes  
 La <xref:System.Windows.Media.Transform> classe fournit les moyens de transformer les formes en un plan bidimensionnel.  Les différents types de<xref:System.Windows.Media.RotateTransform>transformation comprennent<xref:System.Windows.Media.ScaleTransform>la<xref:System.Windows.Media.SkewTransform>rotation (<xref:System.Windows.Media.TranslateTransform>), échelle ( ), biais ( ), et la traduction ( ).  
  
 Une transformation courante à appliquer à une forme est la rotation.  Pour faire pivoter <xref:System.Windows.Media.RotateTransform> une forme, créez un et spécez son <xref:System.Windows.Media.RotateTransform.Angle%2A>. Un <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 tourne l’élément 45 degrés dans le sens des aiguilles d’une montre; un angle de 90 tourne l’élément 90 degrés dans le sens des aiguilles d’une montre; et ainsi de suite. Réglez <xref:System.Windows.Media.RotateTransform.CenterY%2A> le et les <xref:System.Windows.Media.RotateTransform.CenterX%2A> propriétés si vous voulez contrôler le point sur lequel l’élément est tourné. Ces valeurs de propriété sont exprimées dans l’espace de coordonnées de l’élément que vous êtes en train de transformer. <xref:System.Windows.Media.RotateTransform.CenterX%2A>et <xref:System.Windows.Media.RotateTransform.CenterY%2A> ont des valeurs par défaut de zéro. Enfin, appliquez l’élément. <xref:System.Windows.Media.RotateTransform> Si vous ne voulez pas que la transformation affecte <xref:System.Windows.UIElement.RenderTransform%2A> la disposition, définissez la propriété de la forme.  
  
 Dans l’exemple <xref:System.Windows.Media.RotateTransform> suivant, un est utilisé pour faire pivoter une forme de 45 degrés sur le coin supérieur gauche de la forme (0,0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Dans l’exemple suivant, une autre forme effectue une rotation de 45 degrés, mais cette fois-ci par rapport au point (25,50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 L’illustration suivante montre les résultats de l’application des deux transformations.  
  
 ![Rotations de 45 degrés avec différents points centraux](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Dans les exemples précédents, une transformation unique a été appliquée à chaque objet Shape. Pour appliquer plusieurs transformations en forme (ou tout <xref:System.Windows.Media.TransformGroup>autre élément d’interface utilisateur), utilisez un .  
  
## <a name="see-also"></a>Voir aussi

- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Vue d’ensemble de Geometry](geometry-overview.md)
- [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
