---
title: Implémentation du modèle de contrôle RangeValue d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: bb486dc210bc2d03be6400e9fe5c80b2a7c1de8e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659865"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="5ec11-102">Implémentation du modèle de contrôle RangeValue d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="5ec11-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5ec11-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="5ec11-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5ec11-104">Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5ec11-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5ec11-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IRangeValueProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="5ec11-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="5ec11-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="5ec11-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5ec11-107">Le modèle de contrôle <xref:System.Windows.Automation.RangeValuePattern> est utilisé pour prendre en charge les contrôles auxquels vous pouvez affecter une valeur comprise dans une plage.</span><span class="sxs-lookup"><span data-stu-id="5ec11-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="5ec11-108">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5ec11-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5ec11-109">Conventions et recommandations en matière d'implémentation</span><span class="sxs-lookup"><span data-stu-id="5ec11-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5ec11-110">Quand vous implémentez le modèle de contrôle RangeValue, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ec11-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5ec11-111">Les contrôles autorisent le réétalonnage de leurs propriétés prises en charge en fonction des paramètres régionaux ou des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5ec11-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="5ec11-112">Par exemple, vous pouvez définir un contrôle de thermomètre pour afficher la température en degrés Fahrenheit ou Celsius.</span><span class="sxs-lookup"><span data-stu-id="5ec11-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="5ec11-113">Les contrôles qui ont des valeurs de plage ambiguës, telles que les barres de progression ou les curseurs, doivent normaliser ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="5ec11-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="5ec11-114">![Barre de progression. ](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="5ec11-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="5ec11-115">Exemple d’une barre de progression où la valeur est de type entier, et où les valeurs de propriété minimale et maximale sont normalisées à 0 et 100, respectivement</span><span class="sxs-lookup"><span data-stu-id="5ec11-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="5ec11-116">Membres obligatoires pour IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="5ec11-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="5ec11-117">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="5ec11-117">Required member</span></span>|<span data-ttu-id="5ec11-118">Type de membre</span><span class="sxs-lookup"><span data-stu-id="5ec11-118">Member type</span></span>|<span data-ttu-id="5ec11-119">Notes</span><span class="sxs-lookup"><span data-stu-id="5ec11-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="5ec11-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="5ec11-120">Property</span></span>|<span data-ttu-id="5ec11-121">None</span><span class="sxs-lookup"><span data-stu-id="5ec11-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="5ec11-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="5ec11-122">Property</span></span>|<span data-ttu-id="5ec11-123">None</span><span class="sxs-lookup"><span data-stu-id="5ec11-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="5ec11-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="5ec11-124">Property</span></span>|<span data-ttu-id="5ec11-125">None</span><span class="sxs-lookup"><span data-stu-id="5ec11-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="5ec11-126">Propriété</span><span class="sxs-lookup"><span data-stu-id="5ec11-126">Property</span></span>|<span data-ttu-id="5ec11-127">None</span><span class="sxs-lookup"><span data-stu-id="5ec11-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="5ec11-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="5ec11-128">Property</span></span>|<span data-ttu-id="5ec11-129">None</span><span class="sxs-lookup"><span data-stu-id="5ec11-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="5ec11-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="5ec11-130">Property</span></span>|<span data-ttu-id="5ec11-131">None</span><span class="sxs-lookup"><span data-stu-id="5ec11-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="5ec11-132">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5ec11-132">Methods</span></span>|<span data-ttu-id="5ec11-133">None</span><span class="sxs-lookup"><span data-stu-id="5ec11-133">None</span></span>|  
  
 <span data-ttu-id="5ec11-134">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="5ec11-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5ec11-135">Exceptions</span><span class="sxs-lookup"><span data-stu-id="5ec11-135">Exceptions</span></span>  
 <span data-ttu-id="5ec11-136">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="5ec11-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5ec11-137">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="5ec11-137">Exception type</span></span>|<span data-ttu-id="5ec11-138">Condition</span><span class="sxs-lookup"><span data-stu-id="5ec11-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="5ec11-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> est appelé avec une valeur supérieure à <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> , ou inférieure à <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="5ec11-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ec11-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ec11-140">See also</span></span>

- [<span data-ttu-id="5ec11-141">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="5ec11-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5ec11-142">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="5ec11-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5ec11-143">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="5ec11-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5ec11-144">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="5ec11-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="5ec11-145">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="5ec11-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
