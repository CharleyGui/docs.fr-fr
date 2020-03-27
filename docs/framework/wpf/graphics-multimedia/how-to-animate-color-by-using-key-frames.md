---
title: "Comment : animer une couleur à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344750"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="e22c7-102">Comment : animer une couleur à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="e22c7-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="e22c7-103">Cet exemple montre comment animer <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> le d’un en utilisant des cadres clés.</span><span class="sxs-lookup"><span data-stu-id="e22c7-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e22c7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e22c7-104">Example</span></span>  
 <span data-ttu-id="e22c7-105">L’exemple suivant <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour <xref:System.Windows.Media.SolidColorBrush>animer la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="e22c7-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="e22c7-106">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="e22c7-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="e22c7-107">Pendant les deux premières secondes, <xref:System.Windows.Media.Animation.LinearColorKeyFrame> utilise une instance de la classe pour changer progressivement la couleur du vert au rouge.</span><span class="sxs-lookup"><span data-stu-id="e22c7-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="e22c7-108">Cadres de clés <xref:System.Windows.Media.Animation.LinearColorKeyFrame> linéaires comme créer une transition linéaire en douceur entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e22c7-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="e22c7-109">À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> utilise une instance de la classe pour changer rapidement la couleur du rouge au jaune.</span><span class="sxs-lookup"><span data-stu-id="e22c7-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="e22c7-110">Cadres clés discrets <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> comme créer des changements soudains entre les valeurs, c’est-à-dire, le changement de couleur dans cette partie de l’animation se produit rapidement et n’est pas subtile.</span><span class="sxs-lookup"><span data-stu-id="e22c7-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="e22c7-111">Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplineColorKeyFrame> utilise une instance de la classe pour changer la couleur à nouveau, cette fois du jaune de retour au vert.</span><span class="sxs-lookup"><span data-stu-id="e22c7-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="e22c7-112">Les cadres clés <xref:System.Windows.Media.Animation.SplineColorKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e22c7-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e22c7-113">Dans cet exemple, le changement de couleur commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="e22c7-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e22c7-114">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="e22c7-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22c7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e22c7-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="e22c7-116">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="e22c7-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e22c7-117">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="e22c7-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
