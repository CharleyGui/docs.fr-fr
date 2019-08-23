---
title: Obtenir des modèles de contrôle UI Automation pris en charge
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 8987526a572d3c9a239885407c19bd1ad3674f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968993"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="6a63b-102">Obtenir des modèles de contrôle UI Automation pris en charge</span><span class="sxs-lookup"><span data-stu-id="6a63b-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="6a63b-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6a63b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6a63b-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="6a63b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6a63b-105">Cette rubrique montre comment récupérer des objets de modèle de contrôle à partir d’éléments [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a63b-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="6a63b-106">Obtenir tous les modèles de contrôle</span><span class="sxs-lookup"><span data-stu-id="6a63b-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="6a63b-107">Obtenez l’élément <xref:System.Windows.Automation.AutomationElement> dont les modèles de contrôle vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="6a63b-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="6a63b-108">Appelez <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pour obtenir tous les modèles de contrôle de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6a63b-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6a63b-109">Il est fortement déconseillé d’utiliser <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> sur un client.</span><span class="sxs-lookup"><span data-stu-id="6a63b-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="6a63b-110">Cela peut dégrader sérieusement les performances, car cette méthode appelle <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> en interne pour chaque modèle de contrôle existant.</span><span class="sxs-lookup"><span data-stu-id="6a63b-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="6a63b-111">Si possible, un client doit appeler <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pour les modèles les plus intéressants.</span><span class="sxs-lookup"><span data-stu-id="6a63b-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="6a63b-112">Obtenir un modèle de contrôle spécifique</span><span class="sxs-lookup"><span data-stu-id="6a63b-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="6a63b-113">Obtenez l’élément <xref:System.Windows.Automation.AutomationElement> dont les modèles de contrôle vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="6a63b-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="6a63b-114">Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> pour rechercher un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="6a63b-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="6a63b-115">Ces méthodes sont similaires, mais si le modèle est introuvable, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lève une exception et <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="6a63b-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a63b-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a63b-116">Example</span></span>  
 <span data-ttu-id="6a63b-117">L’exemple suivant récupère un élément <xref:System.Windows.Automation.AutomationElement> pour un élément de liste et obtient un modèle <xref:System.Windows.Automation.SelectionItemPattern> à partir de cet élément.</span><span class="sxs-lookup"><span data-stu-id="6a63b-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="6a63b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a63b-118">See also</span></span>

- [<span data-ttu-id="6a63b-119">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="6a63b-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
