---
title: <behavior> de <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139732"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="0107a-102">\<behavior> de \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0107a-102">\<behavior> of \<serviceBehaviors></span></span>
<span data-ttu-id="0107a-103">L'élément `behavior` contient une collection de paramètres concernant le comportement d'un service.</span><span class="sxs-lookup"><span data-stu-id="0107a-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="0107a-104">Chaque comportement est indexé en fonction de son `name`.</span><span class="sxs-lookup"><span data-stu-id="0107a-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="0107a-105">Les services peuvent être liés à chaque comportement via ce nom à l’aide `behaviorConfiguration` de l’attribut de l' [\<endpoint>](endpoint-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="0107a-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="0107a-106">Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="0107a-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="0107a-107">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="0107a-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0107a-108">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0107a-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0107a-109">Les éléments de comportement spécifiques aux activités de flux de travail Windows, tels que l' [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) élément, sont documentés dans la page [ \<behavior> de \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="0107a-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="0107a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0107a-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0107a-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0107a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0107a-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0107a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0107a-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="0107a-113">Attributes</span></span>  
  
|<span data-ttu-id="0107a-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="0107a-114">Attribute</span></span>|<span data-ttu-id="0107a-115">Description</span><span class="sxs-lookup"><span data-stu-id="0107a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0107a-116">name</span><span class="sxs-lookup"><span data-stu-id="0107a-116">name</span></span>|<span data-ttu-id="0107a-117">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="0107a-117">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="0107a-118">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="0107a-118">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="0107a-119">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="0107a-119">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0107a-120">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0107a-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0107a-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0107a-121">Child Elements</span></span>  
  
|<span data-ttu-id="0107a-122">Élément</span><span class="sxs-lookup"><span data-stu-id="0107a-122">Element</span></span>|<span data-ttu-id="0107a-123">Description</span><span class="sxs-lookup"><span data-stu-id="0107a-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="0107a-124">Contient les données de configuration pour DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="0107a-124">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="0107a-125">Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="0107a-125">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="0107a-126">Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="0107a-126">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="0107a-127">Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un expéditeur.</span><span class="sxs-lookup"><span data-stu-id="0107a-127">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="0107a-128">Spécifie les paramètres qui autorisent l'accès aux opérations de service.</span><span class="sxs-lookup"><span data-stu-id="0107a-128">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="0107a-129">Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="0107a-129">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="0107a-130">Spécifie les fonctionnalités de débogage et d’informations d’aide pour un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0107a-130">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="0107a-131">Spécifie la fonctionnalité de découverte des points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="0107a-131">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="0107a-132">Spécifie la publication de métadonnées de service et des informations associées.</span><span class="sxs-lookup"><span data-stu-id="0107a-132">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="0107a-133">Spécifie des paramètres qui activent l'audit d'événements de sécurité pendant des opérations de service.</span><span class="sxs-lookup"><span data-stu-id="0107a-133">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="0107a-134">Spécifie le mécanisme de limitation d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="0107a-134">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="0107a-135">Spécifie le délai d'attente pour un service.</span><span class="sxs-lookup"><span data-stu-id="0107a-135">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="0107a-136">Spécifie les paramètres d’une instance de WorkflowRuntime pour l’hébergement des services WCF basés sur le Workflow.</span><span class="sxs-lookup"><span data-stu-id="0107a-136">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="0107a-137">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="0107a-137">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0107a-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0107a-138">Parent Elements</span></span>  
  
|<span data-ttu-id="0107a-139">Élément</span><span class="sxs-lookup"><span data-stu-id="0107a-139">Element</span></span>|<span data-ttu-id="0107a-140">Description</span><span class="sxs-lookup"><span data-stu-id="0107a-140">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="0107a-141">Collection d’éléments de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="0107a-141">A collection of service behavior elements.</span></span>|
