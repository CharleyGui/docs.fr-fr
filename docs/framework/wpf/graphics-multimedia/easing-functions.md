---
title: Fonctions d'accélération
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965733"
---
# <a name="easing-functions"></a><span data-ttu-id="56add-102">Fonctions d'accélération</span><span class="sxs-lookup"><span data-stu-id="56add-102">Easing Functions</span></span>
<span data-ttu-id="56add-103">Les fonctions d’accélération permettent d’appliquer des formules mathématiques personnalisées à des animations.</span><span class="sxs-lookup"><span data-stu-id="56add-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="56add-104">Par exemple, vous pouvez faire en sorte qu’un objet rebondisse ou se comporte comme s’il était sur un ressort de façon réaliste.</span><span class="sxs-lookup"><span data-stu-id="56add-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="56add-105">On peut utiliser des animations d’images clés ou même From/To/By pour se rapprocher de ces effets, mais cela demanderait beaucoup de travail et l’animation serait moins précise qu’avec une formule mathématique.</span><span class="sxs-lookup"><span data-stu-id="56add-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="56add-106">Outre la création de votre propre fonction d’accélération personnalisée en <xref:System.Windows.Media.Animation.EasingFunctionBase>héritant de, vous pouvez utiliser l’une des nombreuses fonctions d’accélération fournies par le runtime pour créer des effets courants.</span><span class="sxs-lookup"><span data-stu-id="56add-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="56add-107"><xref:System.Windows.Media.Animation.BackEase>: Rétracte légèrement le mouvement d’une animation avant qu’elle ne commence à s’animer dans le chemin indiqué.</span><span class="sxs-lookup"><span data-stu-id="56add-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="56add-108"><xref:System.Windows.Media.Animation.BounceEase>: Crée un effet de rebond.</span><span class="sxs-lookup"><span data-stu-id="56add-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="56add-109"><xref:System.Windows.Media.Animation.CircleEase>: Crée une animation qui accélère et/ou ralentit à l’aide d’une fonction circulaire.</span><span class="sxs-lookup"><span data-stu-id="56add-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="56add-110"><xref:System.Windows.Media.Animation.CubicEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="56add-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="56add-111"><xref:System.Windows.Media.Animation.ElasticEase>: Crée une animation qui ressemble à un ressort oscillant d’avant en arrière jusqu’à ce qu’il s’immobilise.</span><span class="sxs-lookup"><span data-stu-id="56add-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="56add-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Crée une animation qui accélère et/ou ralentit à l’aide d’une formule exponentielle.</span><span class="sxs-lookup"><span data-stu-id="56add-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="56add-113"><xref:System.Windows.Media.Animation.PowerEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>p</sup> , où p <xref:System.Windows.Media.Animation.PowerEase.Power%2A> est égal à la propriété.</span><span class="sxs-lookup"><span data-stu-id="56add-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="56add-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="56add-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="56add-115"><xref:System.Windows.Media.Animation.QuarticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="56add-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="56add-116"><xref:System.Windows.Media.Animation.QuinticEase>: Créez une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="56add-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="56add-117"><xref:System.Windows.Media.Animation.SineEase>: Crée une animation qui accélère et/ou ralentit à l’aide d’une formule de sinus.</span><span class="sxs-lookup"><span data-stu-id="56add-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="56add-118">Pour appliquer une fonction d’accélération à une animation, utilisez `EasingFunction` la propriété de l’animation spécifier la fonction d’accélération à appliquer à l’animation.</span><span class="sxs-lookup"><span data-stu-id="56add-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="56add-119">L’exemple suivant applique une <xref:System.Windows.Media.Animation.BounceEase> fonction d’accélération à <xref:System.Windows.Media.Animation.DoubleAnimation> un pour créer un effet de rebond.</span><span class="sxs-lookup"><span data-stu-id="56add-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="56add-120">Dans l’exemple précédent, la fonction d’accélération a été appliquée à une animation From/To/By.</span><span class="sxs-lookup"><span data-stu-id="56add-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="56add-121">Vous pouvez également appliquer ces fonctions d’accélération aux animations d’images clés.</span><span class="sxs-lookup"><span data-stu-id="56add-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="56add-122">L’exemple suivant montre comment utiliser des images clés avec les fonctions d’accélération associées pour créer une animation d’un rectangle qui se contracte vers le haut, ralentit, s’étend vers le bas (comme s’il tombait), puis rebondit jusqu’à s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="56add-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="56add-123">Vous pouvez utiliser la <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> propriété pour modifier le comportement de la fonction d’accélération, c’est-à-dire modifier le mode d’interpolation de l’animation.</span><span class="sxs-lookup"><span data-stu-id="56add-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="56add-124">Vous pouvez fournir trois valeurs possibles pour <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="56add-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="56add-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: L’interpolation suit la formule mathématique associée à la fonction d’accélération.</span><span class="sxs-lookup"><span data-stu-id="56add-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="56add-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: L’interpolation suit l’interpolation 100% moins la sortie de la formule associée à la fonction d’accélération.</span><span class="sxs-lookup"><span data-stu-id="56add-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="56add-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: L’interpolation utilise <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pour la première moitié de l’animation et <xref:System.Windows.Media.Animation.EasingMode.EaseOut> pour la seconde moitié.</span><span class="sxs-lookup"><span data-stu-id="56add-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="56add-128">Les graphiques ci-dessous illustrent les différentes <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> valeurs de, où *f*(*x*) représente la progression de l’animation et *t* représente l’heure.</span><span class="sxs-lookup"><span data-stu-id="56add-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="56add-129">![Graphiques EasingMode BackEase.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="56add-130">![Graphiques EasingMode BounceEase.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="56add-131">![Graphiques EasingMode CircleEase.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="56add-132">![Graphiques EasingMode CubicEase.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="56add-133">![ElasticEase avec graphiques de différents easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="56add-134">![Graphiques ExponentialEase de différents easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="56add-135">![QuarticEase avec graphiques de différents easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="56add-136">![QuadraticEase avec graphiques de différents easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="56add-137">![QuarticEase avec graphiques de différents easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="56add-138">![QuinticEase avec graphiques de différents easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="56add-139">![SineEase pour différentes valeurs EasingMode](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="56add-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56add-140">Vous pouvez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour créer le même comportement que <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>et <xref:System.Windows.Media.Animation.QuinticEase> en utilisant la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="56add-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="56add-141">Par exemple, si vous souhaitez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour <xref:System.Windows.Media.Animation.CubicEase>remplacer, spécifiez la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> valeur 3.</span><span class="sxs-lookup"><span data-stu-id="56add-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="56add-142">En plus d’utiliser les fonctions d’accélération incluses dans le runtime, vous pouvez créer vos propres fonctions d’accélération personnalisées en héritant <xref:System.Windows.Media.Animation.EasingFunctionBase>de.</span><span class="sxs-lookup"><span data-stu-id="56add-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="56add-143">L’exemple suivant montre comment créer une fonction d’accélération personnalisée simple.</span><span class="sxs-lookup"><span data-stu-id="56add-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="56add-144">Vous pouvez ajouter votre propre logique mathématique pour le comportement de la fonction d’accélération en remplaçant la <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="56add-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
