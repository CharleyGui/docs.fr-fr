---
title: 'Comment : Animer une rotation 3D à l’aide de storyboards'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112210"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a>Comment : Animer une rotation 3D à l’aide de storyboards
L’exemple suivant montre comment faire pivoter un objet 3D pendant <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> qu’il « vacille » en animant les propriétés et <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> les propriétés d’un <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objet. Cet <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objet spécifie la rotation de l’objet 3D et ainsi l’animation de ses propriétés crée l’effet de rotation de désir. Dans le <xref:System.Windows.Media.Animation.DoubleAnimation> Storyboard, est utilisé <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> pour <xref:System.Windows.Media.Animation.Vector3DAnimation> animer la propriété <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> tout en étant utilisé pour animer la propriété.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Animer une rotation 3D à l’aide de Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animez une rotation 3D à l’aide de cadres clés (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Vue d'ensemble des plans conceptuels](storyboards-overview.md)
