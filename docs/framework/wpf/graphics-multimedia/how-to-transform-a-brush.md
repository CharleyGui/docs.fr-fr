---
title: 'Comment : transformer un pinceau'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187336"
---
# <a name="how-to-transform-a-brush"></a>Comment : transformer un pinceau
Cet exemple montre <xref:System.Windows.Media.Brush> comment transformer les objets <xref:System.Windows.Media.Brush.RelativeTransform%2A> en <xref:System.Windows.Media.Brush.Transform%2A>utilisant leurs deux propriétés de transformation : et .  
  
 Les exemples <xref:System.Windows.Media.RotateTransform> suivants utilisent un <xref:System.Windows.Media.ImageBrush> pour faire pivoter le contenu d’un de 45 degrés.  
  
 L’illustration suivante <xref:System.Windows.Media.ImageBrush> montre <xref:System.Windows.Media.RotateTransform>l’sans a <xref:System.Windows.Media.Brush.RelativeTransform%2A> , avec <xref:System.Windows.Media.RotateTransform> l’appliqué <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.RotateTransform> à la propriété, et avec l’appliqué à la propriété.  
  
 ![Paramètres de Brush RelativeTransform et Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a> Exemple  
 Le premier exemple <xref:System.Windows.Media.RotateTransform> s’applique à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété d’un <xref:System.Windows.Media.ImageBrush>. Les <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés <xref:System.Windows.Media.RotateTransform> et les propriétés d’un objet sont toutes deux réglées à 0,5, qui est la coordination relative du point central de ce contenu. En conséquence, <xref:System.Windows.Media.ImageBrush> le contenu tourne autour de son centre.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Le deuxième exemple <xref:System.Windows.Media.RotateTransform> s’applique également à un <xref:System.Windows.Media.ImageBrush>; cependant, cet exemple <xref:System.Windows.Media.Brush.Transform%2A> utilise la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété au lieu de la propriété.  
  
 Pour faire pivoter le pinceau sur <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> son centre, l’exemple définit les propriétés et les propriétés de l’objet <xref:System.Windows.Media.RotateTransform> à des coordonnées absolues. Étant donné que le pinceau peint un rectangle de 175 par 90 pixels, le point central du rectangle est (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Pour une description <xref:System.Windows.Media.Brush.RelativeTransform%2A> du <xref:System.Windows.Media.Brush.Transform%2A> fonctionnement et des propriétés, consultez l’aperçu de la [transformation du pinceau.](brush-transformation-overview.md)  
  
 Pour l’exemple complet, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Pour plus d’informations sur les pinceaux, consultez [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des transformations du pinceau](brush-transformation-overview.md)
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Vue d'ensemble des transformations](transforms-overview.md)
