---
title: 'Comment : Animer une rotation 3D à l’aide de cadres clés'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112308"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a>Comment : Animer une rotation 3D à l’aide de cadres clés
Dans l’exemple <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> suivant, est utilisé pour faire tourner un objet 3D tandis que son axe de rotation anime résultant en un "wobble". Cette animation utilise les cadres clés suivants :  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>est utilisé pour créer une interpolation lisse et linéaire entre les valeurs.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>est utilisé pour créer des « sauts » soudains entre les valeurs (pas d’interpolation).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>est utilisé pour créer une transition <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variable entre les valeurs en fonction de la propriété. Dans l’exemple ci-dessous, cette partie de l’animation commence lentement mais vers la fin du segment de temps, accélère de façon exponentielle.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Animer une rotation 3D à l’aide de storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animer une rotation 3D à l’aide de Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animer une rotation 3D à l’aide de quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animez une rotation 3D à l’aide de cadres clés (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
