---
title: "Comment : animer un point à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344882"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="315fd-102">Comment : animer un point à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="315fd-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="315fd-103">Cet exemple montre comment <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> utiliser la classe <xref:System.Windows.Point>pour animer un .</span><span class="sxs-lookup"><span data-stu-id="315fd-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="315fd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="315fd-104">Example</span></span>  
 <span data-ttu-id="315fd-105">L’exemple suivant déplace une ellipse sur un tracé triangulaire.</span><span class="sxs-lookup"><span data-stu-id="315fd-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="315fd-106">L’exemple <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.EllipseGeometry.Center%2A> pour animer la propriété d’un <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="315fd-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="315fd-107">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="315fd-107">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="315fd-108">Au cours de la première moitié <xref:System.Windows.Media.Animation.LinearPointKeyFrame> de seconde, utilise un exemple de la classe pour déplacer l’ellipse le long d’un chemin à un rythme régulier à partir de sa position de départ.</span><span class="sxs-lookup"><span data-stu-id="315fd-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="315fd-109">Cadres de clés <xref:System.Windows.Media.Animation.LinearPointKeyFrame> linéaires comme créer une interpolation linéaire lisse entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="315fd-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="315fd-110">À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> utilise un exemple de la classe pour soudainement déplacer l’ellipse le long du chemin vers la position suivante.</span><span class="sxs-lookup"><span data-stu-id="315fd-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="315fd-111">Cadres clés discrets <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> comme créer des sauts soudains entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="315fd-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3. <span data-ttu-id="315fd-112">Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplinePointKeyFrame> utilise une instance de la classe pour déplacer l’ellipse de nouveau à sa position de départ.</span><span class="sxs-lookup"><span data-stu-id="315fd-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="315fd-113">Les cadres clés <xref:System.Windows.Media.Animation.SplinePointKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété.</span><span class="sxs-lookup"><span data-stu-id="315fd-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="315fd-114">Dans cet exemple, l’animation commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="315fd-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="315fd-115">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="315fd-115">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="315fd-116">Pour la cohérence avec d’autres exemples d’animation, les versions de code de cet exemple utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="315fd-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="315fd-117">Cependant, lors de l’application d’une seule animation <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> dans le <xref:System.Windows.Media.Animation.Storyboard>code, il est plus simple d’utiliser la méthode au lieu d’utiliser un .</span><span class="sxs-lookup"><span data-stu-id="315fd-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="315fd-118">Par exemple, voir [Animate une propriété sans utiliser un storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="315fd-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315fd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="315fd-119">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="315fd-120">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="315fd-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="315fd-121">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="315fd-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
