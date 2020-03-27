---
title: "Comment : animer une couleur à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344750"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Comment : animer une couleur à l'aide d'images clés
Cet exemple montre comment animer <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> le d’un en utilisant des cadres clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour <xref:System.Windows.Media.SolidColorBrush>animer la propriété d’un . Cette animation utilise trois images clés de la manière suivante :  
  
1. Pendant les deux premières secondes, <xref:System.Windows.Media.Animation.LinearColorKeyFrame> utilise une instance de la classe pour changer progressivement la couleur du vert au rouge. Cadres de clés <xref:System.Windows.Media.Animation.LinearColorKeyFrame> linéaires comme créer une transition linéaire en douceur entre les valeurs.  
  
2. À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> utilise une instance de la classe pour changer rapidement la couleur du rouge au jaune. Cadres clés discrets <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> comme créer des changements soudains entre les valeurs, c’est-à-dire, le changement de couleur dans cette partie de l’animation se produit rapidement et n’est pas subtile.  
  
3. Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplineColorKeyFrame> utilise une instance de la classe pour changer la couleur à nouveau, cette fois du jaune de retour au vert. Les cadres clés <xref:System.Windows.Media.Animation.SplineColorKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété. Dans cet exemple, le changement de couleur commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
