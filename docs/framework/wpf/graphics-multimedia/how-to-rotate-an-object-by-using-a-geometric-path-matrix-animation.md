---
title: "Comment : faire pivoter un objet à l'aide d'un tracé géométrique (animation de matrice)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187413"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Comment : faire pivoter un objet à l'aide d'un tracé géométrique (animation de matrice)
Cet exemple montre comment <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> utiliser <xref:System.Windows.Media.MatrixTransform> un et un pour faire pivoter <xref:System.Windows.Media.PathGeometry> (pivot) un objet le long d’un chemin géométrique défini par un objet.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> utilise l’objet <xref:System.Windows.Media.MatrixTransform.Matrix%2A> pour <xref:System.Windows.Media.MatrixTransform>animer la propriété d’un . Le <xref:System.Windows.Media.MatrixTransform> est appliqué sur un bouton et le fait se déplacer le long d’un chemin incurvé. Parce <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> que la `true`propriété est réglée à , le rectangle tourne le long de la tangente du chemin.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Pour l’échantillon complet, voir [Échantillon d’animation Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 La version de code de <xref:System.Windows.Media.Animation.Storyboard> l’échantillon <xref:System.Windows.Media.EllipseGeometry>précédent a utilisé un pour animer le , même si une seule animation a été appliquée. Un moyen plus facile d’appliquer une seule animation <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> à une propriété en code est d’utiliser la méthode. Par exemple, voir [Animate une propriété sans utiliser un storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)
- [Animation de tracés, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
