---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139691"
---
# <a name="behaviors"></a><span data-ttu-id="d6d53-101">comportements de \<</span><span class="sxs-lookup"><span data-stu-id="d6d53-101">\<behaviors></span></span>
<span data-ttu-id="d6d53-102">Cet élément définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="d6d53-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="d6d53-103">Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services.</span><span class="sxs-lookup"><span data-stu-id="d6d53-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="d6d53-104">Chaque élément de comportement est identifié par son attribut `name` unique.</span><span class="sxs-lookup"><span data-stu-id="d6d53-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="d6d53-105">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="d6d53-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d6d53-106">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d6d53-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="d6d53-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d6d53-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d6d53-108">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d6d53-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d6d53-109">&nbsp;&nbsp;&nbsp;&nbsp;des **comportements**\<</span><span class="sxs-lookup"><span data-stu-id="d6d53-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d53-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6d53-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6d53-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d6d53-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6d53-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d6d53-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6d53-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d6d53-113">Attributes</span></span>  
 <span data-ttu-id="d6d53-114">aucune.</span><span class="sxs-lookup"><span data-stu-id="d6d53-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6d53-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d6d53-115">Child Elements</span></span>  
  
|<span data-ttu-id="d6d53-116">Élément</span><span class="sxs-lookup"><span data-stu-id="d6d53-116">Element</span></span>|<span data-ttu-id="d6d53-117">Description</span><span class="sxs-lookup"><span data-stu-id="d6d53-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6d53-118">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d6d53-118">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="d6d53-119">Cette section de configuration représente tous les comportements définis pour un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="d6d53-119">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="d6d53-120">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d6d53-120">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="d6d53-121">Cette section de configuration représente tous les comportements définis pour un service spécifique.</span><span class="sxs-lookup"><span data-stu-id="d6d53-121">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6d53-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d6d53-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d6d53-123">Élément</span><span class="sxs-lookup"><span data-stu-id="d6d53-123">Element</span></span>|<span data-ttu-id="d6d53-124">Description</span><span class="sxs-lookup"><span data-stu-id="d6d53-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6d53-125">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d6d53-125">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="d6d53-126">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d6d53-126">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6d53-127">Notes</span><span class="sxs-lookup"><span data-stu-id="d6d53-127">Remarks</span></span>  
 <span data-ttu-id="d6d53-128">Vous pouvez utiliser l’élément `<remove>` pour supprimer un comportement particulier de la collection.</span><span class="sxs-lookup"><span data-stu-id="d6d53-128">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="d6d53-129">Pour cela, fournissez le nom du comportement à supprimer dans l'attribut `name` de l'élément `<remove>`.</span><span class="sxs-lookup"><span data-stu-id="d6d53-129">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="d6d53-130">Vous pouvez également utiliser l’élément `<clear>` pour vous assurer qu’une collection de comportements est vide au démarrage en supprimant tout le contenu de la collection.</span><span class="sxs-lookup"><span data-stu-id="d6d53-130">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d53-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6d53-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="d6d53-132">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="d6d53-132">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="d6d53-133">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="d6d53-133">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="d6d53-134">Spécification du comportement du client au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="d6d53-134">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="d6d53-135">Spécification du comportement du service au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="d6d53-135">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="d6d53-136">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="d6d53-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
