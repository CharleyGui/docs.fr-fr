---
title: 'Procédure : Animer une matrice à l’aide d’images clés'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963026"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Procédure : Animer une matrice à l’aide d’images clés
Cet exemple montre comment animer la <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriété d’un <xref:System.Windows.Media.MatrixTransform> à l’aide d’images clés.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise la <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> classe pour animer <xref:System.Windows.Media.MatrixTransform.Matrix%2A> la propriété d' <xref:System.Windows.Media.MatrixTransform>un. L’exemple utilise l' <xref:System.Windows.Media.MatrixTransform> objet pour transformer l’apparence et la position d' <xref:System.Windows.Controls.Button>un.  
  
 Cette animation utilise la <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> classe pour créer deux images clés et effectue les opérations suivantes:  
  
1. Anime le premier <xref:System.Windows.Media.Matrix> pendant les 0,2 premières secondes. L’exemple modifie les <xref:System.Windows.Media.Matrix.M11%2A> propriétés <xref:System.Windows.Media.Matrix.M12%2A> et de <xref:System.Windows.Media.Matrix>. Cette modification entraîne l’étirement et l’inclinaison du bouton. L’exemple modifie également les <xref:System.Windows.Media.Matrix.OffsetX%2A> propriétés <xref:System.Windows.Media.Matrix.OffsetY%2A> et afin que le bouton change de position.  
  
2. Anime la seconde <xref:System.Windows.Media.Matrix> à 1,0 secondes. Le bouton se déplace vers une autre position lorsque le bouton n’est plus incliné ou étiré.  
  
3. Répète l’animation indéfiniment.  
  
> [!NOTE]
> Les images clés qui dérivent de l' <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objet créent des sauts soudains entre les valeurs, autrement dit, le mouvement de l’animation est saccadé.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
