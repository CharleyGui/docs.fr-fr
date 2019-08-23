---
title: Implémentation du modèle de contrôle RangeValue d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 70ee5009e2763348f7c69613a1776e02e82e0391
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932121"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="53ffa-102">Implémentation du modèle de contrôle RangeValue d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="53ffa-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="53ffa-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="53ffa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="53ffa-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="53ffa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="53ffa-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IRangeValueProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="53ffa-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="53ffa-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="53ffa-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="53ffa-107">Le modèle de contrôle <xref:System.Windows.Automation.RangeValuePattern> est utilisé pour prendre en charge les contrôles auxquels vous pouvez affecter une valeur comprise dans une plage.</span><span class="sxs-lookup"><span data-stu-id="53ffa-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="53ffa-108">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="53ffa-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="53ffa-109">Conventions et recommandations en matière d'implémentation</span><span class="sxs-lookup"><span data-stu-id="53ffa-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="53ffa-110">Quand vous implémentez le modèle de contrôle RangeValue, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="53ffa-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="53ffa-111">Les contrôles autorisent le réétalonnage de leurs propriétés prises en charge en fonction des paramètres régionaux ou des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="53ffa-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="53ffa-112">Par exemple, vous pouvez définir un contrôle de thermomètre pour afficher la température en degrés Fahrenheit ou Celsius.</span><span class="sxs-lookup"><span data-stu-id="53ffa-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="53ffa-113">Les contrôles qui ont des valeurs de plage ambiguës, telles que les barres de progression ou les curseurs, doivent normaliser ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="53ffa-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="53ffa-114">![Barre de progression.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="53ffa-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="53ffa-115">Exemple d’une barre de progression où la valeur est de type entier, et où les valeurs de propriété minimale et maximale sont normalisées à 0 et 100, respectivement</span><span class="sxs-lookup"><span data-stu-id="53ffa-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="53ffa-116">Membres obligatoires pour IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="53ffa-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="53ffa-117">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="53ffa-117">Required member</span></span>|<span data-ttu-id="53ffa-118">Type de membre</span><span class="sxs-lookup"><span data-stu-id="53ffa-118">Member type</span></span>|<span data-ttu-id="53ffa-119">Notes</span><span class="sxs-lookup"><span data-stu-id="53ffa-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="53ffa-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="53ffa-120">Property</span></span>|<span data-ttu-id="53ffa-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="53ffa-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="53ffa-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="53ffa-122">Property</span></span>|<span data-ttu-id="53ffa-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="53ffa-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="53ffa-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="53ffa-124">Property</span></span>|<span data-ttu-id="53ffa-125">Aucun</span><span class="sxs-lookup"><span data-stu-id="53ffa-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="53ffa-126">Propriété</span><span class="sxs-lookup"><span data-stu-id="53ffa-126">Property</span></span>|<span data-ttu-id="53ffa-127">Aucun</span><span class="sxs-lookup"><span data-stu-id="53ffa-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="53ffa-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="53ffa-128">Property</span></span>|<span data-ttu-id="53ffa-129">Aucun</span><span class="sxs-lookup"><span data-stu-id="53ffa-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="53ffa-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="53ffa-130">Property</span></span>|<span data-ttu-id="53ffa-131">Aucun</span><span class="sxs-lookup"><span data-stu-id="53ffa-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="53ffa-132">Méthodes</span><span class="sxs-lookup"><span data-stu-id="53ffa-132">Methods</span></span>|<span data-ttu-id="53ffa-133">Aucun</span><span class="sxs-lookup"><span data-stu-id="53ffa-133">None</span></span>|  
  
 <span data-ttu-id="53ffa-134">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="53ffa-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="53ffa-135">Exceptions</span><span class="sxs-lookup"><span data-stu-id="53ffa-135">Exceptions</span></span>  
 <span data-ttu-id="53ffa-136">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="53ffa-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="53ffa-137">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="53ffa-137">Exception type</span></span>|<span data-ttu-id="53ffa-138">Condition</span><span class="sxs-lookup"><span data-stu-id="53ffa-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="53ffa-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> est appelé avec une valeur supérieure à <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> , ou inférieure à <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="53ffa-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53ffa-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53ffa-140">See also</span></span>

- [<span data-ttu-id="53ffa-141">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="53ffa-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="53ffa-142">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="53ffa-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="53ffa-143">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="53ffa-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="53ffa-144">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="53ffa-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="53ffa-145">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="53ffa-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
