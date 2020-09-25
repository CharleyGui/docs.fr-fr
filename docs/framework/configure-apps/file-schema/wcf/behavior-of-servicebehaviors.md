---
title: <behavior> de <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 739f95f527fd73062c8cec43efc6777efeb077f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195153"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="c2db5-102">\<behavior> de \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c2db5-102">\<behavior> of \<serviceBehaviors></span></span>

<span data-ttu-id="c2db5-103">L'élément `behavior` contient une collection de paramètres concernant le comportement d'un service.</span><span class="sxs-lookup"><span data-stu-id="c2db5-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="c2db5-104">Chaque comportement est indexé en fonction de son `name`.</span><span class="sxs-lookup"><span data-stu-id="c2db5-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="c2db5-105">Les services peuvent être liés à chaque comportement via ce nom à l’aide `behaviorConfiguration` de l’attribut de l' [\<endpoint>](endpoint-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="c2db5-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="c2db5-106">Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="c2db5-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="c2db5-107">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="c2db5-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c2db5-108">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c2db5-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2db5-109">Les éléments de comportement spécifiques aux activités de flux de travail Windows, tels que l' [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) élément, sont documentés dans la page [ \<behavior> de \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="c2db5-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="c2db5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2db5-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2db5-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c2db5-111">Attributes and Elements</span></span>  

 <span data-ttu-id="c2db5-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c2db5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2db5-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="c2db5-113">Attributes</span></span>  
  
|<span data-ttu-id="c2db5-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="c2db5-114">Attribute</span></span>|<span data-ttu-id="c2db5-115">Description</span><span class="sxs-lookup"><span data-stu-id="c2db5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2db5-116">name</span><span class="sxs-lookup"><span data-stu-id="c2db5-116">name</span></span>|<span data-ttu-id="c2db5-117">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="c2db5-117">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="c2db5-118">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="c2db5-118">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="c2db5-119">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="c2db5-119">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c2db5-120">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c2db5-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2db5-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c2db5-121">Child Elements</span></span>  
  
|<span data-ttu-id="c2db5-122">Élément</span><span class="sxs-lookup"><span data-stu-id="c2db5-122">Element</span></span>|<span data-ttu-id="c2db5-123">Description</span><span class="sxs-lookup"><span data-stu-id="c2db5-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="c2db5-124">Contient les données de configuration pour DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="c2db5-124">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="c2db5-125">Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="c2db5-125">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="c2db5-126">Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="c2db5-126">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="c2db5-127">Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un expéditeur.</span><span class="sxs-lookup"><span data-stu-id="c2db5-127">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="c2db5-128">Spécifie les paramètres qui autorisent l'accès aux opérations de service.</span><span class="sxs-lookup"><span data-stu-id="c2db5-128">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="c2db5-129">Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="c2db5-129">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="c2db5-130">Spécifie les fonctionnalités de débogage et d’informations d’aide pour un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c2db5-130">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="c2db5-131">Spécifie la fonctionnalité de découverte des points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="c2db5-131">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="c2db5-132">Spécifie la publication de métadonnées de service et des informations associées.</span><span class="sxs-lookup"><span data-stu-id="c2db5-132">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="c2db5-133">Spécifie des paramètres qui activent l'audit d'événements de sécurité pendant des opérations de service.</span><span class="sxs-lookup"><span data-stu-id="c2db5-133">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="c2db5-134">Spécifie le mécanisme de limitation d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="c2db5-134">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="c2db5-135">Spécifie le délai d'attente pour un service.</span><span class="sxs-lookup"><span data-stu-id="c2db5-135">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="c2db5-136">Spécifie les paramètres d’une instance de WorkflowRuntime pour l’hébergement des services WCF basés sur le Workflow.</span><span class="sxs-lookup"><span data-stu-id="c2db5-136">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="c2db5-137">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="c2db5-137">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2db5-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c2db5-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c2db5-139">Élément</span><span class="sxs-lookup"><span data-stu-id="c2db5-139">Element</span></span>|<span data-ttu-id="c2db5-140">Description</span><span class="sxs-lookup"><span data-stu-id="c2db5-140">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="c2db5-141">Collection d’éléments de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="c2db5-141">A collection of service behavior elements.</span></span>|
