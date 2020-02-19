---
title: 'Comment : mettre un élément en rotation'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452790"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Comment : mettre un élément en rotation
Cet exemple montre comment faire pivoter un élément à l’aide d’un <xref:System.Windows.Media.RotateTransform> et d’un <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 L’exemple suivant applique l' <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> de l’élément. L’exemple utilise une <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer le <xref:System.Windows.Media.RotateTransform.Angle%2A> du <xref:System.Windows.Media.RotateTransform>. Pour que l’élément tourne en place, l’exemple définit la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> de l’élément sur le point (0,5, 0,5).  
  
## <a name="example"></a>Exemple  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Pour l’exemple complet, qui comprend d’autres exemples de transformation, consultez [exemple de transformations 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des transformations](transforms-overview.md)
