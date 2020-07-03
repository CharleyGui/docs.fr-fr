---
title: Vue d’ensemble des formes et des dessins de base
description: Améliorez votre interface utilisateur avec des formes prêtes à l’emploi et plusieurs couches de services de rendu en Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 41d8f2b87232740c8945bd6a6099aa86dbe77bc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853697"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Vue d'ensemble des formes et dessins de base dans WPF
Cette rubrique donne une vue d’ensemble de la façon de dessiner avec des <xref:System.Windows.Shapes.Shape> objets. Un <xref:System.Windows.Shapes.Shape> est un type de <xref:System.Windows.UIElement> qui vous permet de dessiner une forme à l’écran. Étant donné qu’il s’agit d’éléments d’interface utilisateur, les <xref:System.Windows.Shapes.Shape> objets peuvent être utilisés à l’intérieur d' <xref:System.Windows.Controls.Panel> éléments et de la plupart des contrôles.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre plusieurs couches d’accès aux services graphiques et de rendu. Au niveau de la couche supérieure, les <xref:System.Windows.Shapes.Shape> objets sont faciles à utiliser et fournissent de nombreuses fonctionnalités utiles, telles que la disposition et la participation au [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] système d’événements.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Objets Shape  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un certain nombre d’objets prêts à l’emploi <xref:System.Windows.Shapes.Shape> .  Tous les objets de forme héritent de la <xref:System.Windows.Shapes.Shape> classe. Les objets de forme disponibles incluent <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.Shapes.Line> , <xref:System.Windows.Shapes.Path> , <xref:System.Windows.Shapes.Polygon> , <xref:System.Windows.Shapes.Polyline> et <xref:System.Windows.Shapes.Rectangle> . <xref:System.Windows.Shapes.Shape>les objets partagent les propriétés communes suivantes.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Décrit la façon dont le contour de la forme est peint.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Décrit l’épaisseur du contour de la forme.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Décrit comment l’intérieur de la forme est peint.  
  
