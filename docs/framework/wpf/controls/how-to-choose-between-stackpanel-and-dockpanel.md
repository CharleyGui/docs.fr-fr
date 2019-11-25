---
title: 'Comment : choisir entre StackPanel et DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976443"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="afe1f-102">Comment : choisir entre StackPanel et DockPanel</span><span class="sxs-lookup"><span data-stu-id="afe1f-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="afe1f-103">Cet exemple montre comment choisir entre l’utilisation d’un <xref:System.Windows.Controls.StackPanel> ou d’un <xref:System.Windows.Controls.DockPanel> quand vous empilez du contenu dans un <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="afe1f-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>

## <a name="example"></a><span data-ttu-id="afe1f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="afe1f-104">Example</span></span>
 <span data-ttu-id="afe1f-105">Bien que vous puissiez utiliser <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.StackPanel> pour empiler des éléments enfants, les deux contrôles ne produisent pas toujours les mêmes résultats.</span><span class="sxs-lookup"><span data-stu-id="afe1f-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="afe1f-106">Par exemple, l’ordre dans lequel vous placez les éléments enfants peut affecter la taille des éléments enfants dans un <xref:System.Windows.Controls.DockPanel>, mais pas dans un <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="afe1f-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="afe1f-107">Ce comportement différent est dû au fait que <xref:System.Windows.Controls.StackPanel> mesures dans le sens de l’empilement à [double. PositiveInfinity](xref:System.Double.PositiveInfinity); Toutefois, <xref:System.Windows.Controls.DockPanel> mesure uniquement la taille disponible.</span><span class="sxs-lookup"><span data-stu-id="afe1f-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at [Double.PositiveInfinity](xref:System.Double.PositiveInfinity); however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>

 <span data-ttu-id="afe1f-108">L’exemple suivant illustre cette différence clé entre <xref:System.Windows.Controls.DockPanel> et <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="afe1f-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="afe1f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afe1f-109">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="afe1f-110">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="afe1f-110">Panels Overview</span></span>](panels-overview.md)
