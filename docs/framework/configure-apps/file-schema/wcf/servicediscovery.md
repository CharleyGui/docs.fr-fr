---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936275"
---
# <a name="servicediscovery"></a><span data-ttu-id="692d7-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="692d7-101">\<serviceDiscovery></span></span>
<span data-ttu-id="692d7-102">Spécifie la fonctionnalité de découverte des points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="692d7-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="692d7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="692d7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="692d7-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="692d7-104">\<behaviors></span></span>  
<span data-ttu-id="692d7-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="692d7-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="692d7-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="692d7-106">\<behavior></span></span>  
<span data-ttu-id="692d7-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="692d7-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="692d7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="692d7-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="692d7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="692d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="692d7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="692d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="692d7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="692d7-111">Attributes</span></span>  
 <span data-ttu-id="692d7-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="692d7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="692d7-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="692d7-113">Child Elements</span></span>  
  
|<span data-ttu-id="692d7-114">Élément</span><span class="sxs-lookup"><span data-stu-id="692d7-114">Element</span></span>|<span data-ttu-id="692d7-115">Description</span><span class="sxs-lookup"><span data-stu-id="692d7-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="692d7-116">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="692d7-116">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="692d7-117">Collection de points de terminaison d’annonce.</span><span class="sxs-lookup"><span data-stu-id="692d7-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="692d7-118">Cette section permet de spécifier les points de terminaison à utiliser pour l'envoi de messages d'annonce.</span><span class="sxs-lookup"><span data-stu-id="692d7-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="692d7-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="692d7-119">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="692d7-120">Collection de points de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="692d7-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="692d7-121">Cette section permet de spécifier les points de terminaison sur lesquels écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="692d7-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="692d7-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="692d7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="692d7-123">Élément</span><span class="sxs-lookup"><span data-stu-id="692d7-123">Element</span></span>|<span data-ttu-id="692d7-124">Description</span><span class="sxs-lookup"><span data-stu-id="692d7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="692d7-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="692d7-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="692d7-126">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="692d7-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="692d7-127">Notes</span><span class="sxs-lookup"><span data-stu-id="692d7-127">Remarks</span></span>  
 <span data-ttu-id="692d7-128">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration rend tous les points de terminaison de ce service détectables.</span><span class="sxs-lookup"><span data-stu-id="692d7-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="692d7-129">Vous pouvez configurer davantage les fonctionnalités de découverte de tels points de terminaison à [ \<](discoveryendpoint.md) l’aide des éléments enfants DiscoveryEndpoint > ou [ \<announcementEndpoint >](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="692d7-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="692d7-130">Utilisez la [ \<section announcementEndpoint >](announcementendpoint.md) pour configurer les annonces en spécifiant la configuration de point de terminaison à utiliser pour envoyer les annonces de service (Online/Hello et offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="692d7-130">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="692d7-131">Utilisez la [ \<section DiscoveryEndpoint >](discoveryendpoint.md) pour spécifier manuellement le point de terminaison sur lequel écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="692d7-131">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="692d7-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="692d7-132">Example</span></span>  
 <span data-ttu-id="692d7-133">L'exemple de configuration suivant spécifie que CalculatorService doit être détectable et indique éventuellement le point de terminaison d'annonce à utiliser.</span><span class="sxs-lookup"><span data-stu-id="692d7-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="692d7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="692d7-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
