---
title: Naviguer entre les éléments UI Automation avec TreeWalker
description: Consultez un exemple de code qui montre comment naviguer entre les éléments UI Automation à l’aide de la classe TreeWalker.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168018"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="611f7-103">Naviguer entre les éléments UI Automation avec TreeWalker</span><span class="sxs-lookup"><span data-stu-id="611f7-103">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="611f7-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="611f7-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="611f7-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="611f7-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="611f7-106">Cette rubrique contient un exemple de code qui montre comment naviguer entre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] les éléments à l’aide de la <xref:System.Windows.Automation.TreeWalker> classe.</span><span class="sxs-lookup"><span data-stu-id="611f7-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="611f7-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="611f7-107">Example</span></span>  
 <span data-ttu-id="611f7-108">L’exemple suivant utilise <xref:System.Windows.Automation.TreeWalker.GetParent%2A> pour remonter l' [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] arborescence jusqu’à ce qu’il trouve l’élément racine ou le bureau.</span><span class="sxs-lookup"><span data-stu-id="611f7-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="611f7-109">Élément situé juste en dessous de la fenêtre parente de l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="611f7-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="611f7-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="611f7-110">Example</span></span>  
 <span data-ttu-id="611f7-111">L’exemple suivant utilise <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> et <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> pour créer un <xref:System.Windows.Forms.TreeView> qui affiche la sous-arborescence entière des [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] éléments qui sont dans l’affichage de contrôle et qui sont activés.</span><span class="sxs-lookup"><span data-stu-id="611f7-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="611f7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="611f7-112">See also</span></span>

- [<span data-ttu-id="611f7-113">Obtention d'éléments UI Automation</span><span class="sxs-lookup"><span data-stu-id="611f7-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
