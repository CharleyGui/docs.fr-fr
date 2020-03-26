---
title: 'Comment : Animer une rotation 3D à l’aide de quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112243"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a>Comment : Animer une rotation 3D à l’aide de quaternions
Cet exemple montre comment animer une rotation d’un objet 3D à l’aide de quaternions.  
  
 Le code ci-dessous montre <xref:System.Windows.Media.Media3D.QuaternionRotation3D> une <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> utilisation <xref:System.Windows.Media.Media3D.RotateTransform3D>comme valeur pour la propriété d’un .  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 Ceci <xref:System.Windows.Media.Media3D.QuaternionRotation3D> est animé <xref:System.Windows.Media.Animation.QuaternionAnimation> avec <xref:System.Windows.Media.Animation.Storyboard> un dans un en utilisant le code ci-dessous.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Exemple  
 Le code suivant affiche l’échantillon entier.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Créer une scène 3D](how-to-create-a-3-d-scene.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Vue d'ensemble des transformations](transforms-overview.md)
- [Animer une rotation 3D à l’aide de storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animer une rotation 3D à l’aide de Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
