---
title: "Comment : animer des modifications de taille à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344653"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Comment : animer des modifications de taille à l'aide d'images clés
Cet exemple explique comment animer des modifications de taille à l’aide d’images clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.ArcSegment.Size%2A> pour <xref:System.Windows.Media.ArcSegment>animer la propriété d’un . Cette animation utilise trois images clés de la manière suivante :  
  
1. Au cours de la première moitié de <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> seconde de l’animation, utilise un exemple de la classe pour augmenter progressivement la taille de l’arc. Cadres de clés <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> linéaires comme créer une transition linéaire en douceur entre les valeurs.  
  
2. À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> utilise un exemple de la classe pour augmenter soudainement la taille de l’arc. Des cadres clés <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> discrets comme créer des sauts soudains entre les valeurs, c’est-à-dire que les changements de taille se produisent soudainement et ne sont pas subtils.  
  
3. Au cours des deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> classe pour augmenter la taille de l’arc. Les cadres clés <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété. Dans cet exemple, la taille de l’arc augmente lentement dans un premier temps, puis augmente de façon exponentielle vers la fin du segment temporel.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
