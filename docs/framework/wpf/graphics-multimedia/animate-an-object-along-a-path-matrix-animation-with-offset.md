---
title: "Comment : animer un objet sur un tracé (animation de matrice avec accumulation d'offsets)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453102"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="a4e60-102">Comment : animer un objet sur un tracé (animation de matrice avec accumulation d'offsets)</span><span class="sxs-lookup"><span data-stu-id="a4e60-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="a4e60-103">Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pour animer un objet le long d’un tracé et faire en sorte que cette animation accumule ses valeurs de décalage à mesure qu’elle se répète.</span><span class="sxs-lookup"><span data-stu-id="a4e60-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4e60-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4e60-104">Example</span></span>  
 <span data-ttu-id="a4e60-105">L’exemple suivant utilise l’objet <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pour animer la propriété <xref:System.Windows.Media.MatrixTransform.Matrix%2A> d’un <xref:System.Windows.Media.MatrixTransform> appliqué à un bouton.</span><span class="sxs-lookup"><span data-stu-id="a4e60-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="a4e60-106">Le bouton se déplace alors le long d’un tracé courbe.</span><span class="sxs-lookup"><span data-stu-id="a4e60-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="a4e60-107">En outre, l’exemple affecte à la propriété <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> la valeur `true`, ce qui entraîne l’accumulation de l’offset de la matrice animée à mesure que l’animation se répète.</span><span class="sxs-lookup"><span data-stu-id="a4e60-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="a4e60-108">Étant donné que les valeurs d’offset s’accumulent, le bouton s’éloigne sur l’écran lorsque l’animation se répète, sans revenir à sa position de départ.</span><span class="sxs-lookup"><span data-stu-id="a4e60-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="a4e60-109">Notez que, bien que la propriété <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> entraîne l’accumulation des valeurs de décalage sur les répétitions, elle n’entraîne pas l’accumulation des valeurs de rotation.</span><span class="sxs-lookup"><span data-stu-id="a4e60-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="a4e60-110">Pour faire en sorte que les valeurs de rotation s’accumulent, définissez les propriétés <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> et <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> de l’animation sur `true`.</span><span class="sxs-lookup"><span data-stu-id="a4e60-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="a4e60-111">Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="a4e60-111">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="a4e60-112">Pour obtenir un exemple illustrant comment animer une valeur de <xref:System.Windows.Media.Matrix> le long d’un tracé sans accumulation d’offsets, consultez [animer un objet sur un tracé (animation de matrice)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="a4e60-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e60-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4e60-113">See also</span></span>

- [<span data-ttu-id="a4e60-114">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="a4e60-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="a4e60-115">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="a4e60-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
