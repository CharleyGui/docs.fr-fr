---
title: Vue d'ensemble des transformations du pinceau
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: deac1be2fd19703055b76af8173111b4453f0d6b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186528"
---
# <a name="brush-transformation-overview"></a>Vue d'ensemble des transformations du pinceau
La classe Brosse offre <xref:System.Windows.Media.Brush.Transform%2A> deux <xref:System.Windows.Media.Brush.RelativeTransform%2A>propriétés de transformation: et . Les propriétés vous permettent de faire pivoter, mettre à l’échelle, incliner et effectuer la translation du contenu d’un pinceau. Cette rubrique décrit les différences entre ces deux propriétés et fournit des exemples de leur utilisation.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez comprendre les fonctionnalités du pinceau que vous transformez. Pour <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>et , voir la [peinture avec des couleurs solides et Gradients Aperçu](painting-with-solid-colors-and-gradients-overview.md). Pour <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush>, ou , voir [Peinture avec des images, des dessins et des visuels](painting-with-images-drawings-and-visuals.md). Vous devez également être familiarisé avec les transformations 2D décrites dans la [Vue d'ensemble des transformations](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Différences entre les propriétés Transform et RelativeTransform  
 Lorsque vous appliquez une transformation <xref:System.Windows.Media.Brush.Transform%2A> à la propriété d’un pinceau, vous devez connaître la taille de la zone peinte si vous voulez transformer le contenu du pinceau sur son centre. Supposons que la zone peinte fasse 200 dip (pixels indépendants de l’appareil) de large et 150 de hauteur.  Si vous <xref:System.Windows.Media.RotateTransform> avez utilisé un pour faire pivoter la sortie de la <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> brosse 45 degrés <xref:System.Windows.Media.RotateTransform.CenterY%2A> sur son centre, vous donneriez l’un de 100 et un de 75.  
  
 Lorsque vous appliquez une transformation <xref:System.Windows.Media.Brush.RelativeTransform%2A> à la propriété d’un pinceau, cette transformation est appliquée sur le pinceau avant que sa sortie ne soit cartographiée sur la zone peinte. La liste suivante décrit l’ordre dans lequel le contenu d’un pinceau est traité et transformé.  
  
1. Traitez le contenu du pinceau. Pour <xref:System.Windows.Media.GradientBrush>un , cela signifie déterminer la zone de gradient. Pour <xref:System.Windows.Media.TileBrush>un <xref:System.Windows.Media.TileBrush.Viewbox%2A> , le est <xref:System.Windows.Media.TileBrush.Viewport%2A>cartographié à la . Cela devient la sortie du pinceau.  
  
2. Projetez la sortie du pinceau sur le rectangle de transformation 1 x 1.  
  
3. Appliquer le <xref:System.Windows.Media.Brush.RelativeTransform%2A>pinceau, si elle en a un.  
  
4. Projetez la sortie transformée sur la zone à peindre.  
  
5. Appliquer le <xref:System.Windows.Media.Transform>pinceau, si elle en a un.  
  
 Parce <xref:System.Windows.Media.Brush.RelativeTransform%2A> que le est appliqué tandis que la sortie du pinceau est cartographiée sur un rectangle de 1 x 1, transformer le centre et les valeurs de compensation semblent être relatifs. Par exemple, si <xref:System.Windows.Media.RotateTransform> vous utiliez un pour faire pivoter la sortie de <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> la brosse de 45 degrés sur son centre, vous donneriez un de 0,5 et un <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 0,5.  
  
 L’illustration suivante montre la sortie de plusieurs brosses qui ont <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A> été tournées de 45 degrés à l’aide de la propriété et des propriétés.  
  
 ![Propriétés RelativeTransform et Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>
## <a name="using-relativetransform-with-a-tilebrush"></a>Utilisation de RelativeTransform avec TileBrush  
 Étant donné que les brosses à carreaux <xref:System.Windows.Media.Brush.RelativeTransform%2A> sont plus complexes que les autres brosses, l’application d’un à un pourrait produire des résultats inattendus. Par exemple, prenons l’image suivante.  
  
 ![Image source](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 L’exemple suivant <xref:System.Windows.Media.ImageBrush> utilise un pour peindre une zone rectangulaire avec l’image précédente. <xref:System.Windows.Media.RotateTransform> Il s’applique <xref:System.Windows.Media.ImageBrush> à <xref:System.Windows.Media.Brush.RelativeTransform%2A> la propriété de <xref:System.Windows.Media.TileBrush.Stretch%2A> l’objet, et définit sa propriété à <xref:System.Windows.Media.Stretch.UniformToFill>, qui doit préserver le rapport d’aspect de l’image quand il est étiré pour remplir complètement le rectangle.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Cet exemple produit la sortie suivante :  
  
 ![Sortie transformée](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Notez que l’image est déformée, <xref:System.Windows.Media.TileBrush.Stretch%2A> même <xref:System.Windows.Media.Stretch.UniformToFill>si le pinceau a été réglé à . C’est parce que la transformation relative <xref:System.Windows.Media.TileBrush.Viewbox%2A> est appliquée après <xref:System.Windows.Media.TileBrush.Viewport%2A>le pinceau est cartographié à son . La liste suivante décrit chaque étape du processus :  
  
1. Projetez le contenu<xref:System.Windows.Media.TileBrush.Viewbox%2A>du pinceau ()<xref:System.Windows.Media.TileBrush.Viewport%2A>sur sa tuile <xref:System.Windows.Media.TileBrush.Stretch%2A> de base () à l’aide du réglage de la brosse.  
  
     ![Étirement de la fenêtre pour adapter à la fenêtre d'affichage](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Projetez la mosaïque de base sur le rectangle de transformation 1 x 1.  
  
     ![Mappage de la fenêtre d'affichage et du rectangle de transformation](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Appliquer <xref:System.Windows.Media.RotateTransform>le .  
  
     ![Application de la transformation relative](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Projetez la mosaïque de base transformée sur la zone à peindre.  
  
     ![Projection du pinceau transformé sur la zone de sortie](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Exemple : Rotation d’un ImageBrush de 45 degrés  
 L’exemple suivant <xref:System.Windows.Media.RotateTransform> s’applique à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété d’un <xref:System.Windows.Media.ImageBrush>. L’objet <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> les propriétés sont tous deux réglés à 0,5, les coordonnées relatives du point central du contenu. Par conséquent, le contenu du pinceau pivote autour de son centre.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 L’exemple suivant <xref:System.Windows.Media.RotateTransform> s’applique également à un <xref:System.Windows.Media.ImageBrush>, mais utilise la <xref:System.Windows.Media.Brush.Transform%2A> propriété au lieu de la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété. Pour faire pivoter la <xref:System.Windows.Media.RotateTransform> brosse sur <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> son centre, l’objet et doit être réglé sur des coordonnées absolues. Le rectangle peint par le pinceau étant de 175 pixels par 90, son point central est (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 L’illustration suivante montre le pinceau sans transformation, <xref:System.Windows.Media.Brush.RelativeTransform%2A> avec la transformation appliquée <xref:System.Windows.Media.Brush.Transform%2A> à la propriété, et avec la transformation appliquée à la propriété.  
  
 ![Paramètres de Brush RelativeTransform et Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Cet exemple fait partie d’un exemple plus complet. Pour l’exemple complet, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Pour plus d’informations sur les pinceaux, consultez la [Vue d'ensemble des pinceaux WPF](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d'ensemble des transformations](transforms-overview.md)
