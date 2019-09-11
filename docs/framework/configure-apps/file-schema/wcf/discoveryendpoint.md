---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855397"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="e3de1-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="e3de1-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="e3de1-102">Cet élément de configuration définit un point de terminaison standard avec un contrat de découverte fixe.</span><span class="sxs-lookup"><span data-stu-id="e3de1-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="e3de1-103">Lorsqu'il est ajouté à la configuration du service, il spécifie où écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="e3de1-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="e3de1-104">Lorsqu'il est ajouté à la configuration client, il spécifie où envoyer les requêtes de découverte.</span><span class="sxs-lookup"><span data-stu-id="e3de1-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="e3de1-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3de1-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3de1-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e3de1-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e3de1-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="e3de1-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="e3de1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="e3de1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3de1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3de1-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3de1-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e3de1-110">Attributes and elements</span></span>

<span data-ttu-id="e3de1-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e3de1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3de1-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3de1-112">Attributes</span></span>

| <span data-ttu-id="e3de1-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3de1-113">Attribute</span></span>        | <span data-ttu-id="e3de1-114">Description</span><span class="sxs-lookup"><span data-stu-id="e3de1-114">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="e3de1-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="e3de1-115">discoveryMode</span></span>    | <span data-ttu-id="e3de1-116">Chaîne qui spécifie le mode de protocole de découverte.</span><span class="sxs-lookup"><span data-stu-id="e3de1-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="e3de1-117">Les valeurs valides sont « adhoc » et « Managed ».</span><span class="sxs-lookup"><span data-stu-id="e3de1-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="e3de1-118">En mode managé, le protocole repose sur un proxy de découverte, qui fait office de référentiel des services détectables.</span><span class="sxs-lookup"><span data-stu-id="e3de1-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="e3de1-119">Le mode ad hoc nécessite que le protocole utilise le mécanisme de multidiffusion UDP pour rechercher les services disponibles.</span><span class="sxs-lookup"><span data-stu-id="e3de1-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="e3de1-120">Pour plus d’informations sur la propriété, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>consultez.</span><span class="sxs-lookup"><span data-stu-id="e3de1-120">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="e3de1-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="e3de1-121">discoveryVersion</span></span> | <span data-ttu-id="e3de1-122">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="e3de1-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="e3de1-123">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="e3de1-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="e3de1-124">Cette valeur est de type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="e3de1-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="e3de1-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="e3de1-125">maxResponseDelay</span></span> | <span data-ttu-id="e3de1-126">Valeur Timespan qui indique la valeur maximale du délai d'attente du protocole de découverte avant l'envoi de certains messages, tels que ceux de type Probe Match ou Resolve Match.</span><span class="sxs-lookup"><span data-stu-id="e3de1-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="e3de1-127">Si tous les messages ProbeMatches sont envoyés en même temps, une tempête de réseau peut en résulter.</span><span class="sxs-lookup"><span data-stu-id="e3de1-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="e3de1-128">Pour empêcher cet effet, les messages ProbeMatches sont envoyés avec un délai aléatoire entre chaque message ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="e3de1-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="e3de1-129">Le délai aléatoire est compris entre 0 et la valeur définie par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="e3de1-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="e3de1-130">Si l'attribut a la valeur 0, les messages ProbeMatches sont envoyés dans une boucle serrée sans délai.</span><span class="sxs-lookup"><span data-stu-id="e3de1-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="e3de1-131">Sinon, les messages ProbeMatches sont envoyés avec un délai aléatoire de sorte que la durée totale nécessaire à l'envoi de tous les messages ProbeMatches ne dépasse pas le maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="e3de1-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="e3de1-132">Cette valeur est uniquement pertinente pour les services, elle n'est pas utilisée par les clients.</span><span class="sxs-lookup"><span data-stu-id="e3de1-132">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="e3de1-133">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="e3de1-133">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e3de1-134">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="e3de1-134">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="e3de1-135">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3de1-135">Child elements</span></span>

<span data-ttu-id="e3de1-136">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e3de1-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3de1-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3de1-137">Parent elements</span></span>

| <span data-ttu-id="e3de1-138">Élément</span><span class="sxs-lookup"><span data-stu-id="e3de1-138">Element</span></span> | <span data-ttu-id="e3de1-139">Description</span><span class="sxs-lookup"><span data-stu-id="e3de1-139">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="e3de1-140">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e3de1-140">\<standardEndpoints></span></span>](standardendpoints.md) | <span data-ttu-id="e3de1-141">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="e3de1-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="e3de1-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3de1-142">Example</span></span>

<span data-ttu-id="e3de1-143">L'exemple suivant montre un service qui écoute des messages de découverte sur un transport de multidiffusion Peernet.</span><span class="sxs-lookup"><span data-stu-id="e3de1-143">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="e3de1-144">L'exemple spécifie de manière explicite la version WS-Discovery Avril 2005.</span><span class="sxs-lookup"><span data-stu-id="e3de1-144">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="e3de1-145">La configuration du point de terminaison standard est définie par service et ne peut pas être partagée entre les services.</span><span class="sxs-lookup"><span data-stu-id="e3de1-145">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="e3de1-146">Si un autre service souhaite avoir le même point de terminaison de découverte, la même configuration doit être ajoutée à la section de ce service.</span><span class="sxs-lookup"><span data-stu-id="e3de1-146">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="e3de1-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3de1-147">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
