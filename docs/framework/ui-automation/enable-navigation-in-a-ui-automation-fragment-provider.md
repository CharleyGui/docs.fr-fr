---
title: Activer la navigation dans un fournisseur de fragment UI Automation
description: Lisez un exemple qui montre comment activer la navigation dans un fournisseur UI Automation pour un élément situé dans un fragment.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: d8fb67a84b7cba84fe65cd2f87baa6549122d2a2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276501"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="e9a0e-103">Activer la navigation dans un fournisseur de fragment UI Automation</span><span class="sxs-lookup"><span data-stu-id="e9a0e-103">Enable Navigation in a UI Automation Fragment Provider</span></span>

> [!NOTE]
> <span data-ttu-id="e9a0e-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e9a0e-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e9a0e-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e9a0e-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e9a0e-106">Cette rubrique contient un exemple de code qui montre comment activer la navigation dans un fournisseur UI Automation pour un élément situé dans un fragment.</span><span class="sxs-lookup"><span data-stu-id="e9a0e-106">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9a0e-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e9a0e-107">Example</span></span>  

 <span data-ttu-id="e9a0e-108">L’exemple de code suivant implémente <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pour un élément de liste situé dans une liste.</span><span class="sxs-lookup"><span data-stu-id="e9a0e-108">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="e9a0e-109">L’élément parent est l’élément de zone de liste. Les éléments frères sont d’autres éléments de la collection de listes.</span><span class="sxs-lookup"><span data-stu-id="e9a0e-109">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="e9a0e-110">La méthode retourne `null` (`Nothing` en Visual Basic) pour les directions non valides. Dans le cas présent, il s’agit de <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> et <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, car l’élément n’a pas d’enfants.</span><span class="sxs-lookup"><span data-stu-id="e9a0e-110">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="e9a0e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9a0e-111">See also</span></span>

- [<span data-ttu-id="e9a0e-112">Vue d'ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="e9a0e-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="e9a0e-113">Implémentation de fournisseur UI Automation côté serveur</span><span class="sxs-lookup"><span data-stu-id="e9a0e-113">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
