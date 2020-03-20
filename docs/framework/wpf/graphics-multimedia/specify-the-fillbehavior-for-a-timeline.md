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
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="3b869-102">Comment : spécifier le FillBehavior pour une chronologie ayant atteint la fin de sa période active</span><span class="sxs-lookup"><span data-stu-id="3b869-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="3b869-103">Cet exemple montre comment <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> spécifier <xref:System.Windows.Media.Animation.Timeline> l’inactif d’une propriété animée.</span><span class="sxs-lookup"><span data-stu-id="3b869-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b869-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3b869-104">Example</span></span>  
 <span data-ttu-id="3b869-105">La <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété <xref:System.Windows.Media.Animation.Timeline> d’un détermine ce qui arrive à la valeur d’une propriété <xref:System.Windows.Media.Animation.Timeline> animée quand il <xref:System.Windows.Media.Animation.Timeline> n’est pas animé, c’est-à-dire, quand le est inactif, mais son parent est à l’intérieur de sa période active ou de retenue.</span><span class="sxs-lookup"><span data-stu-id="3b869-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="3b869-106">Par exemple, une propriété animée reste-t-elle à sa valeur de fin après la fin de l’animation ou revient-elle à la valeur qu’elle avait avant le début de l’animation ?</span><span class="sxs-lookup"><span data-stu-id="3b869-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="3b869-107">L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un <xref:System.Windows.FrameworkElement.Width%2A> pour animer les deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="3b869-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="3b869-108">Chaque rectangle utilise <xref:System.Windows.Media.Animation.Timeline> un objet différent.</span><span class="sxs-lookup"><span data-stu-id="3b869-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="3b869-109">On <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> un qui <xref:System.Windows.Media.Animation.FillBehavior.Stop>est réglé à , ce qui provoque la largeur <xref:System.Windows.Media.Animation.Timeline> du rectangle de revenir à sa valeur non-animée lorsque les extrémités.</span><span class="sxs-lookup"><span data-stu-id="3b869-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="3b869-110">L’autre <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> a <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>un de , ce qui provoque <xref:System.Windows.Media.Animation.Timeline> la largeur de rester à sa valeur de fin lorsque les extrémités.</span><span class="sxs-lookup"><span data-stu-id="3b869-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="3b869-111">Pour l’échantillon complet, voir [Animation Exemple Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="3b869-111">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b869-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b869-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="3b869-113">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="3b869-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="3b869-114">Rubriques "Comment" relatives à l'animation et au minutage</span><span class="sxs-lookup"><span data-stu-id="3b869-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
