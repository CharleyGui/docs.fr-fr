---
title: Aperçu des brosses
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186579"
---
# <a name="wpf-brushes-overview"></a>Vue d'ensemble des pinceaux WPF
Tout ce qui est visible sur votre écran est visible parce qu’il a été peint par un pinceau. Par exemple, une brosse est utilisée pour décrire l’arrière-plan d’un bouton, le premier plan du texte et le remplissage d’une forme. Ce sujet introduit les concepts [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de peinture avec des pinceaux et fournit des exemples. Les pinceaux permettent de peindre des objets de l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aussi bien avec de simples couleurs unies qu’avec des ensembles complexes de modèles et d’images.  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>Peinture avec un pinceau  
 Un <xref:System.Windows.Media.Brush> "peint" une zone avec sa sortie. Des pinceaux différents ont différents types de sortie. Certains pinceaux peignent une zone avec une couleur solide, d’autres avec un gradient, un motif, une image ou un dessin. L’illustration suivante montre des <xref:System.Windows.Media.Brush> exemples de chacun des différents types.  
  
 ![Types de pinceau](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Exemples de brosse  
  
 La plupart des objets visuels vous permettent de spécifier comment ils sont peints. Le tableau suivant répertorie certains objets <xref:System.Windows.Media.Brush>et propriétés communs avec lesquels vous pouvez utiliser un .  
  
|Classe|Propriétés de pinceau|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Les sections suivantes <xref:System.Windows.Media.Brush> décrivent les différents types et fournissent un exemple de chacune.  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>Peinture avec une couleur solide  
 Un <xref:System.Windows.Media.SolidColorBrush> peint une zone <xref:System.Windows.Media.Color>avec un solide . Il existe une variété de <xref:System.Windows.Media.SolidColorBrush.Color%2A> façons <xref:System.Windows.Media.SolidColorBrush>de spécifier le d’un : par exemple, vous pouvez spécifier <xref:System.Windows.Media.Colors> ses canaux alpha, rouge, bleu et vert ou utiliser l’une des couleurs prédéfinie fournies par la classe.  
  
 L’exemple suivant <xref:System.Windows.Media.SolidColorBrush> utilise <xref:System.Windows.Shapes.Shape.Fill%2A> un <xref:System.Windows.Shapes.Rectangle>pour peindre le d’un . L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Un rectangle peint à l’aide d’un solidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.SolidColorBrush> classe, voir Painting with Solid Colors and [Gradients Aperçu](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>Peinture avec un gradient linéaire  
 Un <xref:System.Windows.Media.LinearGradientBrush> peint une zone avec un gradient linéaire. Un gradient linéaire mélange deux couleurs ou plus à travers une ligne, l’axe de gradient. Vous <xref:System.Windows.Media.GradientStop> utilisez des objets pour spécifier les couleurs dans le gradient et leurs positions.  
  
 L’exemple suivant <xref:System.Windows.Media.LinearGradientBrush> utilise <xref:System.Windows.Shapes.Shape.Fill%2A> un <xref:System.Windows.Shapes.Rectangle>pour peindre le d’un . L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Un rectangle peint à l’aide d’un pinceau Linéaire  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.LinearGradientBrush> classe, voir Painting with Solid Colors and [Gradients Aperçu](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>Peinture avec un Gradient Radial  
 Un <xref:System.Windows.Media.RadialGradientBrush> peint une zone avec un gradient radial. Un gradient radial mélange deux couleurs ou plus à travers un cercle. Comme avec <xref:System.Windows.Media.LinearGradientBrush> la classe, vous utilisez des <xref:System.Windows.Media.GradientStop> objets pour spécifier les couleurs dans le gradient et leurs positions.  
  
 L’exemple suivant <xref:System.Windows.Media.RadialGradientBrush> utilise <xref:System.Windows.Shapes.Shape.Fill%2A> un <xref:System.Windows.Shapes.Rectangle>pour peindre le d’un . L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Un rectangle peint à l’aide d’un pinceau RadialGradient  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.RadialGradientBrush> classe, voir Painting with Solid Colors and [Gradients Aperçu](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>Peinture avec une image  
 Un <xref:System.Windows.Media.ImageBrush> peint une zone <xref:System.Windows.Media.ImageSource>avec un .  
  
 L’exemple suivant <xref:System.Windows.Media.ImageBrush> utilise <xref:System.Windows.Shapes.Shape.Fill%2A> un <xref:System.Windows.Shapes.Rectangle>pour peindre le d’un . L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Un rectangle peint à l’aide d’une image  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.ImageBrush> classe, voir Painting with [Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>Peinture avec un dessin  
 Un <xref:System.Windows.Media.DrawingBrush> peint une zone <xref:System.Windows.Media.Drawing>avec un . A <xref:System.Windows.Media.Drawing> peut contenir des formes, des images, du texte et des supports.  
  
 L’exemple suivant <xref:System.Windows.Media.DrawingBrush> utilise <xref:System.Windows.Shapes.Shape.Fill%2A> un <xref:System.Windows.Shapes.Rectangle>pour peindre le d’un . L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Un rectangle peint à l’aide d’un pinceau à dessin  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.DrawingBrush> classe, voir Painting with [Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>Peinture avec un visuel  
 Un <xref:System.Windows.Media.VisualBrush> peint une zone <xref:System.Windows.Media.Visual> avec un objet. Exemples d’objets <xref:System.Windows.Controls.Page>visuels <xref:System.Windows.Controls.MediaElement>comprennent <xref:System.Windows.Controls.Button>, , et . A <xref:System.Windows.Media.VisualBrush> vous permet également de projeter le contenu d’une partie de votre application dans une autre zone ; il est très utile pour créer des effets de réflexion et grossir des parties de l’écran.  
  
 L’exemple suivant <xref:System.Windows.Media.VisualBrush> utilise <xref:System.Windows.Shapes.Shape.Fill%2A> un <xref:System.Windows.Shapes.Rectangle>pour peindre le d’un . L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Un rectangle peint à l’aide d’un pinceau VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.VisualBrush> classe, voir Painting with [Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>Peinture à l’aide de brosses prédéfinies et système  
 Pour plus de commodité, Windows Presentation Foundation (WPF) fournit un ensemble de brosses prédéfinies et système que vous pouvez utiliser pour peindre des objets.  
  
- Pour une liste de brosses prédéfinie disponibles, consultez la <xref:System.Windows.Media.Brushes> classe. Pour un exemple montrant comment utiliser un pinceau prédéfini, voir [Peindre une zone avec une couleur solide](how-to-paint-an-area-with-a-solid-color.md).  
  
- Pour une liste des brosses <xref:System.Windows.SystemColors> système disponibles, voir la classe. Par exemple, voir [Peindre une zone avec un pinceau système](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>Caractéristiques communes de brosse  
 <xref:System.Windows.Media.Brush>les objets <xref:System.Windows.Media.Brush.Opacity%2A> fournissent une propriété qui peut être utilisée pour rendre un pinceau transparent ou partiellement transparent. Une <xref:System.Windows.Media.Brush.Opacity%2A> valeur de 0 rend un <xref:System.Windows.Media.Brush.Opacity%2A> pinceau complètement transparent, tandis qu’une valeur de 1 rend un pinceau complètement opaque. L’exemple suivant <xref:System.Windows.Media.Brush.Opacity%2A> utilise la <xref:System.Windows.Media.SolidColorBrush> propriété pour rendre un 25 pour cent opaque.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Si le pinceau contient des couleurs partiellement transparentes, la valeur de l’opacité de la couleur est combinée par multiplication avec la valeur d’opacité du pinceau. Par exemple, si un pinceau a une valeur d’opacité de 0,5 et une couleur utilisée dans le pinceau a également une valeur d’opacité de 0,5, la couleur de sortie a une valeur d’opacité de 0,25.  
  
> [!NOTE]
> Il est plus efficace de changer la valeur opacité d’un pinceau que de <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> changer l’opacité d’un élément entier en utilisant sa propriété.  
  
 Vous pouvez faire pivoter, évoluer, biaiser et <xref:System.Windows.Media.Brush.Transform%2A> traduire <xref:System.Windows.Media.Brush.RelativeTransform%2A> le contenu d’un pinceau en utilisant son ou ses propriétés. Pour plus d’informations, voir [Aperçu de la transformation du pinceau](brush-transformation-overview.md).  
  
 Parce qu’ils sont <xref:System.Windows.Media.Animation.Animatable> des objets, <xref:System.Windows.Media.Brush> les objets peuvent être animés. Pour plus d’informations, voir [Aperçu animation](animation-overview.md).  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Fonctionnalités Freezable  
 Parce qu’il <xref:System.Windows.Freezable> hérite <xref:System.Windows.Media.Brush> de la classe, <xref:System.Windows.Media.Brush> la classe fournit plusieurs caractéristiques spéciales: les objets peuvent être déclarés comme [des ressources,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)partagés entre plusieurs objets, et clonés. En outre, <xref:System.Windows.Media.Brush> tous <xref:System.Windows.Media.VisualBrush> les types sauf peuvent être faits lus-seulement pour améliorer les performances et fait thread-safe.  
  
 Pour plus d’informations sur <xref:System.Windows.Freezable> les différentes fonctionnalités fournies par les objets, voir [Freezable Objects Overview](../advanced/freezable-objects-overview.md).  
  
 Pour plus d’informations sur les raisons pour lesquelles <xref:System.Windows.Media.VisualBrush> les objets ne peuvent pas être congelés, consultez la page type. <xref:System.Windows.Media.VisualBrush>  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [Pinceaux, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush) (Exemple d’ImageBrush)
- [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush) (Exemple de VisualBrush)
- [Sujets comment se passer](brushes-how-to-topics.md)
- [Autres recommandations relatives aux performances](../advanced/optimizing-performance-other-recommendations.md)
