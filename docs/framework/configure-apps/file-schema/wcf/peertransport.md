---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736510"
---
# \<peerTransport>
<span data-ttu-id="cf01b-101">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="cf01b-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="cf01b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf01b-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf01b-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cf01b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cf01b-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cf01b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf01b-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="cf01b-105">Attributes</span></span>  
  
|<span data-ttu-id="cf01b-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="cf01b-106">Attribute</span></span>|<span data-ttu-id="cf01b-107">Description</span><span class="sxs-lookup"><span data-stu-id="cf01b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf01b-108">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="cf01b-108">listenIpAddress</span></span>|<span data-ttu-id="cf01b-109">Chaîne indiquant une adresse IP utilisée par le nœud homologue pour écouter les messages TCP.</span><span class="sxs-lookup"><span data-stu-id="cf01b-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="cf01b-110">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="cf01b-110">The default is `null`.</span></span>|  
|<span data-ttu-id="cf01b-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="cf01b-111">maxBufferPoolSize</span></span>|<span data-ttu-id="cf01b-112">Entier positif indiquant la taille maximale du pool de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="cf01b-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="cf01b-113">La valeur par défaut est 524288.</span><span class="sxs-lookup"><span data-stu-id="cf01b-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="cf01b-114">De nombreux éléments de WCF utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="cf01b-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="cf01b-115">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="cf01b-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="cf01b-116">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="cf01b-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="cf01b-117">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="cf01b-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="cf01b-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="cf01b-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="cf01b-119">Entier positif définissant la taille maximale du message (en octets, en-têtes compris).</span><span class="sxs-lookup"><span data-stu-id="cf01b-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="cf01b-120">L'expéditeur d'un message reçoit une erreur SOAP si ce message est trop volumineux pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="cf01b-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="cf01b-121">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="cf01b-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="cf01b-122">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="cf01b-122">The default is 65536.</span></span>|  
|<span data-ttu-id="cf01b-123">port</span><span class="sxs-lookup"><span data-stu-id="cf01b-123">port</span></span>|<span data-ttu-id="cf01b-124">Entier indiquant le port d’interface réseau utilisé par cette liaison pour traiter les messages TCP du canal homologue.</span><span class="sxs-lookup"><span data-stu-id="cf01b-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="cf01b-125">Cette valeur doit être comprise entre <xref:System.Net.IPEndPoint.MinPort> et <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="cf01b-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="cf01b-126">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="cf01b-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf01b-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cf01b-127">Child Elements</span></span>  
  
|<span data-ttu-id="cf01b-128">Élément</span><span class="sxs-lookup"><span data-stu-id="cf01b-128">Element</span></span>|<span data-ttu-id="cf01b-129">Description</span><span class="sxs-lookup"><span data-stu-id="cf01b-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="cf01b-130">Définit les paramètres de sécurité correspondant à ce transport.</span><span class="sxs-lookup"><span data-stu-id="cf01b-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="cf01b-131">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="cf01b-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf01b-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cf01b-132">Parent Elements</span></span>  
  
|<span data-ttu-id="cf01b-133">Élément</span><span class="sxs-lookup"><span data-stu-id="cf01b-133">Element</span></span>|<span data-ttu-id="cf01b-134">Description</span><span class="sxs-lookup"><span data-stu-id="cf01b-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="cf01b-135">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="cf01b-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf01b-136">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf01b-136">Remarks</span></span>  
 <span data-ttu-id="cf01b-137">Ce transport ne peut pas être utilisé avec les contrats comportant des opérations de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="cf01b-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf01b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf01b-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cf01b-139">Transports</span><span class="sxs-lookup"><span data-stu-id="cf01b-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="cf01b-140">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="cf01b-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="cf01b-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="cf01b-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cf01b-142">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="cf01b-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cf01b-143">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="cf01b-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
