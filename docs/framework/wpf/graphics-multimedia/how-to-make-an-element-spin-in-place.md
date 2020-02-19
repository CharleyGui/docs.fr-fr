---
title: 'Comment : mettre un élément en rotation'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452790"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="12e49-102">Comment : mettre un élément en rotation</span><span class="sxs-lookup"><span data-stu-id="12e49-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="12e49-103">Cet exemple montre comment faire pivoter un élément à l’aide d’un <xref:System.Windows.Media.RotateTransform> et d’un <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="12e49-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="12e49-104">L’exemple suivant applique l' <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> de l’élément.</span><span class="sxs-lookup"><span data-stu-id="12e49-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="12e49-105">L’exemple utilise une <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer le <xref:System.Windows.Media.RotateTransform.Angle%2A> du <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="12e49-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="12e49-106">Pour que l’élément tourne en place, l’exemple définit la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> de l’élément sur le point (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="12e49-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12e49-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="12e49-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="12e49-108">Pour l’exemple complet, qui comprend d’autres exemples de transformation, consultez [exemple de transformations 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="12e49-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e49-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12e49-109">See also</span></span>

- [<span data-ttu-id="12e49-110">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="12e49-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="12e49-111">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="12e49-111">Transforms Overview</span></span>](transforms-overview.md)
