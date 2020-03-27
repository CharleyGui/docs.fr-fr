---
title: "Comment : animer une géométrie rectangle à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344681"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Comment : animer une géométrie rectangle à l'aide d'images clés
Cet exemple montre comment animer <xref:System.Windows.Media.RectangleGeometry.Rect%2A> la <xref:System.Windows.Media.RectangleGeometry> propriété d’un en utilisant des cadres clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.RectangleGeometry.Rect%2A> pour <xref:System.Windows.Media.RectangleGeometry>animer la propriété d’un . Cette animation utilise trois images clés de la manière suivante :  
  
1. Pendant les deux premières secondes, <xref:System.Windows.Media.Animation.LinearRectKeyFrame> utilise un exemple de la classe pour animer un changement progressif de la position, la largeur et la hauteur d’un rectangle. Cadres de clés <xref:System.Windows.Media.Animation.LinearRectKeyFrame> linéaires comme créer une transition linéaire en douceur entre les valeurs.  
  
2. À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> utilise un exemple de la classe pour diminuer soudainement la hauteur du rectangle. Des cadres clés <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> discrets comme créer des changements soudains entre les valeurs, c’est-à-dire que la diminution de la hauteur se produit rapidement et n’est pas subtile.  
  
3. Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplineRectKeyFrame> utilise une instance de la classe pour changer le rectangle de nouveau à sa taille d’origine et la position. Les cadres clés <xref:System.Windows.Media.Animation.SplineRectKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété. Dans cet exemple, le changement commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
