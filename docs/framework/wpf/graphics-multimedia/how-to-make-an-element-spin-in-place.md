---
title: 'Comment : mettre un élément en rotation'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112074"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Comment : mettre un élément en rotation
Cet exemple montre comment faire tourner <xref:System.Windows.Media.RotateTransform> un <xref:System.Windows.Media.Animation.DoubleAnimation>élément en utilisant un et un .  
  
 L’exemple suivant <xref:System.Windows.Media.RotateTransform> applique <xref:System.Windows.UIElement.RenderTransform%2A> le propriété de l’élément. L’exemple <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour <xref:System.Windows.Media.RotateTransform.Angle%2A> animer le de la <xref:System.Windows.Media.RotateTransform>. Pour faire tourner l’élément en <xref:System.Windows.UIElement.RenderTransformOrigin%2A> place, l’exemple donne la propriété de l’élément au point (0,5, 0,5).  
  
## <a name="example"></a>Exemple  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Pour l’échantillon complet, qui comprend plus d’exemples de transformation, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des transformations](transforms-overview.md)
