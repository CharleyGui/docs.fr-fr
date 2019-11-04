---
title: Vue d'ensemble des transformations
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: ead1d114f773cba88e8b3e20f395019fbde3ee15
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458591"
---
# <a name="transforms-overview"></a>Vue d'ensemble des transformations
Cette rubrique explique comment utiliser les classes de <xref:System.Windows.Media.Transform> 2D pour faire pivoter, mettre à l’échelle, déplacer (translater) et incliner des objets <xref:System.Windows.FrameworkElement>.  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Qu’est qu’une transformation ?  
 Un <xref:System.Windows.Media.Transform> définit comment mapper, ou transformer, les points d’un espace de coordonnées à un autre espace de coordonnées. Ce mappage est décrit par une transformation <xref:System.Windows.Media.Matrix>, qui est une collection de trois lignes avec trois colonnes de valeurs <xref:System.Double>.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) utilise des matrices de lignes-principales. Les vecteurs sont exprimés en lignes de vecteurs et non en colonnes de vecteurs.  
  
 Le tableau suivant montre la structure d’une matrice [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="a-2-d-transformation-matrix"></a>Une matrice de transformation en 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Valeur par défaut : 1,0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Valeur par défaut : 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Valeur par défaut : 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Valeur par défaut : 1,0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Valeur par défaut : 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Valeur par défaut : 0,0|1.0|  
  
 En modifiant les valeurs de la matrice, vous pouvez faire pivoter, mettre à l’échelle, incliner et déplacer (translater) un objet. Par exemple, si vous modifiez la valeur de la première colonne de la troisième ligne (la valeur <xref:System.Windows.Media.Matrix.OffsetX%2A>) en 100, vous pouvez l’utiliser pour déplacer un objet de 100 unités le long de l’axe x. Si vous remplacez la valeur de la case située à l’intersection de la deuxième colonne et de la deuxième par 3, vous pouvez étirer un objet à trois fois sa hauteur actuelle. Si vous modifiez les deux valeurs comme indiqué ci-dessus, vous déplacez l’objet de 100 unités sur l’axe X et multipliez sa hauteur par 3. Étant donné que Windows Presentation Foundation (WPF) prend uniquement en charge les transformations affines, les valeurs de la colonne de droite sont toujours 0, 0, 1.  
  
 Bien que Windows Presentation Foundation (WPF) vous permette de manipuler directement des valeurs de matrice, il fournit également plusieurs classes <xref:System.Windows.Media.Transform> qui vous permettent de transformer un objet sans connaître la configuration de la structure de la matrice sous-jacente. Par exemple, la classe <xref:System.Windows.Media.ScaleTransform> vous permet de mettre à l’échelle un objet en définissant ses propriétés <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, au lieu de manipuler une matrice de transformation. De même, la classe <xref:System.Windows.Media.RotateTransform> vous permet de faire pivoter un objet en définissant simplement sa propriété <xref:System.Windows.Media.RotateTransform.Angle%2A>.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Classes de transformation  
 Windows Presentation Foundation (WPF) fournit les classes de <xref:System.Windows.Media.Transform> 2D suivantes pour les opérations de transformation courantes :  
  
|Class|Description|Exemple|Illustration|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Fait pivoter un élément selon le <xref:System.Windows.Media.RotateTransform.Angle%2A>spécifié.|[Faire pivoter un objet](how-to-rotate-an-object.md)|![Faire pivoter l’illustration](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Met à l’échelle un élément selon le <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et les montants <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> spécifiés.|[Mettre à l'échelle un élément](how-to-scale-an-element.md)|![Illustration de l’échelle](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Incline un élément selon le <xref:System.Windows.Media.SkewTransform.AngleX%2A> et les montants <xref:System.Windows.Media.SkewTransform.AngleY%2A> spécifiés.|[Incliner un élément](how-to-skew-an-element.md)|![Incliner l’illustration](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Déplace (traduit) un élément selon le <xref:System.Windows.Media.TranslateTransform.X%2A> et les valeurs <xref:System.Windows.Media.TranslateTransform.Y%2A> spécifiés.|[Translater un élément](how-to-translate-an-element.md)|![Traduire l’illustration](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pour créer des transformations plus complexes, Windows Presentation Foundation (WPF) fournit les deux classes suivantes :  
  
|Class|Description|Exemple|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Regroupe plusieurs objets <xref:System.Windows.Media.TransformGroup> dans un <xref:System.Windows.Media.Transform> unique que vous pouvez ensuite appliquer aux propriétés de transformation.|[Apply Multiple Transforms to an Object](how-to-apply-multiple-transforms-to-an-object.md) (Appliquer plusieurs transformations à un objet)|  
|<xref:System.Windows.Media.MatrixTransform>|Crée des transformations personnalisées qui ne sont pas fournies par les autres classes <xref:System.Windows.Media.Transform>. Lorsque vous utilisez un <xref:System.Windows.Media.MatrixTransform>, vous manipulez directement une matrice.|[Use a MatrixTransform to Create Custom Transforms](how-to-use-a-matrixtransform-to-create-custom-transforms.md) (Utiliser la classe MatrixTransform pour créer des transformations personnalisées)|  
  
 Windows Presentation Foundation (WPF) fournit également des transformations 3D. Pour plus d'informations, consultez la classe <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Propriétés des opérations de transformation courantes  
 Une façon de transformer un objet consiste à déclarer le type de <xref:System.Windows.Media.Transform> approprié et à l’appliquer à la propriété de transformation de l’objet. Les différents types d’objet ont différents types de propriété de transformation. Le tableau suivant répertorie plusieurs types de Windows Presentation Foundation (WPF) couramment utilisés et leurs propriétés de transformation.  
  
|Tapez|Propriétés de transformation|  
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
 Lorsque vous transformez un objet, vous ne transformez pas simplement l’objet, vous transformez l’espace de coordonnées dans lequel cet objet existe. Par défaut, une opération de transformation est centrée à l’origine du système de coordonnées de l’objet cible : (0,0). La seule exception est <xref:System.Windows.Media.TranslateTransform>; une <xref:System.Windows.Media.TranslateTransform> n’a aucune propriété de centre à définir, car l’effet de traduction est le même, quel que soit l’emplacement où elle est centrée.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.RotateTransform> pour faire pivoter un élément <xref:System.Windows.Shapes.Rectangle>, un type de <xref:System.Windows.FrameworkElement>, de 45 degrés sur son centre par défaut, (0, 0). L’illustration suivante montre l’effet de la rotation.  
  
 ![Un élément FrameworkElement pivoté de 45 degrés autour de &#40;0,0&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Un élément rectangle pivoté de 45 degrés autour du point (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Par défaut, l’élément pivote autour de son coin supérieur gauche, (0, 0). Les classes <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>et <xref:System.Windows.Media.SkewTransform> fournissent des propriétés CenterX et CenterY qui vous permettent de spécifier le point auquel la transformation est appliquée.  
  
 L’exemple suivant utilise également un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un élément <xref:System.Windows.Shapes.Rectangle> de 45 degrés ; Toutefois, cette fois, les propriétés <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> sont définies de façon à ce que le <xref:System.Windows.Media.RotateTransform> ait un centre de (25, 25). L’illustration suivante montre l’effet de la rotation.  
  
 ![Une géométrie pivotée de 45 degrés autour de &#40;25, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Un élément rectangle pivoté de 45 degrés autour du point (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Transformation d’un élément FrameworkElement  
 Pour appliquer des transformations à un <xref:System.Windows.FrameworkElement>, créez un <xref:System.Windows.Media.Transform> et appliquez-le à l’une des deux propriétés fournies par la classe <xref:System.Windows.FrameworkElement> :  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A> : transformation appliquée avant la passe de disposition. Une fois la transformation appliquée, le système de disposition traite la taille et la position transformées de l’élément.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A> : transformation qui modifie l’apparence de l’élément, mais qui est appliquée une fois que la passe de disposition est terminée. En utilisant la propriété <xref:System.Windows.UIElement.RenderTransform%2A> à la place de la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A>, vous pouvez obtenir des avantages en matière de performances.  
  
 Quelle propriété utiliser ? En raison des avantages en matière de performances qu’il offre, utilisez la propriété <xref:System.Windows.UIElement.RenderTransform%2A> chaque fois que cela est possible, en particulier quand vous utilisez des objets de <xref:System.Windows.Media.Transform> animés. Utilisez la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A> lors de la mise à l’échelle, de la rotation ou de l’inclinaison, et que vous avez besoin du parent de l’élément pour ajuster à la taille transformée de l’élément. Notez que, lorsqu’ils sont utilisés avec la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A>, <xref:System.Windows.Media.TranslateTransform> objets semblent ne pas avoir d’effet sur les éléments. Ceci est dû au fait que le système de disposition remet l’élément translaté dans sa position d’origine au cours de son traitement.  
  
 Pour plus d’informations sur la disposition dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consultez l’article [Layout](../advanced/layout.md) (Le système de disposition).  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Exemple : faire pivoter un FrameworkElement de 45 degrés  
 L’exemple suivant utilise une <xref:System.Windows.Media.RotateTransform> pour faire pivoter un bouton dans le sens des aiguilles d’une montre, de 45 degrés. Le bouton est contenu dans un <xref:System.Windows.Controls.StackPanel> qui a deux autres boutons.  
  
 Par défaut, un <xref:System.Windows.Media.RotateTransform> pivote autour du point (0, 0). L’exemple ne spécifie pas de valeur pour le centre donc le bouton pivote autour du point (0, 0), qui se trouve dans le coin supérieur gauche. La <xref:System.Windows.Media.RotateTransform> est appliquée à la propriété <xref:System.Windows.UIElement.RenderTransform%2A>. L’illustration suivante montre les résultats de la transformation.  
  
 ![Bouton transformé à l'aide de RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Rotation de 45 degrés dans le sens des aiguilles d’une montre à partir du coin supérieur gauche  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 L’exemple suivant utilise également un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un bouton de 45 degrés dans le sens des aiguilles d’une montre, mais il définit également la <xref:System.Windows.UIElement.RenderTransformOrigin%2A> du bouton sur (0,5, 0,5). La valeur de la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> est relative à la taille du bouton. Par conséquent, la rotation est appliquée au centre du bouton et non à partir de son coin supérieur gauche. L’illustration suivante montre les résultats de la transformation.  
  
 ![Un bouton transformé à partir de son centre](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Une rotation de 45 degrés dans le sens des aiguilles d’une montre autour de centre  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 L’exemple suivant utilise la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A> à la place de la propriété <xref:System.Windows.UIElement.RenderTransform%2A> pour faire pivoter le bouton.  Ainsi, la transformation affecte la disposition du bouton, ce qui déclenche une passe entière par le système de disposition. Par conséquent, le bouton est pivoté, puis repositionné, car sa taille a changé. L’illustration suivante montre les résultats de la transformation.  
  
 ![Un bouton transformé à l'aide de LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Classe LayoutTransform utilisée pour faire pivoter le bouton  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animation de transformations  
 Étant donné qu’elles héritent de la classe <xref:System.Windows.Media.Animation.Animatable>, les classes <xref:System.Windows.Media.Transform> peuvent être animées. Pour animer une <xref:System.Windows.Media.Transform>, appliquez une animation d’un type compatible à la propriété que vous souhaitez animer.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.Animation.Storyboard> et un <xref:System.Windows.Media.Animation.DoubleAnimation> avec un <xref:System.Windows.Media.RotateTransform> pour rendre une <xref:System.Windows.Controls.Button> tourner en place quand l’utilisateur clique dessus.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D). Pour plus d’informations sur les animations, consultez l’article [Vue d’ensemble de l’animation](animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Fonctionnalités Freezable  
 Comme elle hérite de la classe <xref:System.Windows.Freezable>, la classe <xref:System.Windows.Media.Transform> fournit plusieurs fonctionnalités spéciales : les objets <xref:System.Windows.Media.Transform> peuvent être déclarés en tant que [ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, mis en lecture seule pour améliorer les performances, clonés et rendus thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Rubriques de guide pratique](transformations-how-to-topics.md)
- [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D)
