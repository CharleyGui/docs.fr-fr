---
title: "Comment : animer un double à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344938"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Comment : animer un double à l'aide d'images clés
Cet exemple montre comment animer la valeur d’une propriété qui prend un <xref:System.Double> en utilisant des cadres clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déplace un rectangle sur l’écran. L’exemple <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.TranslateTransform.X%2A> pour animer la propriété d’un <xref:System.Windows.Media.TranslateTransform> appliqué à un <xref:System.Windows.Shapes.Rectangle>. Cette animation, répétée indéfiniment, utilise trois images clés de la manière suivante :  
  
1. Pendant les trois premières secondes, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> utilise une instance de la classe pour déplacer le rectangle le long d’un chemin à un rythme régulier de sa position de départ à la position 500. Cadres de clés <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> linéaires comme créer une transition linéaire en douceur entre les valeurs.  
  
2. À la fin de la quatrième seconde, utilise une instance de la <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> classe pour soudainement déplacer le rectangle à la position suivante. Cadres clés discrets <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> comme créer des sauts soudains entre les valeurs. Dans cet exemple, le rectangle se trouve à la position de départ et passe subitement à la position 500.  
  
3. Dans les deux dernières secondes, <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> utilise une instance de la classe pour déplacer le rectangle vers sa position de départ. Les cadres clés <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> variable entre les valeurs en fonction de la valeur de la propriété. Dans cet exemple, le rectangle commence par se déplacer lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Pour la cohérence avec d’autres exemples d’animation, les versions de code de cet exemple utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer le <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Alternativement, lors de l’application d’une seule <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> animation dans le <xref:System.Windows.Media.Animation.Storyboard>code, il est plus simple d’utiliser la méthode au lieu d’utiliser un . Par exemple, voir [Animate une propriété sans utiliser un storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
