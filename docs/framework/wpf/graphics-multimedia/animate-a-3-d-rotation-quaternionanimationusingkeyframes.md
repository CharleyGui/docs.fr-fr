---
title: 'Comment : Animer une rotation 3D à l’aide de cadres clés (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112295"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Comment : Animer une rotation 3D à l’aide de cadres clés (QuaternionAnimationUsingKeyFrames)
Dans l’exemple <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> suivant, est utilisé pour faire tourner un objet 3D. Cette animation utilise les cadres clés suivants :  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>est utilisé pour créer une interpolation lisse et linéaire entre les valeurs.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>est utilisé pour créer des « sauts » soudains entre les valeurs (pas d’interpolation).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>est utilisé pour créer une transition <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variable entre les valeurs en fonction de la propriété. Dans l’exemple ci-dessous, cette partie de l’animation commence lentement mais vers la fin du segment de temps, accélère de façon exponentielle.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Animer une rotation 3D à l’aide de storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animer une rotation 3D à l’aide de Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animer une rotation 3D à l’aide de quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animez une rotation 3D à l’aide de cadres clés (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
