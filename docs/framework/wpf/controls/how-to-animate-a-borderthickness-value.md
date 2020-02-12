---
title: 'Comment : animer une valeur BorderThickness'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124661"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Comment : animer une valeur BorderThickness
Cet exemple montre comment animer les modifications apportées à l’épaisseur d’une bordure à l’aide de la classe <xref:System.Windows.Media.Animation.ThicknessAnimation>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant anime l’épaisseur d’une bordure à l’aide de <xref:System.Windows.Media.Animation.ThicknessAnimation>. L’exemple utilise la propriété <xref:System.Windows.Controls.Border.BorderThickness%2A> de <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Pour obtenir l’exemple complet, consultez [Galerie d’exemples d’animations](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md)
- [Rubriques de procédures relatives à l’animation et au minutage](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Animer l’épaisseur d’une bordure à l’aide d’images clés](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
