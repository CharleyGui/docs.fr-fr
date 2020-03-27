---
title: "Comment : animer une valeur booléenne à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 35704996dcf21fe463169dc13572941bcd8fbad1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344936"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="b65f0-102">Comment : animer une valeur booléenne à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="b65f0-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="b65f0-103">Cet exemple montre comment animer la valeur <xref:System.Windows.Controls.Button> de propriété Boolean d’un contrôle en utilisant des cadres clés.</span><span class="sxs-lookup"><span data-stu-id="b65f0-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b65f0-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b65f0-104">Example</span></span>  
 <span data-ttu-id="b65f0-105">L’exemple suivant <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.UIElement.IsEnabled%2A> pour <xref:System.Windows.Controls.Button> animer la propriété d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="b65f0-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="b65f0-106">Tous les cadres clés de cet exemple <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> utilisent un exemple de la classe.</span><span class="sxs-lookup"><span data-stu-id="b65f0-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="b65f0-107">Des cadres discrets <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> comme créer des sauts soudains entre les valeurs, c’est-à-dire que le mouvement de l’animation est saccadédant.</span><span class="sxs-lookup"><span data-stu-id="b65f0-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="b65f0-108">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="b65f0-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65f0-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b65f0-109">See also</span></span>

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="b65f0-110">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="b65f0-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="b65f0-111">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="b65f0-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
