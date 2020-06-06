---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 1729255c68c75f824b8cd8c87f106a4a9b3550f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854896"
---
# \<udpDiscoveryEndpoint>
<span data-ttu-id="cb3cb-101">Cet élément de configuration définit un point de terminaison standard préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-101">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="cb3cb-102">Ce point de terminaison a un contrat fixe et prend en charge deux versions de protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-102">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="cb3cb-103">De plus, il a une liaison UDP fixe et une valeur d’adresse par défaut indiquée dans les spécifications WS-Discovery (WS-Discovery Avril 2005 ou WS-Discovery V1.1).</span><span class="sxs-lookup"><span data-stu-id="cb3cb-103">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="cb3cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb3cb-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb3cb-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cb3cb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cb3cb-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb3cb-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="cb3cb-107">Attributes</span></span>  
  
|<span data-ttu-id="cb3cb-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="cb3cb-108">Attribute</span></span>|<span data-ttu-id="cb3cb-109">Description</span><span class="sxs-lookup"><span data-stu-id="cb3cb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb3cb-110">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="cb3cb-110">discoveryMode</span></span>|<span data-ttu-id="cb3cb-111">Chaîne qui spécifie le mode de protocole de découverte.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="cb3cb-112">Les valeurs valides sont « adhoc » et « Managed ».</span><span class="sxs-lookup"><span data-stu-id="cb3cb-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="cb3cb-113">En mode managé, le protocole repose sur un proxy de découverte, qui fait office de référentiel des services détectables.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="cb3cb-114">Le mode ad hoc nécessite que le protocole utilise le mécanisme de multidiffusion UDP pour rechercher les services disponibles.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="cb3cb-115">Cette valeur est de type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-115">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="cb3cb-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="cb3cb-116">discoveryVersion</span></span>|<span data-ttu-id="cb3cb-117">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="cb3cb-118">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="cb3cb-119">Cette valeur est de type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="cb3cb-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="cb3cb-120">maxResponseDelay</span></span>|<span data-ttu-id="cb3cb-121">Valeur Timespan qui indique la valeur maximale du délai d'attente du protocole de découverte avant l'envoi de certains messages, tels que ceux de type Probe Match ou Resolve Match.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="cb3cb-122">Si tous les messages ProbeMatches sont envoyés en même temps, une tempête de réseau peut en résulter.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="cb3cb-123">Pour empêcher cet effet, les messages ProbeMatches sont envoyés avec un délai aléatoire entre chaque message ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="cb3cb-124">Le délai aléatoire est compris entre 0 et la valeur définie par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="cb3cb-125">Si l'attribut a la valeur 0, les messages ProbeMatches sont envoyés dans une boucle serrée sans délai.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="cb3cb-126">Sinon, les messages ProbeMatches sont envoyés avec un délai aléatoire de sorte que la durée totale nécessaire à l'envoi de tous les messages ProbeMatches ne dépasse pas le maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="cb3cb-127">Cette valeur est uniquement pertinente pour les services, elle n'est pas utilisée par les clients.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-127">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="cb3cb-128">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="cb3cb-128">multicastAddress</span></span>|<span data-ttu-id="cb3cb-129">URI qui spécifie une adresse de multidiffusion à utiliser pour l'envoi et la réception des messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-129">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="cb3cb-130">La valeur par défaut est représentée par l'adresse de multidiffusion conforme à la spécification du protocole.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-130">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="cb3cb-131">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="cb3cb-132">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb3cb-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb3cb-133">Child Elements</span></span>  
  
|<span data-ttu-id="cb3cb-134">Élément</span><span class="sxs-lookup"><span data-stu-id="cb3cb-134">Element</span></span>|<span data-ttu-id="cb3cb-135">Description</span><span class="sxs-lookup"><span data-stu-id="cb3cb-135">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="cb3cb-136">Collection de paramètres qui vous permettent de configurer le transport UDP pour le point de terminaison UDP.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-136">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb3cb-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb3cb-137">Parent Elements</span></span>  
  
|<span data-ttu-id="cb3cb-138">Élément</span><span class="sxs-lookup"><span data-stu-id="cb3cb-138">Element</span></span>|<span data-ttu-id="cb3cb-139">Description</span><span class="sxs-lookup"><span data-stu-id="cb3cb-139">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="cb3cb-140">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb3cb-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb3cb-141">Example</span></span>  
 <span data-ttu-id="cb3cb-142">L'exemple suivant montre un service qui écoute des messages de découverte sur un transport de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="cb3cb-142">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb3cb-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb3cb-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
