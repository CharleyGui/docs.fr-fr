---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: e6e567e8a657b4c1683ae4abfb14f96a0f272e4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934592"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="343bb-101">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="343bb-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="343bb-102">Cet élément de configuration définit un point de terminaison standard préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="343bb-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="343bb-103">Ce point de terminaison a un contrat fixe et prend en charge deux versions de protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="343bb-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="343bb-104">De plus, il a une liaison UDP fixe et une valeur d’adresse par défaut indiquée dans les spécifications WS-Discovery (WS-Discovery Avril 2005 ou WS-Discovery V1.1).</span><span class="sxs-lookup"><span data-stu-id="343bb-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="343bb-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="343bb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="343bb-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="343bb-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343bb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="343bb-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="343bb-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="343bb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="343bb-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="343bb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="343bb-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="343bb-110">Attributes</span></span>  
  
|<span data-ttu-id="343bb-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="343bb-111">Attribute</span></span>|<span data-ttu-id="343bb-112">Description</span><span class="sxs-lookup"><span data-stu-id="343bb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="343bb-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="343bb-113">discoveryMode</span></span>|<span data-ttu-id="343bb-114">Chaîne qui spécifie le mode de protocole de découverte.</span><span class="sxs-lookup"><span data-stu-id="343bb-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="343bb-115">Les valeurs valides sont «adhoc» et «Managed».</span><span class="sxs-lookup"><span data-stu-id="343bb-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="343bb-116">En mode managé, le protocole repose sur un proxy de découverte, qui fait office de référentiel des services détectables.</span><span class="sxs-lookup"><span data-stu-id="343bb-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="343bb-117">Le mode ad hoc nécessite que le protocole utilise le mécanisme de multidiffusion UDP pour rechercher les services disponibles.</span><span class="sxs-lookup"><span data-stu-id="343bb-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="343bb-118">Cette valeur est de type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="343bb-118">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="343bb-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="343bb-119">discoveryVersion</span></span>|<span data-ttu-id="343bb-120">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="343bb-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="343bb-121">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="343bb-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="343bb-122">Cette valeur est de type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="343bb-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="343bb-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="343bb-123">maxResponseDelay</span></span>|<span data-ttu-id="343bb-124">Valeur Timespan qui indique la valeur maximale du délai d'attente du protocole de découverte avant l'envoi de certains messages, tels que ceux de type Probe Match ou Resolve Match.</span><span class="sxs-lookup"><span data-stu-id="343bb-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="343bb-125">Si tous les messages ProbeMatches sont envoyés en même temps, une tempête de réseau peut en résulter.</span><span class="sxs-lookup"><span data-stu-id="343bb-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="343bb-126">Pour empêcher cet effet, les messages ProbeMatches sont envoyés avec un délai aléatoire entre chaque message ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="343bb-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="343bb-127">Le délai aléatoire est compris entre 0 et la valeur définie par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="343bb-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="343bb-128">Si l'attribut a la valeur 0, les messages ProbeMatches sont envoyés dans une boucle serrée sans délai.</span><span class="sxs-lookup"><span data-stu-id="343bb-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="343bb-129">Sinon, les messages ProbeMatches sont envoyés avec un délai aléatoire de sorte que la durée totale nécessaire à l'envoi de tous les messages ProbeMatches ne dépasse pas le maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="343bb-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="343bb-130">Cette valeur est uniquement pertinente pour les services, elle n'est pas utilisée par les clients.</span><span class="sxs-lookup"><span data-stu-id="343bb-130">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="343bb-131">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="343bb-131">multicastAddress</span></span>|<span data-ttu-id="343bb-132">URI qui spécifie une adresse de multidiffusion à utiliser pour l'envoi et la réception des messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="343bb-132">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="343bb-133">La valeur par défaut est représentée par l'adresse de multidiffusion conforme à la spécification du protocole.</span><span class="sxs-lookup"><span data-stu-id="343bb-133">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="343bb-134">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="343bb-134">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="343bb-135">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="343bb-135">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="343bb-136">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="343bb-136">Child Elements</span></span>  
  
|<span data-ttu-id="343bb-137">Élément</span><span class="sxs-lookup"><span data-stu-id="343bb-137">Element</span></span>|<span data-ttu-id="343bb-138">Description</span><span class="sxs-lookup"><span data-stu-id="343bb-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="343bb-139">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="343bb-139">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="343bb-140">Collection de paramètres qui vous permettent de configurer le transport UDP pour le point de terminaison UDP.</span><span class="sxs-lookup"><span data-stu-id="343bb-140">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="343bb-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="343bb-141">Parent Elements</span></span>  
  
|<span data-ttu-id="343bb-142">Élément</span><span class="sxs-lookup"><span data-stu-id="343bb-142">Element</span></span>|<span data-ttu-id="343bb-143">Description</span><span class="sxs-lookup"><span data-stu-id="343bb-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="343bb-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="343bb-144">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="343bb-145">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="343bb-145">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="343bb-146">Exemples</span><span class="sxs-lookup"><span data-stu-id="343bb-146">Example</span></span>  
 <span data-ttu-id="343bb-147">L'exemple suivant montre un service qui écoute des messages de découverte sur un transport de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="343bb-147">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="343bb-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="343bb-148">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
