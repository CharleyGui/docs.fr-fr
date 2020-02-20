---
title: "Comment : animer la position ou la couleur d'un point de dégradé"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452842"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Comment : animer la position ou la couleur d'un point de dégradé
Cet exemple montre comment animer les <xref:System.Windows.Media.GradientStop.Color%2A> et les <xref:System.Windows.Media.GradientStop.Offset%2A> d’objets <xref:System.Windows.Media.GradientStop>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant anime trois points de dégradé à l’intérieur d’un <xref:System.Windows.Media.LinearGradientBrush>. L’exemple utilise trois animations, chacune qui anime un point de dégradé différent :  
  
- La première animation, un <xref:System.Windows.Media.Animation.DoubleAnimation>, anime le <xref:System.Windows.Media.GradientStop.Offset%2A> du premier point de dégradé de 0,0 à 1,0, puis revient à 0,0. Par conséquent, la première couleur du dégradé se déplace du côté gauche vers le côté droit du rectangle, puis de nouveau vers le côté gauche.  
  
- La deuxième animation, un <xref:System.Windows.Media.Animation.ColorAnimation>, anime le <xref:System.Windows.Media.GradientStop.Color%2A> du deuxième point de dégradé de <xref:System.Windows.Media.Colors.Purple%2A> à <xref:System.Windows.Media.Colors.Yellow%2A> puis revient à <xref:System.Windows.Media.Colors.Purple%2A>. Par conséquent, la couleur intermédiaire du dégradé passe du violet au jaune, puis à la couleur violette.  
  
- La troisième animation, une autre <xref:System.Windows.Media.Animation.ColorAnimation>, anime l’opacité du troisième point de dégradé <xref:System.Windows.Media.GradientStop.Color%2A> de-1, puis de nouveau. En conséquence, la troisième couleur du dégradé disparaît, puis redevient opaque.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Media.LinearGradientBrush>, le processus est le même pour animer des objets <xref:System.Windows.Media.GradientStop> à l’intérieur d’un <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Pour obtenir des exemples supplémentaires, consultez l' [exemple pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.GradientStop>
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des storyboards](storyboards-overview.md)
