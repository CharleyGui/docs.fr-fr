---
title: Implémentation du modèle de contrôle GridItem d’UI Automation
description: Connaître les recommandations et les conventions permettant d’implémenter le modèle de contrôle GridItemPattern pour les éléments de grille dans UI Automation. Consultez les membres requis pour IGridItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165823"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="6b77b-104">Implémentation du modèle de contrôle GridItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="6b77b-104">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="6b77b-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6b77b-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6b77b-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="6b77b-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6b77b-107">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IGridItemProvider>, notamment des informations sur les propriétés.</span><span class="sxs-lookup"><span data-stu-id="6b77b-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="6b77b-108">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="6b77b-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="6b77b-109">Le modèle de contrôle <xref:System.Windows.Automation.GridItemPattern> est utilisé pour prendre en charge les contrôles enfants individuels des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="6b77b-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="6b77b-110">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="6b77b-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="6b77b-111">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="6b77b-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="6b77b-112">Quand vous implémentez <xref:System.Windows.Automation.Provider.IGridProvider>, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b77b-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="6b77b-113">Les coordonnées de grille ont une base zéro et la cellule supérieure gauche possède les coordonnées (0, 0).</span><span class="sxs-lookup"><span data-stu-id="6b77b-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="6b77b-114">Les cellules fusionnées signalent leurs propriétés <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> et <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> en fonction de leur cellule d’ancrage sous-jacente, comme défini par le fournisseur UI Automation.</span><span class="sxs-lookup"><span data-stu-id="6b77b-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="6b77b-115">En règle générale, il s’agit de la ligne la plus haute ou de la colonne la plus à gauche.</span><span class="sxs-lookup"><span data-stu-id="6b77b-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="6b77b-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> ne fournit pas de manipulation active de la grille telle que la fusion ou le fractionnement des cellules.</span><span class="sxs-lookup"><span data-stu-id="6b77b-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="6b77b-117">Les contrôles qui implémentent <xref:System.Windows.Automation.Provider.IGridItemProvider> peuvent généralement être parcourus (c’est-à-dire qu’un client UI Automation peut se déplacer vers les contrôles adjacents) à l’aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="6b77b-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="6b77b-118">Membres obligatoires pour IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="6b77b-118">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="6b77b-119">Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="6b77b-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="6b77b-120">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="6b77b-120">Required members</span></span>|<span data-ttu-id="6b77b-121">Type de membre</span><span class="sxs-lookup"><span data-stu-id="6b77b-121">Member type</span></span>|<span data-ttu-id="6b77b-122">Notes</span><span class="sxs-lookup"><span data-stu-id="6b77b-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="6b77b-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="6b77b-123">Property</span></span>|<span data-ttu-id="6b77b-124">None</span><span class="sxs-lookup"><span data-stu-id="6b77b-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="6b77b-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="6b77b-125">Property</span></span>|<span data-ttu-id="6b77b-126">None</span><span class="sxs-lookup"><span data-stu-id="6b77b-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="6b77b-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="6b77b-127">Property</span></span>|<span data-ttu-id="6b77b-128">None</span><span class="sxs-lookup"><span data-stu-id="6b77b-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="6b77b-129">Propriété</span><span class="sxs-lookup"><span data-stu-id="6b77b-129">Property</span></span>|<span data-ttu-id="6b77b-130">None</span><span class="sxs-lookup"><span data-stu-id="6b77b-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="6b77b-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="6b77b-131">Property</span></span>|<span data-ttu-id="6b77b-132">None</span><span class="sxs-lookup"><span data-stu-id="6b77b-132">None</span></span>|  
  
 <span data-ttu-id="6b77b-133">Ce modèle de contrôle n’est associé à aucune méthode ou aucun événement.</span><span class="sxs-lookup"><span data-stu-id="6b77b-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="6b77b-134">Exceptions</span><span class="sxs-lookup"><span data-stu-id="6b77b-134">Exceptions</span></span>  
 <span data-ttu-id="6b77b-135">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="6b77b-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b77b-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b77b-136">See also</span></span>

- [<span data-ttu-id="6b77b-137">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="6b77b-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="6b77b-138">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="6b77b-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="6b77b-139">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="6b77b-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="6b77b-140">Implémentation du modèle de contrôle Grid d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="6b77b-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="6b77b-141">Vue d’ensemble de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="6b77b-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="6b77b-142">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="6b77b-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
