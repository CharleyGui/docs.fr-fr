---
title: 'Procédure : Créer un effet de substitution à l’aide d’événements'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960386"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="f8d99-102">Procédure : Créer un effet de substitution à l’aide d’événements</span><span class="sxs-lookup"><span data-stu-id="f8d99-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="f8d99-103">Cet exemple montre comment modifier la couleur d’un élément lorsque le pointeur de la souris entre dans la zone occupée par l’élément.</span><span class="sxs-lookup"><span data-stu-id="f8d99-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="f8d99-104">Cet exemple se compose d' [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] un fichier et d’un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="f8d99-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8d99-105">Cet exemple montre comment utiliser des événements, mais la méthode recommandée pour obtenir ce même effet consiste à utiliser un <xref:System.Windows.Trigger> dans un style.</span><span class="sxs-lookup"><span data-stu-id="f8d99-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="f8d99-106">Pour plus d’informations, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="f8d99-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8d99-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8d99-107">Example</span></span>  
 <span data-ttu-id="f8d99-108">Le code [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] suivant crée l’interface utilisateur, qui se <xref:System.Windows.Controls.Border> compose de <xref:System.Windows.Controls.TextBlock>autour d’un et attache <xref:System.Windows.Input.Mouse.MouseEnter> les <xref:System.Windows.UIElement.MouseLeave> gestionnaires d’événements et à <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="f8d99-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="f8d99-109">Le code-behind suivant crée <xref:System.Windows.UIElement.MouseEnter> les <xref:System.Windows.UIElement.MouseLeave> gestionnaires d’événements et.</span><span class="sxs-lookup"><span data-stu-id="f8d99-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="f8d99-110">Lorsque le pointeur <xref:System.Windows.Controls.Border> de la souris <xref:System.Windows.Controls.Border>entre dans, l’arrière-plan de est remplacé par le rouge.</span><span class="sxs-lookup"><span data-stu-id="f8d99-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="f8d99-111">Lorsque le pointeur <xref:System.Windows.Controls.Border> de la souris <xref:System.Windows.Controls.Border>quitte le, l’arrière-plan du est rétabli en blanc.</span><span class="sxs-lookup"><span data-stu-id="f8d99-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
