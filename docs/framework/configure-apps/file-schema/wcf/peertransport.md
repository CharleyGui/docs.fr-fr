---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 68832c3a5bd4cc423642a6272e70cbecab86d6a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181542"
---
# \<peerTransport>

<span data-ttu-id="9cd2f-101">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="9cd2f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cd2f-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cd2f-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9cd2f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9cd2f-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cd2f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="9cd2f-105">Attributes</span></span>  
  
|<span data-ttu-id="9cd2f-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="9cd2f-106">Attribute</span></span>|<span data-ttu-id="9cd2f-107">Description</span><span class="sxs-lookup"><span data-stu-id="9cd2f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cd2f-108">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="9cd2f-108">listenIpAddress</span></span>|<span data-ttu-id="9cd2f-109">Chaîne indiquant une adresse IP utilisée par le nœud homologue pour écouter les messages TCP.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="9cd2f-110">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-110">The default is `null`.</span></span>|  
|<span data-ttu-id="9cd2f-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9cd2f-111">maxBufferPoolSize</span></span>|<span data-ttu-id="9cd2f-112">Entier positif indiquant la taille maximale du pool de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="9cd2f-113">La valeur par défaut est 524288.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="9cd2f-114">De nombreux éléments de WCF utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="9cd2f-115">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9cd2f-116">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9cd2f-117">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="9cd2f-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9cd2f-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="9cd2f-119">Entier positif définissant la taille maximale du message (en octets, en-têtes compris).</span><span class="sxs-lookup"><span data-stu-id="9cd2f-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="9cd2f-120">L'expéditeur d'un message reçoit une erreur SOAP si ce message est trop volumineux pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="9cd2f-121">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9cd2f-122">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-122">The default is 65536.</span></span>|  
|<span data-ttu-id="9cd2f-123">port</span><span class="sxs-lookup"><span data-stu-id="9cd2f-123">port</span></span>|<span data-ttu-id="9cd2f-124">Entier indiquant le port d’interface réseau utilisé par cette liaison pour traiter les messages TCP du canal homologue.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="9cd2f-125">Cette valeur doit être comprise entre <xref:System.Net.IPEndPoint.MinPort> et <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="9cd2f-126">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cd2f-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9cd2f-127">Child Elements</span></span>  
  
|<span data-ttu-id="9cd2f-128">Élément</span><span class="sxs-lookup"><span data-stu-id="9cd2f-128">Element</span></span>|<span data-ttu-id="9cd2f-129">Description</span><span class="sxs-lookup"><span data-stu-id="9cd2f-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="9cd2f-130">Définit les paramètres de sécurité correspondant à ce transport.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="9cd2f-131">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9cd2f-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9cd2f-132">Parent Elements</span></span>  
  
|<span data-ttu-id="9cd2f-133">Élément</span><span class="sxs-lookup"><span data-stu-id="9cd2f-133">Element</span></span>|<span data-ttu-id="9cd2f-134">Description</span><span class="sxs-lookup"><span data-stu-id="9cd2f-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="9cd2f-135">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cd2f-136">Notes</span><span class="sxs-lookup"><span data-stu-id="9cd2f-136">Remarks</span></span>  

 <span data-ttu-id="9cd2f-137">Ce transport ne peut pas être utilisé avec les contrats comportant des opérations de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="9cd2f-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd2f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cd2f-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9cd2f-139">Transports</span><span class="sxs-lookup"><span data-stu-id="9cd2f-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="9cd2f-140">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="9cd2f-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="9cd2f-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9cd2f-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9cd2f-142">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="9cd2f-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9cd2f-143">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="9cd2f-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
