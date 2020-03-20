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
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="6cf3c-102">Comment : répéter une animation</span><span class="sxs-lookup"><span data-stu-id="6cf3c-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="6cf3c-103">Cet exemple montre comment <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> utiliser <xref:System.Windows.Media.Animation.Timeline> la propriété d’un afin de contrôler le comportement répété d’une animation.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cf3c-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="6cf3c-104">Example</span></span>  
 <span data-ttu-id="6cf3c-105">La <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété <xref:System.Windows.Media.Animation.Timeline> d’un contrôle combien de fois une animation répète sa durée simple.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="6cf3c-106">En <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>utilisant , vous <xref:System.Windows.Media.Animation.Timeline> pouvez spécifier qu’une répétition pour un certain nombre de fois (un nombre d’itération) ou pour une période de temps spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="6cf3c-107">Dans les deux cas, l’animation passe par autant de courses de début en bout dont elle a besoin afin de remplir le nombre demandé ou la durée.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="6cf3c-108">Par défaut, les délais ont un nombre répété de 1,0, ce qui signifie qu’ils jouent une fois et ne se répètent pas.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="6cf3c-109">Toutefois, si vous <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> définissez <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>la propriété d’un à , le calendrier se répète indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="6cf3c-110">L’exemple suivant montre <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> comment utiliser la propriété pour contrôler le comportement répété d’une animation.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="6cf3c-111">L’exemple anime <xref:System.Windows.FrameworkElement.Width%2A> la propriété de cinq rectangles avec chaque rectangle à l’aide d’un type différent de comportement répétitif.</span><span class="sxs-lookup"><span data-stu-id="6cf3c-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="6cf3c-112">Pour l’échantillon complet, voir [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span><span class="sxs-lookup"><span data-stu-id="6cf3c-112">For the complete sample, see [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf3c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cf3c-113">See also</span></span>

- [<span data-ttu-id="6cf3c-114">Accumuler des valeurs d'animation pendant des cycles de répétition</span><span class="sxs-lookup"><span data-stu-id="6cf3c-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="6cf3c-115">Spécifier l’inversion automatique d’une chronologie</span><span class="sxs-lookup"><span data-stu-id="6cf3c-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="6cf3c-116">Rubriques "Comment" relatives à l'animation et au minutage</span><span class="sxs-lookup"><span data-stu-id="6cf3c-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="6cf3c-117">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="6cf3c-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="6cf3c-118">Comportement de minuterie d’animation exemple</span><span class="sxs-lookup"><span data-stu-id="6cf3c-118">Animation Timing Behavior Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
