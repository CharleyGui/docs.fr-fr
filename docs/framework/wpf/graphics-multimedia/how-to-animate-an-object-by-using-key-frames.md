---
title: "Comment : animer un objet à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344704"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Comment : animer un objet à l'aide d'images clés
Cet exemple montre comment animer un objet, qui <xref:System.Windows.Controls.Page.Background%2A> dans <xref:System.Windows.Controls.Page> cet exemple est la propriété d’un contrôle, en utilisant des cadres clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> utilise la classe pour <xref:System.Windows.Controls.Page.Background%2A> animer <xref:System.Windows.Controls.Page> les changements de couleur pour la propriété d’un contrôle. L’exemple de l’animation change à un pinceau d’arrière-plan différent à intervalles réguliers. Cette animation <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> utilise la classe pour créer trois cadres clés différents. L’animation utilise des cadres clés de la manière suivante :  
  
1. À la fin de la première seconde, <xref:System.Windows.Media.LinearGradientBrush> anime un exemple de la classe. Cette section de l’exemple applique un gradient linéaire à la couleur de fond de sorte que la couleur passe du jaune à l’orange au rouge.  
  
2. À la fin de la seconde suivante, <xref:System.Windows.Media.RadialGradientBrush> anime un exemple de la classe. Cette section de l’exemple applique un gradient radial à la couleur de fond de sorte que la couleur passe du blanc au bleu au noir.  
  
3. À la fin de la troisième seconde, <xref:System.Windows.Media.DrawingBrush> anime un exemple de la classe. Cette section de l’exemple applique un modèle de damier à l’arrière-plan.  
  
4. L’animation recommence et se répète indéfiniment.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>est le seul type de cadre clé <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> que vous pouvez utiliser avec la classe. Les cadres <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> clés comme créer des changements soudains dans les valeurs, c’est-à-dire, les changements de couleur dans cet exemple se produisent soudainement.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
