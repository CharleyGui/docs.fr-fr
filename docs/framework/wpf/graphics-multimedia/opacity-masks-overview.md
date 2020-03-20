---
title: Vue d'ensemble des masques d'opacité
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 0c859659c35e2a5806b8585214c87c18fbcb62d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187691"
---
# <a name="opacity-masks-overview"></a>Vue d'ensemble des masques d'opacité
Les masques d’opacité vous permettent de rendre les parties d’un élément ou d’un visuel totalement ou partiellement transparentes. Pour créer un masque d’opacité, vous appliquez un <xref:System.Windows.Media.Brush> à la <xref:System.Windows.UIElement.OpacityMask%2A> propriété d’un élément ou <xref:System.Windows.Media.Visual>.  Le pinceau est mappé à l’élément ou à l’objet visuel, et la valeur d’opacité de chaque pixel de pinceau est utilisée pour déterminer l’opacité obtenu pour chaque pixel correspondant de l’élément ou de l’objet visuel.  
  
<a name="prereqs"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette vue d’ensemble suppose <xref:System.Windows.Media.Brush> que vous êtes familier avec les objets. Pour une introduction à l’utilisation des pinceaux, consultez [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md). Pour plus <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>d’informations sur et , voir [Peinture avec des images, des dessins et des visuels](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>
## <a name="creating-visual-effects-with-opacity-masks"></a>Création d’effets visuels avec les masques d’opacité  
 Un masque d’opacité consiste à mapper son contenu à l’élément ou à l’objet visuel. Le canal alpha de chacun des pixels du pinceau est ensuite utilisé pour déterminer l’opacité obtenue pour les pixels correspondants de l’élément ou de l’objet visuel ; la couleur réelle du pinceau est ignorée. Si une partie donnée du pinceau est transparente, la partie correspondante de l’élément ou de l’objet visuel devient transparente. Si une partie donnée du pinceau est opaque, la partie correspondante de l’élément ou de l’objet visuel reste inchangée. L’opacité spécifiée par le masque d’opacité est associée à tous les paramètres d’opacité présents dans l’élément ou l’objet visuel. Par exemple, si un élément est opaque à 25 % et si le masque d’opacité appliqué passe d’une opacité totale à une transparence totale, l’élément passera d’une opacité à 25 % à une transparence totale.  
  
> [!NOTE]
> Bien que les exemples de cette vue démontrent l’utilisation de masques d’opacité <xref:System.Windows.Media.Visual>sur les éléments d’image, un masque d’opacité peut être appliqué à n’importe quel élément ou, y compris les panneaux et les contrôles.  
  
 Les masques d’opacité sont utilisés pour créer des effets visuels intéressants, par exemple pour créer des images ou des boutons qui s’effacent de la vue, pour ajouter des textures à des éléments, ou pour combiner des dégradés pour produire des surfaces semblables à du verre. L’illustration suivante montre l’utilisation d’un masque d’opacité. Un arrière-plan à carreaux est utilisé pour afficher les parties transparentes du masque.  
  
 ![Objet avec un masque d'opacité LinearGradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Exemple de masque d’opacité  
  
<a name="creatingopacitymasks"></a>
## <a name="creating-an-opacity-mask"></a>Création d’un masque d’opacité  
 Pour créer un masque d’opacité, vous créez un <xref:System.Windows.Media.Brush> et l’appliquez à la <xref:System.Windows.UIElement.OpacityMask%2A> propriété d’un élément ou d’un visuel. Vous pouvez utiliser <xref:System.Windows.Media.Brush> n’importe quel type de masque d’opacité.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Utilisé pour faire un élément ou un fondu visuel de la vue.  
  
     L’image suivante <xref:System.Windows.Media.LinearGradientBrush> montre un masque utilisé comme un masque d’opacité.  
  
     ![Objet avec un masque d’opacité LinearGradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Exemple de masque d’opacité LinearGradientBrush  
  
- <xref:System.Windows.Media.ImageBrush>: Utilisé pour créer de la texture et des effets de bord doux ou déchirés.  
  
     L’image suivante <xref:System.Windows.Media.ImageBrush> montre un masque utilisé comme un masque d’opacité.  
  
     ![Objet avec un masque d’opacité ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Exemple de masque d’opacité LinearGradientBrush  
  
- <xref:System.Windows.Media.DrawingBrush>: Utilisé pour créer des masques complexes d’opacité à partir de motifs de formes, d’images et de gradients.  
  
     L’image suivante <xref:System.Windows.Media.DrawingBrush> montre un masque utilisé comme un masque d’opacité.  
  
     ![Objet avec un masque d’opacité DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Exemple de masque d’opacité DrawingBrush  
  
 Les pinceaux de<xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>gradient ( et ) sont particulièrement bien adaptés pour une utilisation comme masque d’opacité. Parce <xref:System.Windows.Media.SolidColorBrush> qu’un remplit une zone avec une couleur uniforme, ils font de pauvres masques d’opacité; l’utilisation d’un <xref:System.Windows.Media.SolidColorBrush> est équivalent à <xref:System.Windows.UIElement.OpacityMask%2A> la définition de la propriété de l’élément ou du visuel.  
  
<a name="creatingopacitymaskswithgradients"></a>
## <a name="using-a-gradient-as-an-opacity-mask"></a>Utilisation d’un dégradé comme masque d’opacité  
 Pour créer un remplissage en dégradé, vous devez spécifier au moins deux points de dégradé. Chaque point de dégradé décrit une couleur et une position (voir [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md) pour plus d’informations sur la création et l’utilisation des dégradés). Le processus est le même lorsque vous utilisez un dégradé comme masque d’opacité, sauf que, au lieu de fusionner des couleurs, le dégradé du masque d’opacité fusionne les valeurs du canal alpha. Par conséquent, la couleur réelle du contenu du dégradé n’a aucune importance ; seul compte le canal alpha, ou l’opacité, de chaque couleur. Voici un exemple.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Spécification des points de dégradé pour un masque d’opacité  
 Dans l’exemple précédent, la <xref:System.Windows.Media.Colors.Black%2A> couleur définie par le système est utilisée comme couleur de départ du gradient. Parce que toutes les <xref:System.Windows.Media.Colors> couleurs <xref:System.Windows.Media.Colors.Transparent%2A>de la classe, sauf, sont entièrement opaques, ils peuvent être utilisés pour simplement définir une couleur de départ pour un masque d’opacité gradient.  
  
 Pour un contrôle supplémentaire sur les valeurs alpha lors de la définition d’un masque d’opacité, <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> vous pouvez spécifier le canal alpha des couleurs en utilisant la notation hexadecimal ARGB dans le balisage ou en utilisant la méthode.  
  
<a name="argbsyntax"></a>
### <a name="specifying-color-opacity-in-xaml"></a>Spécification de l’opacité de couleur en « XAML »  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous utilisez argB hexadecimal notation pour spécifier l’opacité des couleurs individuelles. La notation hexadecimal ARGB utilise la syntaxe suivante :  
  
 `#` **aa** *rrggbb*  
  
 *aa* dans la ligne précédente représente une valeur hexadécimale à deux chiffres utilisée pour spécifier l’opacité de la couleur. *rr*, *gg* et *bb* représentent une valeur hexadécimale à deux chiffres utilisée pour spécifier la quantité de rouge, de vert et de bleu dans la couleur. Chaque chiffre hexadécimal peut avoir une valeur comprise entre 0 et 9 ou A et F. 0 est la plus petite valeur et F est la plus grande. Une valeur alpha de 00 indique qu’une couleur est entièrement transparente, tandis qu’une valeur alpha de FF crée une couleur entièrement opaque.  Dans l’exemple suivant, la notation hexadecimal ARGB est utilisée pour spécifier deux couleurs. La première est totalement opaque, tandis que la seconde est totalement transparente.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>
## <a name="using-an-image-as-an-opacity-mask"></a>Utilisation d’une image comme masque d’opacité  
 Les images peuvent également être utilisées comme masque d’opacité. L’image suivante en montre un exemple. Un arrière-plan à carreaux est utilisé pour afficher les parties transparentes du masque.  
  
 ![Objet avec un masque d’opacité ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Exemple de masque d’opacité  
  
 Pour utiliser une image comme masque d’opacité, utilisez un <xref:System.Windows.Media.ImageBrush> pour contenir l’image. Lors de la création d’une image à utiliser comme masque d’opacité, enregistrer l’image dans un format qui prend en charge plusieurs niveaux de transparence, tels que Portable Network Graphics (PNG). L’exemple suivant montre le code utilisé pour créer l’illustration précédente.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Utilisation d’une image en mosaïque comme masque d’opacité  
 Dans l’exemple suivant, la même <xref:System.Windows.Media.ImageBrush>image est utilisée avec une autre, mais les caractéristiques de carrelage de la brosse sont utilisées pour produire des tuiles de l’image 50 pixels carrés.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Création d’un masque d’opacité à partir d’un dessin  
 Les dessins peuvent être utilisés comme masque d’opacité. Les formes contenues dans le dessin peuvent être remplies avec des dégradés, des couleurs unies, des images ou même d’autres dessins. L’image suivante montre un exemple de dessin utilisé comme masque d’opacité. Un arrière-plan à carreaux est utilisé pour afficher les parties transparentes du masque.  
  
 ![Objet avec un masque d’opacité DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Exemple de masque d’opacité DrawingBrush  
  
 Pour utiliser un dessin comme masque d’opacité, utilisez un <xref:System.Windows.Media.DrawingBrush> pour contenir le dessin. L’exemple suivant montre le code utilisé pour créer l’illustration précédente :  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Utilisation d’un dessin en mosaïque comme masque d’opacité  
 Comme <xref:System.Windows.Media.ImageBrush>le <xref:System.Windows.Media.DrawingBrush> , le peut être fait pour carreler son dessin. Dans l’exemple suivant, un pinceau de dessin est utilisé pour créer un masque d’opacité en mosaïque.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Voir aussi

- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
