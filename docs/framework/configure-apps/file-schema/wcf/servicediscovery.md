---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: b38496b77d80fcb66b1b48485a9eef6abfd72299
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198819"
---
# \<serviceDiscovery>

<span data-ttu-id="8e604-101">Spécifie la fonctionnalité de découverte des points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="8e604-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="8e604-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e604-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e604-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8e604-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8e604-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8e604-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e604-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="8e604-105">Attributes</span></span>  

 <span data-ttu-id="8e604-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8e604-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e604-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8e604-107">Child Elements</span></span>  
  
|<span data-ttu-id="8e604-108">Élément</span><span class="sxs-lookup"><span data-stu-id="8e604-108">Element</span></span>|<span data-ttu-id="8e604-109">Description</span><span class="sxs-lookup"><span data-stu-id="8e604-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="8e604-110">Collection de points de terminaison d’annonce.</span><span class="sxs-lookup"><span data-stu-id="8e604-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="8e604-111">Cette section permet de spécifier les points de terminaison à utiliser pour l'envoi de messages d'annonce.</span><span class="sxs-lookup"><span data-stu-id="8e604-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="8e604-112">Collection de points de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="8e604-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="8e604-113">Cette section permet de spécifier les points de terminaison sur lesquels écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="8e604-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e604-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8e604-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8e604-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8e604-115">Element</span></span>|<span data-ttu-id="8e604-116">Description</span><span class="sxs-lookup"><span data-stu-id="8e604-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8e604-117">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="8e604-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e604-118">Notes</span><span class="sxs-lookup"><span data-stu-id="8e604-118">Remarks</span></span>  

 <span data-ttu-id="8e604-119">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration rend tous les points de terminaison de ce service détectables.</span><span class="sxs-lookup"><span data-stu-id="8e604-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="8e604-120">Vous pouvez configurer davantage les fonctionnalités de découverte de tels points de terminaison à l’aide des [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) éléments enfants ou.</span><span class="sxs-lookup"><span data-stu-id="8e604-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="8e604-121">Utilisez la [\<announcementEndpoint>](announcementendpoint.md) section pour configurer les annonces en spécifiant la configuration de point de terminaison à utiliser pour envoyer les annonces de service (Online/Hello et offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="8e604-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="8e604-122">Utilisez la [\<discoveryEndpoint>](discoveryendpoint.md) section pour spécifier manuellement le point de terminaison sur lequel écouter les messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="8e604-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e604-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="8e604-123">Example</span></span>  

 <span data-ttu-id="8e604-124">L'exemple de configuration suivant spécifie que CalculatorService doit être détectable et indique éventuellement le point de terminaison d'annonce à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8e604-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e604-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e604-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
