---
title: "Comment : animer une chaîne à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344671"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="e08eb-102">Comment : animer une chaîne à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="e08eb-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="e08eb-103">Cet exemple montre comment animer une chaîne, qui <xref:System.Windows.Controls.ContentControl.Content%2A> dans <xref:System.Windows.Controls.Button> cet exemple est la propriété d’un contrôle, en utilisant des cadres clés.</span><span class="sxs-lookup"><span data-stu-id="e08eb-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e08eb-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e08eb-104">Example</span></span>  
 <span data-ttu-id="e08eb-105">L’exemple suivant <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Controls.ContentControl.Content%2A> pour <xref:System.Windows.Controls.Button>animer la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="e08eb-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="e08eb-106">Toutes les images clés de cet exemple <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> utilisent un exemple de la classe parce qu’une animation de chaîne qui est créée avec des cadres clés ne peut utiliser que des cadres clés discrets.</span><span class="sxs-lookup"><span data-stu-id="e08eb-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="e08eb-107">Les cadres clés <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> discrets comme créer des sauts soudains entre les valeurs, c’est-à-dire, les changements à l’animation se produisent rapidement et ne sont pas subtils.</span><span class="sxs-lookup"><span data-stu-id="e08eb-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e08eb-108">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="e08eb-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e08eb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e08eb-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="e08eb-110">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="e08eb-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e08eb-111">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="e08eb-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
