---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736586"
---
# \<namedPipeTransport>
<span data-ttu-id="90675-101">Définit un transport qui entraîne un canal à transférer des messages à l’aide de canaux nommés lorsqu’il est inclus dans une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="90675-101">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="90675-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90675-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90675-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="90675-103">Attributes and Elements</span></span>  
<span data-ttu-id="90675-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="90675-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90675-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="90675-105">Attributes</span></span>  
<span data-ttu-id="90675-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="90675-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90675-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="90675-107">Child Elements</span></span>  
  
|<span data-ttu-id="90675-108">Élément</span><span class="sxs-lookup"><span data-stu-id="90675-108">Element</span></span>|<span data-ttu-id="90675-109">Description</span><span class="sxs-lookup"><span data-stu-id="90675-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90675-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="90675-110">ChannelInitializationTimeout</span></span>|<span data-ttu-id="90675-111">Obtient ou définit un <xref:System.TimeSpan> qui détermine la durée maximale de l'état d'initialisation du canal avant sa déconnexion.</span><span class="sxs-lookup"><span data-stu-id="90675-111">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="90675-112">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="90675-112">ConnectionBufferSize</span></span>|<span data-ttu-id="90675-113">Obtient ou définit la taille de la mémoire tampon utilisée pour transmettre un bloc du message sérialisé sur le câble depuis le client ou le service.</span><span class="sxs-lookup"><span data-stu-id="90675-113">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="90675-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="90675-114">hostNameComparisonMode</span></span>|<span data-ttu-id="90675-115">Obtient ou définit une valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.</span><span class="sxs-lookup"><span data-stu-id="90675-115">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="90675-116">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="90675-116">manualAddressing</span></span>|<span data-ttu-id="90675-117">Obtient ou définit une valeur qui indique si l'adressage manuel du message est requis.</span><span class="sxs-lookup"><span data-stu-id="90675-117">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="90675-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="90675-118">maxBufferPoolSize</span></span>|<span data-ttu-id="90675-119">Obtient ou définit la taille maximale (en octets) des pools de mémoires tampons utilisés par le transport.</span><span class="sxs-lookup"><span data-stu-id="90675-119">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="90675-120">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="90675-120">maxBufferSize</span></span>|<span data-ttu-id="90675-121">Obtient ou définit la taille maximale de la mémoire tampon à utiliser.</span><span class="sxs-lookup"><span data-stu-id="90675-121">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="90675-122">Pour les messages diffusés en continu, cette valeur doit être au moins égale à la taille maximale possible des en-têtes de message, qui sont lus en mode mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="90675-122">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="90675-123">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="90675-123">maxOutputDelay</span></span>|<span data-ttu-id="90675-124">Obtient ou définit la durée maximale pendant laquelle un bloc d'un message ou un message complet peut être conservé dans la mémoire tampon avant d'être expédié.</span><span class="sxs-lookup"><span data-stu-id="90675-124">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="90675-125">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="90675-125">maxPendingAccepts</span></span>|<span data-ttu-id="90675-126">Obtient ou définit le nombre maximal de canaux qu'un service peut posséder lors de l'attente sur un écouteur pour traiter les connexions entrantes au service.</span><span class="sxs-lookup"><span data-stu-id="90675-126">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="90675-127">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="90675-127">maxPendingConnections</span></span>|<span data-ttu-id="90675-128">Obtient ou définit le nombre maximal de connexions en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="90675-128">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="90675-129">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="90675-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="90675-130">Obtient et définit la taille maximale autorisée pour le message, en octets, qui peut être reçue.</span><span class="sxs-lookup"><span data-stu-id="90675-130">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="90675-131">transferMode</span><span class="sxs-lookup"><span data-stu-id="90675-131">transferMode</span></span>|<span data-ttu-id="90675-132">Obtient ou définit une valeur qui indique si les messages sont mis en mémoire tampon ou transmis en continu par le transport orienté connexion.</span><span class="sxs-lookup"><span data-stu-id="90675-132">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="90675-133">\<connectionPoolSettings>of\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="90675-133">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="90675-134">Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="90675-134">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90675-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="90675-135">Parent Elements</span></span>  
  
|<span data-ttu-id="90675-136">Élément</span><span class="sxs-lookup"><span data-stu-id="90675-136">Element</span></span>|<span data-ttu-id="90675-137">Description</span><span class="sxs-lookup"><span data-stu-id="90675-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="90675-138">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="90675-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90675-139">Remarques</span><span class="sxs-lookup"><span data-stu-id="90675-139">Remarks</span></span>  
<span data-ttu-id="90675-140">Ce transport utilise des URI au format "net.pipe://nom_hôte/chemin".</span><span class="sxs-lookup"><span data-stu-id="90675-140">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="90675-141">Les autres composants URI sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="90675-141">Other URI components are optional.</span></span>  
  
<span data-ttu-id="90675-142">L’élément `namedPipeTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport des canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="90675-142">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="90675-143">Ce transport est utilisé pour la communication entre WCF (Windows Communication Foundation) et WCF sur des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="90675-143">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90675-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90675-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="90675-145">Transports</span><span class="sxs-lookup"><span data-stu-id="90675-145">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="90675-146">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="90675-146">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="90675-147">Liaisons</span><span class="sxs-lookup"><span data-stu-id="90675-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="90675-148">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="90675-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="90675-149">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="90675-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
