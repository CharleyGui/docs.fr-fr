---
title: 'Procédure : Animer un objet à l’aide d’images clés'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933905"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Procédure : Animer un objet à l’aide d’images clés
Cet exemple montre comment animer un objet, qui, dans cet exemple, <xref:System.Windows.Controls.Page.Background%2A> est la propriété <xref:System.Windows.Controls.Page> d’un contrôle, à l’aide d’images clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe pour animer des modifications de <xref:System.Windows.Controls.Page.Background%2A> couleur pour la <xref:System.Windows.Controls.Page> propriété d’un contrôle. L’exemple d’animation change en un pinceau d’arrière-plan différent à intervalles réguliers. Cette animation utilise la <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> classe pour créer trois images clés différentes. L’animation utilise des images clés de la manière suivante:  
  
1. À la fin de la première seconde, anime une instance de la <xref:System.Windows.Media.LinearGradientBrush> classe. Cette section de l’exemple applique un dégradé linéaire à la couleur d’arrière-plan afin que la couleur passe du jaune au rouge.  
  
2. À la fin de la seconde suivante, anime une instance de la <xref:System.Windows.Media.RadialGradientBrush> classe. Cette section de l’exemple applique un dégradé radial à la couleur d’arrière-plan afin que la couleur passe du blanc au bleu et au noir.  
  
3. À la fin de la troisième seconde, anime une instance de la <xref:System.Windows.Media.DrawingBrush> classe. Cette section de l’exemple applique un modèle de damier à l’arrière-plan.  
  
4. L’animation recommence et se répète indéfiniment.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>est le seul type d’image clé que vous pouvez utiliser avec la <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe. Les images clés <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> telles que créent des changements soudains dans les valeurs, autrement dit, les modifications de couleur dans cet exemple se produisent soudainement.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
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
