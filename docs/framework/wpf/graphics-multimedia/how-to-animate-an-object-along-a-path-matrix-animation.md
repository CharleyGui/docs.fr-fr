---
title: 'Comment : animer un objet sur un tracé (animation de matrice)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452907"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="f6513-102">Comment : animer un objet sur un tracé (animation de matrice)</span><span class="sxs-lookup"><span data-stu-id="f6513-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="f6513-103">Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pour animer un objet le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="f6513-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6513-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6513-104">Example</span></span>  
 <span data-ttu-id="f6513-105">L’exemple suivant anime un objet sur un tracé de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="f6513-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="f6513-106">Applique une <xref:System.Windows.Media.MatrixTransform> à l’objet pour le déplacer.</span><span class="sxs-lookup"><span data-stu-id="f6513-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="f6513-107">Définit le chemin d’accès à l’aide d’un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="f6513-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="f6513-108">Crée un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> et l’utilise pour animer la propriété <xref:System.Windows.Media.Matrix> du <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="f6513-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="f6513-109">Le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> prend le <xref:System.Windows.Media.PathGeometry> et l’utilise pour générer des valeurs de <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="f6513-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="f6513-110">Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="f6513-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="f6513-111">Pour plus d’informations sur les tracés géométriques, consultez [vue d’ensemble de Geometry](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f6513-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6513-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6513-112">See also</span></span>

- [<span data-ttu-id="f6513-113">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="f6513-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="f6513-114">Animation de tracés, exemple</span><span class="sxs-lookup"><span data-stu-id="f6513-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="f6513-115">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="f6513-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
