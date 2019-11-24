---
title: Implémentation du modèle de contrôle TableItem d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 4374666ba5e03720413614c63b00ba987f81f58f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447082"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="4abb7-102">Implémentation du modèle de contrôle TableItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="4abb7-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="4abb7-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="4abb7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4abb7-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="4abb7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4abb7-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITableItemProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="4abb7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="4abb7-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="4abb7-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="4abb7-107">Le modèle de contrôle <xref:System.Windows.Automation.TableItemPattern> est utilisé pour prendre en charge les contrôles enfants des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="4abb7-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="4abb7-108">Un accès aux fonctionnalités des cellules individuelles est fourni par l’implémentation simultanée obligatoire de <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="4abb7-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="4abb7-109">Ce modèle de contrôle est analogue à <xref:System.Windows.Automation.Provider.IGridItemProvider>, à la différence que tout contrôle implémentant <xref:System.Windows.Automation.Provider.ITableItemProvider> doit exposer par programmation la relation entre la cellule individuelle et ses informations de ligne et de colonne.</span><span class="sxs-lookup"><span data-stu-id="4abb7-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="4abb7-110">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4abb7-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="4abb7-111">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="4abb7-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="4abb7-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4abb7-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="4abb7-113">Membres obligatoires pour ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="4abb7-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="4abb7-114">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="4abb7-114">Required member</span></span>|<span data-ttu-id="4abb7-115">Type de membre</span><span class="sxs-lookup"><span data-stu-id="4abb7-115">Member type</span></span>|<span data-ttu-id="4abb7-116">Notes</span><span class="sxs-lookup"><span data-stu-id="4abb7-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="4abb7-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="4abb7-117">Method</span></span>|<span data-ttu-id="4abb7-118">aucune.</span><span class="sxs-lookup"><span data-stu-id="4abb7-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="4abb7-119">Méthode</span><span class="sxs-lookup"><span data-stu-id="4abb7-119">Method</span></span>|<span data-ttu-id="4abb7-120">aucune.</span><span class="sxs-lookup"><span data-stu-id="4abb7-120">None</span></span>|  
  
 <span data-ttu-id="4abb7-121">Ce modèle de contrôle n’est associé à aucune propriété ni à aucun événement.</span><span class="sxs-lookup"><span data-stu-id="4abb7-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="4abb7-122">Exceptions</span><span class="sxs-lookup"><span data-stu-id="4abb7-122">Exceptions</span></span>  
 <span data-ttu-id="4abb7-123">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="4abb7-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abb7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4abb7-124">See also</span></span>

- [<span data-ttu-id="4abb7-125">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="4abb7-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="4abb7-126">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="4abb7-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="4abb7-127">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="4abb7-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="4abb7-128">Implémentation du modèle de contrôle Table d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="4abb7-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="4abb7-129">Implémentation du modèle de contrôle GridItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="4abb7-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="4abb7-130">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="4abb7-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="4abb7-131">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="4abb7-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
