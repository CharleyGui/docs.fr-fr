---
title: 'Comment : répéter une animation'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141547"
---
# <a name="how-to-repeat-an-animation"></a>Comment : répéter une animation
Cet exemple montre comment <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> utiliser <xref:System.Windows.Media.Animation.Timeline> la propriété d’un afin de contrôler le comportement répété d’une animation.  
  
## <a name="example"></a> Exemple  
 La <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété <xref:System.Windows.Media.Animation.Timeline> d’un contrôle combien de fois une animation répète sa durée simple. En <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>utilisant , vous <xref:System.Windows.Media.Animation.Timeline> pouvez spécifier qu’une répétition pour un certain nombre de fois (un nombre d’itération) ou pour une période de temps spécifiée. Dans les deux cas, l’animation passe par autant de courses de début en bout dont elle a besoin afin de remplir le nombre demandé ou la durée.  
  
 Par défaut, les délais ont un nombre répété de 1,0, ce qui signifie qu’ils jouent une fois et ne se répètent pas. Toutefois, si vous <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> définissez <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>la propriété d’un à , le calendrier se répète indéfiniment.  
  
 L’exemple suivant montre <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> comment utiliser la propriété pour contrôler le comportement répété d’une animation. L’exemple anime <xref:System.Windows.FrameworkElement.Width%2A> la propriété de cinq rectangles avec chaque rectangle à l’aide d’un type différent de comportement répétitif.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Pour l’échantillon complet, voir [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).  
  
## <a name="see-also"></a>Voir aussi

- [Accumuler des valeurs d'animation pendant des cycles de répétition](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Spécifier l’inversion automatique d’une chronologie](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [Rubriques "Comment" relatives à l'animation et au minutage](animation-and-timing-how-to-topics.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Comportement de minuterie d’animation exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
