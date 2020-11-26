---
title: Implémentation du modèle de contrôle RangeValue d’UI Automation
description: Passez en revue les recommandations et les conventions d’implémentation du modèle de contrôle RangeValue dans UI Automation. Consultez les membres requis pour l’interface IRangeValueProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 9b5bfd571b078b7aeab149f5371004ac832fadcc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239560"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="e975f-104">Implémentation du modèle de contrôle RangeValue d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="e975f-104">Implementing the UI Automation RangeValue Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="e975f-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e975f-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e975f-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e975f-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e975f-107">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IRangeValueProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="e975f-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="e975f-108">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="e975f-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="e975f-109">Le modèle de contrôle <xref:System.Windows.Automation.RangeValuePattern> est utilisé pour prendre en charge les contrôles auxquels vous pouvez affecter une valeur comprise dans une plage.</span><span class="sxs-lookup"><span data-stu-id="e975f-109">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="e975f-110">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e975f-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e975f-111">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="e975f-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="e975f-112">Quand vous implémentez le modèle de contrôle RangeValue, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e975f-112">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="e975f-113">Les contrôles autorisent le réétalonnage de leurs propriétés prises en charge en fonction des paramètres régionaux ou des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e975f-113">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="e975f-114">Par exemple, vous pouvez définir un contrôle de thermomètre pour afficher la température en degrés Fahrenheit ou Celsius.</span><span class="sxs-lookup"><span data-stu-id="e975f-114">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="e975f-115">Les contrôles qui ont des valeurs de plage ambiguës, telles que les barres de progression ou les curseurs, doivent normaliser ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="e975f-115">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="e975f-116">![Barre de progression.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="e975f-116">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="e975f-117">Exemple d’une barre de progression où la valeur est de type entier, et où les valeurs de propriété minimale et maximale sont normalisées à 0 et 100, respectivement</span><span class="sxs-lookup"><span data-stu-id="e975f-117">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>

## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="e975f-118">Membres obligatoires pour IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="e975f-118">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="e975f-119">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="e975f-119">Required member</span></span>|<span data-ttu-id="e975f-120">Type de membre</span><span class="sxs-lookup"><span data-stu-id="e975f-120">Member type</span></span>|<span data-ttu-id="e975f-121">Notes</span><span class="sxs-lookup"><span data-stu-id="e975f-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="e975f-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="e975f-122">Property</span></span>|<span data-ttu-id="e975f-123">None</span><span class="sxs-lookup"><span data-stu-id="e975f-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="e975f-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="e975f-124">Property</span></span>|<span data-ttu-id="e975f-125">None</span><span class="sxs-lookup"><span data-stu-id="e975f-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="e975f-126">Propriété</span><span class="sxs-lookup"><span data-stu-id="e975f-126">Property</span></span>|<span data-ttu-id="e975f-127">None</span><span class="sxs-lookup"><span data-stu-id="e975f-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="e975f-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="e975f-128">Property</span></span>|<span data-ttu-id="e975f-129">None</span><span class="sxs-lookup"><span data-stu-id="e975f-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="e975f-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="e975f-130">Property</span></span>|<span data-ttu-id="e975f-131">None</span><span class="sxs-lookup"><span data-stu-id="e975f-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="e975f-132">Propriété</span><span class="sxs-lookup"><span data-stu-id="e975f-132">Property</span></span>|<span data-ttu-id="e975f-133">None</span><span class="sxs-lookup"><span data-stu-id="e975f-133">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="e975f-134">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e975f-134">Methods</span></span>|<span data-ttu-id="e975f-135">None</span><span class="sxs-lookup"><span data-stu-id="e975f-135">None</span></span>|  
  
 <span data-ttu-id="e975f-136">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="e975f-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="e975f-137">Exceptions</span><span class="sxs-lookup"><span data-stu-id="e975f-137">Exceptions</span></span>  

 <span data-ttu-id="e975f-138">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="e975f-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="e975f-139">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="e975f-139">Exception type</span></span>|<span data-ttu-id="e975f-140">Condition</span><span class="sxs-lookup"><span data-stu-id="e975f-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="e975f-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> est appelé avec une valeur supérieure à <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> , ou inférieure à <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="e975f-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e975f-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e975f-142">See also</span></span>

- [<span data-ttu-id="e975f-143">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="e975f-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e975f-144">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="e975f-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="e975f-145">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="e975f-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e975f-146">Vue d’ensemble de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="e975f-146">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="e975f-147">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="e975f-147">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
