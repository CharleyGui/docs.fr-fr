---
title: "Procédure : Modifier la couleur d'un élément à l'aide d'événements Focus"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004837"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="dde27-102">Procédure : Modifier la couleur d'un élément à l'aide d'événements Focus</span><span class="sxs-lookup"><span data-stu-id="dde27-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="dde27-103">Cet exemple montre comment modifier la couleur d’un élément quand il gagne et perd le focus à l’aide des événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="dde27-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="dde27-104">Cet exemple se compose d’un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d’un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="dde27-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde27-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="dde27-105">Example</span></span>  
 <span data-ttu-id="dde27-106">Le code XAML suivant crée l’interface utilisateur, qui se compose de deux objets <xref:System.Windows.Controls.Button>, et attache des gestionnaires d’événements pour les événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus> aux objets <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="dde27-106">The following XAML creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="dde27-107">Le code-behind suivant crée les gestionnaires d’événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="dde27-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="dde27-108">Lorsque l' <xref:System.Windows.Controls.Button> obtient le focus clavier, la <xref:System.Windows.Controls.Control.Background%2A> de la <xref:System.Windows.Controls.Button> est remplacée par la couleur rouge.</span><span class="sxs-lookup"><span data-stu-id="dde27-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="dde27-109">Lorsque l' <xref:System.Windows.Controls.Button> perd le focus clavier, le <xref:System.Windows.Controls.Control.Background%2A> du <xref:System.Windows.Controls.Button> est rétabli en blanc.</span><span class="sxs-lookup"><span data-stu-id="dde27-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="dde27-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dde27-110">See also</span></span>

- [<span data-ttu-id="dde27-111">Vue d’ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="dde27-111">Input Overview</span></span>](input-overview.md)
