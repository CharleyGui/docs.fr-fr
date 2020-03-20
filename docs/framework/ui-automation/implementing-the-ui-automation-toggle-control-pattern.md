---
title: Implémentation du modèle de contrôle Toggle d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180064"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="2b044-102">Implémentation du modèle de contrôle Toggle d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="2b044-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="2b044-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="2b044-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2b044-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2b044-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2b044-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IToggleProvider>, notamment des informations sur les méthodes et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="2b044-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="2b044-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="2b044-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="2b044-107">Le modèle de contrôle <xref:System.Windows.Automation.TogglePattern> est utilisé pour prendre en charge les contrôles qui peuvent passer par un ensemble d’états, et conserver un état une fois ce dernier défini.</span><span class="sxs-lookup"><span data-stu-id="2b044-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="2b044-108">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="2b044-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="2b044-109">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="2b044-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="2b044-110">Quand vous implémentez le modèle de contrôle Toggle, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2b044-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="2b044-111">Les contrôles qui ne conservent pas l’état une fois ce dernier activé, par exemple les boutons, les boutons de barre d’outils et les liens hypertexte, doivent implémenter <xref:System.Windows.Automation.Provider.IInvokeProvider> à la place.</span><span class="sxs-lookup"><span data-stu-id="2b044-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="2b044-112">Un contrôle doit parcourir <xref:System.Windows.Automation.ToggleState> dans l’ordre suivant : <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> et, si cela est pris en charge, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="2b044-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="2b044-113"><xref:System.Windows.Automation.TogglePattern> ne fournit pas de méthode SetState(newState) en raison de problèmes liés à la définition directe d’une case à cocher à trois états sans parcourir sa séquence <xref:System.Windows.Automation.ToggleState> appropriée.</span><span class="sxs-lookup"><span data-stu-id="2b044-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="2b044-114">Le contrôle de type RadioButton n’implémente pas <xref:System.Windows.Automation.Provider.IToggleProvider>, car il n’est pas capable de parcourir ses états valides.</span><span class="sxs-lookup"><span data-stu-id="2b044-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="2b044-115">Membres obligatoires pour IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="2b044-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="2b044-116">Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="2b044-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="2b044-117">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="2b044-117">Required member</span></span>|<span data-ttu-id="2b044-118">Type de membre</span><span class="sxs-lookup"><span data-stu-id="2b044-118">Member type</span></span>|<span data-ttu-id="2b044-119">Notes</span><span class="sxs-lookup"><span data-stu-id="2b044-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="2b044-120">Méthode</span><span class="sxs-lookup"><span data-stu-id="2b044-120">Method</span></span>|<span data-ttu-id="2b044-121">None</span><span class="sxs-lookup"><span data-stu-id="2b044-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="2b044-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="2b044-122">Property</span></span>|<span data-ttu-id="2b044-123">None</span><span class="sxs-lookup"><span data-stu-id="2b044-123">None</span></span>|  
  
 <span data-ttu-id="2b044-124">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="2b044-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="2b044-125">Exceptions</span><span class="sxs-lookup"><span data-stu-id="2b044-125">Exceptions</span></span>  
 <span data-ttu-id="2b044-126">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="2b044-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b044-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b044-127">See also</span></span>

- [<span data-ttu-id="2b044-128">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="2b044-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2b044-129">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="2b044-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="2b044-130">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="2b044-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2b044-131">Obtenir l'état bascule d'une case à cocher à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="2b044-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="2b044-132">UI Automation Tree Overview</span><span class="sxs-lookup"><span data-stu-id="2b044-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="2b044-133">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="2b044-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
