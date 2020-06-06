---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855397"
---
# \<discoveryEndpoint>

<span data-ttu-id="330a6-101">Cet élément de configuration définit un point de terminaison standard avec un contrat de découverte fixe.</span><span class="sxs-lookup"><span data-stu-id="330a6-101">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="330a6-102">Lorsqu'il est ajouté à la configuration du service, il spécifie où écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="330a6-102">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="330a6-103">Lorsqu'il est ajouté à la configuration client, il spécifie où envoyer les requêtes de découverte.</span><span class="sxs-lookup"><span data-stu-id="330a6-103">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="330a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="330a6-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="330a6-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="330a6-105">Attributes and elements</span></span>

<span data-ttu-id="330a6-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="330a6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="330a6-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="330a6-107">Attributes</span></span>

| <span data-ttu-id="330a6-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="330a6-108">Attribute</span></span>        | <span data-ttu-id="330a6-109">Description</span><span class="sxs-lookup"><span data-stu-id="330a6-109">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="330a6-110">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="330a6-110">discoveryMode</span></span>    | <span data-ttu-id="330a6-111">Chaîne qui spécifie le mode de protocole de découverte.</span><span class="sxs-lookup"><span data-stu-id="330a6-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="330a6-112">Les valeurs valides sont « adhoc » et « Managed ».</span><span class="sxs-lookup"><span data-stu-id="330a6-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="330a6-113">En mode managé, le protocole repose sur un proxy de découverte, qui fait office de référentiel des services détectables.</span><span class="sxs-lookup"><span data-stu-id="330a6-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="330a6-114">Le mode ad hoc nécessite que le protocole utilise le mécanisme de multidiffusion UDP pour rechercher les services disponibles.</span><span class="sxs-lookup"><span data-stu-id="330a6-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="330a6-115">Pour plus d’informations sur la propriété, consultez <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="330a6-115">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="330a6-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="330a6-116">discoveryVersion</span></span> | <span data-ttu-id="330a6-117">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="330a6-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="330a6-118">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="330a6-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="330a6-119">Cette valeur est de type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="330a6-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="330a6-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="330a6-120">maxResponseDelay</span></span> | <span data-ttu-id="330a6-121">Valeur Timespan qui indique la valeur maximale du délai d'attente du protocole de découverte avant l'envoi de certains messages, tels que ceux de type Probe Match ou Resolve Match.</span><span class="sxs-lookup"><span data-stu-id="330a6-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="330a6-122">Si tous les messages ProbeMatches sont envoyés en même temps, une tempête de réseau peut en résulter.</span><span class="sxs-lookup"><span data-stu-id="330a6-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="330a6-123">Pour empêcher cet effet, les messages ProbeMatches sont envoyés avec un délai aléatoire entre chaque message ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="330a6-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="330a6-124">Le délai aléatoire est compris entre 0 et la valeur définie par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="330a6-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="330a6-125">Si l'attribut a la valeur 0, les messages ProbeMatches sont envoyés dans une boucle serrée sans délai.</span><span class="sxs-lookup"><span data-stu-id="330a6-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="330a6-126">Sinon, les messages ProbeMatches sont envoyés avec un délai aléatoire de sorte que la durée totale nécessaire à l'envoi de tous les messages ProbeMatches ne dépasse pas le maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="330a6-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="330a6-127">Cette valeur est uniquement pertinente pour les services, elle n'est pas utilisée par les clients.</span><span class="sxs-lookup"><span data-stu-id="330a6-127">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="330a6-128">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="330a6-128">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="330a6-129">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="330a6-129">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="330a6-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="330a6-130">Child elements</span></span>

<span data-ttu-id="330a6-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="330a6-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="330a6-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="330a6-132">Parent elements</span></span>

| <span data-ttu-id="330a6-133">Élément</span><span class="sxs-lookup"><span data-stu-id="330a6-133">Element</span></span> | <span data-ttu-id="330a6-134">Description</span><span class="sxs-lookup"><span data-stu-id="330a6-134">Description</span></span> |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | <span data-ttu-id="330a6-135">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="330a6-135">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="330a6-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="330a6-136">Example</span></span>

<span data-ttu-id="330a6-137">L'exemple suivant montre un service qui écoute des messages de découverte sur un transport de multidiffusion Peernet.</span><span class="sxs-lookup"><span data-stu-id="330a6-137">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="330a6-138">L'exemple spécifie de manière explicite la version WS-Discovery Avril 2005.</span><span class="sxs-lookup"><span data-stu-id="330a6-138">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="330a6-139">La configuration du point de terminaison standard est définie par service et ne peut pas être partagée entre les services.</span><span class="sxs-lookup"><span data-stu-id="330a6-139">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="330a6-140">Si un autre service souhaite avoir le même point de terminaison de découverte, la même configuration doit être ajoutée à la section de ce service.</span><span class="sxs-lookup"><span data-stu-id="330a6-140">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="330a6-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="330a6-141">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
