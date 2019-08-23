---
title: <connectionPoolSettings> de <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 787b50296b7ed4f6fdceef244a99dffffae63c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919399"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="048ba-102">\<connectionPoolSettings > de \<TcpTransport ></span><span class="sxs-lookup"><span data-stu-id="048ba-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="048ba-103">Spécifie des paramètres de pool de connexions supplémentaires pour un transport TCP.</span><span class="sxs-lookup"><span data-stu-id="048ba-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="048ba-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="048ba-104">\<system.serviceModel></span></span>  
<span data-ttu-id="048ba-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="048ba-105">\<bindings></span></span>  
<span data-ttu-id="048ba-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="048ba-106">\<customBinding></span></span>  
<span data-ttu-id="048ba-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="048ba-107">\<binding></span></span>  
<span data-ttu-id="048ba-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="048ba-108">\<tcpTransport></span></span>  
<span data-ttu-id="048ba-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="048ba-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048ba-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="048ba-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="048ba-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="048ba-111">Attributes and Elements</span></span>  
 <span data-ttu-id="048ba-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="048ba-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="048ba-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="048ba-113">Attributes</span></span>  
  
|<span data-ttu-id="048ba-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="048ba-114">Attribute</span></span>|<span data-ttu-id="048ba-115">Description</span><span class="sxs-lookup"><span data-stu-id="048ba-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="048ba-116">Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.</span><span class="sxs-lookup"><span data-stu-id="048ba-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="048ba-117">En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.</span><span class="sxs-lookup"><span data-stu-id="048ba-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="048ba-118">La valeur par défaut est une chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="048ba-118">The default is a "default" string.</span></span> <span data-ttu-id="048ba-119">Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.</span><span class="sxs-lookup"><span data-stu-id="048ba-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="048ba-120"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="048ba-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="048ba-121">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="048ba-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="048ba-122"><xref:System.TimeSpan> qui spécifie le délai après lequel une connexion active est fermée.</span><span class="sxs-lookup"><span data-stu-id="048ba-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="048ba-123">La valeur par défaut est 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="048ba-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="048ba-124">Une connexion est fermée après qu'elle ait été retournée au cache de connexions et non pendant la transmission active.</span><span class="sxs-lookup"><span data-stu-id="048ba-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="048ba-125">Le cache de connexions utilisé par le transport TCP crée les connexions requises pour chaque point de terminaison jusqu'à la limite de cache définie par `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="048ba-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="048ba-126">Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.</span><span class="sxs-lookup"><span data-stu-id="048ba-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="048ba-127">Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.</span><span class="sxs-lookup"><span data-stu-id="048ba-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="048ba-128">`idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.</span><span class="sxs-lookup"><span data-stu-id="048ba-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="048ba-129">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="048ba-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="048ba-130">Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.</span><span class="sxs-lookup"><span data-stu-id="048ba-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="048ba-131">Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.</span><span class="sxs-lookup"><span data-stu-id="048ba-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="048ba-132">Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="048ba-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="048ba-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="048ba-133">Child Elements</span></span>  
 <span data-ttu-id="048ba-134">Aucun.</span><span class="sxs-lookup"><span data-stu-id="048ba-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="048ba-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="048ba-135">Parent Elements</span></span>  
  
|<span data-ttu-id="048ba-136">Élément</span><span class="sxs-lookup"><span data-stu-id="048ba-136">Element</span></span>|<span data-ttu-id="048ba-137">Description</span><span class="sxs-lookup"><span data-stu-id="048ba-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="048ba-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="048ba-138">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="048ba-139">Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="048ba-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="048ba-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="048ba-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="048ba-141">Transports</span><span class="sxs-lookup"><span data-stu-id="048ba-141">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="048ba-142">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="048ba-142">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="048ba-143">Liaisons</span><span class="sxs-lookup"><span data-stu-id="048ba-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="048ba-144">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="048ba-144">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="048ba-145">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="048ba-145">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="048ba-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="048ba-146">\<customBinding></span></span>](custombinding.md)
