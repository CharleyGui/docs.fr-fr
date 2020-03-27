---
title: "Comment : contrôler le minutage d'une animation d'image clé"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344732"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="84f7f-102">Comment : contrôler le minutage d'une animation d'image clé</span><span class="sxs-lookup"><span data-stu-id="84f7f-102">How to: Control Key-Frame Animation Timing</span></span>

<span data-ttu-id="84f7f-103">Cet exemple montre comment contrôler le timing des cadres clés dans une animation à cadre clé.</span><span class="sxs-lookup"><span data-stu-id="84f7f-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="84f7f-104">Comme d’autres animations, les <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animations à cadre clé ont une propriété.</span><span class="sxs-lookup"><span data-stu-id="84f7f-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="84f7f-105">En plus de spécifier la durée d’une animation, vous devez spécifier quelle partie de cette durée est allouée à chacun de ses cadres clés.</span><span class="sxs-lookup"><span data-stu-id="84f7f-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="84f7f-106">Pour allouer le temps, vous spécifiez un <xref:System.Windows.Media.Animation.KeyTime> pour chaque cadre clé de l’animation.</span><span class="sxs-lookup"><span data-stu-id="84f7f-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>

<span data-ttu-id="84f7f-107">Le <xref:System.Windows.Media.Animation.KeyTime> pour chaque cadre de clé spécifie quand un cadre de clé se termine (il ne spécifie pas la durée d’un cadre clé joue).</span><span class="sxs-lookup"><span data-stu-id="84f7f-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="84f7f-108">Vous pouvez <xref:System.Windows.Media.Animation.KeyTime> spécifier une <xref:System.TimeSpan> valeur, en <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> pourcentage ou comme valeur spéciale.</span><span class="sxs-lookup"><span data-stu-id="84f7f-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>

## <a name="example"></a><span data-ttu-id="84f7f-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="84f7f-109">Example</span></span>

<span data-ttu-id="84f7f-110">L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utilise un rectangle pour animer l’écran.</span><span class="sxs-lookup"><span data-stu-id="84f7f-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="84f7f-111">Les temps clés des cadres <xref:System.TimeSpan> sont définis avec des valeurs.</span><span class="sxs-lookup"><span data-stu-id="84f7f-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

<span data-ttu-id="84f7f-112">L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.</span><span class="sxs-lookup"><span data-stu-id="84f7f-112">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="84f7f-113">![Valeurs de clés atteintes à 3, 4 et 10 secondes](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="84f7f-113">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>

<span data-ttu-id="84f7f-114">L’exemple suivant montre une animation identique, sauf que les temps clés des cadres sont définis avec des valeurs en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="84f7f-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

<span data-ttu-id="84f7f-115">L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.</span><span class="sxs-lookup"><span data-stu-id="84f7f-115">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="84f7f-116">![Valeurs de clés atteintes à 3, 4 et 10 secondes](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="84f7f-116">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>

<span data-ttu-id="84f7f-117">L’exemple <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> suivant utilise des valeurs temporelles clés.</span><span class="sxs-lookup"><span data-stu-id="84f7f-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

<span data-ttu-id="84f7f-118">L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.</span><span class="sxs-lookup"><span data-stu-id="84f7f-118">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="84f7f-119">![Valeurs de clés atteintes à 3,3, 6,6 et 9,9 secondes](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="84f7f-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>

<span data-ttu-id="84f7f-120">L’exemple <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> final utilise des valeurs temporelles clés.</span><span class="sxs-lookup"><span data-stu-id="84f7f-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

<span data-ttu-id="84f7f-121">L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.</span><span class="sxs-lookup"><span data-stu-id="84f7f-121">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="84f7f-122">![Valeurs de clés atteintes à 0, 5 et 10 secondes](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="84f7f-122">![Key values are reached at 0, 5, and 10 seconds](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>

<span data-ttu-id="84f7f-123">Par souci de simplicité, les versions de code de cet exemple utilisent des animations locales, et non des storyboards, car seule une seule animation est appliquée à une seule propriété, mais les exemples peuvent être modifiés pour utiliser des storyboards à la place.</span><span class="sxs-lookup"><span data-stu-id="84f7f-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="84f7f-124">Pour un exemple montrant comment déclarer un storyboard dans le code, voir [Animate une propriété en utilisant un storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="84f7f-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>

<span data-ttu-id="84f7f-125">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="84f7f-125">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span> <span data-ttu-id="84f7f-126">Pour plus d’informations sur les animations de cadres clés, consultez le [Aperçu des animations Key-Frame](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84f7f-126">For more information about key frame animations, see the [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84f7f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84f7f-127">See also</span></span>

- [<span data-ttu-id="84f7f-128">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="84f7f-128">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="84f7f-129">Vue d'ensemble de l'animation</span><span class="sxs-lookup"><span data-stu-id="84f7f-129">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="84f7f-130">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="84f7f-130">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
