---
title: 'Comment : animer un objet sur un tracé (animation double)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452855"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="fe7c4-102">Comment : animer un objet sur un tracé (animation double)</span><span class="sxs-lookup"><span data-stu-id="fe7c4-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="fe7c4-103">Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> pour déplacer un objet le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="fe7c4-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe7c4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="fe7c4-104">Example</span></span>  
 <span data-ttu-id="fe7c4-105">L’exemple suivant utilise deux objets <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> pour déplacer un rectangle le long d’un tracé géométrique :</span><span class="sxs-lookup"><span data-stu-id="fe7c4-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
- <span data-ttu-id="fe7c4-106">La première <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anime la <xref:System.Windows.Media.TranslateTransform.X%2A> de la <xref:System.Windows.Media.TranslateTransform> appliquée au rectangle.</span><span class="sxs-lookup"><span data-stu-id="fe7c4-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="fe7c4-107">Le rectangle se déplace alors horizontalement sur le tracé.</span><span class="sxs-lookup"><span data-stu-id="fe7c4-107">It makes the rectangle move horizontally along the path.</span></span>  
  
- <span data-ttu-id="fe7c4-108">La deuxième <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anime la <xref:System.Windows.Media.TranslateTransform.Y%2A> de la <xref:System.Windows.Media.TranslateTransform> appliquée au rectangle.</span><span class="sxs-lookup"><span data-stu-id="fe7c4-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="fe7c4-109">Le rectangle se déplace alors verticalement sur le tracé.</span><span class="sxs-lookup"><span data-stu-id="fe7c4-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="fe7c4-110">Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="fe7c4-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="fe7c4-111">Une autre façon de déplacer un objet à l’aide d’un tracé géométrique consiste à utiliser un objet <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>.</span><span class="sxs-lookup"><span data-stu-id="fe7c4-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="fe7c4-112">Pour obtenir un exemple, consultez [animer un objet sur un tracé (animation de matrice)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="fe7c4-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe7c4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe7c4-113">See also</span></span>

- [<span data-ttu-id="fe7c4-114">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="fe7c4-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="fe7c4-115">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="fe7c4-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