- Des propriétés de données pour spécifier des coordonnées et des sommets, mesurés en dip (device independent pixel).  
  
 Étant donné qu’ils dérivent de <xref:System.Windows.UIElement> , les objets Shape peuvent être utilisés dans les panneaux et la plupart des contrôles. Le <xref:System.Windows.Controls.Canvas> panneau est un bon choix pour créer des dessins complexes, car il prend en charge le positionnement absolu de ses objets enfants.  
  
 La <xref:System.Windows.Shapes.Line> classe vous permet de dessiner une ligne entre deux points. L’exemple suivant montre plusieurs façons de spécifier les propriétés du trait et les coordonnées de la ligne.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 L’illustration suivante montre le rendu <xref:System.Windows.Shapes.Line> .  
  
 ![Illustration d'une ligne](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Bien que la <xref:System.Windows.Shapes.Line> classe fournisse une <xref:System.Windows.Shapes.Shape.Fill%2A> propriété, son paramétrage n’a aucun effet, car un n' <xref:System.Windows.Shapes.Line> a aucune zone.  
  
 Une autre forme courante est <xref:System.Windows.Shapes.Ellipse> .  Créez un <xref:System.Windows.Shapes.Ellipse> en définissant les propriétés et de la forme <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> . Pour dessiner un cercle, spécifiez un <xref:System.Windows.Shapes.Ellipse> dont <xref:System.Windows.FrameworkElement.Width%2A> les <xref:System.Windows.FrameworkElement.Height%2A> valeurs et sont égales.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 L’image suivante montre un exemple d’un rendu <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Illustration d'une ellipse](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Utilisation des tracés et des géométries  
 La <xref:System.Windows.Shapes.Path> classe vous permet de dessiner des courbes et des formes complexes. Ces courbes et formes sont décrites à l’aide d' <xref:System.Windows.Media.Geometry> objets. Pour utiliser un <xref:System.Windows.Shapes.Path> , vous devez créer un <xref:System.Windows.Media.Geometry> et l’utiliser pour définir la <xref:System.Windows.Shapes.Path> propriété de l’objet <xref:System.Windows.Shapes.Path.Data%2A> .  
  
 Vous avez le <xref:System.Windows.Media.Geometry> choix entre plusieurs objets. Les <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry> classes, et <xref:System.Windows.Media.EllipseGeometry> décrivent des formes relativement simples. Pour créer des formes plus complexes ou créer des courbes, utilisez un <xref:System.Windows.Media.PathGeometry> .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>Éléments PathGeometry et PathSegments  
 <xref:System.Windows.Media.PathGeometry>les objets sont constitués d’un ou de plusieurs <xref:System.Windows.Media.PathFigure> objets, chacun <xref:System.Windows.Media.PathFigure> représentant une forme ou une « figure » différente. Chaque <xref:System.Windows.Media.PathFigure> se compose d’un ou plusieurs <xref:System.Windows.Media.PathSegment> objets, chacun représentant une partie connectée de la figure ou de la forme. Les types de segment sont les suivants : <xref:System.Windows.Media.LineSegment> , <xref:System.Windows.Media.BezierSegment> et <xref:System.Windows.Media.ArcSegment> .  
  
 Dans l’exemple suivant, un <xref:System.Windows.Shapes.Path> est utilisé pour dessiner une courbe de Bézier quadratique.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 L’illustration suivante montre le rendu de la forme.  
  
 ![Illustration d’un chemin d’accès](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Pour plus d’informations sur <xref:System.Windows.Media.PathGeometry> et les autres <xref:System.Windows.Media.Geometry> classes, consultez [vue d’ensemble](geometry-overview.md)de la géométrie.  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Syntaxe XAML abrégée  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , vous pouvez également utiliser une syntaxe abrégée spéciale pour décrire un <xref:System.Windows.Shapes.Path> . Dans l’exemple suivant, la syntaxe abrégée est utilisée pour dessiner une forme complexe.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 L’illustration suivante montre un rendu <xref:System.Windows.Shapes.Path> .  
  
 ![Illustration d’un chemin d’accès](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 La <xref:System.Windows.Shapes.Path.Data%2A> chaîne d’attribut commence par la commande « MoveTo », indiquée par M, qui établit un point de départ pour le chemin d’accès dans le système de coordonnées de <xref:System.Windows.Controls.Canvas> . <xref:System.Windows.Shapes.Path>les paramètres de données respectent la casse. Le M majuscule indique un emplacement absolu pour le nouveau point actuel. Un m minuscule indiquerait des coordonnées relatives. Le premier segment est une courbe de Bézier cubique commençant à (100,200) et se terminant à (400,175), tracée en utilisant les deux points de contrôle (100,25) et (400,350). Ce segment est indiqué par la commande C dans la <xref:System.Windows.Shapes.Path.Data%2A> chaîne d’attribut. Là encore, le C majuscule indique un tracé absolu ; le c minuscule indiquerait un tracé relatif.  
  
 Le deuxième segment commence par une commande H « lineto » horizontale absolue, qui indique une ligne tracée à partir du point de fin du sous-tracé précédent (400,175) vers un nouveau point de fin (280,175). Étant donné qu’il s’agit d’une commande « LineTo » horizontale, la valeur spécifiée est une coordonnée *x*.  
  
 Pour connaître la syntaxe de chemin d’accès complète, consultez la <xref:System.Windows.Shapes.Path.Data%2A> référence et [créez une forme à l’aide d’un PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Peindre des formes  
 <xref:System.Windows.Media.Brush>les objets sont utilisés pour peindre <xref:System.Windows.Shapes.Shape.Stroke%2A> les et les d’une forme <xref:System.Windows.Shapes.Shape.Fill%2A> . Dans l’exemple suivant, le trait et le remplissage d’un <xref:System.Windows.Shapes.Ellipse> sont spécifiés. Notez que les entrées valides pour les propriétés de pinceau peuvent être une valeur de couleur hexadécimale ou un mot clé de couleur. Pour plus d’informations sur les mots clés de couleur disponibles, consultez Propriétés de la <xref:System.Windows.Media.Colors> classe dans l' <xref:System.Windows.Media> espace de noms.  
  
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
  
 L’illustration suivante montre le rendu <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Vous pouvez également utiliser la syntaxe d’élément de propriété pour créer explicitement un <xref:System.Windows.Media.SolidColorBrush> objet afin de peindre la forme avec une couleur unie.  
  
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
  
 Vous pouvez également peindre le trait ou le remplissage d’une forme avec des dégradés, des images, des motifs, etc. Pour plus d’informations, consultez [vue d’ensemble de la peinture avec des couleurs unies et des dégradés](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Formes étirables  
 Les <xref:System.Windows.Shapes.Line> classes,,, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> et <xref:System.Windows.Shapes.Rectangle> ont toutes une <xref:System.Windows.Shapes.Shape.Stretch%2A> propriété. Cette propriété détermine la façon dont <xref:System.Windows.Shapes.Shape> le contenu d’un objet (la forme à dessiner) est étiré pour remplir l' <xref:System.Windows.Shapes.Shape> espace de disposition de l’objet. L' <xref:System.Windows.Shapes.Shape> espace de disposition d’un objet correspond à la quantité d’espace <xref:System.Windows.Shapes.Shape> allouée par le système de disposition, en raison d’un explicite et d’un <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> paramètre ou de ses <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> paramètres et. Pour plus d’informations sur la disposition dans Windows Presentation Foundation, consultez vue d’ensemble de la [disposition](../advanced/layout.md) .  
  
 La propriété Stretch peut prendre les valeurs suivantes :  
  
- <xref:System.Windows.Media.Stretch.None>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet n’est pas étiré.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet est étiré pour remplir son espace de disposition.  Les proportions ne sont pas conservées.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet est étiré autant que possible pour remplir son espace de disposition tout en conservant ses proportions d’origine.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet est étiré pour remplir complètement son espace de disposition tout en conservant ses proportions d’origine.  
  
 Notez que, lorsque le <xref:System.Windows.Shapes.Shape> contenu d’un objet est étiré, le <xref:System.Windows.Shapes.Shape> contour de l’objet est peint après l’étirement.  
  
 Dans l’exemple suivant, un <xref:System.Windows.Shapes.Polygon> est utilisé pour dessiner un très petit triangle de (0,0) à (0, 1) à (1,1). L' <xref:System.Windows.Shapes.Polygon> objet <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> ont la valeur 100, et sa propriété Stretch est définie sur Fill. Par conséquent, le <xref:System.Windows.Shapes.Polygon> contenu de l’objet (le triangle) est étiré pour remplir l’espace le plus grand.  
  
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
 La <xref:System.Windows.Media.Transform> classe fournit les moyens de transformer des formes dans un plan à deux dimensions.  Les différents types de transformations incluent la rotation (), la mise à l' <xref:System.Windows.Media.RotateTransform> échelle ( <xref:System.Windows.Media.ScaleTransform> ), l’inclinaison ( <xref:System.Windows.Media.SkewTransform> ) et la translation ( <xref:System.Windows.Media.TranslateTransform> ).  
  
 Une transformation courante à appliquer à une forme est la rotation.  Pour faire pivoter une forme, créez un <xref:System.Windows.Media.RotateTransform> et spécifiez son <xref:System.Windows.Media.RotateTransform.Angle%2A> . Un <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 fait pivoter l’élément de 45 degrés dans le sens des aiguilles d’une montre ; un angle de 90 fait pivoter l’élément de 90 degrés dans le sens horaire, et ainsi de suite. Définissez les <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> Propriétés et si vous souhaitez contrôler le point de rotation de l’élément. Ces valeurs de propriété sont exprimées dans l’espace de coordonnées de l’élément que vous êtes en train de transformer. <xref:System.Windows.Media.RotateTransform.CenterX%2A>et <xref:System.Windows.Media.RotateTransform.CenterY%2A> ont des valeurs par défaut égales à zéro. Enfin, appliquez le <xref:System.Windows.Media.RotateTransform> à l’élément. Si vous ne souhaitez pas que la transformation affecte la disposition, définissez la propriété de la forme <xref:System.Windows.UIElement.RenderTransform%2A> .  
  
 Dans l’exemple suivant, un <xref:System.Windows.Media.RotateTransform> est utilisé pour faire pivoter une forme de 45 degrés à partir du coin supérieur gauche de la forme (0,0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Dans l’exemple suivant, une autre forme effectue une rotation de 45 degrés, mais cette fois-ci par rapport au point (25,50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 L’illustration suivante montre les résultats de l’application des deux transformations.  
  
 ![Rotations de 45 degrés avec différents points centraux](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Dans les exemples précédents, une transformation unique a été appliquée à chaque objet Shape. Pour appliquer plusieurs transformations à une forme (ou à tout autre élément d’interface utilisateur), utilisez un <xref:System.Windows.Media.TransformGroup> .  
  
## <a name="see-also"></a>Voir aussi

- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Vue d'ensemble de Geometry](geometry-overview.md)
- [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Vue d'ensemble de l'animation](animation-overview.md)
