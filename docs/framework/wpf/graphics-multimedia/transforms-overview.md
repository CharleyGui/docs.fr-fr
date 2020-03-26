---
title: Vue d'ensemble des transformations
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2D transform
- transform classes [WPF], 2D
- 2D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: c5f29404a301eb023ff24b2890531dede6440ec4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111957"
---
# <a name="transforms-overview"></a>Vue d'ensemble des transformations
Ce sujet décrit comment utiliser les <xref:System.Windows.Media.Transform> classes 2D pour faire pivoter, évoluer, déplacer (traduire) et biaiser les <xref:System.Windows.FrameworkElement> objets.  

<a name="whatIsATransformSection"></a>
## <a name="what-is-a-transform"></a>Qu’est qu’une transformation ?  
 A <xref:System.Windows.Media.Transform> définit comment cartographier, ou transformer, les points d’un espace de coordonnées à un autre espace de coordonnées. Cette cartographie est décrite <xref:System.Windows.Media.Matrix>par une transformation , qui est <xref:System.Double> une collection de trois rangées avec trois colonnes de valeurs.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) utilise des matrices en ligne. Les vecteurs sont exprimés en lignes de vecteurs et non en colonnes de vecteurs.  
  
 Le tableau suivant montre la structure d’une matrice [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="a-2d-transformation-matrix"></a>Une matrice de transformation 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Valeur par défaut : 1,0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Valeur par défaut : 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Valeur par défaut : 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Valeur par défaut : 1,0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Valeur par défaut : 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Valeur par défaut : 0,0|1.0|  
  
 En modifiant les valeurs de la matrice, vous pouvez faire pivoter, mettre à l’échelle, incliner et déplacer (translater) un objet. Par exemple, si vous modifiez la valeur de <xref:System.Windows.Media.Matrix.OffsetX%2A> la première colonne de la troisième rangée (la valeur) à 100, vous pouvez l’utiliser pour déplacer un objet de 100 unités le long de l’axe x. Si vous remplacez la valeur de la case située à l’intersection de la deuxième colonne et de la deuxième par 3, vous pouvez étirer un objet à trois fois sa hauteur actuelle. Si vous modifiez les deux valeurs comme indiqué ci-dessus, vous déplacez l’objet de 100 unités sur l’axe X et multipliez sa hauteur par 3. Parce que Windows Presentation Foundation (WPF) ne prend en charge les transformations affine, les valeurs dans la colonne de droite sont toujours 0, 0, 1.  
  
 Bien que Windows Presentation Foundation (WPF) vous permette <xref:System.Windows.Media.Transform> de manipuler directement les valeurs de la matrice, il fournit également plusieurs classes qui vous permettent de transformer un objet sans savoir comment la structure de la matrice sous-jacente est configurée. Par exemple, <xref:System.Windows.Media.ScaleTransform> la classe vous permet d’escalader un objet en définissant ses <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriétés et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ses propriétés, au lieu de manipuler une matrice de transformation. De même, la <xref:System.Windows.Media.RotateTransform> classe vous permet de <xref:System.Windows.Media.RotateTransform.Angle%2A> faire pivoter un objet en plaçant simplement sa propriété.  
  
<a name="transformClassesSection"></a>
## <a name="transform-classes"></a>Classes de transformation  
 Windows Presentation Foundation (WPF) fournit <xref:System.Windows.Media.Transform> les classes 2D suivantes pour les opérations de transformation communes :  
  
|Classe|Description|Exemple|Illustration|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Tourne un élément par <xref:System.Windows.Media.RotateTransform.Angle%2A>le spécifié .|[Faire pivoter un objet](how-to-rotate-an-object.md)|![Pivoter l'illustration](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Échelles d’un <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> élément <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> par les spécifiés et les montants.|[Mettre à l'échelle un élément](how-to-scale-an-element.md)|![Mettre à l'échelle l'illustration](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Skews un élément <xref:System.Windows.Media.SkewTransform.AngleX%2A> par <xref:System.Windows.Media.SkewTransform.AngleY%2A> les spécifiés et les montants.|[Incliner un élément](how-to-skew-an-element.md)|![Incliner l'illustration](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Déplace (traduit) un élément <xref:System.Windows.Media.TranslateTransform.X%2A> par <xref:System.Windows.Media.TranslateTransform.Y%2A> les spécifiés et les montants.|[Translater un élément](how-to-translate-an-element.md)|![Traduire l'illustration](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pour créer des transformations plus complexes, Windows Presentation Foundation (WPF) propose les deux classes suivantes :  
  
|Classe|Description|Exemple|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Regroupe <xref:System.Windows.Media.TransformGroup> plusieurs objets <xref:System.Windows.Media.Transform> en un seul que vous pouvez ensuite appliquer pour transformer les propriétés.|[Apply Multiple Transforms to an Object](how-to-apply-multiple-transforms-to-an-object.md) (Appliquer plusieurs transformations à un objet)|  
|<xref:System.Windows.Media.MatrixTransform>|Crée des transformations personnalisées qui <xref:System.Windows.Media.Transform> ne sont pas fournies par les autres classes. Lorsque vous <xref:System.Windows.Media.MatrixTransform>utilisez un , vous manipulez une matrice directement.|[Use a MatrixTransform to Create Custom Transforms](how-to-use-a-matrixtransform-to-create-custom-transforms.md) (Utiliser la classe MatrixTransform pour créer des transformations personnalisées)|  
  
 Windows Presentation Foundation (WPF) propose également des transformations 3D. Pour plus d'informations, consultez la classe <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>
## <a name="common-transformation-properties"></a>Propriétés des opérations de transformation courantes  
 Une façon de transformer un objet <xref:System.Windows.Media.Transform> est de déclarer le type approprié et de l’appliquer à la propriété de transformation de l’objet. Les différents types d’objet ont différents types de propriété de transformation. Le tableau suivant répertorie plusieurs types de windows Presentation Foundation (WPF) couramment utilisés et leurs propriétés de transformation.  
  
|Type|Propriétés de transformation|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>
## <a name="transformations-and-coordinate-systems"></a>Transformations et systèmes de coordonnées  
 Lorsque vous transformez un objet, vous ne transformez pas simplement l’objet, vous transformez l’espace de coordonnées dans lequel cet objet existe. Par défaut, une opération de transformation est centrée à l’origine du système de coordonnées de l’objet cible : (0,0). La seule <xref:System.Windows.Media.TranslateTransform>exception est ; a <xref:System.Windows.Media.TranslateTransform> n’a pas de propriétés centrales à définir parce que l’effet de traduction est le même quel que soit l’endroit où il est centré.  
  
 L’exemple suivant <xref:System.Windows.Media.RotateTransform> utilise <xref:System.Windows.Shapes.Rectangle> un élément de <xref:System.Windows.FrameworkElement>rotation, un type de , par 45 degrés sur son centre par défaut, (0, 0). L’illustration suivante montre l’effet de la rotation.  
  
 ![Un élément FrameworkElement pivoté de 45 degrés autour de &#40;0,0&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Un élément rectangle pivoté de 45 degrés autour du point (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Par défaut, l’élément pivote autour de son coin supérieur gauche, (0, 0). Les <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ScaleTransform>classes, <xref:System.Windows.Media.SkewTransform> et les classes fournissent des propriétés CenterX et CenterY qui vous permettent de spécifier le point où la transformation est appliquée.  
  
 L’exemple suivant <xref:System.Windows.Media.RotateTransform> utilise également <xref:System.Windows.Shapes.Rectangle> un élément pour faire pivoter un élément de 45 degrés; cependant, cette <xref:System.Windows.Media.RotateTransform.CenterX%2A> fois, les propriétés et <xref:System.Windows.Media.RotateTransform.CenterY%2A> les propriétés sont définies de sorte que le <xref:System.Windows.Media.RotateTransform> a un centre de (25, 25). L’illustration suivante montre l’effet de la rotation.  
  
 ![Une géométrie pivotée de 45 degrés autour de &#40;25, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Un élément rectangle pivoté de 45 degrés autour du point (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>
## <a name="transforming-a-frameworkelement"></a>Transformation d’un élément FrameworkElement  
 Pour appliquer les <xref:System.Windows.FrameworkElement>transformations <xref:System.Windows.Media.Transform> à un , créer un et <xref:System.Windows.FrameworkElement> l’appliquer à l’une des deux propriétés que la classe fournit:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>Une transformation qui est appliquée avant le passage de la mise en page. Une fois la transformation appliquée, le système de disposition traite la taille et la position transformées de l’élément.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>Une transformation qui modifie l’apparence de l’élément mais qui est appliquée une fois le passage de mise en page terminé. En utilisant <xref:System.Windows.UIElement.RenderTransform%2A> la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A> au lieu de la propriété, vous pouvez obtenir des avantages de performance.  
  
 Quelle propriété utiliser ? En raison des avantages de performance <xref:System.Windows.UIElement.RenderTransform%2A> qu’il fournit, utilisez <xref:System.Windows.Media.Transform> la propriété chaque fois que possible, surtout lorsque vous utilisez des objets animés. Utilisez <xref:System.Windows.FrameworkElement.LayoutTransform%2A> la propriété lors de l’échelle, la rotation ou la faussement et vous avez besoin du parent de l’élément pour s’adapter à la taille transformée de l’élément. Notez que, lorsqu’ils <xref:System.Windows.FrameworkElement.LayoutTransform%2A> sont <xref:System.Windows.Media.TranslateTransform> utilisés avec la propriété, les objets semblent n’avoir aucun effet sur les éléments. Ceci est dû au fait que le système de disposition remet l’élément translaté dans sa position d’origine au cours de son traitement.  
  
 Pour plus d’informations sur la disposition dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consultez l’article [Layout](../advanced/layout.md) (Le système de disposition).  
  
<a name="exampleRotateAnElement45degSection"></a>
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Exemple : faire pivoter un FrameworkElement de 45 degrés  
 L’exemple suivant <xref:System.Windows.Media.RotateTransform> utilise un pour faire pivoter un bouton dans le sens des aiguilles d’une montre de 45 degrés. Le bouton est <xref:System.Windows.Controls.StackPanel> contenu dans un qui a deux autres boutons.  
  
 Par défaut, <xref:System.Windows.Media.RotateTransform> une rotation environ le point (0, 0). L’exemple ne spécifie pas de valeur pour le centre donc le bouton pivote autour du point (0, 0), qui se trouve dans le coin supérieur gauche. Le <xref:System.Windows.Media.RotateTransform> est appliqué <xref:System.Windows.UIElement.RenderTransform%2A> à la propriété. L’illustration suivante montre les résultats de la transformation.  
  
 ![Bouton transformé à l'aide de RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Rotation de 45 degrés dans le sens des aiguilles d’une montre à partir du coin supérieur gauche  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 L’exemple suivant <xref:System.Windows.Media.RotateTransform> utilise également un pour faire pivoter un bouton <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 45 degrés dans le sens des aiguilles d’une montre, mais il définit également le bouton à (0,5, 0,5). La valeur <xref:System.Windows.UIElement.RenderTransformOrigin%2A> de la propriété est relative à la taille du bouton. Par conséquent, la rotation est appliquée au centre du bouton et non à partir de son coin supérieur gauche. L’illustration suivante montre les résultats de la transformation.  
  
 ![Un bouton transformé à partir de son centre](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Une rotation de 45 degrés dans le sens des aiguilles d’une montre autour de centre  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 L’exemple suivant <xref:System.Windows.FrameworkElement.LayoutTransform%2A> utilise la <xref:System.Windows.UIElement.RenderTransform%2A> propriété au lieu de la propriété pour faire pivoter le bouton.  Ainsi, la transformation affecte la disposition du bouton, ce qui déclenche une passe entière par le système de disposition. Par conséquent, le bouton est pivoté, puis repositionné, car sa taille a changé. L’illustration suivante montre les résultats de la transformation.  
  
 ![Un bouton transformé à l'aide de LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Classe LayoutTransform utilisée pour faire pivoter le bouton  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>
## <a name="animating-transformations"></a>Animation de transformations  
 Parce qu’ils <xref:System.Windows.Media.Animation.Animatable> héritent de la classe, les <xref:System.Windows.Media.Transform> classes peuvent être animées. Pour animer <xref:System.Windows.Media.Transform>un , appliquez une animation d’un type compatible à la propriété que vous souhaitez animer.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.Storyboard> utilise <xref:System.Windows.Media.Animation.DoubleAnimation> un <xref:System.Windows.Media.RotateTransform> et <xref:System.Windows.Controls.Button> un avec un pour faire un tour en place quand il est cliqué.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Pour l’échantillon complet, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms). Pour plus d’informations sur les animations, consultez l’article [Vue d’ensemble de l’animation](animation-overview.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Fonctionnalités Freezable  
 Parce qu’il <xref:System.Windows.Freezable> hérite <xref:System.Windows.Media.Transform> de la classe, <xref:System.Windows.Media.Transform> la classe fournit plusieurs caractéristiques spéciales: les objets peuvent être déclarés comme [des ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, faits en lecture seulement pour améliorer les performances, cloné, et fait thread-safe. Pour plus d’informations sur les <xref:System.Windows.Freezable> différentes fonctionnalités fournies par les objets, voir le [Aperçu des objets freezable](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Sujets comment se passer](transformations-how-to-topics.md)
- [2D transforme l’échantillon](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
