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
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="bca4a-102">Vue d'ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="bca4a-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="bca4a-103">Ce sujet donne un aperçu <xref:System.Windows.Shapes.Shape> de la façon de dessiner avec des objets.</span><span class="sxs-lookup"><span data-stu-id="bca4a-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="bca4a-104">A <xref:System.Windows.Shapes.Shape> est un <xref:System.Windows.UIElement> type qui vous permet de dessiner une forme à l’écran.</span><span class="sxs-lookup"><span data-stu-id="bca4a-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="bca4a-105">Parce qu’ils sont <xref:System.Windows.Shapes.Shape> des éléments <xref:System.Windows.Controls.Panel> d’interface utilisateur, les objets peuvent être utilisés à l’intérieur des éléments et la plupart des contrôles.</span><span class="sxs-lookup"><span data-stu-id="bca4a-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="bca4a-106">offre plusieurs couches d’accès aux services graphiques et de rendu.</span><span class="sxs-lookup"><span data-stu-id="bca4a-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="bca4a-107">À la couche <xref:System.Windows.Shapes.Shape> supérieure, les objets sont faciles à utiliser et [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournissent de nombreuses fonctionnalités utiles, telles que la mise en page et la participation au système d’événements.</span><span class="sxs-lookup"><span data-stu-id="bca4a-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>
## <a name="shape-objects"></a><span data-ttu-id="bca4a-108">Objets Shape</span><span class="sxs-lookup"><span data-stu-id="bca4a-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="bca4a-109">fournit un certain nombre d’objets prêts à l’emploi. <xref:System.Windows.Shapes.Shape></span><span class="sxs-lookup"><span data-stu-id="bca4a-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="bca4a-110">Tous les objets <xref:System.Windows.Shapes.Shape> de forme héritent de la classe.</span><span class="sxs-lookup"><span data-stu-id="bca4a-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="bca4a-111">Les objets <xref:System.Windows.Shapes.Ellipse>de <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>forme <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>disponibles <xref:System.Windows.Shapes.Rectangle>incluent , , , , et .</span><span class="sxs-lookup"><span data-stu-id="bca4a-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bca4a-112"><xref:System.Windows.Shapes.Shape>les objets partagent les propriétés communes suivantes.</span><span class="sxs-lookup"><span data-stu-id="bca4a-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="bca4a-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Décrit comment le contour de la forme est peint.</span><span class="sxs-lookup"><span data-stu-id="bca4a-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="bca4a-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Décrit l’épaisseur du contour de la forme.</span><span class="sxs-lookup"><span data-stu-id="bca4a-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="bca4a-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Décrit comment l’intérieur de la forme est peint.</span><span class="sxs-lookup"><span data-stu-id="bca4a-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="bca4a-116">Des propriétés de données pour spécifier des coordonnées et des sommets, mesurés en dip (device independent pixel).</span><span class="sxs-lookup"><span data-stu-id="bca4a-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="bca4a-117">Parce qu’ils dérivent de , les objets de <xref:System.Windows.UIElement>forme peuvent être utilisés à l’intérieur des panneaux et la plupart des contrôles.</span><span class="sxs-lookup"><span data-stu-id="bca4a-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="bca4a-118">Le <xref:System.Windows.Controls.Canvas> panneau est un choix particulièrement bon pour créer des dessins complexes car il soutient le positionnement absolu de ses objets pour enfants.</span><span class="sxs-lookup"><span data-stu-id="bca4a-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="bca4a-119">La <xref:System.Windows.Shapes.Line> classe vous permet de tracer une ligne entre deux points.</span><span class="sxs-lookup"><span data-stu-id="bca4a-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="bca4a-120">L’exemple suivant montre plusieurs façons de spécifier les propriétés du trait et les coordonnées de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bca4a-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="bca4a-121">L’image suivante montre <xref:System.Windows.Shapes.Line>le rendu .</span><span class="sxs-lookup"><span data-stu-id="bca4a-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="bca4a-122">![Illustration d'une ligne](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="bca4a-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="bca4a-123">Bien <xref:System.Windows.Shapes.Line> que la <xref:System.Windows.Shapes.Shape.Fill%2A> classe ne fournissent une propriété, la mise n’a aucun effet parce qu’un <xref:System.Windows.Shapes.Line> n’a pas de zone.</span><span class="sxs-lookup"><span data-stu-id="bca4a-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="bca4a-124">Une autre forme <xref:System.Windows.Shapes.Ellipse>commune est le .</span><span class="sxs-lookup"><span data-stu-id="bca4a-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="bca4a-125">Créez <xref:System.Windows.Shapes.Ellipse> un en définissant <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> la forme et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="bca4a-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="bca4a-126">Pour dessiner un cercle, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> spécifiez un <xref:System.Windows.Shapes.Ellipse> dont et les valeurs sont égales.</span><span class="sxs-lookup"><span data-stu-id="bca4a-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="bca4a-127">L’image suivante montre un <xref:System.Windows.Shapes.Ellipse>exemple d’un rendu .</span><span class="sxs-lookup"><span data-stu-id="bca4a-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="bca4a-128">![Illustration d'une ellipse](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="bca4a-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a><span data-ttu-id="bca4a-129">Utilisation des tracés et des géométries</span><span class="sxs-lookup"><span data-stu-id="bca4a-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="bca4a-130">La <xref:System.Windows.Shapes.Path> classe vous permet de dessiner des courbes et des formes complexes.</span><span class="sxs-lookup"><span data-stu-id="bca4a-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="bca4a-131">Ces courbes et formes <xref:System.Windows.Media.Geometry> sont décrites à l’aide d’objets.</span><span class="sxs-lookup"><span data-stu-id="bca4a-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="bca4a-132">Pour utiliser <xref:System.Windows.Shapes.Path>un , <xref:System.Windows.Media.Geometry> vous créez un <xref:System.Windows.Shapes.Path> et <xref:System.Windows.Shapes.Path.Data%2A> l’utilisez pour définir la propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="bca4a-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="bca4a-133">Il ya une <xref:System.Windows.Media.Geometry> variété d’objets à choisir.</span><span class="sxs-lookup"><span data-stu-id="bca4a-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="bca4a-134">Les <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>classes <xref:System.Windows.Media.EllipseGeometry> , et décrire des formes relativement simples.</span><span class="sxs-lookup"><span data-stu-id="bca4a-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="bca4a-135">Pour créer des formes plus complexes <xref:System.Windows.Media.PathGeometry>ou créer des courbes, utilisez un .</span><span class="sxs-lookup"><span data-stu-id="bca4a-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="bca4a-136">Éléments PathGeometry et PathSegments</span><span class="sxs-lookup"><span data-stu-id="bca4a-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="bca4a-137"><xref:System.Windows.Media.PathGeometry>les objets sont composés <xref:System.Windows.Media.PathFigure> d’un ou plusieurs objets; chacun <xref:System.Windows.Media.PathFigure> représente une « figure » ou une forme différente.</span><span class="sxs-lookup"><span data-stu-id="bca4a-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="bca4a-138">Chacun <xref:System.Windows.Media.PathFigure> est lui-même composé <xref:System.Windows.Media.PathSegment> d’un ou plusieurs objets, chacun représentant une partie connectée de la figure ou de la forme.</span><span class="sxs-lookup"><span data-stu-id="bca4a-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="bca4a-139">Les types de <xref:System.Windows.Media.LineSegment>segment <xref:System.Windows.Media.BezierSegment>incluent <xref:System.Windows.Media.ArcSegment>ce qui suit : , , et .</span><span class="sxs-lookup"><span data-stu-id="bca4a-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="bca4a-140">Dans l’exemple <xref:System.Windows.Shapes.Path> suivant, un est utilisé pour dessiner une courbe quadratique bézier.</span><span class="sxs-lookup"><span data-stu-id="bca4a-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="bca4a-141">L’illustration suivante montre le rendu de la forme.</span><span class="sxs-lookup"><span data-stu-id="bca4a-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="bca4a-142">![Illustration d’un chemin d’accès](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="bca4a-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="bca4a-143">Pour plus <xref:System.Windows.Media.PathGeometry> d’informations <xref:System.Windows.Media.Geometry> sur et les autres classes, voir la [vue d’ensemble de](geometry-overview.md)géométrie .</span><span class="sxs-lookup"><span data-stu-id="bca4a-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="bca4a-144">Syntaxe XAML abrégée</span><span class="sxs-lookup"><span data-stu-id="bca4a-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="bca4a-145">Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez également utiliser une syntaxe <xref:System.Windows.Shapes.Path>abrégée spéciale pour décrire un .</span><span class="sxs-lookup"><span data-stu-id="bca4a-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="bca4a-146">Dans l’exemple suivant, la syntaxe abrégée est utilisée pour dessiner une forme complexe.</span><span class="sxs-lookup"><span data-stu-id="bca4a-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="bca4a-147">L’image suivante montre <xref:System.Windows.Shapes.Path>un rendu .</span><span class="sxs-lookup"><span data-stu-id="bca4a-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="bca4a-148">![Illustration d’un chemin d’accès](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="bca4a-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="bca4a-149">La <xref:System.Windows.Shapes.Path.Data%2A> chaîne d’attribut commence par la commande "moveto", indiquée par M, qui <xref:System.Windows.Controls.Canvas>établit un point de départ pour le chemin dans le système de coordonnées du .</span><span class="sxs-lookup"><span data-stu-id="bca4a-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="bca4a-150"><xref:System.Windows.Shapes.Path>les paramètres de données sont sensibles aux cas.</span><span class="sxs-lookup"><span data-stu-id="bca4a-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="bca4a-151">La capitale M indique un emplacement absolu pour le nouveau point actuel.</span><span class="sxs-lookup"><span data-stu-id="bca4a-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="bca4a-152">Un m minuscule indiquerait des coordonnées relatives.</span><span class="sxs-lookup"><span data-stu-id="bca4a-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="bca4a-153">Le premier segment est une courbe de Bézier cubique commençant à (100,200) et se terminant à (400,175), tracée en utilisant les deux points de contrôle (100,25) et (400,350).</span><span class="sxs-lookup"><span data-stu-id="bca4a-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="bca4a-154">Ce segment est indiqué par <xref:System.Windows.Shapes.Path.Data%2A> la commande C dans la chaîne d’attribut.</span><span class="sxs-lookup"><span data-stu-id="bca4a-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="bca4a-155">Là encore, le C majuscule indique un tracé absolu ; le c minuscule indiquerait un tracé relatif.</span><span class="sxs-lookup"><span data-stu-id="bca4a-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="bca4a-156">Le deuxième segment commence par une commande H « lineto » horizontale absolue, qui indique une ligne tracée à partir du point de fin du sous-tracé précédent (400,175) vers un nouveau point de fin (280,175).</span><span class="sxs-lookup"><span data-stu-id="bca4a-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="bca4a-157">Étant donné qu’il s’agit d’une commande horizontale de « lineto », la valeur spécifiée est *une*x-coordonnées.</span><span class="sxs-lookup"><span data-stu-id="bca4a-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="bca4a-158">Pour la syntaxe complète <xref:System.Windows.Shapes.Path.Data%2A> du chemin, voir la référence et [créer une forme en utilisant un PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="bca4a-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a><span data-ttu-id="bca4a-159">Peindre des formes</span><span class="sxs-lookup"><span data-stu-id="bca4a-159">Painting Shapes</span></span>  
 <span data-ttu-id="bca4a-160"><xref:System.Windows.Media.Brush>objets sont utilisés pour peindre <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Shapes.Shape.Fill%2A>une forme et .</span><span class="sxs-lookup"><span data-stu-id="bca4a-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="bca4a-161">Dans l’exemple suivant, l’AVC et le remplissage d’un <xref:System.Windows.Shapes.Ellipse> sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bca4a-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="bca4a-162">Notez que les entrées valides pour les propriétés de pinceau peuvent être une valeur de couleur hexadécimale ou un mot clé de couleur.</span><span class="sxs-lookup"><span data-stu-id="bca4a-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="bca4a-163">Pour plus d’informations sur les mots <xref:System.Windows.Media.Colors> clés <xref:System.Windows.Media> de couleur disponibles, voir les propriétés de la classe dans l’espace de nom.</span><span class="sxs-lookup"><span data-stu-id="bca4a-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="bca4a-164">L’image suivante montre <xref:System.Windows.Shapes.Ellipse>le rendu .</span><span class="sxs-lookup"><span data-stu-id="bca4a-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="bca4a-165">![Ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="bca4a-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="bca4a-166">Alternativement, vous pouvez utiliser la syntaxe d’élément de propriété pour créer explicitement un <xref:System.Windows.Media.SolidColorBrush> objet pour peindre la forme avec une couleur solide.</span><span class="sxs-lookup"><span data-stu-id="bca4a-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="bca4a-167">L’illustration suivante montre le rendu de la forme.</span><span class="sxs-lookup"><span data-stu-id="bca4a-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="bca4a-168">![Illustration de SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="bca4a-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="bca4a-169">Vous pouvez également peindre le trait ou le remplissage d’une forme avec des dégradés, des images, des motifs, etc.</span><span class="sxs-lookup"><span data-stu-id="bca4a-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="bca4a-170">Pour plus d’informations, voir la [peinture avec des couleurs solides et Gradients Aperçu](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bca4a-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a><span data-ttu-id="bca4a-171">Formes étirables</span><span class="sxs-lookup"><span data-stu-id="bca4a-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="bca4a-172">Le <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> , et <xref:System.Windows.Shapes.Shape.Stretch%2A> les classes ont tous une propriété.</span><span class="sxs-lookup"><span data-stu-id="bca4a-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="bca4a-173">Cette propriété détermine <xref:System.Windows.Shapes.Shape> comment le contenu d’un objet (la forme <xref:System.Windows.Shapes.Shape> à dessiner) est étiré pour remplir l’espace de disposition de l’objet.</span><span class="sxs-lookup"><span data-stu-id="bca4a-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="bca4a-174">L’espace de mise en page <xref:System.Windows.Shapes.Shape> <xref:System.Windows.Shapes.Shape> d’un objet est la quantité d’espace allouée par le système de mise en page, en raison d’un réglage explicite <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de réglage ou en raison de son <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="bca4a-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="bca4a-175">Pour plus d’informations sur la mise en page de Windows Presentation Foundation, consultez [l’aperçu de la mise en page.](../advanced/layout.md)</span><span class="sxs-lookup"><span data-stu-id="bca4a-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="bca4a-176">La propriété Stretch peut prendre les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="bca4a-176">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="bca4a-177"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet n’est pas étiré.</span><span class="sxs-lookup"><span data-stu-id="bca4a-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="bca4a-178"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet est étiré pour remplir son espace de mise en page.</span><span class="sxs-lookup"><span data-stu-id="bca4a-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="bca4a-179">Les proportions ne sont pas conservées.</span><span class="sxs-lookup"><span data-stu-id="bca4a-179">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="bca4a-180"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet est étiré autant que possible pour remplir son espace de mise en page tout en préservant son rapport d’aspect d’origine.</span><span class="sxs-lookup"><span data-stu-id="bca4a-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="bca4a-181"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Le contenu de l’objet est étiré pour remplir complètement son espace de mise en page tout en préservant son rapport d’aspect d’origine.</span><span class="sxs-lookup"><span data-stu-id="bca4a-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="bca4a-182">Notez que, <xref:System.Windows.Shapes.Shape> lorsque le contenu d’un objet est étiré, le contour de l’objet <xref:System.Windows.Shapes.Shape> est peint après l’étirement.</span><span class="sxs-lookup"><span data-stu-id="bca4a-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="bca4a-183">Dans l’exemple <xref:System.Windows.Shapes.Polygon> suivant, a est utilisé pour dessiner un très petit triangle de (0,0) à (0,1) à (1,1).</span><span class="sxs-lookup"><span data-stu-id="bca4a-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="bca4a-184">L’objet <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> sont réglés à 100, et sa propriété extensible est réglé pour remplir.</span><span class="sxs-lookup"><span data-stu-id="bca4a-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="bca4a-185">En conséquence, <xref:System.Windows.Shapes.Polygon> le contenu de l’objet (le triangle) est étiré pour remplir l’espace plus grand.</span><span class="sxs-lookup"><span data-stu-id="bca4a-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="bca4a-186">Transformer des formes</span><span class="sxs-lookup"><span data-stu-id="bca4a-186">Transforming Shapes</span></span>  
 <span data-ttu-id="bca4a-187">La <xref:System.Windows.Media.Transform> classe fournit les moyens de transformer les formes en un plan bidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="bca4a-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="bca4a-188">Les différents types de<xref:System.Windows.Media.RotateTransform>transformation comprennent<xref:System.Windows.Media.ScaleTransform>la<xref:System.Windows.Media.SkewTransform>rotation (<xref:System.Windows.Media.TranslateTransform>), échelle ( ), biais ( ), et la traduction ( ).</span><span class="sxs-lookup"><span data-stu-id="bca4a-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="bca4a-189">Une transformation courante à appliquer à une forme est la rotation.</span><span class="sxs-lookup"><span data-stu-id="bca4a-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="bca4a-190">Pour faire pivoter <xref:System.Windows.Media.RotateTransform> une forme, créez un et spécez son <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="bca4a-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="bca4a-191">Un <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 tourne l’élément 45 degrés dans le sens des aiguilles d’une montre; un angle de 90 tourne l’élément 90 degrés dans le sens des aiguilles d’une montre; et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="bca4a-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="bca4a-192">Réglez <xref:System.Windows.Media.RotateTransform.CenterY%2A> le et les <xref:System.Windows.Media.RotateTransform.CenterX%2A> propriétés si vous voulez contrôler le point sur lequel l’élément est tourné.</span><span class="sxs-lookup"><span data-stu-id="bca4a-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="bca4a-193">Ces valeurs de propriété sont exprimées dans l’espace de coordonnées de l’élément que vous êtes en train de transformer.</span><span class="sxs-lookup"><span data-stu-id="bca4a-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="bca4a-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A>et <xref:System.Windows.Media.RotateTransform.CenterY%2A> ont des valeurs par défaut de zéro.</span><span class="sxs-lookup"><span data-stu-id="bca4a-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="bca4a-195">Enfin, appliquez l’élément. <xref:System.Windows.Media.RotateTransform></span><span class="sxs-lookup"><span data-stu-id="bca4a-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="bca4a-196">Si vous ne voulez pas que la transformation affecte <xref:System.Windows.UIElement.RenderTransform%2A> la disposition, définissez la propriété de la forme.</span><span class="sxs-lookup"><span data-stu-id="bca4a-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="bca4a-197">Dans l’exemple <xref:System.Windows.Media.RotateTransform> suivant, un est utilisé pour faire pivoter une forme de 45 degrés sur le coin supérieur gauche de la forme (0,0).</span><span class="sxs-lookup"><span data-stu-id="bca4a-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="bca4a-198">Dans l’exemple suivant, une autre forme effectue une rotation de 45 degrés, mais cette fois-ci par rapport au point (25,50).</span><span class="sxs-lookup"><span data-stu-id="bca4a-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="bca4a-199">L’illustration suivante montre les résultats de l’application des deux transformations.</span><span class="sxs-lookup"><span data-stu-id="bca4a-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="bca4a-200">![Rotations de 45 degrés avec différents points centraux](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="bca4a-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="bca4a-201">Dans les exemples précédents, une transformation unique a été appliquée à chaque objet Shape.</span><span class="sxs-lookup"><span data-stu-id="bca4a-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="bca4a-202">Pour appliquer plusieurs transformations en forme (ou tout <xref:System.Windows.Media.TransformGroup>autre élément d’interface utilisateur), utilisez un .</span><span class="sxs-lookup"><span data-stu-id="bca4a-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca4a-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bca4a-203">See also</span></span>

- [<span data-ttu-id="bca4a-204">Graphisme 2D et acquisition d’images</span><span class="sxs-lookup"><span data-stu-id="bca4a-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="bca4a-205">Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="bca4a-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="bca4a-206">Vue d’ensemble de Geometry</span><span class="sxs-lookup"><span data-stu-id="bca4a-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="bca4a-207">Procédure pas à pas : ma première application de bureau WPF</span><span class="sxs-lookup"><span data-stu-id="bca4a-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="bca4a-208">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="bca4a-208">Animation Overview</span></span>](animation-overview.md)
