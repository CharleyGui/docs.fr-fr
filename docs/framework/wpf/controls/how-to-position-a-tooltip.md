---
title: 'Comment : positionner une info-bulle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186949"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="6a1a5-102">Comment : positionner une info-bulle</span><span class="sxs-lookup"><span data-stu-id="6a1a5-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="6a1a5-103">Cet exemple montre comment spécifier la position d’un tooltip sur l’écran.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a1a5-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="6a1a5-104">Example</span></span>  
 <span data-ttu-id="6a1a5-105">Vous pouvez positionner un tooltip en utilisant un ensemble <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> de cinq propriétés qui sont définies dans les deux et les classes.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="6a1a5-106">Le tableau suivant montre ces deux ensembles de cinq propriétés et fournit des liens vers leur documentation de référence selon la classe.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="6a1a5-107">Propriétés de boîte à outils correspondantes selon la classe</span><span class="sxs-lookup"><span data-stu-id="6a1a5-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="6a1a5-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>propriétés de classe</span><span class="sxs-lookup"><span data-stu-id="6a1a5-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="6a1a5-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>propriétés de classe</span><span class="sxs-lookup"><span data-stu-id="6a1a5-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="6a1a5-110">Si vous définissez le contenu d’un tooltip à l’aide d’un <xref:System.Windows.Controls.ToolTip> objet, vous pouvez utiliser les propriétés de l’une ou l’autre classe; cependant, <xref:System.Windows.Controls.ToolTipService> les propriétés ont préséance.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="6a1a5-111">Utilisez <xref:System.Windows.Controls.ToolTipService> les propriétés pour les outils <xref:System.Windows.Controls.ToolTip> qui ne sont pas définis comme des objets.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="6a1a5-112">Les illustrations suivantes montrent comment positionner un tooltip en utilisant ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="6a1a5-113">Bien que, les [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemples dans ces illustrations montrent <xref:System.Windows.Controls.ToolTip> comment définir les propriétés qui sont définies par la classe, les propriétés correspondantes de la <xref:System.Windows.Controls.ToolTipService> classe suivent les mêmes règles de mise en page.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="6a1a5-114">Pour plus d’informations sur les valeurs possibles pour la propriété Placement, voir [Popup Placement Behavior](popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="6a1a5-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  

 <span data-ttu-id="6a1a5-115">L’image suivante montre le placement de l’outiltip en utilisant la propriété Placement :</span><span class="sxs-lookup"><span data-stu-id="6a1a5-115">The following image shows tooltip placement by using the Placement property:</span></span>  
  
 ![Diagramme montrant le placement ToolTip en utilisant la propriété Placement.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 <span data-ttu-id="6a1a5-117">L’image suivante montre le placement de l’outil en utilisant les propriétés Placement et PlacementRectangle :</span><span class="sxs-lookup"><span data-stu-id="6a1a5-117">The following image shows tooltip placement by using the Placement and PlacementRectangle properties:</span></span>

 ![Diagramme montrant le placement ToolTip à l’aide d’une propriété PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 <span data-ttu-id="6a1a5-119">L’image suivante montre le placement de l’outil en utilisant les propriétés Placement, PlacementRectangle et Offset :</span><span class="sxs-lookup"><span data-stu-id="6a1a5-119">The following image shows tooltip placement by using the Placement, PlacementRectangle, and Offset properties:</span></span>
  
 ![Diagramme montrant le placement ToolTip en utilisant la propriété Offset.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <span data-ttu-id="6a1a5-121">L’exemple suivant montre <xref:System.Windows.Controls.ToolTip> comment utiliser les propriétés pour spécifier la position d’un tooltip dont le contenu est un <xref:System.Windows.Controls.ToolTip> objet.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="6a1a5-122">L’exemple suivant montre <xref:System.Windows.Controls.ToolTipService> comment utiliser les propriétés pour spécifier <xref:System.Windows.Controls.ToolTip> la position d’un tooltip dont le contenu n’est pas un objet.</span><span class="sxs-lookup"><span data-stu-id="6a1a5-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="6a1a5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a1a5-123">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="6a1a5-124">Sujets comment se passer</span><span class="sxs-lookup"><span data-stu-id="6a1a5-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="6a1a5-125">Vue d’ensemble de l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="6a1a5-125">ToolTip Overview</span></span>](tooltip-overview.md)
