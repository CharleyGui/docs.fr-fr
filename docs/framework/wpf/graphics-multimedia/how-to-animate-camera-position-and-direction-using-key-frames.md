---
title: "Comment : animer la position et la direction d'une caméra à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112165"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Comment : animer la position et la direction d'une caméra à l'aide d'images clés
Dans l’exemple <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> suivant, est utilisé pour <xref:System.Windows.Media.Media3D.PerspectiveCamera> animer la position d’une scène 3D. En outre, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> est utilisé pour animer la direction de la caméra est pointant dans la scène 3D. Ces deux animations utilisent plusieurs cadres clés qui créent une série d’effets d’animation :  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>et <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> sont utilisés pour créer une interpolation lisse et linéaire entre les valeurs.  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>et <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> sont utilisés pour créer des « sauts » soudains entre les valeurs (pas d’interpolation).  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>et <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> sont utilisés pour créer une transition <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> variable entre les valeurs en fonction de la propriété. Dans l’exemple ci-dessous, l’animation commence lentement, mais vers la fin du segment de temps, accélère de façon exponentielle.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Animer la position et la direction de la caméra d’une scène 3D](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
