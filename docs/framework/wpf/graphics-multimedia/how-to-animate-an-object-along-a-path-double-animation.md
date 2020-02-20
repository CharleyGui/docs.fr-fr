---
title: 'Comment : animer un objet sur un tracé (animation double)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452855"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Comment : animer un objet sur un tracé (animation double)
Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> pour déplacer un objet le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise deux objets <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> pour déplacer un rectangle le long d’un tracé géométrique :  
  
- La première <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anime la <xref:System.Windows.Media.TranslateTransform.X%2A> de la <xref:System.Windows.Media.TranslateTransform> appliquée au rectangle. Le rectangle se déplace alors horizontalement sur le tracé.  
  
- La deuxième <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anime la <xref:System.Windows.Media.TranslateTransform.Y%2A> de la <xref:System.Windows.Media.TranslateTransform> appliquée au rectangle. Le rectangle se déplace alors verticalement sur le tracé.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Une autre façon de déplacer un objet à l’aide d’un tracé géométrique consiste à utiliser un objet <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>. Pour obtenir un exemple, consultez [animer un objet sur un tracé (animation de matrice)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)
