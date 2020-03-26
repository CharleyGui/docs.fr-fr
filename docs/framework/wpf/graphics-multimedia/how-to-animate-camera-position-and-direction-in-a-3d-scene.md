---
title: "Comment : animer la position et la direction d'une caméra dans une scène 3D"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3D scenes
- camera direction [WPF], animating in 3D scenes
- 3D scenes [WPF], animating camera position
- 3D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3D scenes
- animation [WPF], camera direction in 3D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 5ce94e154cd5aa29b59260f893ec2b63a08db0fc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112207"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Comment : animer la position et la direction d'une caméra dans une scène 3D
L’exemple suivant montre comment animer la position d’une caméra et animer la direction qu’elle pointe dans une scène 3D. Ceci est fait <xref:System.Windows.Media.Animation.Point3DAnimation> <xref:System.Windows.Media.Animation.Vector3DAnimation> en utilisant et <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> pour animer <xref:System.Windows.Media.Media3D.PerspectiveCamera>le et les propriétés respectivement de la . Vous pouvez utiliser une animation comme celle-ci pour changer la vue du spectateur d’une scène en réponse à un événement.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [Animer la position et la direction de la caméra à l’aide d’images clés](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
