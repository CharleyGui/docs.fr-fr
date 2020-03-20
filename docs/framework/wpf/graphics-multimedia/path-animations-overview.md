---
title: Vue d'ensemble des animations de tracés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 07628d26c8222c7c01f58826a36a15e13dc31ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181865"
---
# <a name="path-animations-overview"></a>Vue d'ensemble des animations de tracés
<a name="introduction"></a> Cette rubrique présente les animations de tracés qui vous permettent d’utiliser un tracé géométrique pour générer des valeurs de sortie. Les animations de tracés sont utiles pour déplacer et faire pivoter des objets le long des tracés complexes.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre ce sujet, vous [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] devez être familier avec les fonctionnalités d’animations. Pour une introduction aux fonctionnalités d’animation, voir [l’Aperçu de l’animation](animation-overview.md).  
  
 Parce que <xref:System.Windows.Media.PathGeometry> vous utilisez un objet pour définir une <xref:System.Windows.Media.PathGeometry> animation de <xref:System.Windows.Media.PathSegment> chemin, vous devez également être familier avec et les différents types d’objets. Pour plus d’informations, voir [l’aperçu de](geometry-overview.md)la géométrie .  
  
<a name="what_is_a_path_animation"></a>
## <a name="what-is-a-path-animation"></a>Qu’est-ce qu’une animation de tracés ?  
 Une animation de chemin <xref:System.Windows.Media.Animation.AnimationTimeline> est <xref:System.Windows.Media.PathGeometry> un type qui utilise un comme son entrée. Au lieu de définir un From, To ou By propriété (comme vous le faites pour une animation From/To/By) ou en utilisant des `PathGeometry` cadres clés (comme vous l’utilisez pour une animation à cadre clé), vous définissez un chemin géométrique et l’utilisez pour définir la propriété de l’animation du chemin. À mesure que l’animation de tracés avance, elle lit les informations relatives aux coordonnées x, y et à l’angle à partir du tracé et les utilise pour générer sa sortie.  
  
 Les animations de tracés sont très utiles pour animer un objet le long d’un tracé complexe. Une façon de déplacer un objet le <xref:System.Windows.Media.MatrixTransform> long <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> d’un chemin est d’utiliser un et un pour transformer un objet le long d’un chemin complexe. L’exemple suivant démontre cette <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> technique en utilisant <xref:System.Windows.Media.MatrixTransform.Matrix%2A> l’objet <xref:System.Windows.Media.MatrixTransform>pour animer la propriété d’un . Le <xref:System.Windows.Media.MatrixTransform> est appliqué sur un bouton et le fait se déplacer le long d’un chemin incurvé. Parce <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> que la `true`propriété est réglée à , le rectangle tourne le long de la tangente du chemin.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Pour plus d’informations sur la syntaxe de chemin qui est utilisée dans l’exemple, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] voir la vue d’ensemble de la [syntaxe Path Markup.](path-markup-syntax.md) Pour l’échantillon complet, voir [Échantillon d’animation Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Vous pouvez appliquer une animation de <xref:System.Windows.Media.Animation.Storyboard> chemin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à une propriété <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> en utilisant un in et un code, ou en utilisant la méthode dans le code. Vous pouvez également utiliser une <xref:System.Windows.Media.Animation.AnimationClock> animation de chemin pour créer un et l’appliquer à une ou plusieurs propriétés. Pour plus d’informations sur les différentes méthodes d’application des animations, voir [Property Animation Techniques Aperçu](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>
## <a name="path-animation-types"></a>Types d’animation de tracés  
 Étant donné que les animations génèrent des valeurs de propriété, il existe différents types d’animation pour différents types de propriété. Pour animer une propriété <xref:System.Double> qui prend <xref:System.Windows.Media.TranslateTransform.X%2A> un (comme la propriété d’un <xref:System.Windows.Media.TranslateTransform>), vous utilisez une animation qui produit des <xref:System.Double> valeurs. Pour animer une propriété <xref:System.Windows.Point>qui prend un , <xref:System.Windows.Point> vous utilisez une animation qui produit des valeurs, et ainsi de suite.  
  
 Les cours d’animation de chemin appartiennent à l’espace <xref:System.Windows.Media.Animation> de nom et utilisent la convention de nommage suivante :  
  
 * \<Type>*`AnimationUsingPath`  
  
 Lorsque * \<type>* est le type de valeur que la classe anime.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les classes d’animation de tracés suivantes.  
  
|Type de propriété|Classe d’animation de tracés correspondante| Exemple|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animer un objet sur un tracé (animation double)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animer un objet sur un tracé (animation de matrice)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animer un objet sur un tracé (animation de point)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> génère <xref:System.Windows.Media.Matrix> des <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>valeurs à partir de son . Lorsqu’il <xref:System.Windows.Media.MatrixTransform>est <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> utilisé avec un , un peut déplacer un objet le long d’un chemin. Si vous <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> définissez <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> la `true`propriété du à , il tourne également l’objet le long des courbes du chemin.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> génère <xref:System.Windows.Point> des valeurs à partir des x- et y-coordonnées de son <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. En utilisant <xref:System.Windows.Media.Animation.PointAnimationUsingPath> un pour animer <xref:System.Windows.Point> une propriété qui prend des valeurs, vous pouvez déplacer un objet le long d’un chemin. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> ne peut pas faire pivoter les objets.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> génère <xref:System.Double> des <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>valeurs à partir de son . En définissant la <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> propriété, <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> vous pouvez spécifier si les utilisations de la x-coordonner, y-coordinate, ou l’angle du chemin comme sa sortie. Vous pouvez <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> utiliser un pour faire pivoter un objet ou le déplacer le long de l’axe x ou y-axe.  
  
<a name="pathanimationinput"></a>
## <a name="path-animation-input"></a>Entrée d’animation de tracés  
 Chaque classe d’animation de chemin fournit une <xref:System.Windows.Media.PathGeometry> propriété pour spécifier son entrée. L’animation de <xref:System.Windows.Media.PathGeometry> chemin utilise le pour générer ses valeurs de sortie. La <xref:System.Windows.Media.PathGeometry> classe vous permet de décrire plusieurs figures complexes composées d’arcs, de courbes et de lignes.  
  
 Au cœur <xref:System.Windows.Media.PathGeometry> d’une <xref:System.Windows.Media.PathFigure> collection d’objets; ces objets sont ainsi nommés parce que chaque <xref:System.Windows.Media.PathGeometry>figure décrit une forme discrète dans le . Chacun <xref:System.Windows.Media.PathFigure> se compose <xref:System.Windows.Media.PathSegment> d’un ou de plusieurs objets, chacun décrivant un segment de la figure.  
  
 Il existe un grand nombre de segments.  
  
|Type de segment|Description|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Crée un arc elliptique entre deux points.|  
|<xref:System.Windows.Media.BezierSegment>|Crée une courbe de Bézier cubique entre deux points.|  
|<xref:System.Windows.Media.LineSegment>|Crée une ligne entre deux points.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Crée une série de courbes de Bézier cubiques.|  
|<xref:System.Windows.Media.PolyLineSegment>|Crée une série de lignes.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Crée une série de courbes de Bézier quadratiques.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Crée une courbe de Bézier quadratique.|  
  
 Les segments <xref:System.Windows.Media.PathFigure> d’un sont combinés en une seule forme géométrique, qui utilise le point final d’un segment comme point de départ du segment suivant. La <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriété <xref:System.Windows.Media.PathFigure> d’un précise le point à partir duquel le premier segment est dessiné. Chaque segment suivant démarre à l’extrémité du segment précédent. Par exemple, une `10,50` ligne `10,150` verticale de à <xref:System.Windows.Media.PathFigure.StartPoint%2A> partir `10,50` peut <xref:System.Windows.Media.LineSegment> être <xref:System.Windows.Media.LineSegment.Point%2A> définie en `10,150`fixant la propriété à et en créant un avec un cadre de propriété de .  
  
 Pour plus <xref:System.Windows.Media.PathGeometry> d’informations sur les objets, voir la [vue d’ensemble de](geometry-overview.md)géométrie .  
  
 En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également utiliser une syntaxe <xref:System.Windows.Media.PathGeometry.Figures%2A> abrégée spéciale pour définir la propriété d’un <xref:System.Windows.Media.PathGeometry>. Pour plus d’informations, voir vue d’ensemble [Path Markup Syntax.](path-markup-syntax.md)  
  
 Pour plus d’informations sur la syntaxe de chemin qui est utilisée dans l’exemple, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] voir la vue d’ensemble de la [syntaxe Path Markup.](path-markup-syntax.md)  
  
## <a name="see-also"></a>Voir aussi

- [Animation de tracés, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Syntaxe XAML pour les tracés](path-markup-syntax.md)
- [Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des techniques d'animation de propriétés](property-animation-techniques-overview.md)
