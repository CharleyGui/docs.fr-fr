---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 8fcb5ac0c552d1ac2e849c95a5c0757d0c142f3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926393"
---
# <a name="behaviors"></a><span data-ttu-id="749eb-101">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="749eb-101">\<behaviors></span></span>
<span data-ttu-id="749eb-102">Cet élément définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="749eb-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="749eb-103">Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services.</span><span class="sxs-lookup"><span data-stu-id="749eb-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="749eb-104">Chaque élément de comportement est identifié par son attribut `name` unique.</span><span class="sxs-lookup"><span data-stu-id="749eb-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="749eb-105">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="749eb-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="749eb-106">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="749eb-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="749eb-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="749eb-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="749eb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="749eb-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="749eb-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="749eb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="749eb-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="749eb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="749eb-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="749eb-111">Attributes</span></span>  
 <span data-ttu-id="749eb-112">Aucun</span><span class="sxs-lookup"><span data-stu-id="749eb-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="749eb-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="749eb-113">Child Elements</span></span>  
  
|<span data-ttu-id="749eb-114">Élément</span><span class="sxs-lookup"><span data-stu-id="749eb-114">Element</span></span>|<span data-ttu-id="749eb-115">Description</span><span class="sxs-lookup"><span data-stu-id="749eb-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="749eb-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="749eb-116">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="749eb-117">Cette section de configuration représente tous les comportements définis pour un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="749eb-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="749eb-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="749eb-118">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="749eb-119">Cette section de configuration représente tous les comportements définis pour un service spécifique.</span><span class="sxs-lookup"><span data-stu-id="749eb-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="749eb-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="749eb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="749eb-121">Élément</span><span class="sxs-lookup"><span data-stu-id="749eb-121">Element</span></span>|<span data-ttu-id="749eb-122">Description</span><span class="sxs-lookup"><span data-stu-id="749eb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="749eb-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="749eb-123">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="749eb-124">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="749eb-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="749eb-125">Notes</span><span class="sxs-lookup"><span data-stu-id="749eb-125">Remarks</span></span>  
 <span data-ttu-id="749eb-126">Vous pouvez utiliser l’élément `<remove>` pour supprimer un comportement particulier de la collection.</span><span class="sxs-lookup"><span data-stu-id="749eb-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="749eb-127">Pour cela, fournissez le nom du comportement à supprimer dans l'attribut `name` de l'élément `<remove>`.</span><span class="sxs-lookup"><span data-stu-id="749eb-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="749eb-128">Vous pouvez également utiliser l’élément `<clear>` pour vous assurer qu’une collection de comportements est vide au démarrage en supprimant tout le contenu de la collection.</span><span class="sxs-lookup"><span data-stu-id="749eb-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="749eb-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="749eb-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="749eb-130">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="749eb-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="749eb-131">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="749eb-131">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="749eb-132">Spécification du comportement du client au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="749eb-132">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="749eb-133">Spécification du comportement du service au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="749eb-133">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="749eb-134">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="749eb-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
