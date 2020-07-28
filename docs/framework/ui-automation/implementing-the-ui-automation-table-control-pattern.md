---
title: Implémentation du modèle de contrôle Table d’UI Automation
description: Passez en revue les recommandations et les conventions pour implémenter le modèle de contrôle table dans UI Automation. Connaître les membres requis pour l’interface ITableProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168234"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="8363e-104">Implémentation du modèle de contrôle Table d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="8363e-104">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="8363e-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="8363e-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8363e-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8363e-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8363e-107">Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITableProvider>, notamment les informations sur les propriétés, les méthodes et les événements.</span><span class="sxs-lookup"><span data-stu-id="8363e-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="8363e-108">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="8363e-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="8363e-109">Le modèle de contrôle <xref:System.Windows.Automation.TablePattern> permet de prendre en charge les contrôles qui agissent comme des conteneurs pour une collection d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="8363e-109">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="8363e-110">Les enfants de cet élément doivent implémenter <xref:System.Windows.Automation.Provider.ITableItemProvider> et être organisés en un système de coordonnées logiques à deux dimensions, qui peut être parcouru par ligne et par colonne.</span><span class="sxs-lookup"><span data-stu-id="8363e-110">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="8363e-111">Ce modèle de contrôle est analogue à <xref:System.Windows.Automation.Provider.IGridProvider>, à la différence que tout contrôle implémentant <xref:System.Windows.Automation.Provider.ITableProvider> doit également exposer une relation d’en-tête de colonne et/ou de ligne pour chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="8363e-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="8363e-112">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8363e-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8363e-113">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="8363e-113">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8363e-114">Quand vous implémentez le modèle de contrôle Table, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8363e-114">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8363e-115">L’accès au contenu des cellules individuelles s’effectue via un système de coordonnées logiques à deux dimensions ou un tableau fourni par l’implémentation simultanée requise de <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="8363e-115">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="8363e-116">Un en-tête de colonne ou de ligne peut figurer dans un objet table ou être un objet d’en-tête séparé, associé à un objet table.</span><span class="sxs-lookup"><span data-stu-id="8363e-116">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="8363e-117">Les en-têtes de colonne et de ligne peuvent inclure un en-tête principal et des en-têtes de prise en charge quelconques.</span><span class="sxs-lookup"><span data-stu-id="8363e-117">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8363e-118">Ce concept devient évident dans une feuille de calcul Microsoft Excel où un utilisateur a défini une colonne de « prénom ».</span><span class="sxs-lookup"><span data-stu-id="8363e-118">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="8363e-119">Cette colonne a désormais deux en-têtes : l’en-tête « Prénom » défini par l’utilisateur et la désignation alphanumérique de cette colonne affectée par l’application.</span><span class="sxs-lookup"><span data-stu-id="8363e-119">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="8363e-120">Consultez [implémentation du modèle de contrôle Grid d’UI Automation](implementing-the-ui-automation-grid-control-pattern.md) pour les fonctionnalités de grille associées.</span><span class="sxs-lookup"><span data-stu-id="8363e-120">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="8363e-121">![Table avec éléments d'en-tête complexes.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="8363e-121">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="8363e-122">Exemple de table avec des en-têtes de colonne complexes</span><span class="sxs-lookup"><span data-stu-id="8363e-122">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="8363e-123">![Table avec propriété RowOrColumnMajor ambiguë.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="8363e-123">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="8363e-124">Exemple de table avec une propriété RowOrColumnMajor ambiguë</span><span class="sxs-lookup"><span data-stu-id="8363e-124">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="8363e-125">Membres requis pour ITableProvider</span><span class="sxs-lookup"><span data-stu-id="8363e-125">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="8363e-126">Les propriétés et les méthodes suivantes sont requises pour l’interface ITableProvider.</span><span class="sxs-lookup"><span data-stu-id="8363e-126">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="8363e-127">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="8363e-127">Required members</span></span>|<span data-ttu-id="8363e-128">Type de membre</span><span class="sxs-lookup"><span data-stu-id="8363e-128">Member type</span></span>|<span data-ttu-id="8363e-129">Notes</span><span class="sxs-lookup"><span data-stu-id="8363e-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="8363e-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="8363e-130">Property</span></span>|<span data-ttu-id="8363e-131">None</span><span class="sxs-lookup"><span data-stu-id="8363e-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="8363e-132">Méthode</span><span class="sxs-lookup"><span data-stu-id="8363e-132">Method</span></span>|<span data-ttu-id="8363e-133">None</span><span class="sxs-lookup"><span data-stu-id="8363e-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="8363e-134">Méthode</span><span class="sxs-lookup"><span data-stu-id="8363e-134">Method</span></span>|<span data-ttu-id="8363e-135">None</span><span class="sxs-lookup"><span data-stu-id="8363e-135">None</span></span>|  
  
 <span data-ttu-id="8363e-136">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="8363e-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="8363e-137">Exceptions</span><span class="sxs-lookup"><span data-stu-id="8363e-137">Exceptions</span></span>  
 <span data-ttu-id="8363e-138">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="8363e-138">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8363e-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8363e-139">See also</span></span>

- [<span data-ttu-id="8363e-140">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="8363e-140">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8363e-141">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="8363e-141">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8363e-142">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="8363e-142">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8363e-143">Implémentation du modèle de contrôle TableItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="8363e-143">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="8363e-144">Implémentation du modèle de contrôle Grid d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="8363e-144">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="8363e-145">Vue d’ensemble de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="8363e-145">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="8363e-146">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="8363e-146">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
