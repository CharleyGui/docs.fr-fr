---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: aa4cd8f4d7dcfa438ede71c394f1d0b0ac6faa50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926549"
---
# <a name="announcementendpoint"></a><span data-ttu-id="ca419-101">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="ca419-101">\<announcementEndpoint></span></span>
<span data-ttu-id="ca419-102">Cet élément de configuration définit un point de terminaison standard avec un contrat d'annonce fixe.</span><span class="sxs-lookup"><span data-stu-id="ca419-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="ca419-103">Un service peut éventuellement annoncer sa disponibilité en envoyant un message d'annonce en ligne ou hors connexion selon qu'il est respectivement ouvert ou fermé.</span><span class="sxs-lookup"><span data-stu-id="ca419-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="ca419-104">Un service Windows Communication Foundation (WCF) spécifie les points de terminaison d’annonce dans l' [ \<élément serviceDiscovery >](servicediscovery.md) et utilise AnnouncementClient pour effectuer les annonces.</span><span class="sxs-lookup"><span data-stu-id="ca419-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="ca419-105">Un client qui souhaite écouter l’annonce d’un autre service joue en fait le rôle de service WCF. vous devez donc configurer les points de terminaison d’annonce pour ce client dans la [ \<section services >](services.md) .</span><span class="sxs-lookup"><span data-stu-id="ca419-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
<span data-ttu-id="ca419-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ca419-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="ca419-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ca419-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca419-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca419-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca419-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ca419-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ca419-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ca419-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca419-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ca419-111">Attributes</span></span>  
  
|<span data-ttu-id="ca419-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ca419-112">Attribute</span></span>|<span data-ttu-id="ca419-113">Description</span><span class="sxs-lookup"><span data-stu-id="ca419-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca419-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="ca419-114">discoveryVersion</span></span>|<span data-ttu-id="ca419-115">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="ca419-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="ca419-116">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="ca419-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="ca419-117">Cette valeur est de type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="ca419-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="ca419-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="ca419-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="ca419-119">Valeur Timespan qui spécifie le délai d'attente maximal du protocole de découverte avant l'envoi d'un message de type Hello.</span><span class="sxs-lookup"><span data-stu-id="ca419-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="ca419-120">Les messages attendent pendant un délai aléatoire compris entre 0 et la valeur de cet attribut avant d'être envoyés.</span><span class="sxs-lookup"><span data-stu-id="ca419-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="ca419-121">Cet attribut permet de définir un délai court et aléatoire pour empêcher toute tempête de réseau lorsqu'un réseau est en panne et que tous les services reviennent en ligne en même temps.</span><span class="sxs-lookup"><span data-stu-id="ca419-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="ca419-122">name</span><span class="sxs-lookup"><span data-stu-id="ca419-122">name</span></span>|<span data-ttu-id="ca419-123">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="ca419-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="ca419-124">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="ca419-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca419-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca419-125">Child Elements</span></span>  
 <span data-ttu-id="ca419-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ca419-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca419-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca419-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ca419-128">Élément</span><span class="sxs-lookup"><span data-stu-id="ca419-128">Element</span></span>|<span data-ttu-id="ca419-129">Description</span><span class="sxs-lookup"><span data-stu-id="ca419-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca419-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ca419-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ca419-131">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="ca419-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ca419-132">Exemples</span><span class="sxs-lookup"><span data-stu-id="ca419-132">Example</span></span>  
 <span data-ttu-id="ca419-133">L'exemple suivant montre un client qui écoute des messages d'annonce sur HTTP et Peernet.</span><span class="sxs-lookup"><span data-stu-id="ca419-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="ca419-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca419-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
