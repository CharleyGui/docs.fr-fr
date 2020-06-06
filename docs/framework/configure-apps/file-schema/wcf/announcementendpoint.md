---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: decaaa1cea5345ff971b16cbb20a85dd803a52d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850288"
---
# \<announcementEndpoint>
<span data-ttu-id="98cc4-101">Cet élément de configuration définit un point de terminaison standard avec un contrat d'annonce fixe.</span><span class="sxs-lookup"><span data-stu-id="98cc4-101">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="98cc4-102">Un service peut éventuellement annoncer sa disponibilité en envoyant un message d'annonce en ligne ou hors connexion selon qu'il est respectivement ouvert ou fermé.</span><span class="sxs-lookup"><span data-stu-id="98cc4-102">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="98cc4-103">Un service Windows Communication Foundation (WCF) spécifie les points de terminaison d’annonce dans l' [\<serviceDiscovery>](servicediscovery.md) élément et utilise AnnouncementClient pour effectuer les annonces.</span><span class="sxs-lookup"><span data-stu-id="98cc4-103">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="98cc4-104">Un client qui souhaite écouter l’annonce d’un autre service joue en fait le rôle de service WCF. vous devez donc configurer les points de terminaison d’annonce pour ce client dans la [\<services>](services.md) section.</span><span class="sxs-lookup"><span data-stu-id="98cc4-104">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<announcementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="98cc4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98cc4-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98cc4-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="98cc4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="98cc4-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="98cc4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98cc4-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="98cc4-108">Attributes</span></span>  
  
|<span data-ttu-id="98cc4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="98cc4-109">Attribute</span></span>|<span data-ttu-id="98cc4-110">Description</span><span class="sxs-lookup"><span data-stu-id="98cc4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98cc4-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="98cc4-111">discoveryVersion</span></span>|<span data-ttu-id="98cc4-112">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="98cc4-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="98cc4-113">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="98cc4-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="98cc4-114">Cette valeur est de type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="98cc4-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="98cc4-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="98cc4-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="98cc4-116">Valeur Timespan qui spécifie le délai d'attente maximal du protocole de découverte avant l'envoi d'un message de type Hello.</span><span class="sxs-lookup"><span data-stu-id="98cc4-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="98cc4-117">Les messages attendent pendant un délai aléatoire compris entre 0 et la valeur de cet attribut avant d'être envoyés.</span><span class="sxs-lookup"><span data-stu-id="98cc4-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="98cc4-118">Cet attribut permet de définir un délai court et aléatoire pour empêcher toute tempête de réseau lorsqu'un réseau est en panne et que tous les services reviennent en ligne en même temps.</span><span class="sxs-lookup"><span data-stu-id="98cc4-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="98cc4-119">name</span><span class="sxs-lookup"><span data-stu-id="98cc4-119">name</span></span>|<span data-ttu-id="98cc4-120">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="98cc4-120">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="98cc4-121">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="98cc4-121">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98cc4-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="98cc4-122">Child Elements</span></span>  
 <span data-ttu-id="98cc4-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="98cc4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98cc4-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="98cc4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="98cc4-125">Élément</span><span class="sxs-lookup"><span data-stu-id="98cc4-125">Element</span></span>|<span data-ttu-id="98cc4-126">Description</span><span class="sxs-lookup"><span data-stu-id="98cc4-126">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="98cc4-127">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="98cc4-127">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="98cc4-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="98cc4-128">Example</span></span>  
 <span data-ttu-id="98cc4-129">L'exemple suivant montre un client qui écoute des messages d'annonce sur HTTP et Peernet.</span><span class="sxs-lookup"><span data-stu-id="98cc4-129">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98cc4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98cc4-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
