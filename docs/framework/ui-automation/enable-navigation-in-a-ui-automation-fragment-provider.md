---
title: Activer la navigation dans un fournisseur de fragment UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: 264a24646f7a3c3b5b20e94fa0ed98a1341f8273
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435762"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="24c4d-102">Activer la navigation dans un fournisseur de fragment UI Automation</span><span class="sxs-lookup"><span data-stu-id="24c4d-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="24c4d-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="24c4d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="24c4d-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="24c4d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="24c4d-105">Cette rubrique contient un exemple de code qui montre comment activer la navigation dans un fournisseur UI Automation pour un élément situé dans un fragment.</span><span class="sxs-lookup"><span data-stu-id="24c4d-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c4d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="24c4d-106">Example</span></span>  
 <span data-ttu-id="24c4d-107">L’exemple de code suivant implémente <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pour un élément de liste situé dans une liste.</span><span class="sxs-lookup"><span data-stu-id="24c4d-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="24c4d-108">L’élément parent est l’élément de zone de liste. Les éléments frères sont d’autres éléments de la collection de listes.</span><span class="sxs-lookup"><span data-stu-id="24c4d-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="24c4d-109">La méthode retourne `null` (`Nothing` en Visual Basic) pour les directions non valides. Dans le cas présent, il s’agit de <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> et <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, car l’élément n’a pas d’enfants.</span><span class="sxs-lookup"><span data-stu-id="24c4d-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="24c4d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24c4d-110">See also</span></span>

- [<span data-ttu-id="24c4d-111">Vue d’ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="24c4d-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="24c4d-112">Implémentation de fournisseur UI Automation côté serveur</span><span class="sxs-lookup"><span data-stu-id="24c4d-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
