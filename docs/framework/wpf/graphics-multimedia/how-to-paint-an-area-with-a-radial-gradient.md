---
title: 'Procédure : Peindre une zone avec un pinceau dégradé radial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916097"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="4fe33-102">Procédure : Peindre une zone avec un pinceau dégradé radial</span><span class="sxs-lookup"><span data-stu-id="4fe33-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="4fe33-103">Cet exemple montre comment utiliser la <xref:System.Windows.Media.RadialGradientBrush> classe pour peindre une zone avec un dégradé radial.</span><span class="sxs-lookup"><span data-stu-id="4fe33-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe33-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4fe33-104">Example</span></span>  
 <span data-ttu-id="4fe33-105">L’exemple suivant utilise un <xref:System.Windows.Media.RadialGradientBrush> pour peindre un rectangle avec un dégradé radial qui passe du jaune au rouge, au bleu et au vert citron.</span><span class="sxs-lookup"><span data-stu-id="4fe33-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="4fe33-106">L’illustration suivante montre le dégradé de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="4fe33-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="4fe33-107">Les arrêts du dégradé ont été mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="4fe33-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="4fe33-108">![Points de dégradé dans un dégradé radial](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="4fe33-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fe33-109">Les exemples de cette rubrique utilisent le système de coordonnées par défaut pour la définition des points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="4fe33-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="4fe33-110">Le système de coordonnées par défaut est relatif à un cadre englobant: 0 indique 0 pour cent de la zone englobante, et 1 indique 100 pour cent de la zone englobante.</span><span class="sxs-lookup"><span data-stu-id="4fe33-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="4fe33-111">Vous pouvez modifier ce système de coordonnées en affectant à la <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriété la valeur. <xref:System.Windows.Media.BrushMappingMode.Absolute></span><span class="sxs-lookup"><span data-stu-id="4fe33-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="4fe33-112">Un système de coordonnées absolu n’est pas relatif à un rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="4fe33-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="4fe33-113">Les valeurs sont interprétées directement dans l’espace local.</span><span class="sxs-lookup"><span data-stu-id="4fe33-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="4fe33-114">Pour obtenir <xref:System.Windows.Media.RadialGradientBrush> des exemples supplémentaires, consultez l' [exemple pinceaux](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="4fe33-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="4fe33-115">Pour plus d’informations sur les dégradés et d’autres types de pinceaux, consultez [vue d’ensemble de la peinture avec des couleurs unies et](painting-with-solid-colors-and-gradients-overview.md)des dégradés.</span><span class="sxs-lookup"><span data-stu-id="4fe33-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
