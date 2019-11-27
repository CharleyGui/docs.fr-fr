---
title: Prendre en charge des modèles de contrôle dans un fournisseur UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446822"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="6dd9b-102">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="6dd9b-102">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="6dd9b-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6dd9b-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="6dd9b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="6dd9b-105">Cette rubrique montre comment implémenter un ou plusieurs modèles de contrôle sur un fournisseur UI Automation de sorte que les applications clientes puissent manipuler les contrôles et en obtenir les données.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="6dd9b-106">Prendre en charge les modèles de contrôle</span><span class="sxs-lookup"><span data-stu-id="6dd9b-106">Support Control Patterns</span></span>

1. <span data-ttu-id="6dd9b-107">Implémentez les interfaces appropriées pour les modèles de contrôle que l’élément doit prendre en charge, telles que <xref:System.Windows.Automation.Provider.IInvokeProvider> pour <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="6dd9b-108">Retournez l’objet contenant votre implémentation de chaque interface de contrôle dans votre implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="6dd9b-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="6dd9b-109">Example</span></span>

<span data-ttu-id="6dd9b-110">L’exemple suivant illustre une implémentation de <xref:System.Windows.Automation.Provider.ISelectionProvider> pour une zone de liste personnalisée à sélection unique.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="6dd9b-111">Elle retourne trois propriétés et obtient l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-111">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="6dd9b-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="6dd9b-112">Example</span></span>

<span data-ttu-id="6dd9b-113">L’exemple suivant illustre une implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> qui retourne la classe implémentant <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="6dd9b-114">La plupart des contrôles de zone de liste prendront également en charge d’autres modèles, mais dans cet exemple, une référence null (`Nothing` dans Microsoft Visual Basic .NET) est retournée pour tous les autres identificateurs de modèle.</span><span class="sxs-lookup"><span data-stu-id="6dd9b-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="6dd9b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dd9b-115">See also</span></span>

- [<span data-ttu-id="6dd9b-116">Vue d’ensemble des fournisseurs UI Automation</span><span class="sxs-lookup"><span data-stu-id="6dd9b-116">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="6dd9b-117">Implémentation de fournisseur UI Automation côté serveur</span><span class="sxs-lookup"><span data-stu-id="6dd9b-117">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
