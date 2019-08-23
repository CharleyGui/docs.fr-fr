---
title: 'Procédure : Partitionner l’espace à l’aide de l’élément DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960200"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="1d82f-102">Procédure : Partitionner l’espace à l’aide de l’élément DockPanel</span><span class="sxs-lookup"><span data-stu-id="1d82f-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="1d82f-103">L’exemple suivant crée un Framework [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] simple à l' <xref:System.Windows.Controls.DockPanel> aide d’un élément.</span><span class="sxs-lookup"><span data-stu-id="1d82f-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="1d82f-104">Le <xref:System.Windows.Controls.DockPanel> partitionnement de l’espace disponible pour ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="1d82f-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d82f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d82f-105">Example</span></span>  
 <span data-ttu-id="1d82f-106">Cet exemple utilise la <xref:System.Windows.Controls.DockPanel.Dock%2A> propriété, qui est une propriété jointe, pour ancrer <xref:System.Windows.Controls.Border> deux éléments identiques <xref:System.Windows.Controls.Dock.Top> au de l’espace partitionné.</span><span class="sxs-lookup"><span data-stu-id="1d82f-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="1d82f-107">Un troisième <xref:System.Windows.Controls.Border> élément est ancré <xref:System.Windows.Controls.Dock.Left>au, avec sa largeur définie sur 200 pixels.</span><span class="sxs-lookup"><span data-stu-id="1d82f-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="1d82f-108">Un quatrième <xref:System.Windows.Controls.Border> est ancré <xref:System.Windows.Controls.Dock.Bottom> au de l’écran.</span><span class="sxs-lookup"><span data-stu-id="1d82f-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="1d82f-109">Le dernier <xref:System.Windows.Controls.Border> élément remplit automatiquement l’espace restant.</span><span class="sxs-lookup"><span data-stu-id="1d82f-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> <span data-ttu-id="1d82f-110">Par défaut, le dernier enfant d’un <xref:System.Windows.Controls.DockPanel> élément remplit l’espace non alloué restant.</span><span class="sxs-lookup"><span data-stu-id="1d82f-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="1d82f-111">Si ce comportement ne vous convient pas, définissez `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="1d82f-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="1d82f-112">L’application compilée produit une nouvelle IU qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="1d82f-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="1d82f-113">![Scénario classique d’utilisation de l’élément DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="1d82f-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d82f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d82f-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="1d82f-115">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="1d82f-115">Panels Overview</span></span>](panels-overview.md)
