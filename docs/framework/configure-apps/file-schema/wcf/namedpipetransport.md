---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 473d0fbd543a056ec2b152f43a76a0417a18016f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933207"
---
# <a name="namedpipetransport"></a><span data-ttu-id="c66a8-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="c66a8-101">\<namedPipeTransport></span></span>
<span data-ttu-id="c66a8-102">Définit un transport qui entraîne un canal à transférer des messages à l’aide de canaux nommés lorsqu’il est inclus dans une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c66a8-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="c66a8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c66a8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c66a8-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c66a8-104">\<bindings></span></span>  
<span data-ttu-id="c66a8-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c66a8-105">\<customBinding></span></span>  
<span data-ttu-id="c66a8-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="c66a8-106">\<binding></span></span>  
<span data-ttu-id="c66a8-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="c66a8-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c66a8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c66a8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c66a8-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c66a8-109">Attributes and Elements</span></span>  
<span data-ttu-id="c66a8-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c66a8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c66a8-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="c66a8-111">Attributes</span></span>  
<span data-ttu-id="c66a8-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c66a8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c66a8-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c66a8-113">Child Elements</span></span>  
  
|<span data-ttu-id="c66a8-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c66a8-114">Element</span></span>|<span data-ttu-id="c66a8-115">Description</span><span class="sxs-lookup"><span data-stu-id="c66a8-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c66a8-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="c66a8-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="c66a8-117">Obtient ou définit une <xref:System.TimeSpan> valeur qui détermine la durée maximale pendant laquelle un canal peut être dans l’état d’initialisation avant d’être déconnecté.</span><span class="sxs-lookup"><span data-stu-id="c66a8-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="c66a8-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="c66a8-118">ConnectionBufferSize</span></span>|<span data-ttu-id="c66a8-119">Obtient ou définit la taille de la mémoire tampon utilisée pour transmettre un bloc du message sérialisé sur le câble depuis le client ou le service.</span><span class="sxs-lookup"><span data-stu-id="c66a8-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="c66a8-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c66a8-120">hostNameComparisonMode</span></span>|<span data-ttu-id="c66a8-121">Obtient ou définit une valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.</span><span class="sxs-lookup"><span data-stu-id="c66a8-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="c66a8-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="c66a8-122">manualAddressing</span></span>|<span data-ttu-id="c66a8-123">Obtient ou définit une valeur qui indique si l'adressage manuel du message est requis.</span><span class="sxs-lookup"><span data-stu-id="c66a8-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="c66a8-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c66a8-124">maxBufferPoolSize</span></span>|<span data-ttu-id="c66a8-125">Obtient ou définit la taille maximale, en octets, des pools de mémoires tampons utilisés par le transport.</span><span class="sxs-lookup"><span data-stu-id="c66a8-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="c66a8-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c66a8-126">maxBufferSize</span></span>|<span data-ttu-id="c66a8-127">Obtient ou définit la taille maximale de la mémoire tampon à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c66a8-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="c66a8-128">Pour les messages diffusés en continu, cette valeur doit être au moins égale à la taille maximale possible des en-têtes de message, qui sont lus en mode mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c66a8-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="c66a8-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="c66a8-129">maxOutputDelay</span></span>|<span data-ttu-id="c66a8-130">Obtient ou définit la durée maximale pendant laquelle un bloc d'un message ou un message complet peut être conservé dans la mémoire tampon avant d'être expédié.</span><span class="sxs-lookup"><span data-stu-id="c66a8-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="c66a8-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="c66a8-131">maxPendingAccepts</span></span>|<span data-ttu-id="c66a8-132">Obtient ou définit le nombre maximal de canaux qu’un service peut avoir en attente sur un écouteur pour traiter les connexions entrantes au service.</span><span class="sxs-lookup"><span data-stu-id="c66a8-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="c66a8-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c66a8-133">maxPendingConnections</span></span>|<span data-ttu-id="c66a8-134">Obtient ou définit le nombre maximal de connexions en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="c66a8-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="c66a8-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c66a8-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="c66a8-136">Obtient et définit la taille maximale autorisée pour le message, en octets, qui peut être reçue.</span><span class="sxs-lookup"><span data-stu-id="c66a8-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="c66a8-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="c66a8-137">transferMode</span></span>|<span data-ttu-id="c66a8-138">Obtient ou définit une valeur qui indique si les messages sont mis en mémoire tampon ou transmis en continu par le transport orienté connexion.</span><span class="sxs-lookup"><span data-stu-id="c66a8-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="c66a8-139">\<connectionPoolSettings> of \<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="c66a8-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="c66a8-140">Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="c66a8-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c66a8-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c66a8-141">Parent Elements</span></span>  
  
|<span data-ttu-id="c66a8-142">Élément</span><span class="sxs-lookup"><span data-stu-id="c66a8-142">Element</span></span>|<span data-ttu-id="c66a8-143">Description</span><span class="sxs-lookup"><span data-stu-id="c66a8-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c66a8-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="c66a8-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="c66a8-145">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c66a8-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c66a8-146">Notes</span><span class="sxs-lookup"><span data-stu-id="c66a8-146">Remarks</span></span>  
<span data-ttu-id="c66a8-147">Ce transport utilise des URI au format "net.pipe://nom_hôte/chemin".</span><span class="sxs-lookup"><span data-stu-id="c66a8-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="c66a8-148">Les autres composants URI sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c66a8-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="c66a8-149">L’élément `namedPipeTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport des canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="c66a8-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="c66a8-150">Ce transport est utilisé pour la communication entre WCF (Windows Communication Foundation) et WCF sur des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="c66a8-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66a8-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c66a8-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c66a8-152">Transports</span><span class="sxs-lookup"><span data-stu-id="c66a8-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="c66a8-153">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="c66a8-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c66a8-154">Liaisons</span><span class="sxs-lookup"><span data-stu-id="c66a8-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c66a8-155">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="c66a8-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c66a8-156">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="c66a8-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c66a8-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c66a8-157">\<customBinding></span></span>](custombinding.md)
