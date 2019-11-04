---
title: Implémentation du modèle de contrôle Table d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 1fec3671f017ae6c6864537805e6c793b5f9046b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458144"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="f80cf-102">Implémentation du modèle de contrôle Table d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="f80cf-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="f80cf-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f80cf-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f80cf-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f80cf-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f80cf-105">Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITableProvider>, notamment les informations sur les propriétés, les méthodes et les événements.</span><span class="sxs-lookup"><span data-stu-id="f80cf-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="f80cf-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="f80cf-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="f80cf-107">Le modèle de contrôle <xref:System.Windows.Automation.TablePattern> permet de prendre en charge les contrôles qui agissent comme des conteneurs pour une collection d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="f80cf-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="f80cf-108">Les enfants de cet élément doivent implémenter <xref:System.Windows.Automation.Provider.ITableItemProvider> et être organisés en un système de coordonnées logiques à deux dimensions, qui peut être parcouru par ligne et par colonne.</span><span class="sxs-lookup"><span data-stu-id="f80cf-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="f80cf-109">Ce modèle de contrôle est analogue à <xref:System.Windows.Automation.Provider.IGridProvider>, à la différence que tout contrôle implémentant <xref:System.Windows.Automation.Provider.ITableProvider> doit également exposer une relation d’en-tête de colonne et/ou de ligne pour chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="f80cf-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="f80cf-110">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="f80cf-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="f80cf-111">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="f80cf-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="f80cf-112">Quand vous implémentez le modèle de contrôle Table, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f80cf-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="f80cf-113">L’accès au contenu des cellules individuelles s’effectue via un système de coordonnées logiques à deux dimensions ou un tableau fourni par l’implémentation simultanée requise de <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="f80cf-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="f80cf-114">Un en-tête de colonne ou de ligne peut figurer dans un objet table ou être un objet d’en-tête séparé, associé à un objet table.</span><span class="sxs-lookup"><span data-stu-id="f80cf-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="f80cf-115">Les en-têtes de colonne et de ligne peuvent inclure un en-tête principal et des en-têtes de prise en charge quelconques.</span><span class="sxs-lookup"><span data-stu-id="f80cf-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f80cf-116">Ce concept devient évident dans une feuille de calcul Microsoft Excel où un utilisateur a défini une colonne de « prénom ».</span><span class="sxs-lookup"><span data-stu-id="f80cf-116">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="f80cf-117">Cette colonne a désormais deux en-têtes : l’en-tête « Prénom » défini par l’utilisateur et la désignation alphanumérique de cette colonne affectée par l’application.</span><span class="sxs-lookup"><span data-stu-id="f80cf-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="f80cf-118">Consultez [implémentation du modèle de contrôle Grid d’UI Automation](implementing-the-ui-automation-grid-control-pattern.md) pour les fonctionnalités de grille associées.</span><span class="sxs-lookup"><span data-stu-id="f80cf-118">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="f80cf-119">![Table avec éléments d’en-tête complexes.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="f80cf-119">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="f80cf-120">Exemple de table avec des en-têtes de colonne complexes</span><span class="sxs-lookup"><span data-stu-id="f80cf-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="f80cf-121">![Table avec propriété RowOrColumnMajor ambiguë.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="f80cf-121">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="f80cf-122">Exemple de table avec une propriété RowOrColumnMajor ambiguë</span><span class="sxs-lookup"><span data-stu-id="f80cf-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="f80cf-123">Membres requis pour ITableProvider</span><span class="sxs-lookup"><span data-stu-id="f80cf-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="f80cf-124">Les propriétés et les méthodes suivantes sont requises pour l’interface ITableProvider.</span><span class="sxs-lookup"><span data-stu-id="f80cf-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="f80cf-125">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="f80cf-125">Required members</span></span>|<span data-ttu-id="f80cf-126">Type de membre</span><span class="sxs-lookup"><span data-stu-id="f80cf-126">Member type</span></span>|<span data-ttu-id="f80cf-127">Notes</span><span class="sxs-lookup"><span data-stu-id="f80cf-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="f80cf-128">Property</span><span class="sxs-lookup"><span data-stu-id="f80cf-128">Property</span></span>|<span data-ttu-id="f80cf-129">aucune.</span><span class="sxs-lookup"><span data-stu-id="f80cf-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="f80cf-130">Méthode</span><span class="sxs-lookup"><span data-stu-id="f80cf-130">Method</span></span>|<span data-ttu-id="f80cf-131">aucune.</span><span class="sxs-lookup"><span data-stu-id="f80cf-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="f80cf-132">Méthode</span><span class="sxs-lookup"><span data-stu-id="f80cf-132">Method</span></span>|<span data-ttu-id="f80cf-133">aucune.</span><span class="sxs-lookup"><span data-stu-id="f80cf-133">None</span></span>|  
  
 <span data-ttu-id="f80cf-134">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="f80cf-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="f80cf-135">Exceptions</span><span class="sxs-lookup"><span data-stu-id="f80cf-135">Exceptions</span></span>  
 <span data-ttu-id="f80cf-136">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="f80cf-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80cf-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f80cf-137">See also</span></span>

- [<span data-ttu-id="f80cf-138">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="f80cf-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="f80cf-139">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="f80cf-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="f80cf-140">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="f80cf-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="f80cf-141">Implémentation du modèle de contrôle TableItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="f80cf-141">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="f80cf-142">Implémentation du modèle de contrôle Grid d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="f80cf-142">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="f80cf-143">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="f80cf-143">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="f80cf-144">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="f80cf-144">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
