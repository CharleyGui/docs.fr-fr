---
title: Implémentation du modèle de contrôle Transform d’UI Automation
description: Passez en revue les recommandations et les conventions pour implémenter le modèle de contrôle Transform dans UI Automation. Connaître les membres requis pour l’interface ITransformProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: fc47170a08ff08f6cd8f67996ef8fbf19c40f819
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265646"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="b0135-104">Implémentation du modèle de contrôle Transform d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="b0135-104">Implementing the UI Automation Transform Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="b0135-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="b0135-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b0135-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="b0135-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b0135-107">Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITransformProvider>, notamment les informations sur les propriétés, les méthodes et les événements.</span><span class="sxs-lookup"><span data-stu-id="b0135-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="b0135-108">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="b0135-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b0135-109">Le modèle de contrôle <xref:System.Windows.Automation.TransformPattern> permet de prendre en charge des contrôles qui peuvent être déplacés, redimensionnés ou pivotés dans un espace à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="b0135-109">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="b0135-110">Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b0135-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b0135-111">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="b0135-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="b0135-112">Quand vous implémentez le modèle de contrôle Transform, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0135-112">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b0135-113">La prise en charge pour ce modèle de contrôle ne se limite pas aux objets sur le bureau.</span><span class="sxs-lookup"><span data-stu-id="b0135-113">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="b0135-114">Ce modèle de contrôle doit également être pris en charge par les enfants d’un objet conteneur si les enfants peuvent être déplacés, redimensionnés et pivotés librement dans les limites du conteneur.</span><span class="sxs-lookup"><span data-stu-id="b0135-114">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
- <span data-ttu-id="b0135-115">Il n’est pas possible de déplacer, redimensionner ni pivoter un objet de manière à ce que son emplacement résultant à l’écran soit complètement en dehors des coordonnées de son conteneur et, par conséquent, inaccessible via le clavier et la souris (par exemple, quand une fenêtre de niveau supérieur est déplacée hors de l’écran ou qu’un objet enfant est déplacé en dehors des limites de la fenêtre d’affichage du conteneur).</span><span class="sxs-lookup"><span data-stu-id="b0135-115">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="b0135-116">Dans ce cas, l’objet est placé le plus près possible des coordonnées d’écran demandées avec les coordonnées en haut et à gauche substituées de façon à être incluses dans les limites du conteneur.</span><span class="sxs-lookup"><span data-stu-id="b0135-116">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
- <span data-ttu-id="b0135-117">Pour les systèmes à plusieurs écrans, si un objet est déplacé, redimensionné ou pivoté complètement en dehors des coordonnées d’écran du bureau combiné, l’objet est placé sur le moniteur principal, aussi près que possible des coordonnées demandées.</span><span class="sxs-lookup"><span data-stu-id="b0135-117">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
- <span data-ttu-id="b0135-118">Tous les paramètres et valeurs de propriété sont absolus et indépendants des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="b0135-118">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="b0135-119">Membres requis pour ITransformProvider</span><span class="sxs-lookup"><span data-stu-id="b0135-119">Required Members for ITransformProvider</span></span>  

 <span data-ttu-id="b0135-120">Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.ITransformProvider>.</span><span class="sxs-lookup"><span data-stu-id="b0135-120">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="b0135-121">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="b0135-121">Required members</span></span>|<span data-ttu-id="b0135-122">Type de membre</span><span class="sxs-lookup"><span data-stu-id="b0135-122">Member type</span></span>|<span data-ttu-id="b0135-123">Notes</span><span class="sxs-lookup"><span data-stu-id="b0135-123">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="b0135-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="b0135-124">Property</span></span>|<span data-ttu-id="b0135-125">None</span><span class="sxs-lookup"><span data-stu-id="b0135-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="b0135-126">Propriété</span><span class="sxs-lookup"><span data-stu-id="b0135-126">Property</span></span>|<span data-ttu-id="b0135-127">None</span><span class="sxs-lookup"><span data-stu-id="b0135-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="b0135-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="b0135-128">Property</span></span>|<span data-ttu-id="b0135-129">None</span><span class="sxs-lookup"><span data-stu-id="b0135-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="b0135-130">Méthode</span><span class="sxs-lookup"><span data-stu-id="b0135-130">Method</span></span>|<span data-ttu-id="b0135-131">None</span><span class="sxs-lookup"><span data-stu-id="b0135-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="b0135-132">Méthode</span><span class="sxs-lookup"><span data-stu-id="b0135-132">Method</span></span>|<span data-ttu-id="b0135-133">None</span><span class="sxs-lookup"><span data-stu-id="b0135-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="b0135-134">Méthode</span><span class="sxs-lookup"><span data-stu-id="b0135-134">Method</span></span>|<span data-ttu-id="b0135-135">None</span><span class="sxs-lookup"><span data-stu-id="b0135-135">None</span></span>|  
  
 <span data-ttu-id="b0135-136">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="b0135-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="b0135-137">Exceptions</span><span class="sxs-lookup"><span data-stu-id="b0135-137">Exceptions</span></span>  

 <span data-ttu-id="b0135-138">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="b0135-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b0135-139">Type d’exception</span><span class="sxs-lookup"><span data-stu-id="b0135-139">Exception Type</span></span>|<span data-ttu-id="b0135-140">Condition</span><span class="sxs-lookup"><span data-stu-id="b0135-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="b0135-141">-Si <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="b0135-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="b0135-142">-Si <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="b0135-142">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="b0135-143">-Si <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="b0135-143">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0135-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0135-144">See also</span></span>

- [<span data-ttu-id="b0135-145">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="b0135-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b0135-146">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="b0135-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b0135-147">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="b0135-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b0135-148">Vue d’ensemble de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="b0135-148">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="b0135-149">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="b0135-149">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
