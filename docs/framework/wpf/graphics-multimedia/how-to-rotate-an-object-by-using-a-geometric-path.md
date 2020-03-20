---
title: "Comment : faire pivoter un objet à l'aide d'un tracé géométrique"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186877"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Comment : faire pivoter un objet à l'aide d'un tracé géométrique
Cet exemple montre comment faire pivoter (pivot) un objet <xref:System.Windows.Media.PathGeometry> le long d’un chemin géométrique défini par un objet.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> utilise trois objets pour déplacer un rectangle le long d’un chemin géométrique.  
  
- Le <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> premier anime <xref:System.Windows.Media.RotateTransform> un qui est appliqué sur le rectangle. L’animation génère des valeurs d’angle. Le rectangle tourne (pivote) ainsi sur les contours du tracé.  
  
- Les deux autres objets <xref:System.Windows.Media.TranslateTransform.X%2A> animent les valeurs et <xref:System.Windows.Media.TranslateTransform.Y%2A> les valeurs d’un <xref:System.Windows.Media.TranslateTransform> qui est appliqué sur le rectangle. Le rectangle se déplace alors horizontalement et verticalement sur le tracé.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Une autre façon de faire pivoter un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objet en <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> utilisant `true`un chemin géométrique est d’utiliser un objet et de définir sa propriété à . Pour plus d’informations et un exemple, voir [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Pour l’échantillon complet, voir [Échantillon d’animation Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Animation de tracés, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)
