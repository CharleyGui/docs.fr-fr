---
title: Implémentation du modèle de contrôle TableItem d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 8f368fee6df6ebe5455f2029670e90f036d3d89a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932107"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="7203b-102">Implémentation du modèle de contrôle TableItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="7203b-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="7203b-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="7203b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7203b-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="7203b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7203b-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITableItemProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="7203b-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="7203b-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="7203b-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="7203b-107">Le modèle de contrôle <xref:System.Windows.Automation.TableItemPattern> est utilisé pour prendre en charge les contrôles enfants des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="7203b-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="7203b-108">Un accès aux fonctionnalités des cellules individuelles est fourni par l’implémentation simultanée obligatoire de <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="7203b-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="7203b-109">Ce modèle de contrôle est analogue à <xref:System.Windows.Automation.Provider.IGridItemProvider>, à la différence que tout contrôle implémentant <xref:System.Windows.Automation.Provider.ITableItemProvider> doit exposer par programmation la relation entre la cellule individuelle et ses informations de ligne et de colonne.</span><span class="sxs-lookup"><span data-stu-id="7203b-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="7203b-110">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7203b-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7203b-111">Conventions et recommandations en matière d'implémentation</span><span class="sxs-lookup"><span data-stu-id="7203b-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="7203b-112">Pour obtenir des fonctionnalités d’élément de grille associées, consultez [implémentation du modèle de contrôle GridItem d’UI Automation](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="7203b-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="7203b-113">Membres obligatoires pour ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="7203b-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="7203b-114">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="7203b-114">Required member</span></span>|<span data-ttu-id="7203b-115">Type de membre</span><span class="sxs-lookup"><span data-stu-id="7203b-115">Member type</span></span>|<span data-ttu-id="7203b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="7203b-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="7203b-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="7203b-117">Method</span></span>|<span data-ttu-id="7203b-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="7203b-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="7203b-119">Méthode</span><span class="sxs-lookup"><span data-stu-id="7203b-119">Method</span></span>|<span data-ttu-id="7203b-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="7203b-120">None</span></span>|  
  
 <span data-ttu-id="7203b-121">Ce modèle de contrôle n’est associé à aucune propriété ni à aucun événement.</span><span class="sxs-lookup"><span data-stu-id="7203b-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="7203b-122">Exceptions</span><span class="sxs-lookup"><span data-stu-id="7203b-122">Exceptions</span></span>  
 <span data-ttu-id="7203b-123">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="7203b-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7203b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7203b-124">See also</span></span>

- [<span data-ttu-id="7203b-125">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="7203b-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="7203b-126">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="7203b-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="7203b-127">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="7203b-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="7203b-128">Implémentation du modèle de contrôle Table d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="7203b-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="7203b-129">Implémentation du modèle de contrôle GridItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="7203b-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="7203b-130">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="7203b-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="7203b-131">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="7203b-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
