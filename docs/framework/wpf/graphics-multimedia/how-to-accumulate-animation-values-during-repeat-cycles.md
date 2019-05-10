---
title: 'Procédure : Accumuler des valeurs d’animation pendant des cycles de répétition'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: bccdc9b7bf2d5a0ea476e39e8d54107854db7ae3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591469"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="a7ad5-102">Procédure : Accumuler des valeurs d’animation pendant des cycles de répétition</span><span class="sxs-lookup"><span data-stu-id="a7ad5-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="a7ad5-103">Cet exemple montre comment utiliser le <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété à accumuler des valeurs d’animation des cycles de répétition.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7ad5-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7ad5-104">Example</span></span>  
 <span data-ttu-id="a7ad5-105">Utilisez le <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété à accumuler des valeurs de base d’une animation sur des cycles de répétition.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="a7ad5-106">Par exemple, si vous définissez une animation se répète 9 fois (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = « 9 x ») et que vous définissez la propriété à animer entre 10 et 15 (de = 10 à = 15), la propriété s’anime de 10 à 15 pendant le premier cycle, de 15 à 20 pendant le deuxième cycle , de 20 à 25 pendant le troisième cycle et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="a7ad5-107">Par conséquent, chaque cycle d’animation utilise la valeur de l’animation de fin du cycle d’animation précédente comme sa valeur de base.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="a7ad5-108">Vous pouvez utiliser le `IsCumulative` propriété avec des animations plus simples et la plupart des animations d’image clé.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="a7ad5-109">Pour plus d’informations, consultez [vue d’ensemble de l’Animation](animation-overview.md) et [vue d’ensemble des Animations image clé](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-109">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="a7ad5-110">L’exemple suivant illustre ce comportement en animant la largeur de quatre rectangles.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="a7ad5-111">L’exemple :</span><span class="sxs-lookup"><span data-stu-id="a7ad5-111">The example:</span></span>  
  
- <span data-ttu-id="a7ad5-112">Anime le premier rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimation> et définit le <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
- <span data-ttu-id="a7ad5-113">Anime le deuxième rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimation> et définit le <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété à la valeur par défaut de `false`.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
- <span data-ttu-id="a7ad5-114">Anime le troisième rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> et définit le <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
- <span data-ttu-id="a7ad5-115">Anime le dernier rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> et définit le <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a7ad5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7ad5-116">See also</span></span>

- [<span data-ttu-id="a7ad5-117">Ajouter une valeur de sortie d'animation à une valeur de départ d'animation</span><span class="sxs-lookup"><span data-stu-id="a7ad5-117">Add an Animation Output Value to an Animation Starting Value</span></span>](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [<span data-ttu-id="a7ad5-118">Répéter une animation</span><span class="sxs-lookup"><span data-stu-id="a7ad5-118">Repeat an Animation</span></span>](how-to-repeat-an-animation.md)
- [<span data-ttu-id="a7ad5-119">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="a7ad5-119">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="a7ad5-120">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="a7ad5-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="a7ad5-121">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="a7ad5-121">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
