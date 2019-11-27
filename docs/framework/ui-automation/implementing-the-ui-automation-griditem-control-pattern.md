---
title: Implémentation du modèle de contrôle GridItem d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435253"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="9eee5-102">Implémentation du modèle de contrôle GridItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="9eee5-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9eee5-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="9eee5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9eee5-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9eee5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9eee5-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IGridItemProvider>, notamment des informations sur les propriétés.</span><span class="sxs-lookup"><span data-stu-id="9eee5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="9eee5-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="9eee5-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9eee5-107">Le modèle de contrôle <xref:System.Windows.Automation.GridItemPattern> est utilisé pour prendre en charge les contrôles enfants individuels des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="9eee5-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="9eee5-108">Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9eee5-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9eee5-109">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="9eee5-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9eee5-110">Quand vous implémentez <xref:System.Windows.Automation.Provider.IGridProvider>, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9eee5-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="9eee5-111">Les coordonnées de grille ont une base zéro et la cellule supérieure gauche possède les coordonnées (0, 0).</span><span class="sxs-lookup"><span data-stu-id="9eee5-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="9eee5-112">Les cellules fusionnées signalent leurs propriétés <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> et <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> en fonction de leur cellule d’ancrage sous-jacente, comme défini par le fournisseur UI Automation.</span><span class="sxs-lookup"><span data-stu-id="9eee5-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="9eee5-113">En règle générale, il s’agit de la ligne la plus haute ou de la colonne la plus à gauche.</span><span class="sxs-lookup"><span data-stu-id="9eee5-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="9eee5-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> ne permet pas une manipulation active de la grille telle que la fusion ou le fractionnement des cellules.</span><span class="sxs-lookup"><span data-stu-id="9eee5-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="9eee5-115">Les contrôles qui implémentent <xref:System.Windows.Automation.Provider.IGridItemProvider> peuvent généralement être parcourus (c’est-à-dire qu’un client UI Automation peut se déplacer vers les contrôles adjacents) à l’aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="9eee5-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="9eee5-116">Membres obligatoires pour IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="9eee5-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="9eee5-117">Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="9eee5-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="9eee5-118">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="9eee5-118">Required members</span></span>|<span data-ttu-id="9eee5-119">Type de membre</span><span class="sxs-lookup"><span data-stu-id="9eee5-119">Member type</span></span>|<span data-ttu-id="9eee5-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="9eee5-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="9eee5-121">Propriété</span><span class="sxs-lookup"><span data-stu-id="9eee5-121">Property</span></span>|<span data-ttu-id="9eee5-122">Aucune</span><span class="sxs-lookup"><span data-stu-id="9eee5-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="9eee5-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="9eee5-123">Property</span></span>|<span data-ttu-id="9eee5-124">Aucune</span><span class="sxs-lookup"><span data-stu-id="9eee5-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="9eee5-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="9eee5-125">Property</span></span>|<span data-ttu-id="9eee5-126">Aucune</span><span class="sxs-lookup"><span data-stu-id="9eee5-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="9eee5-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="9eee5-127">Property</span></span>|<span data-ttu-id="9eee5-128">Aucune</span><span class="sxs-lookup"><span data-stu-id="9eee5-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="9eee5-129">Propriété</span><span class="sxs-lookup"><span data-stu-id="9eee5-129">Property</span></span>|<span data-ttu-id="9eee5-130">Aucune</span><span class="sxs-lookup"><span data-stu-id="9eee5-130">None</span></span>|  
  
 <span data-ttu-id="9eee5-131">Ce modèle de contrôle n’est associé à aucune méthode ou aucun événement.</span><span class="sxs-lookup"><span data-stu-id="9eee5-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="9eee5-132">Exceptions</span><span class="sxs-lookup"><span data-stu-id="9eee5-132">Exceptions</span></span>  
 <span data-ttu-id="9eee5-133">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="9eee5-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eee5-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eee5-134">See also</span></span>

- [<span data-ttu-id="9eee5-135">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="9eee5-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9eee5-136">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="9eee5-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9eee5-137">UI Automation Control Patterns for Clients</span><span class="sxs-lookup"><span data-stu-id="9eee5-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9eee5-138">Implémentation du modèle de contrôle Grid d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="9eee5-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="9eee5-139">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="9eee5-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="9eee5-140">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="9eee5-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
