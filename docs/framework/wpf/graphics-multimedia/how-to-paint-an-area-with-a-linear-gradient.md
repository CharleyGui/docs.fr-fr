---
title: 'Procédure : Peindre une zone avec un pinceau dégradé linéaire'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916166"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="0a14d-102">Procédure : Peindre une zone avec un pinceau dégradé linéaire</span><span class="sxs-lookup"><span data-stu-id="0a14d-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="0a14d-103">Cet exemple montre comment utiliser la <xref:System.Windows.Media.LinearGradientBrush> classe pour peindre une zone avec un dégradé linéaire.</span><span class="sxs-lookup"><span data-stu-id="0a14d-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="0a14d-104">Dans l’exemple suivant, le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire Diagonal qui passe du jaune au rouge et du bleu au vert citron.</span><span class="sxs-lookup"><span data-stu-id="0a14d-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a14d-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a14d-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="0a14d-106">L’illustration suivante montre le dégradé créé par l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0a14d-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0a14d-107">![Dégradé linéaire Diagonal](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="0a14d-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="0a14d-108">Pour créer un dégradé linéaire horizontal, remplacez <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> de <xref:System.Windows.Media.LinearGradientBrush> par (0, 0.5) et (1, 0.5).</span><span class="sxs-lookup"><span data-stu-id="0a14d-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="0a14d-109">Dans l’exemple suivant, un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire horizontal.</span><span class="sxs-lookup"><span data-stu-id="0a14d-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="0a14d-110">L’illustration suivante montre le dégradé créé par l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0a14d-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0a14d-111">![Dégradé linéaire horizontal](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="0a14d-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="0a14d-112">Pour créer un dégradé linéaire vertical, remplacez la <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> valeur <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> de et de par (0.5, 0) et (0.5, 1).</span><span class="sxs-lookup"><span data-stu-id="0a14d-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="0a14d-113">Dans l’exemple suivant, un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire vertical.</span><span class="sxs-lookup"><span data-stu-id="0a14d-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="0a14d-114">L’illustration suivante montre le dégradé créé par l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0a14d-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0a14d-115">![Dégradé linéaire vertical](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="0a14d-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a14d-116">Les exemples de cette rubrique utilisent le système de coordonnées par défaut pour définir les points de départ et les points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0a14d-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="0a14d-117">Le système de coordonnées par défaut est relatif à un cadre englobant: 0 indique 0 pour cent de la zone englobante, et 1 indique 100 pour cent de la zone englobante.</span><span class="sxs-lookup"><span data-stu-id="0a14d-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="0a14d-118">Vous pouvez modifier ce système de coordonnées en affectant à la <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriété la valeur. <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0a14d-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0a14d-119">Un système de coordonnées absolu n’est pas relatif à un rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="0a14d-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="0a14d-120">Les valeurs sont interprétées directement dans l’espace local.</span><span class="sxs-lookup"><span data-stu-id="0a14d-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="0a14d-121">Pour obtenir des exemples supplémentaires, consultez [exemples](https://go.microsoft.com/fwlink/?LinkID=159973)de pinceaux.</span><span class="sxs-lookup"><span data-stu-id="0a14d-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="0a14d-122">Pour plus d’informations sur les dégradés et d’autres types de pinceaux, consultez [vue d’ensemble de la peinture avec des couleurs unies et](painting-with-solid-colors-and-gradients-overview.md)des dégradés.</span><span class="sxs-lookup"><span data-stu-id="0a14d-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
