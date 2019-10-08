---
title: "Procédure : Créer un effet de substitution à l'aide d'événements"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005178"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="2bd9f-102">Procédure : Créer un effet de substitution à l'aide d'événements</span><span class="sxs-lookup"><span data-stu-id="2bd9f-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="2bd9f-103">Cet exemple montre comment modifier la couleur d’un élément lorsque le pointeur de la souris entre dans la zone occupée par l’élément.</span><span class="sxs-lookup"><span data-stu-id="2bd9f-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="2bd9f-104">Cet exemple se compose d’un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d’un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="2bd9f-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bd9f-105">Cet exemple montre comment utiliser des événements, mais la méthode recommandée pour obtenir ce même effet consiste à utiliser un <xref:System.Windows.Trigger> dans un style.</span><span class="sxs-lookup"><span data-stu-id="2bd9f-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="2bd9f-106">Pour plus d’informations, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="2bd9f-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd9f-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bd9f-107">Example</span></span>  
 <span data-ttu-id="2bd9f-108">Le code XAML suivant crée l’interface utilisateur, qui se compose de <xref:System.Windows.Controls.Border> autour d’une <xref:System.Windows.Controls.TextBlock>, et associe les gestionnaires d’événements <xref:System.Windows.Input.Mouse.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave> au <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="2bd9f-108">The following XAML creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="2bd9f-109">Le code-behind suivant crée les gestionnaires d’événements <xref:System.Windows.UIElement.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave>.</span><span class="sxs-lookup"><span data-stu-id="2bd9f-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="2bd9f-110">Lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.Border>, l’arrière-plan de la <xref:System.Windows.Controls.Border> est remplacé par le rouge.</span><span class="sxs-lookup"><span data-stu-id="2bd9f-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="2bd9f-111">Lorsque le pointeur de la souris quitte le <xref:System.Windows.Controls.Border>, l’arrière-plan du <xref:System.Windows.Controls.Border> est rétabli en blanc.</span><span class="sxs-lookup"><span data-stu-id="2bd9f-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
