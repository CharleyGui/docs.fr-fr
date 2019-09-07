---
title: <connectionPoolSettings> de <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: f9b0fff741c32c1a3d6f9461f478e89acc18114e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398093"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="5d3c5-102">\<connectionPoolSettings > de \<TcpTransport ></span><span class="sxs-lookup"><span data-stu-id="5d3c5-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="5d3c5-103">Spécifie des paramètres de pool de connexions supplémentaires pour un transport TCP.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
<span data-ttu-id="5d3c5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d3c5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5d3c5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5d3c5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5d3c5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5d3c5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5d3c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5d3c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5d3c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="5d3c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5d3c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tcpTransport >** ](tcptransport.md)</span><span class="sxs-lookup"><span data-stu-id="5d3c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)</span></span>\
<span data-ttu-id="5d3c5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="5d3c5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3c5-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d3c5-111">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d3c5-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5d3c5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5d3c5-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d3c5-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="5d3c5-114">Attributes</span></span>  
  
|<span data-ttu-id="5d3c5-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="5d3c5-115">Attribute</span></span>|<span data-ttu-id="5d3c5-116">Description</span><span class="sxs-lookup"><span data-stu-id="5d3c5-116">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="5d3c5-117">Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-117">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="5d3c5-118">En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-118">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="5d3c5-119">La valeur par défaut est une chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-119">The default is a "default" string.</span></span> <span data-ttu-id="5d3c5-120">Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-120">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="5d3c5-121"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-121">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="5d3c5-122">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-122">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="5d3c5-123"><xref:System.TimeSpan> qui spécifie le délai après lequel une connexion active est fermée.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-123">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="5d3c5-124">La valeur par défaut est 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-124">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="5d3c5-125">Une connexion est fermée après qu'elle ait été retournée au cache de connexions et non pendant la transmission active.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-125">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="5d3c5-126">Le cache de connexions utilisé par le transport TCP crée les connexions requises pour chaque point de terminaison jusqu'à la limite de cache définie par `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="5d3c5-126">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="5d3c5-127">Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-127">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="5d3c5-128">Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-128">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="5d3c5-129">`idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-129">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="5d3c5-130">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-130">The default is 10.</span></span><br /><br /> <span data-ttu-id="5d3c5-131">Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-131">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="5d3c5-132">Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-132">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="5d3c5-133">Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-133">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d3c5-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5d3c5-134">Child Elements</span></span>  
 <span data-ttu-id="5d3c5-135">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d3c5-136">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5d3c5-136">Parent Elements</span></span>  
  
|<span data-ttu-id="5d3c5-137">Élément</span><span class="sxs-lookup"><span data-stu-id="5d3c5-137">Element</span></span>|<span data-ttu-id="5d3c5-138">Description</span><span class="sxs-lookup"><span data-stu-id="5d3c5-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d3c5-139">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="5d3c5-139">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="5d3c5-140">Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="5d3c5-140">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d3c5-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d3c5-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5d3c5-142">Transports</span><span class="sxs-lookup"><span data-stu-id="5d3c5-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="5d3c5-143">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="5d3c5-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="5d3c5-144">Liaisons</span><span class="sxs-lookup"><span data-stu-id="5d3c5-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5d3c5-145">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="5d3c5-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5d3c5-146">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="5d3c5-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5d3c5-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5d3c5-147">\<customBinding></span></span>](custombinding.md)
