---
title: "Comment : animer des modifications de taille à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344653"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="e8a22-102">Comment : animer des modifications de taille à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="e8a22-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="e8a22-103">Cet exemple explique comment animer des modifications de taille à l’aide d’images clés.</span><span class="sxs-lookup"><span data-stu-id="e8a22-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8a22-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8a22-104">Example</span></span>  
 <span data-ttu-id="e8a22-105">L’exemple suivant <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.ArcSegment.Size%2A> pour <xref:System.Windows.Media.ArcSegment>animer la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="e8a22-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="e8a22-106">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="e8a22-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="e8a22-107">Au cours de la première moitié de <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> seconde de l’animation, utilise un exemple de la classe pour augmenter progressivement la taille de l’arc. Cadres de clés <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> linéaires comme créer une transition linéaire en douceur entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e8a22-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="e8a22-108">À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> utilise un exemple de la classe pour augmenter soudainement la taille de l’arc. Des cadres clés <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> discrets comme créer des sauts soudains entre les valeurs, c’est-à-dire que les changements de taille se produisent soudainement et ne sont pas subtils.</span><span class="sxs-lookup"><span data-stu-id="e8a22-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="e8a22-109">Au cours des deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> classe pour augmenter la taille de l’arc. Les cadres clés <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e8a22-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e8a22-110">Dans cet exemple, la taille de l’arc augmente lentement dans un premier temps, puis augmente de façon exponentielle vers la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="e8a22-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e8a22-111">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="e8a22-111">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a22-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8a22-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="e8a22-113">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="e8a22-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e8a22-114">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="e8a22-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
