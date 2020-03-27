---
title: "Comment : animer une matrice à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344916"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Comment : animer une matrice à l'aide d'images clés
Cet exemple montre comment animer <xref:System.Windows.Media.MatrixTransform.Matrix%2A> la <xref:System.Windows.Media.MatrixTransform> propriété d’un en utilisant des cadres clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.MatrixTransform.Matrix%2A> pour <xref:System.Windows.Media.MatrixTransform>animer la propriété d’un . L’exemple <xref:System.Windows.Media.MatrixTransform> utilise l’objet pour transformer <xref:System.Windows.Controls.Button>l’apparence et la position d’un .  
  
 Cette animation <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> utilise la classe pour créer deux cadres clés et fait ce qui suit avec eux:  
  
1. Animates le <xref:System.Windows.Media.Matrix> premier au cours des 0,2 premières secondes. L’exemple <xref:System.Windows.Media.Matrix.M11%2A> change <xref:System.Windows.Media.Matrix.M12%2A> le <xref:System.Windows.Media.Matrix>et les propriétés de la . Ce changement provoque l’étirement du bouton et devient biaisé. L’exemple modifie <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> également les propriétés et les propriétés de sorte que le bouton change de position.  
  
2. Animates la <xref:System.Windows.Media.Matrix> seconde à 1,0 seconde. Le bouton se déplace vers une autre position tandis que le bouton n’est plus biaisé ou étiré.  
  
3. Répète l’animation indéfiniment.  
  
> [!NOTE]
> Les cadres clés qui <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> dérivent de l’objet créent des sauts soudains entre les valeurs, c’est-à-dire que le mouvement de l’animation est saccadédant.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
