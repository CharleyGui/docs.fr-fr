---
title: "Comment : animer un point à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344882"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Comment : animer un point à l'aide d'images clés
Cet exemple montre comment <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> utiliser la classe <xref:System.Windows.Point>pour animer un .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déplace une ellipse sur un tracé triangulaire. L’exemple <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.EllipseGeometry.Center%2A> pour animer la propriété d’un <xref:System.Windows.Media.EllipseGeometry>. Cette animation utilise trois images clés de la manière suivante :  
  
1. Au cours de la première moitié <xref:System.Windows.Media.Animation.LinearPointKeyFrame> de seconde, utilise un exemple de la classe pour déplacer l’ellipse le long d’un chemin à un rythme régulier à partir de sa position de départ. Cadres de clés <xref:System.Windows.Media.Animation.LinearPointKeyFrame> linéaires comme créer une interpolation linéaire lisse entre les valeurs.  
  
2. À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> utilise un exemple de la classe pour soudainement déplacer l’ellipse le long du chemin vers la position suivante. Cadres clés discrets <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> comme créer des sauts soudains entre les valeurs.  
  
3. Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplinePointKeyFrame> utilise une instance de la classe pour déplacer l’ellipse de nouveau à sa position de départ. Les cadres clés <xref:System.Windows.Media.Animation.SplinePointKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété. Dans cet exemple, l’animation commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Pour la cohérence avec d’autres exemples d’animation, les versions de code de cet exemple utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Cependant, lors de l’application d’une seule animation <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> dans le <xref:System.Windows.Media.Animation.Storyboard>code, il est plus simple d’utiliser la méthode au lieu d’utiliser un . Par exemple, voir [Animate une propriété sans utiliser un storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
