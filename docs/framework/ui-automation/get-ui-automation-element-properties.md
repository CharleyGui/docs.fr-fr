---
title: Obtenir les propriétés d'éléments UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: e3b3b118c3db95f55c67c2b27149734efc8cbea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968967"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="79606-102">Obtenir les propriétés d'éléments UI Automation</span><span class="sxs-lookup"><span data-stu-id="79606-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="79606-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="79606-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="79606-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="79606-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="79606-105">Cette rubrique montre comment récupérer les propriétés d’un [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] élément.</span><span class="sxs-lookup"><span data-stu-id="79606-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="79606-106">Obtenir une valeur de propriété actuelle</span><span class="sxs-lookup"><span data-stu-id="79606-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="79606-107">Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.</span><span class="sxs-lookup"><span data-stu-id="79606-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="79606-108">Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>ou récupérez la <xref:System.Windows.Automation.AutomationElement.Current%2A> structure de propriété et récupérez la valeur de l’un de ses membres.</span><span class="sxs-lookup"><span data-stu-id="79606-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="79606-109">Obtenir une valeur de propriété mise en cache</span><span class="sxs-lookup"><span data-stu-id="79606-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="79606-110">Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.</span><span class="sxs-lookup"><span data-stu-id="79606-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="79606-111">La propriété doit avoir été spécifiée dans le <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="79606-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="79606-112">Appelez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>ou récupérez la <xref:System.Windows.Automation.AutomationElement.Cached%2A> structure de propriété et récupérez la valeur de l’un de ses membres.</span><span class="sxs-lookup"><span data-stu-id="79606-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79606-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="79606-113">Example</span></span>  
 <span data-ttu-id="79606-114">L’exemple suivant montre différentes façons de récupérer les propriétés actuelles d' <xref:System.Windows.Automation.AutomationElement>un.</span><span class="sxs-lookup"><span data-stu-id="79606-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="79606-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79606-115">See also</span></span>

- [<span data-ttu-id="79606-116">Propriétés UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="79606-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="79606-117">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="79606-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="79606-118">Mise en cache dans les clients UI Automation</span><span class="sxs-lookup"><span data-stu-id="79606-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
