---
title: Implémentation du modèle de contrôle Grid d’UI Automation
description: Comprendre les recommandations et les conventions pour implémenter le modèle de contrôle Grid GridPattern dans UI Automation. Apprenez à implémenter l’interface IGridProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 2290fd91c8eee0ab969eef2827d3c7440ef21e20
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274879"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="3c3f6-104">Implémentation du modèle de contrôle Grid d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="3c3f6-104">Implementing the UI Automation Grid Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="3c3f6-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3c3f6-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3c3f6-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3c3f6-107">Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.IGridProvider>, notamment les informations sur les propriétés, les méthodes et les événements.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="3c3f6-108">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="3c3f6-109">Le modèle de contrôle <xref:System.Windows.Automation.GridPattern> permet de prendre en charge les contrôles qui agissent comme des conteneurs pour une collection d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-109">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="3c3f6-110">Les enfants de cet élément doivent implémenter <xref:System.Windows.Automation.Provider.IGridItemProvider> et être organisés en un système de coordonnées logiques à deux dimensions, qui peut être parcouru par ligne et par colonne.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-110">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="3c3f6-111">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3c3f6-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="3c3f6-112">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="3c3f6-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="3c3f6-113">Quand vous implémentez le modèle de contrôle Grid, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c3f6-113">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="3c3f6-114">Les coordonnées de grille sont de base zéro, les coordonnées de la cellule supérieure gauche (ou supérieure droite en fonction des paramètres régionaux) ayant pour coordonnées (0, 0).</span><span class="sxs-lookup"><span data-stu-id="3c3f6-114">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="3c3f6-115">Si une cellule est vide, un élément UI Automation doit être retourné pour permettre la prise en charge de la propriété <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> de cette cellule.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-115">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="3c3f6-116">Cela est possible quand la disposition des éléments enfants de la grille est semblable à celle d’un tableau non justifié (consultez l’exemple ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="3c3f6-116">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="3c3f6-117">![Vue de l'Explorateur Windows montrant une disposition irrégulière.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="3c3f6-117">![Windows Explorer view showing ragged layout.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="3c3f6-118">Exemple de contrôle Grid avec des coordonnées vides</span><span class="sxs-lookup"><span data-stu-id="3c3f6-118">Example of a Grid Control with Empty Coordinates</span></span>  
  
- <span data-ttu-id="3c3f6-119">Une grille avec un seul élément est nécessaire pour implémenter <xref:System.Windows.Automation.Provider.IGridProvider> , s’il est logiquement considéré comme une grille.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-119">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="3c3f6-120">Le nombre d’éléments enfants de la grille est immatériel.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-120">The number of child items in the grid is immaterial.</span></span>  
  
- <span data-ttu-id="3c3f6-121">Selon l’implémentation du fournisseur, les lignes et les colonnes masquées peuvent être chargées dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , et sont donc reflétées dans les propriétés <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> et <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> .</span><span class="sxs-lookup"><span data-stu-id="3c3f6-121">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="3c3f6-122">Si les lignes et les colonnes masquées n’ont pas encore été chargées, elles ne doivent pas être comptabilisées.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-122">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
- <span data-ttu-id="3c3f6-123"><xref:System.Windows.Automation.Provider.IGridProvider> n’active pas la manipulation active d’une grille. <xref:System.Windows.Automation.Provider.ITransformProvider> doit être implémenté pour activer cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-123"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
- <span data-ttu-id="3c3f6-124">Utilisez <xref:System.Windows.Automation.StructureChangedEventHandler> pour écouter les changements de structure ou de disposition apportés à la grille, par exemple quand des cellules sont ajoutées, supprimées ou fusionnées.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-124">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
- <span data-ttu-id="3c3f6-125">Utilisez <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> pour suivre le parcours des éléments ou des cellules d’une grille.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-125">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>

## <a name="required-members-for-igridprovider"></a><span data-ttu-id="3c3f6-126">Membres obligatoires pour IGridProvider</span><span class="sxs-lookup"><span data-stu-id="3c3f6-126">Required Members for IGridProvider</span></span>  

 <span data-ttu-id="3c3f6-127">Les propriétés et méthodes suivantes sont nécessaires à l’implémentation de l’interface IGridProvider.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-127">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="3c3f6-128">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="3c3f6-128">Required members</span></span>|<span data-ttu-id="3c3f6-129">Type</span><span class="sxs-lookup"><span data-stu-id="3c3f6-129">Type</span></span>|<span data-ttu-id="3c3f6-130">Notes</span><span class="sxs-lookup"><span data-stu-id="3c3f6-130">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="3c3f6-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="3c3f6-131">Property</span></span>|<span data-ttu-id="3c3f6-132">None</span><span class="sxs-lookup"><span data-stu-id="3c3f6-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="3c3f6-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="3c3f6-133">Property</span></span>|<span data-ttu-id="3c3f6-134">None</span><span class="sxs-lookup"><span data-stu-id="3c3f6-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="3c3f6-135">Méthode</span><span class="sxs-lookup"><span data-stu-id="3c3f6-135">Method</span></span>|<span data-ttu-id="3c3f6-136">None</span><span class="sxs-lookup"><span data-stu-id="3c3f6-136">None</span></span>|  
  
 <span data-ttu-id="3c3f6-137">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-137">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="3c3f6-138">Exceptions</span><span class="sxs-lookup"><span data-stu-id="3c3f6-138">Exceptions</span></span>  

 <span data-ttu-id="3c3f6-139">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-139">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="3c3f6-140">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="3c3f6-140">Exception type</span></span>|<span data-ttu-id="3c3f6-141">Condition</span><span class="sxs-lookup"><span data-stu-id="3c3f6-141">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="3c3f6-142">-Si la coordonnée de la ligne demandée est supérieure à ou si la <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> coordonnée de la colonne est supérieure à <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A> .</span><span class="sxs-lookup"><span data-stu-id="3c3f6-142">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="3c3f6-143">-Si l’une des coordonnées de la ligne ou de la colonne demandée est inférieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="3c3f6-143">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c3f6-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c3f6-144">See also</span></span>

- [<span data-ttu-id="3c3f6-145">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="3c3f6-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="3c3f6-146">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="3c3f6-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="3c3f6-147">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="3c3f6-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="3c3f6-148">Implémentation du modèle de contrôle GridItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="3c3f6-148">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="3c3f6-149">Vue d’ensemble de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="3c3f6-149">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="3c3f6-150">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="3c3f6-150">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
