---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 914fa04c9aff0c287913104cd9bedc570c473330
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201484"
---
# \<behaviors>

<span data-ttu-id="48c87-101">Cet élément définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="48c87-101">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="48c87-102">Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services.</span><span class="sxs-lookup"><span data-stu-id="48c87-102">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="48c87-103">Chaque élément de comportement est identifié par son attribut `name` unique.</span><span class="sxs-lookup"><span data-stu-id="48c87-103">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="48c87-104">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="48c87-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="48c87-105">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="48c87-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="48c87-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48c87-106">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48c87-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="48c87-107">Attributes and Elements</span></span>  

 <span data-ttu-id="48c87-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="48c87-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48c87-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="48c87-109">Attributes</span></span>  

 <span data-ttu-id="48c87-110">None</span><span class="sxs-lookup"><span data-stu-id="48c87-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48c87-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="48c87-111">Child Elements</span></span>  
  
|<span data-ttu-id="48c87-112">Élément</span><span class="sxs-lookup"><span data-stu-id="48c87-112">Element</span></span>|<span data-ttu-id="48c87-113">Description</span><span class="sxs-lookup"><span data-stu-id="48c87-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="48c87-114">Cette section de configuration représente tous les comportements définis pour un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="48c87-114">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="48c87-115">Cette section de configuration représente tous les comportements définis pour un service spécifique.</span><span class="sxs-lookup"><span data-stu-id="48c87-115">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48c87-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="48c87-116">Parent Elements</span></span>  
  
|<span data-ttu-id="48c87-117">Élément</span><span class="sxs-lookup"><span data-stu-id="48c87-117">Element</span></span>|<span data-ttu-id="48c87-118">Description</span><span class="sxs-lookup"><span data-stu-id="48c87-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="48c87-119">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="48c87-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48c87-120">Notes</span><span class="sxs-lookup"><span data-stu-id="48c87-120">Remarks</span></span>  

 <span data-ttu-id="48c87-121">Vous pouvez utiliser l’élément `<remove>` pour supprimer un comportement particulier de la collection.</span><span class="sxs-lookup"><span data-stu-id="48c87-121">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="48c87-122">Pour cela, fournissez le nom du comportement à supprimer dans l'attribut `name` de l'élément `<remove>`.</span><span class="sxs-lookup"><span data-stu-id="48c87-122">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="48c87-123">Vous pouvez également utiliser l’élément `<clear>` pour vous assurer qu’une collection de comportements est vide au démarrage en supprimant tout le contenu de la collection.</span><span class="sxs-lookup"><span data-stu-id="48c87-123">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c87-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48c87-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="48c87-125">Configuration et extension de l'exécution à l'aide de comportements</span><span class="sxs-lookup"><span data-stu-id="48c87-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="48c87-126">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="48c87-126">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="48c87-127">Spécification du comportement du client au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="48c87-127">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="48c87-128">Spécification du comportement du service au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="48c87-128">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="48c87-129">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="48c87-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
