---
title: Obtenir les propriétés d'éléments UI Automation
description: Consultez les instructions et un exemple qui montre comment récupérer les propriétés actuelles ou mises en cache d’un élément UI Automation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164107"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="bf586-103">Obtenir les propriétés d'éléments UI Automation</span><span class="sxs-lookup"><span data-stu-id="bf586-103">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="bf586-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="bf586-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bf586-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bf586-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bf586-106">Cette rubrique montre comment récupérer les propriétés d’un [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] élément.</span><span class="sxs-lookup"><span data-stu-id="bf586-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="bf586-107">Obtenir une valeur de propriété actuelle</span><span class="sxs-lookup"><span data-stu-id="bf586-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="bf586-108">Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.</span><span class="sxs-lookup"><span data-stu-id="bf586-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="bf586-109">Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou récupérez la <xref:System.Windows.Automation.AutomationElement.Current%2A> structure de propriété et récupérez la valeur de l’un de ses membres.</span><span class="sxs-lookup"><span data-stu-id="bf586-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="bf586-110">Obtenir une valeur de propriété mise en cache</span><span class="sxs-lookup"><span data-stu-id="bf586-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="bf586-111">Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.</span><span class="sxs-lookup"><span data-stu-id="bf586-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="bf586-112">La propriété doit avoir été spécifiée dans le <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bf586-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="bf586-113">Appelez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou récupérez la <xref:System.Windows.Automation.AutomationElement.Cached%2A> structure de propriété et récupérez la valeur de l’un de ses membres.</span><span class="sxs-lookup"><span data-stu-id="bf586-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf586-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf586-114">Example</span></span>  
 <span data-ttu-id="bf586-115">L’exemple suivant montre différentes façons de récupérer les propriétés actuelles d’un <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="bf586-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="bf586-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf586-116">See also</span></span>

- [<span data-ttu-id="bf586-117">Propriétés UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="bf586-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="bf586-118">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="bf586-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="bf586-119">Mise en cache dans les clients UI Automation</span><span class="sxs-lookup"><span data-stu-id="bf586-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
