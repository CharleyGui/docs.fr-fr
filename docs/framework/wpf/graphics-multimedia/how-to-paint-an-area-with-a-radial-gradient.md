---
title: 'Comment : peindre une zone avec un dégradé radial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452751"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="345f1-102">Comment : peindre une zone avec un dégradé radial</span><span class="sxs-lookup"><span data-stu-id="345f1-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="345f1-103">Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.RadialGradientBrush> pour peindre une zone avec un dégradé radial.</span><span class="sxs-lookup"><span data-stu-id="345f1-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="345f1-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="345f1-104">Example</span></span>  
 <span data-ttu-id="345f1-105">L’exemple suivant utilise une <xref:System.Windows.Media.RadialGradientBrush> pour peindre un rectangle avec un dégradé radial qui passe du jaune au rouge, au bleu et au vert citron.</span><span class="sxs-lookup"><span data-stu-id="345f1-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="345f1-106">L’illustration suivante montre le dégradé de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="345f1-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="345f1-107">Les arrêts du dégradé ont été mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="345f1-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="345f1-108">![Points de dégradé dans un dégradé radial](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="345f1-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="345f1-109">Les exemples de cette rubrique utilisent le système de coordonnées par défaut pour la définition des points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="345f1-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="345f1-110">Le système de coordonnées par défaut est relatif à une zone englobante : 0 indique 0 pour cent du rectangle englobant, et 1 indique 100% du cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="345f1-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="345f1-111">Vous pouvez modifier ce système de coordonnées en affectant à la propriété <xref:System.Windows.Media.GradientBrush.MappingMode%2A> la valeur <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="345f1-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="345f1-112">Un système de coordonnées absolu n’est pas relatif à un rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="345f1-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="345f1-113">Les valeurs sont interprétées directement dans l’espace local.</span><span class="sxs-lookup"><span data-stu-id="345f1-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="345f1-114">Pour obtenir des exemples supplémentaires <xref:System.Windows.Media.RadialGradientBrush>, consultez l' [exemple Brush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="345f1-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="345f1-115">Pour plus d’informations sur les dégradés et d’autres types de pinceaux, consultez [vue d’ensemble de la peinture avec des couleurs unies et des dégradés](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="345f1-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
