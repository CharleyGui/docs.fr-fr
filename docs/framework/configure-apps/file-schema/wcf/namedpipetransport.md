---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736586"
---
# <a name="namedpipetransport"></a><span data-ttu-id="c57ad-101">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="c57ad-101">\<namedPipeTransport></span></span>
<span data-ttu-id="c57ad-102">Définit un transport qui entraîne un canal à transférer des messages à l’aide de canaux nommés lorsqu’il est inclus dans une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c57ad-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="c57ad-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c57ad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c57ad-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c57ad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c57ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="c57ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="c57ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="c57ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="c57ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="c57ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="c57ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**namedPipeTransport >**</span><span class="sxs-lookup"><span data-stu-id="c57ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c57ad-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c57ad-109">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c57ad-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c57ad-110">Attributes and Elements</span></span>  
<span data-ttu-id="c57ad-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c57ad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c57ad-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c57ad-112">Attributes</span></span>  
<span data-ttu-id="c57ad-113">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="c57ad-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c57ad-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c57ad-114">Child Elements</span></span>  
  
|<span data-ttu-id="c57ad-115">Élément</span><span class="sxs-lookup"><span data-stu-id="c57ad-115">Element</span></span>|<span data-ttu-id="c57ad-116">Description</span><span class="sxs-lookup"><span data-stu-id="c57ad-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c57ad-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="c57ad-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="c57ad-118">Obtient ou définit une <xref:System.TimeSpan> qui détermine la durée maximale pendant laquelle un canal peut être dans l’état d’initialisation avant d’être déconnecté.</span><span class="sxs-lookup"><span data-stu-id="c57ad-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="c57ad-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="c57ad-119">ConnectionBufferSize</span></span>|<span data-ttu-id="c57ad-120">Obtient ou définit la taille de la mémoire tampon utilisée pour transmettre un bloc du message sérialisé sur le câble depuis le client ou le service.</span><span class="sxs-lookup"><span data-stu-id="c57ad-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="c57ad-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c57ad-121">hostNameComparisonMode</span></span>|<span data-ttu-id="c57ad-122">Obtient ou définit une valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.</span><span class="sxs-lookup"><span data-stu-id="c57ad-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="c57ad-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="c57ad-123">manualAddressing</span></span>|<span data-ttu-id="c57ad-124">Obtient ou définit une valeur qui indique si l'adressage manuel du message est requis.</span><span class="sxs-lookup"><span data-stu-id="c57ad-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="c57ad-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c57ad-125">maxBufferPoolSize</span></span>|<span data-ttu-id="c57ad-126">Obtient ou définit la taille maximale, en octets, des pools de mémoires tampons utilisés par le transport.</span><span class="sxs-lookup"><span data-stu-id="c57ad-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="c57ad-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c57ad-127">maxBufferSize</span></span>|<span data-ttu-id="c57ad-128">Obtient ou définit la taille maximale de la mémoire tampon à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c57ad-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="c57ad-129">Pour les messages diffusés en continu, cette valeur doit être au moins égale à la taille maximale possible des en-têtes de message, qui sont lus en mode mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c57ad-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="c57ad-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="c57ad-130">maxOutputDelay</span></span>|<span data-ttu-id="c57ad-131">Obtient ou définit la durée maximale pendant laquelle un bloc d'un message ou un message complet peut être conservé dans la mémoire tampon avant d'être expédié.</span><span class="sxs-lookup"><span data-stu-id="c57ad-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="c57ad-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="c57ad-132">maxPendingAccepts</span></span>|<span data-ttu-id="c57ad-133">Obtient ou définit le nombre maximal de canaux qu’un service peut avoir en attente sur un écouteur pour traiter les connexions entrantes au service.</span><span class="sxs-lookup"><span data-stu-id="c57ad-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="c57ad-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c57ad-134">maxPendingConnections</span></span>|<span data-ttu-id="c57ad-135">Obtient ou définit le nombre maximal de connexions en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="c57ad-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="c57ad-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c57ad-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="c57ad-137">Obtient et définit la taille maximale autorisée pour le message, en octets, qui peut être reçue.</span><span class="sxs-lookup"><span data-stu-id="c57ad-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="c57ad-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="c57ad-138">transferMode</span></span>|<span data-ttu-id="c57ad-139">Obtient ou définit une valeur qui indique si les messages sont mis en mémoire tampon ou transmis en continu par le transport orienté connexion.</span><span class="sxs-lookup"><span data-stu-id="c57ad-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="c57ad-140">\<> connectionPoolSettings de \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="c57ad-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="c57ad-141">Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="c57ad-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c57ad-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c57ad-142">Parent Elements</span></span>  
  
|<span data-ttu-id="c57ad-143">Élément</span><span class="sxs-lookup"><span data-stu-id="c57ad-143">Element</span></span>|<span data-ttu-id="c57ad-144">Description</span><span class="sxs-lookup"><span data-stu-id="c57ad-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c57ad-145">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="c57ad-145">\<binding></span></span>](bindings.md)|<span data-ttu-id="c57ad-146">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c57ad-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c57ad-147">Notes</span><span class="sxs-lookup"><span data-stu-id="c57ad-147">Remarks</span></span>  
<span data-ttu-id="c57ad-148">Ce transport utilise des URI au format "net.pipe://nom_hôte/chemin".</span><span class="sxs-lookup"><span data-stu-id="c57ad-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="c57ad-149">Les autres composants URI sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c57ad-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="c57ad-150">L’élément `namedPipeTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport des canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="c57ad-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="c57ad-151">Ce transport est utilisé pour la communication entre WCF (Windows Communication Foundation) et WCF sur des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="c57ad-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57ad-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c57ad-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c57ad-153">Transports</span><span class="sxs-lookup"><span data-stu-id="c57ad-153">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="c57ad-154">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="c57ad-154">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c57ad-155">Liaisons</span><span class="sxs-lookup"><span data-stu-id="c57ad-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c57ad-156">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="c57ad-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c57ad-157">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="c57ad-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c57ad-158">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c57ad-158">\<customBinding></span></span>](custombinding.md)
