---
title: <behavior> de <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: d191b968e1c3fd1db0837ba7e03f210a1b00062d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201497"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="858d7-102">\<behavior> de \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="858d7-102">\<behavior> of \<endpointBehaviors></span></span>

<span data-ttu-id="858d7-103">L’élément `behavior` contient une collection de paramètres concernant le comportement d’un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="858d7-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="858d7-104">Chaque comportement est indexé en fonction de son `name`.</span><span class="sxs-lookup"><span data-stu-id="858d7-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="858d7-105">Les points de terminaison peuvent être liés à chaque comportement à travers ce nom.</span><span class="sxs-lookup"><span data-stu-id="858d7-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="858d7-106">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="858d7-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="858d7-107">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="858d7-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="858d7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="858d7-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="858d7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="858d7-109">Attributes and Elements</span></span>  

 <span data-ttu-id="858d7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="858d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="858d7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="858d7-111">Attributes</span></span>  
  
|<span data-ttu-id="858d7-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="858d7-112">Attribute</span></span>|<span data-ttu-id="858d7-113">Description</span><span class="sxs-lookup"><span data-stu-id="858d7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="858d7-114">name</span><span class="sxs-lookup"><span data-stu-id="858d7-114">name</span></span>|<span data-ttu-id="858d7-115">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="858d7-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="858d7-116">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="858d7-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="858d7-117">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="858d7-117">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="858d7-118">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="858d7-118">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="858d7-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="858d7-119">Child Elements</span></span>  
  
|<span data-ttu-id="858d7-120">Élément</span><span class="sxs-lookup"><span data-stu-id="858d7-120">Element</span></span>|<span data-ttu-id="858d7-121">Description</span><span class="sxs-lookup"><span data-stu-id="858d7-121">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="858d7-122">Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="858d7-122">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="858d7-123">Spécifie le débogage de service pour un objet de rappel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="858d7-123">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="858d7-124">Spécifie le délai d'attente pour le rappel du client.</span><span class="sxs-lookup"><span data-stu-id="858d7-124">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="858d7-125">Spécifie l'itinéraire qu'un message doit suivre.</span><span class="sxs-lookup"><span data-stu-id="858d7-125">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="858d7-126">Contient les données de configuration pour DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="858d7-126">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="858d7-127">Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="858d7-127">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="858d7-128">Active le comportement de point de terminaison qui permet de consommer le service à partir de pages Web ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="858d7-128">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="858d7-129">Le comportement doit être utilisé uniquement avec la \<webHttpBinding> liaison standard ou l' \<webMessageEncoding> élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="858d7-129">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="858d7-130">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="858d7-130">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="858d7-131">Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.</span><span class="sxs-lookup"><span data-stu-id="858d7-131">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="858d7-132">Spécifie le comportement au moment de l'exécution pour la réception de messages dans une application de service ou cliente.</span><span class="sxs-lookup"><span data-stu-id="858d7-132">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="858d7-133">Il n'a aucun attribut ou élément enfant.</span><span class="sxs-lookup"><span data-stu-id="858d7-133">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="858d7-134">Spécifie si le traitement par lots de la transaction est pris en charge pour les opérations de réception.</span><span class="sxs-lookup"><span data-stu-id="858d7-134">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="858d7-135">Spécifie le WebHttpBehavior d'un point de terminaison via la configuration.</span><span class="sxs-lookup"><span data-stu-id="858d7-135">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="858d7-136">Ce comportement, lorsqu’il est utilisé conjointement avec la \<webHttpBinding> liaison standard, active le modèle de programmation Web pour un service WCF.</span><span class="sxs-lookup"><span data-stu-id="858d7-136">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="858d7-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="858d7-137">Parent Elements</span></span>  
  
|<span data-ttu-id="858d7-138">Élément</span><span class="sxs-lookup"><span data-stu-id="858d7-138">Element</span></span>|<span data-ttu-id="858d7-139">Description</span><span class="sxs-lookup"><span data-stu-id="858d7-139">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="858d7-140">Collection d’éléments de comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="858d7-140">A collection of endpoint behavior elements.</span></span>|
