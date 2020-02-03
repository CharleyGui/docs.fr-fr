---
title: Vue d’ensemble des pinceaux
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 18ca9b79a6ee801638a54fcb227c44e9aea21fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746211"
---
# <a name="wpf-brushes-overview"></a>Vue d'ensemble des pinceaux WPF
Tout ce qui est visible sur votre écran est visible, car il a été peint par un pinceau. Par exemple, un pinceau est utilisé pour décrire l’arrière-plan d’un bouton, le premier plan du texte et le remplissage d’une forme. Cette rubrique présente les concepts de peinture avec [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pinceaux et fournit des exemples. Les pinceaux permettent de peindre des objets de l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aussi bien avec de simples couleurs unies qu’avec des ensembles complexes de modèles et d’images.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Peindre avec un pinceau  
 Un <xref:System.Windows.Media.Brush> « peint » une zone avec sa sortie. Les différents pinceaux ont différents types de sortie. Certains pinceaux peignent une zone avec une couleur unie, d’autres avec un dégradé, un motif, une image ou un dessin. L’illustration suivante montre des exemples de chacun des différents types de <xref:System.Windows.Media.Brush>.  
  
 ![Types de pinceau](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Exemples de pinceaux  
  
 La plupart des objets visuels vous permettent de spécifier la façon dont ils sont peints. Le tableau suivant répertorie certains objets et propriétés courants avec lesquels vous pouvez utiliser un <xref:System.Windows.Media.Brush>.  
  
|Class|Propriétés de pinceau|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Les sections suivantes décrivent les différents types de <xref:System.Windows.Media.Brush> et fournissent un exemple de chacun d’eux.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Peindre avec une couleur unie  
 Un <xref:System.Windows.Media.SolidColorBrush> peint une zone avec un <xref:System.Windows.Media.Color>solide. Il existe plusieurs façons de spécifier la <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush>: par exemple, vous pouvez spécifier ses canaux alpha, rouge, bleu et vert ou utiliser l’une des couleurs prédéfinies fournies par la classe <xref:System.Windows.Media.Colors>.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.SolidColorBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint à l’aide d’un SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Rectangle peint à l’aide d’un SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Pour plus d’informations sur la classe <xref:System.Windows.Media.SolidColorBrush>, consultez [vue d’ensemble de la peinture avec des couleurs unies et des dégradés](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Peindre avec un dégradé linéaire  
 Un <xref:System.Windows.Media.LinearGradientBrush> peint une zone avec un dégradé linéaire. Un dégradé linéaire fusionne deux couleurs ou plus sur une ligne, l’axe du dégradé. Vous utilisez <xref:System.Windows.Media.GradientStop> objets pour spécifier les couleurs du dégradé et leurs positions.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.LinearGradientBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint à l’aide d’un LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Rectangle peint à l’aide d’un LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Pour plus d’informations sur la classe <xref:System.Windows.Media.LinearGradientBrush>, consultez [vue d’ensemble de la peinture avec des couleurs unies et des dégradés](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Peindre avec un dégradé radial  
 Un <xref:System.Windows.Media.RadialGradientBrush> peint une zone avec un dégradé radial. Un dégradé radial fusionne deux couleurs ou plus sur un cercle. Comme pour la classe <xref:System.Windows.Media.LinearGradientBrush>, vous utilisez des objets <xref:System.Windows.Media.GradientStop> pour spécifier les couleurs du dégradé et leurs positions.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.RadialGradientBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint à l’aide d’un RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Rectangle peint à l’aide d’un RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Pour plus d’informations sur la classe <xref:System.Windows.Media.RadialGradientBrush>, consultez [vue d’ensemble de la peinture avec des couleurs unies et des dégradés](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Peindre avec une image  
 Un <xref:System.Windows.Media.ImageBrush> peint une zone avec une <xref:System.Windows.Media.ImageSource>.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.ImageBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint par un ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Rectangle peint à l’aide d’une image  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Pour plus d’informations sur la classe <xref:System.Windows.Media.ImageBrush>, consultez [peinture avec des images, des dessins et](painting-with-images-drawings-and-visuals.md)des éléments visuels.  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Peindre avec un dessin  
 Un <xref:System.Windows.Media.DrawingBrush> peint une zone avec une <xref:System.Windows.Media.Drawing>. Une <xref:System.Windows.Media.Drawing> peut contenir des formes, des images, du texte et des médias.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.DrawingBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint à l’aide d’un DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Rectangle peint à l’aide d’un DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Pour plus d’informations sur la classe <xref:System.Windows.Media.DrawingBrush>, consultez [peinture avec des images, des dessins et](painting-with-images-drawings-and-visuals.md)des éléments visuels.  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Peindre avec un visuel  
 Un <xref:System.Windows.Media.VisualBrush> peint une zone avec un objet <xref:System.Windows.Media.Visual>. <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>et <xref:System.Windows.Controls.MediaElement>sont des exemples d’objets visuels. Un <xref:System.Windows.Media.VisualBrush> vous permet également de projeter du contenu d’une partie de votre application dans une autre zone. C’est très utile pour créer des effets de reflet et des parties de l’écran.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.VisualBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint à l’aide d’un VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Rectangle peint à l’aide d’un VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Pour plus d’informations sur la classe <xref:System.Windows.Media.VisualBrush>, consultez [peinture avec des images, des dessins et](painting-with-images-drawings-and-visuals.md)des éléments visuels.  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Peindre à l’aide de pinceaux système et prédéfinis  
 Pour plus de commodité, Windows Presentation Foundation (WPF) fournit un ensemble de pinceaux système et prédéfinis que vous pouvez utiliser pour peindre des objets.  
  
- Pour obtenir la liste des pinceaux prédéfinis disponibles, consultez la classe <xref:System.Windows.Media.Brushes>. Pour obtenir un exemple illustrant l’utilisation d’un pinceau prédéfini, consultez [peindre une zone avec une couleur unie](how-to-paint-an-area-with-a-solid-color.md).  
  
- Pour obtenir la liste des pinceaux système disponibles, consultez la classe <xref:System.Windows.SystemColors>. Pour obtenir un exemple, consultez [peindre une zone avec un pinceau système](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Fonctionnalités courantes du pinceau  
 les objets <xref:System.Windows.Media.Brush> fournissent une <xref:System.Windows.Media.Brush.Opacity%2A> propriété qui peut être utilisée pour rendre un pinceau transparent ou partiellement transparent. Une <xref:System.Windows.Media.Brush.Opacity%2A> valeur de 0 rend un pinceau complètement transparent, tandis qu’une valeur de <xref:System.Windows.Media.Brush.Opacity%2A> de 1 rend un pinceau entièrement opaque. L’exemple suivant utilise la propriété <xref:System.Windows.Media.Brush.Opacity%2A> pour rendre un <xref:System.Windows.Media.SolidColorBrush> opaque à 25%.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Si le pinceau contient des couleurs partiellement transparentes, la valeur d’opacité de la couleur est combinée à la multiplication par la valeur d’opacité du pinceau. Par exemple, si un pinceau a une valeur d’opacité de 0,5 et qu’une couleur utilisée dans le pinceau a également une valeur d’opacité de 0,5, la couleur de sortie a une valeur d’opacité de 0,25.  
  
> [!NOTE]
> Il est plus efficace de modifier la valeur d’opacité d’un pinceau que de modifier l’opacité d’un élément entier à l’aide de sa propriété <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>.  
  
 Vous pouvez faire pivoter, mettre à l’échelle, incliner et traduire le contenu d’un pinceau à l’aide de ses propriétés <xref:System.Windows.Media.Brush.Transform%2A> ou <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Pour plus d’informations, consultez [vue d’ensemble](brush-transformation-overview.md)de la transformation de pinceau.  
  
 Étant donné qu’il s’agit d’objets <xref:System.Windows.Media.Animation.Animatable>, les objets <xref:System.Windows.Media.Brush> peuvent être animés. Pour plus d’informations, consultez [Vue d’ensemble de l’animation](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Fonctionnalités Freezable  
 Comme elle hérite de la classe <xref:System.Windows.Freezable>, la classe <xref:System.Windows.Media.Brush> fournit plusieurs fonctionnalités spéciales : les objets <xref:System.Windows.Media.Brush> peuvent être déclarés en tant que [ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets et clonés. En outre, tous les types de <xref:System.Windows.Media.Brush>, à l’exception des <xref:System.Windows.Media.VisualBrush> peuvent être mis en lecture seule pour améliorer les performances et rendre thread-safe.  
  
 Pour plus d’informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
 Pour plus d’informations sur la raison pour laquelle <xref:System.Windows.Media.VisualBrush> objets ne peuvent pas être figés, consultez la page type de <xref:System.Windows.Media.VisualBrush>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Peinture avec des objets d'image, de dessin et visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [Pinceaux, exemple](https://go.microsoft.com/fwlink/?LinkID=159973)
- [ImageBrush, exemple](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049) (Exemple de VisualBrush)
- [Rubriques Comment](brushes-how-to-topics.md)
- [Autres recommandations relatives aux performances](../advanced/optimizing-performance-other-recommendations.md)
