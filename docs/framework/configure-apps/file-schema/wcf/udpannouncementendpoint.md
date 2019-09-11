---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854916"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="71483-101">\<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="71483-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="71483-102">Cet élément de configuration définit un point de terminaison standard utilisé par les services pour envoyer des messages d'annonce via une liaison UDP.</span><span class="sxs-lookup"><span data-stu-id="71483-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="71483-103">Il a un contrat fixe et prend en charge deux versions de découverte.</span><span class="sxs-lookup"><span data-stu-id="71483-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="71483-104">De plus, il possède une liaison UDP fixe et une valeur d'adresse par défaut indiquée dans les spécifications WS-Discovery (WS-Discovery Avril 2005 ou WS-Discovery version 1.1).</span><span class="sxs-lookup"><span data-stu-id="71483-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="71483-105">Vous pouvez spécifier l'adresse de multidiffusion à utiliser pour l'envoi et la réception de messages d'annonce.</span><span class="sxs-lookup"><span data-stu-id="71483-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="71483-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="71483-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="71483-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="71483-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="71483-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="71483-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="71483-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpAnnouncementEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="71483-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71483-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71483-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71483-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="71483-111">Attributes and Elements</span></span>  
 <span data-ttu-id="71483-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="71483-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71483-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="71483-113">Attributes</span></span>  
  
|<span data-ttu-id="71483-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="71483-114">Attribute</span></span>|<span data-ttu-id="71483-115">Description</span><span class="sxs-lookup"><span data-stu-id="71483-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71483-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="71483-116">discoveryVersion</span></span>|<span data-ttu-id="71483-117">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="71483-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="71483-118">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="71483-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="71483-119">Cette valeur est de type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="71483-119">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="71483-120">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="71483-120">maxAnnouncementDelay</span></span>|<span data-ttu-id="71483-121">Valeur Timespan qui spécifie le délai d'attente maximal du protocole de découverte avant l'envoi d'un message de type Hello.</span><span class="sxs-lookup"><span data-stu-id="71483-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="71483-122">Les messages attendent pendant un délai aléatoire compris entre 0 et la valeur de cet attribut avant d'être envoyés.</span><span class="sxs-lookup"><span data-stu-id="71483-122">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="71483-123">Cet attribut permet de définir un délai court et aléatoire pour empêcher toute tempête de réseau lorsqu'un réseau est en panne et que tous les services reviennent en ligne en même temps.</span><span class="sxs-lookup"><span data-stu-id="71483-123">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="71483-124">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="71483-124">multicastAddress</span></span>|<span data-ttu-id="71483-125">URI qui spécifie une adresse de multidiffusion à utiliser pour l'envoi et la réception des messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="71483-125">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="71483-126">La valeur par défaut est représentée par l'adresse de multidiffusion conforme à la spécification du protocole.</span><span class="sxs-lookup"><span data-stu-id="71483-126">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="71483-127">name</span><span class="sxs-lookup"><span data-stu-id="71483-127">name</span></span>|<span data-ttu-id="71483-128">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="71483-128">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="71483-129">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="71483-129">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71483-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="71483-130">Child Elements</span></span>  
  
|<span data-ttu-id="71483-131">Élément</span><span class="sxs-lookup"><span data-stu-id="71483-131">Element</span></span>|<span data-ttu-id="71483-132">Description</span><span class="sxs-lookup"><span data-stu-id="71483-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71483-133">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="71483-133">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="71483-134">Collection de paramètres qui vous permettent de configurer le transport UDP pour le point de terminaison UDP.</span><span class="sxs-lookup"><span data-stu-id="71483-134">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71483-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="71483-135">Parent Elements</span></span>  
  
|<span data-ttu-id="71483-136">Élément</span><span class="sxs-lookup"><span data-stu-id="71483-136">Element</span></span>|<span data-ttu-id="71483-137">Description</span><span class="sxs-lookup"><span data-stu-id="71483-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71483-138">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="71483-138">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="71483-139">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="71483-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="71483-140">Exemples</span><span class="sxs-lookup"><span data-stu-id="71483-140">Example</span></span>  
 <span data-ttu-id="71483-141">L'exemple suivant montre un client à l'écoute d'une annonce sur un transport de multidiffusion UDP avec adresse de multidiffusion par défaut, et sur un transport de multidiffusion UDP avec l'adresse de multidiffusion spécifiée.</span><span class="sxs-lookup"><span data-stu-id="71483-141">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="71483-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71483-142">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
