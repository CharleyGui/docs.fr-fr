---
title: 'Comment : spécifier le FillBehavior pour une chronologie ayant atteint la fin de sa période active'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141171"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Comment : spécifier le FillBehavior pour une chronologie ayant atteint la fin de sa période active
Cet exemple montre comment <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> spécifier <xref:System.Windows.Media.Animation.Timeline> l’inactif d’une propriété animée.  
  
## <a name="example"></a> Exemple  
 La <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété <xref:System.Windows.Media.Animation.Timeline> d’un détermine ce qui arrive à la valeur d’une propriété <xref:System.Windows.Media.Animation.Timeline> animée quand il <xref:System.Windows.Media.Animation.Timeline> n’est pas animé, c’est-à-dire, quand le est inactif, mais son parent est à l’intérieur de sa période active ou de retenue. Par exemple, une propriété animée reste-t-elle à sa valeur de fin après la fin de l’animation ou revient-elle à la valeur qu’elle avait avant le début de l’animation ?  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un <xref:System.Windows.FrameworkElement.Width%2A> pour animer les deux rectangles. Chaque rectangle utilise <xref:System.Windows.Media.Animation.Timeline> un objet différent.  
  
 On <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> un qui <xref:System.Windows.Media.Animation.FillBehavior.Stop>est réglé à , ce qui provoque la largeur <xref:System.Windows.Media.Animation.Timeline> du rectangle de revenir à sa valeur non-animée lorsque les extrémités. L’autre <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> a <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>un de , ce qui provoque <xref:System.Windows.Media.Animation.Timeline> la largeur de rester à sa valeur de fin lorsque les extrémités.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Pour l’échantillon complet, voir [Animation Exemple Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Rubriques "Comment" relatives à l'animation et au minutage](animation-and-timing-how-to-topics.md)
