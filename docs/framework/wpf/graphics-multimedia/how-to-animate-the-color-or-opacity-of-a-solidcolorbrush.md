---
title: "Comment : animer la couleur ou l'opacité d'un SolidColorBrush"
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452881"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Comment : animer la couleur ou l'opacité d'un SolidColorBrush
Cet exemple montre comment animer les <xref:System.Windows.Media.SolidColorBrush.Color%2A> et les <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise trois animations pour animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> et <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.SolidColorBrush>.  
  
- La première animation, un <xref:System.Windows.Media.Animation.ColorAnimation>, modifie la couleur du pinceau en <xref:System.Windows.Media.Colors.Gray%2A> lorsque la souris entre dans le rectangle.  
  
- L’animation suivante, une autre <xref:System.Windows.Media.Animation.ColorAnimation>, modifie la couleur du pinceau en <xref:System.Windows.Media.Colors.Orange%2A> lorsque la souris quitte le rectangle.  
  
- La dernière animation, un <xref:System.Windows.Media.Animation.DoubleAnimation>, modifie l’opacité du pinceau sur 0,0 quand l’utilisateur appuie sur le bouton gauche de la souris.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Pour obtenir un exemple plus complet qui montre comment animer différents types de pinceaux, consultez l' [exemple pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Pour plus d’informations sur l’animation, consultez [vue d’ensemble](animation-overview.md)de l’animation.  
  
 Pour assurer la cohérence avec d’autres exemples d’animation, les versions de code de cet exemple utilisent un objet <xref:System.Windows.Media.Animation.Storyboard> pour appliquer leurs animations. Toutefois, lors de l’application d’une seule animation dans le code, il est plus simple d’utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> au lieu d’utiliser une <xref:System.Windows.Media.Animation.Storyboard>. Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des storyboards](storyboards-overview.md)
- [Pinceaux, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
