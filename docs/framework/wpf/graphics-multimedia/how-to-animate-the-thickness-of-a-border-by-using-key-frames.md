---
title: "Comment : animer l'épaisseur d'une bordure à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344690"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="03c9f-102">Comment : animer l'épaisseur d'une bordure à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="03c9f-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="03c9f-103">Cet exemple montre comment animer <xref:System.Windows.Controls.Control.BorderThickness%2A> la <xref:System.Windows.Controls.Border>propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="03c9f-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03c9f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="03c9f-104">Example</span></span>  
 <span data-ttu-id="03c9f-105">L’exemple suivant <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Controls.Control.BorderThickness%2A> pour <xref:System.Windows.Controls.Border>animer la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="03c9f-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="03c9f-106">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="03c9f-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="03c9f-107">Au cours de la première moitié <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> de seconde, utilise un exemple de la classe pour augmenter progressivement l’épaisseur de la frontière.</span><span class="sxs-lookup"><span data-stu-id="03c9f-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="03c9f-108">L’exemple <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> sert à créer une augmentation linéaire lisse entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="03c9f-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2. <span data-ttu-id="03c9f-109">À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> utilise un exemple de la classe pour augmenter soudainement l’épaisseur de la frontière.</span><span class="sxs-lookup"><span data-stu-id="03c9f-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="03c9f-110">Cadres clés discrets comme <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> ceux dérivés de créer des sauts soudains entre les valeurs, c’est-à-dire, le mouvement de l’animation est saccadée.</span><span class="sxs-lookup"><span data-stu-id="03c9f-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3. <span data-ttu-id="03c9f-111">Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> utilise un exemple de la classe pour diminuer l’épaisseur de la bordure.</span><span class="sxs-lookup"><span data-stu-id="03c9f-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="03c9f-112">Les cadres clés de Spline comme ceux dérivés de <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> créer <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> une transition variable entre les valeurs en fonction des valeurs de la propriété.</span><span class="sxs-lookup"><span data-stu-id="03c9f-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="03c9f-113">Dans cette image clé, l’animation commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="03c9f-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="03c9f-114">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="03c9f-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c9f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03c9f-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="03c9f-116">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="03c9f-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="03c9f-117">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="03c9f-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="03c9f-118">Animer une valeur BorderThickness</span><span class="sxs-lookup"><span data-stu-id="03c9f-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
