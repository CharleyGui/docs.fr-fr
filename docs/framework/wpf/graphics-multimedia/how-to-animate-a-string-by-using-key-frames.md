---
title: "Comment : animer une chaîne à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344671"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Comment : animer une chaîne à l'aide d'images clés
Cet exemple montre comment animer une chaîne, qui <xref:System.Windows.Controls.ContentControl.Content%2A> dans <xref:System.Windows.Controls.Button> cet exemple est la propriété d’un contrôle, en utilisant des cadres clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Controls.ContentControl.Content%2A> pour <xref:System.Windows.Controls.Button>animer la propriété d’un .  
  
 Toutes les images clés de cet exemple <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> utilisent un exemple de la classe parce qu’une animation de chaîne qui est créée avec des cadres clés ne peut utiliser que des cadres clés discrets. Les cadres clés <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> discrets comme créer des sauts soudains entre les valeurs, c’est-à-dire, les changements à l’animation se produisent rapidement et ne sont pas subtils.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
