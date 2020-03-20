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
# <a name="how-to-position-a-tooltip"></a>Comment : positionner une info-bulle
Cet exemple montre comment spécifier la position d’un tooltip sur l’écran.  
  
## <a name="example"></a> Exemple  
 Vous pouvez positionner un tooltip en utilisant un ensemble <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> de cinq propriétés qui sont définies dans les deux et les classes. Le tableau suivant montre ces deux ensembles de cinq propriétés et fournit des liens vers leur documentation de référence selon la classe.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Propriétés de boîte à outils correspondantes selon la classe  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>propriétés de classe|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>propriétés de classe|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Si vous définissez le contenu d’un tooltip à l’aide d’un <xref:System.Windows.Controls.ToolTip> objet, vous pouvez utiliser les propriétés de l’une ou l’autre classe; cependant, <xref:System.Windows.Controls.ToolTipService> les propriétés ont préséance. Utilisez <xref:System.Windows.Controls.ToolTipService> les propriétés pour les outils <xref:System.Windows.Controls.ToolTip> qui ne sont pas définis comme des objets.  
  
 Les illustrations suivantes montrent comment positionner un tooltip en utilisant ces propriétés. Bien que, les [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemples dans ces illustrations montrent <xref:System.Windows.Controls.ToolTip> comment définir les propriétés qui sont définies par la classe, les propriétés correspondantes de la <xref:System.Windows.Controls.ToolTipService> classe suivent les mêmes règles de mise en page. Pour plus d’informations sur les valeurs possibles pour la propriété Placement, voir [Popup Placement Behavior](popup-placement-behavior.md).  

 L’image suivante montre le placement de l’outiltip en utilisant la propriété Placement :  
  
 ![Diagramme montrant le placement ToolTip en utilisant la propriété Placement.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 L’image suivante montre le placement de l’outil en utilisant les propriétés Placement et PlacementRectangle :

 ![Diagramme montrant le placement ToolTip à l’aide d’une propriété PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 L’image suivante montre le placement de l’outil en utilisant les propriétés Placement, PlacementRectangle et Offset :
  
 ![Diagramme montrant le placement ToolTip en utilisant la propriété Offset.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 L’exemple suivant montre <xref:System.Windows.Controls.ToolTip> comment utiliser les propriétés pour spécifier la position d’un tooltip dont le contenu est un <xref:System.Windows.Controls.ToolTip> objet.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 L’exemple suivant montre <xref:System.Windows.Controls.ToolTipService> comment utiliser les propriétés pour spécifier <xref:System.Windows.Controls.ToolTip> la position d’un tooltip dont le contenu n’est pas un objet.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Sujets comment se passer](tooltip-how-to-topics.md)
- [Vue d’ensemble de l’info-bulle](tooltip-overview.md)
