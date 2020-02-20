---
title: "Comment : animer un objet sur un tracé (animation de matrice avec accumulation d'offsets)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453102"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Comment : animer un objet sur un tracé (animation de matrice avec accumulation d'offsets)
Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pour animer un objet le long d’un tracé et faire en sorte que cette animation accumule ses valeurs de décalage à mesure qu’elle se répète.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’objet <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pour animer la propriété <xref:System.Windows.Media.MatrixTransform.Matrix%2A> d’un <xref:System.Windows.Media.MatrixTransform> appliqué à un bouton. Le bouton se déplace alors le long d’un tracé courbe.  
  
 En outre, l’exemple affecte à la propriété <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> la valeur `true`, ce qui entraîne l’accumulation de l’offset de la matrice animée à mesure que l’animation se répète. Étant donné que les valeurs d’offset s’accumulent, le bouton s’éloigne sur l’écran lorsque l’animation se répète, sans revenir à sa position de départ.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Notez que, bien que la propriété <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> entraîne l’accumulation des valeurs de décalage sur les répétitions, elle n’entraîne pas l’accumulation des valeurs de rotation. Pour faire en sorte que les valeurs de rotation s’accumulent, définissez les propriétés <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> et <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> de l’animation sur `true`.  
  
 Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Pour obtenir un exemple illustrant comment animer une valeur de <xref:System.Windows.Media.Matrix> le long d’un tracé sans accumulation d’offsets, consultez [animer un objet sur un tracé (animation de matrice)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)
