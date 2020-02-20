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
ms.openlocfilehash: 1d3a56014e0975f3616b7f90021b4290ced5daab
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453128"
---
# <a name="brush-transformation-overview"></a>Vue d'ensemble des transformations du pinceau
La classe Brush fournit deux propriétés de transformation : <xref:System.Windows.Media.Brush.Transform%2A> et <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Les propriétés vous permettent de faire pivoter, mettre à l’échelle, incliner et effectuer la translation du contenu d’un pinceau. Cette rubrique décrit les différences entre ces deux propriétés et fournit des exemples de leur utilisation.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez comprendre les fonctionnalités du pinceau que vous transformez. Pour obtenir des <xref:System.Windows.Media.LinearGradientBrush> et des <xref:System.Windows.Media.RadialGradientBrush>, consultez [vue d’ensemble de la peinture avec des couleurs unies et des dégradés](painting-with-solid-colors-and-gradients-overview.md). Pour <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>ou <xref:System.Windows.Media.VisualBrush>, consultez [peinture avec des images, des dessins et](painting-with-images-drawings-and-visuals.md)des éléments visuels. Vous devez également être familiarisé avec les transformations 2D décrites dans la [Vue d'ensemble des transformations](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Différences entre les propriétés Transform et RelativeTransform  
 Lorsque vous appliquez une transformation à la propriété <xref:System.Windows.Media.Brush.Transform%2A> d’un pinceau, vous devez connaître la taille de la zone peinte si vous souhaitez transformer le contenu du pinceau sur son centre. Supposons que la zone peinte fasse 200 dip (pixels indépendants de l’appareil) de large et 150 de hauteur.  Si vous avez utilisé un <xref:System.Windows.Media.RotateTransform> pour faire pivoter la sortie du pinceau 45 degrés autour de son centre, vous devez attribuer à l' <xref:System.Windows.Media.RotateTransform> une <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 100 et une <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 75.  
  
 Lorsque vous appliquez une transformation à la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A> d’un pinceau, cette transformation est appliquée au pinceau avant que sa sortie ne soit mappée à la zone peinte. La liste suivante décrit l’ordre dans lequel le contenu d’un pinceau est traité et transformé.  
  
1. Traitez le contenu du pinceau. Pour une <xref:System.Windows.Media.GradientBrush>, cela signifie que vous déterminez la zone de dégradé. Pour un <xref:System.Windows.Media.TileBrush>, le <xref:System.Windows.Media.TileBrush.Viewbox%2A> est mappé au <xref:System.Windows.Media.TileBrush.Viewport%2A>. Cela devient la sortie du pinceau.  
  
2. Projetez la sortie du pinceau sur le rectangle de transformation 1 x 1.  
  
3. Appliquez la <xref:System.Windows.Media.Brush.RelativeTransform%2A>du pinceau, le cas échéant.  
  
4. Projetez la sortie transformée sur la zone à peindre.  
  
5. Appliquez la <xref:System.Windows.Media.Transform>du pinceau, le cas échéant.  
  
 Étant donné que la <xref:System.Windows.Media.Brush.RelativeTransform%2A> est appliquée alors que la sortie du pinceau est mappée à un rectangle 1 x 1, les valeurs de décalage et du centre de transformation semblent être relatives. Par exemple, si vous avez utilisé un <xref:System.Windows.Media.RotateTransform> pour faire pivoter la sortie du pinceau 45 degrés autour de son centre, vous devez attribuer à l' <xref:System.Windows.Media.RotateTransform> une <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 0,5 et une <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 0,5.  
  
 L’illustration suivante montre la sortie de plusieurs pinceaux ayant subi une rotation de 45 degrés à l’aide des propriétés <xref:System.Windows.Media.Brush.RelativeTransform%2A> et <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Propriétés RelativeTransform et Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Utilisation de RelativeTransform avec TileBrush  
 Étant donné que les pinceaux de mosaïque sont plus complexes que les autres pinceaux, l’application d’un <xref:System.Windows.Media.Brush.RelativeTransform%2A> à un peut produire des résultats inattendus. Par exemple, prenons l’image suivante.  
  
 ![L’image source](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.ImageBrush> pour peindre une zone rectangulaire avec l’image précédente. Il applique une <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A> de l’objet <xref:System.Windows.Media.ImageBrush> et définit sa propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> sur <xref:System.Windows.Media.Stretch.UniformToFill>, qui doit conserver les proportions de l’image lorsqu’elle est étirée pour remplir complètement le rectangle.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Cet exemple produit la sortie suivante :  
  
 ![Sortie transformée](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Notez que l’image est déformée, même si la <xref:System.Windows.Media.TileBrush.Stretch%2A> du pinceau a été définie sur <xref:System.Windows.Media.Stretch.UniformToFill>. Cela est dû au fait que la transformation relative est appliquée après que le <xref:System.Windows.Media.TileBrush.Viewbox%2A> du pinceau est mappé à son <xref:System.Windows.Media.TileBrush.Viewport%2A>. La liste suivante décrit chaque étape du processus :  
  
1. Projetez le contenu du pinceau (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) sur sa mosaïque de base (<xref:System.Windows.Media.TileBrush.Viewport%2A>) à l’aide du paramètre de <xref:System.Windows.Media.TileBrush.Stretch%2A> du pinceau.  
  
     ![Étirer le Viewbox pour l’ajuster à la fenêtre d’affichage](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Projetez la mosaïque de base sur le rectangle de transformation 1 x 1.  
  
     ![Mapper la fenêtre d’affichage au rectangle de transformation](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Appliquez la <xref:System.Windows.Media.RotateTransform>.  
  
     ![Appliquer la transformation relative](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Projetez la mosaïque de base transformée sur la zone à peindre.  
  
     ![Projeter le pinceau transformé sur la zone de sortie](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Exemple : Rotation d’un ImageBrush de 45 degrés  
 L’exemple suivant applique une <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A> d’un <xref:System.Windows.Media.ImageBrush>. Les propriétés <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> de l’objet <xref:System.Windows.Media.RotateTransform> sont toutes deux définies sur 0,5, les coordonnées relatives du point central du contenu. Par conséquent, le contenu du pinceau pivote autour de son centre.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 L’exemple suivant applique également un <xref:System.Windows.Media.RotateTransform> à un <xref:System.Windows.Media.ImageBrush>, mais utilise la propriété <xref:System.Windows.Media.Brush.Transform%2A> à la place de la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Pour faire pivoter le pinceau autour de son centre, les <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> de l’objet <xref:System.Windows.Media.RotateTransform> doivent être définis sur des coordonnées absolues. Le rectangle peint par le pinceau étant de 175 pixels par 90, son point central est (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 L’illustration suivante montre le pinceau sans transformation, avec la transformation appliquée à la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A>, et avec la transformation appliquée à la propriété <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Paramètres Brush RelativeTransform et Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Cet exemple fait partie d’un exemple plus complet. Pour l’exemple complet, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Pour plus d’informations sur les pinceaux, consultez la [Vue d'ensemble des pinceaux WPF](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Peinture avec des objets d'image, de dessin et visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d'ensemble des transformations](transforms-overview.md)
