---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399650"
---
# <a name="servicediscovery"></a><span data-ttu-id="af2fa-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="af2fa-101">\<serviceDiscovery></span></span>
<span data-ttu-id="af2fa-102">Spécifie la fonctionnalité de découverte des points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="af2fa-102">Specifies the discoverability of service endpoints.</span></span>  
  
<span data-ttu-id="af2fa-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="af2fa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="af2fa-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="af2fa-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="af2fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="af2fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="af2fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="af2fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="af2fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="af2fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="af2fa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="af2fa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2fa-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af2fa-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af2fa-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="af2fa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="af2fa-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="af2fa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af2fa-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="af2fa-112">Attributes</span></span>  
 <span data-ttu-id="af2fa-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="af2fa-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="af2fa-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="af2fa-114">Child Elements</span></span>  
  
|<span data-ttu-id="af2fa-115">Élément</span><span class="sxs-lookup"><span data-stu-id="af2fa-115">Element</span></span>|<span data-ttu-id="af2fa-116">Description</span><span class="sxs-lookup"><span data-stu-id="af2fa-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af2fa-117">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="af2fa-117">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="af2fa-118">Collection de points de terminaison d’annonce.</span><span class="sxs-lookup"><span data-stu-id="af2fa-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="af2fa-119">Cette section permet de spécifier les points de terminaison à utiliser pour l'envoi de messages d'annonce.</span><span class="sxs-lookup"><span data-stu-id="af2fa-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="af2fa-120">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="af2fa-120">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="af2fa-121">Collection de points de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="af2fa-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="af2fa-122">Cette section permet de spécifier les points de terminaison sur lesquels écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="af2fa-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af2fa-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="af2fa-123">Parent Elements</span></span>  
  
|<span data-ttu-id="af2fa-124">Élément</span><span class="sxs-lookup"><span data-stu-id="af2fa-124">Element</span></span>|<span data-ttu-id="af2fa-125">Description</span><span class="sxs-lookup"><span data-stu-id="af2fa-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af2fa-126">\<behavior></span><span class="sxs-lookup"><span data-stu-id="af2fa-126">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="af2fa-127">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="af2fa-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af2fa-128">Notes</span><span class="sxs-lookup"><span data-stu-id="af2fa-128">Remarks</span></span>  
 <span data-ttu-id="af2fa-129">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration rend tous les points de terminaison de ce service détectables.</span><span class="sxs-lookup"><span data-stu-id="af2fa-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="af2fa-130">Vous pouvez configurer davantage les fonctionnalités de découverte de tels points de terminaison à [ \<](discoveryendpoint.md) l’aide des éléments enfants DiscoveryEndpoint > ou [ \<announcementEndpoint >](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="af2fa-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="af2fa-131">Utilisez la [ \<section announcementEndpoint >](announcementendpoint.md) pour configurer les annonces en spécifiant la configuration de point de terminaison à utiliser pour envoyer les annonces de service (Online/Hello et offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="af2fa-131">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="af2fa-132">Utilisez la [ \<section DiscoveryEndpoint >](discoveryendpoint.md) pour spécifier manuellement le point de terminaison sur lequel écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="af2fa-132">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af2fa-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="af2fa-133">Example</span></span>  
 <span data-ttu-id="af2fa-134">L'exemple de configuration suivant spécifie que CalculatorService doit être détectable et indique éventuellement le point de terminaison d'annonce à utiliser.</span><span class="sxs-lookup"><span data-stu-id="af2fa-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af2fa-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af2fa-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
