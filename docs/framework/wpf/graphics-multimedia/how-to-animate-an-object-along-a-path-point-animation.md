---
title: 'Comment : animer un objet sur un tracé (animation de point)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452894"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Comment : animer un objet sur un tracé (animation de point)
Cet exemple montre comment utiliser un objet <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pour animer une <xref:System.Windows.Point> le long d’un tracé courbé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déplace un <xref:System.Windows.Media.EllipseGeometry> le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>. La propriété de <xref:System.Windows.Media.EllipseGeometry.Center%2A> de la géométrie d’ellipse, qui prend une valeur de <xref:System.Windows.Point>, spécifie sa position ; pour déplacer la géométrie d’ellipse, vous animez sa propriété <xref:System.Windows.Media.EllipseGeometry.Center%2A>. L’exemple utilise une <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pour animer la propriété <xref:System.Windows.Media.EllipseGeometry.Center%2A> de l’objet <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 La version de code de l’exemple précédent utilisait une <xref:System.Windows.Media.Animation.Storyboard> pour animer le <xref:System.Windows.Media.EllipseGeometry>, même si une seule animation a été appliquée. Un <xref:System.Windows.Media.Animation.Storyboard> est souvent le moyen le plus simple d’appliquer plusieurs animations, car ces animations peuvent être contrôlées par le même <xref:System.Windows.Media.Animation.Storyboard>. Toutefois, un moyen plus simple d’appliquer une seule animation à une propriété lors de l’utilisation du code consiste à utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>. Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi

- [Animation de tracés, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)
