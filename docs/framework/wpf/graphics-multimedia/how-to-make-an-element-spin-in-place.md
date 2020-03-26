---
title: 'Comment : mettre un élément en rotation'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112074"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="e3615-102">Comment : mettre un élément en rotation</span><span class="sxs-lookup"><span data-stu-id="e3615-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="e3615-103">Cet exemple montre comment faire tourner <xref:System.Windows.Media.RotateTransform> un <xref:System.Windows.Media.Animation.DoubleAnimation>élément en utilisant un et un .</span><span class="sxs-lookup"><span data-stu-id="e3615-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="e3615-104">L’exemple suivant <xref:System.Windows.Media.RotateTransform> applique <xref:System.Windows.UIElement.RenderTransform%2A> le propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="e3615-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="e3615-105">L’exemple <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour <xref:System.Windows.Media.RotateTransform.Angle%2A> animer le de la <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="e3615-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="e3615-106">Pour faire tourner l’élément en <xref:System.Windows.UIElement.RenderTransformOrigin%2A> place, l’exemple donne la propriété de l’élément au point (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="e3615-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3615-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3615-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="e3615-108">Pour l’échantillon complet, qui comprend plus d’exemples de transformation, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="e3615-108">For the complete sample, which includes more transformation examples, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3615-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3615-109">See also</span></span>

- [<span data-ttu-id="e3615-110">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="e3615-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e3615-111">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="e3615-111">Transforms Overview</span></span>](transforms-overview.md)
