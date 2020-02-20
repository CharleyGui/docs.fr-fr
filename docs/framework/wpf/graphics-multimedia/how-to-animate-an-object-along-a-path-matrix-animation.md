---
title: 'Comment : animer un objet sur un tracé (animation de matrice)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452907"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Comment : animer un objet sur un tracé (animation de matrice)
Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pour animer un objet le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant anime un objet sur un tracé de la manière suivante :  
  
- Applique une <xref:System.Windows.Media.MatrixTransform> à l’objet pour le déplacer.  
  
- Définit le chemin d’accès à l’aide d’un <xref:System.Windows.Media.PathGeometry>.  
  
- Crée un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> et l’utilise pour animer la propriété <xref:System.Windows.Media.Matrix> du <xref:System.Windows.Media.MatrixTransform>. Le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> prend le <xref:System.Windows.Media.PathGeometry> et l’utilise pour générer des valeurs de <xref:System.Windows.Media.Matrix>.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Pour plus d’informations sur les tracés géométriques, consultez [vue d’ensemble de Geometry](geometry-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Animation de tracés, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)
