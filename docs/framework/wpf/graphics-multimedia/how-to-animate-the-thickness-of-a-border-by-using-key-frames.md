---
title: "Comment : animer l'épaisseur d'une bordure à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344690"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Comment : animer l'épaisseur d'une bordure à l'aide d'images clés
Cet exemple montre comment animer <xref:System.Windows.Controls.Control.BorderThickness%2A> la <xref:System.Windows.Controls.Border>propriété d’un .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Controls.Control.BorderThickness%2A> pour <xref:System.Windows.Controls.Border>animer la propriété d’un . Cette animation utilise trois images clés de la manière suivante :  
  
1. Au cours de la première moitié <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> de seconde, utilise un exemple de la classe pour augmenter progressivement l’épaisseur de la frontière. L’exemple <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> sert à créer une augmentation linéaire lisse entre les valeurs.  
  
2. À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> utilise un exemple de la classe pour augmenter soudainement l’épaisseur de la frontière. Cadres clés discrets comme <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> ceux dérivés de créer des sauts soudains entre les valeurs, c’est-à-dire, le mouvement de l’animation est saccadée.  
  
3. Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> utilise un exemple de la classe pour diminuer l’épaisseur de la bordure. Les cadres clés de Spline comme ceux dérivés de <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> créer <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> une transition variable entre les valeurs en fonction des valeurs de la propriété. Dans cette image clé, l’animation commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
- [Animer une valeur BorderThickness](../controls/how-to-animate-a-borderthickness-value.md)
