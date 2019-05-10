---
title: 'Procédure : Animer une propriété à l’aide d’un objet AnimationClock'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: 13d91e8589c40d84ba374ffc613388e24407796a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591286"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="3754f-102">Procédure : Animer une propriété à l’aide d’un objet AnimationClock</span><span class="sxs-lookup"><span data-stu-id="3754f-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="3754f-103">Cet exemple montre comment utiliser <xref:System.Windows.Media.Animation.Clock> objets à animer une propriété.</span><span class="sxs-lookup"><span data-stu-id="3754f-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="3754f-104">Il existe trois façons d’animer une propriété de dépendance :</span><span class="sxs-lookup"><span data-stu-id="3754f-104">There are three ways to animate a dependency property:</span></span>  
  
- <span data-ttu-id="3754f-105">Créer un <xref:System.Windows.Media.Animation.AnimationTimeline> et l’associer à cette propriété à l’aide un <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="3754f-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
- <span data-ttu-id="3754f-106">Utilisez l’objet <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode pour appliquer un seul <xref:System.Windows.Media.Animation.AnimationTimeline> à une propriété cible.</span><span class="sxs-lookup"><span data-stu-id="3754f-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
- <span data-ttu-id="3754f-107">Créer un <xref:System.Windows.Media.Animation.AnimationClock> à partir d’un <xref:System.Windows.Media.Animation.AnimationTimeline> et appliquez-le à une propriété.</span><span class="sxs-lookup"><span data-stu-id="3754f-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="3754f-108"><xref:System.Windows.Media.Animation.Storyboard> objets et le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> activer la méthode vous permet d’animer des propriétés sans créer et distribuer des horloges directement (pour obtenir des exemples, consultez [animer une propriété à l’aide d’un Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) et [animer une propriété sans À l’aide d’un Storyboard](how-to-animate-a-property-without-using-a-storyboard.md)) ; horloges sont créées et distribuées automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="3754f-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3754f-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="3754f-109">Example</span></span>  
 <span data-ttu-id="3754f-110">L’exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.AnimationClock> et l’appliquer à deux propriétés similaires.</span><span class="sxs-lookup"><span data-stu-id="3754f-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="3754f-111">Pour obtenir un exemple montrant comment contrôler de manière interactive un <xref:System.Windows.Media.Animation.Clock> après son démarrage, consultez [contrôler une horloge de façon interactive](how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="3754f-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3754f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3754f-112">See also</span></span>

- [<span data-ttu-id="3754f-113">Animer une propriété à l’aide d’une table de montage séquentiel</span><span class="sxs-lookup"><span data-stu-id="3754f-113">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="3754f-114">Animer une propriété sans utiliser de storyboard</span><span class="sxs-lookup"><span data-stu-id="3754f-114">Animate a Property Without Using a Storyboard</span></span>](how-to-animate-a-property-without-using-a-storyboard.md)
- [<span data-ttu-id="3754f-115">Vue d’ensemble des techniques d’animation de propriétés</span><span class="sxs-lookup"><span data-stu-id="3754f-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
