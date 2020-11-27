---
title: Obtenir des modèles de contrôle UI Automation pris en charge
description: Lisez un exemple qui montre comment récupérer des objets de modèle de contrôle pris en charge à partir d’éléments UI Automation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 68abe272e91c40932aba5bcf99394c4a8f815c53
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276449"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="f215e-103">Obtenir des modèles de contrôle UI Automation pris en charge</span><span class="sxs-lookup"><span data-stu-id="f215e-103">Get Supported UI Automation Control Patterns</span></span>

> [!NOTE]
> <span data-ttu-id="f215e-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f215e-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f215e-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="f215e-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f215e-106">Cette rubrique montre comment récupérer des objets de modèle de contrôle à partir d’éléments [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f215e-106">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="f215e-107">Obtenir tous les modèles de contrôle</span><span class="sxs-lookup"><span data-stu-id="f215e-107">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="f215e-108">Obtenez l’élément <xref:System.Windows.Automation.AutomationElement> dont les modèles de contrôle vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="f215e-108">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="f215e-109">Appelez <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pour obtenir tous les modèles de contrôle de l’élément.</span><span class="sxs-lookup"><span data-stu-id="f215e-109">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f215e-110">Il est fortement déconseillé d’utiliser <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> sur un client.</span><span class="sxs-lookup"><span data-stu-id="f215e-110">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="f215e-111">Cela peut dégrader sérieusement les performances, car cette méthode appelle <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> en interne pour chaque modèle de contrôle existant.</span><span class="sxs-lookup"><span data-stu-id="f215e-111">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="f215e-112">Si possible, un client doit appeler <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pour les modèles les plus intéressants.</span><span class="sxs-lookup"><span data-stu-id="f215e-112">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="f215e-113">Obtenir un modèle de contrôle spécifique</span><span class="sxs-lookup"><span data-stu-id="f215e-113">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="f215e-114">Obtenez l’élément <xref:System.Windows.Automation.AutomationElement> dont les modèles de contrôle vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="f215e-114">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="f215e-115">Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> pour rechercher un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="f215e-115">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="f215e-116">Ces méthodes sont similaires, mais si le modèle est introuvable, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lève une exception et <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="f215e-116">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f215e-117"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f215e-117">Example</span></span>  

 <span data-ttu-id="f215e-118">L’exemple suivant récupère un élément <xref:System.Windows.Automation.AutomationElement> pour un élément de liste et obtient un modèle <xref:System.Windows.Automation.SelectionItemPattern> à partir de cet élément.</span><span class="sxs-lookup"><span data-stu-id="f215e-118">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="f215e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f215e-119">See also</span></span>

- [<span data-ttu-id="f215e-120">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="f215e-120">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
