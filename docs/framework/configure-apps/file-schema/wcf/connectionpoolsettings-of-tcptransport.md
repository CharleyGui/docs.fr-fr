---
title: <connectionPoolSettings> de <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 53523fd550ecad931bfb2af5eb9beb71c60d44f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176004"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="a356e-102">\<connectionPoolSettings> de \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="a356e-102">\<connectionPoolSettings> of \<tcpTransport></span></span>

<span data-ttu-id="a356e-103">Spécifie des paramètres de pool de connexions supplémentaires pour un transport TCP.</span><span class="sxs-lookup"><span data-stu-id="a356e-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="a356e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a356e-104">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a356e-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a356e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a356e-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a356e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a356e-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a356e-107">Attributes</span></span>  
  
|<span data-ttu-id="a356e-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a356e-108">Attribute</span></span>|<span data-ttu-id="a356e-109">Description</span><span class="sxs-lookup"><span data-stu-id="a356e-109">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="a356e-110">Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.</span><span class="sxs-lookup"><span data-stu-id="a356e-110">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="a356e-111">En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a356e-111">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="a356e-112">La valeur par défaut est une chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="a356e-112">The default is a "default" string.</span></span> <span data-ttu-id="a356e-113">Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.</span><span class="sxs-lookup"><span data-stu-id="a356e-113">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="a356e-114"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="a356e-114">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="a356e-115">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="a356e-115">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="a356e-116"><xref:System.TimeSpan> qui spécifie le délai après lequel une connexion active est fermée.</span><span class="sxs-lookup"><span data-stu-id="a356e-116">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="a356e-117">La valeur par défaut est 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="a356e-117">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="a356e-118">Une connexion est fermée après qu'elle ait été retournée au cache de connexions et non pendant la transmission active.</span><span class="sxs-lookup"><span data-stu-id="a356e-118">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="a356e-119">Le cache de connexions utilisé par le transport TCP crée les connexions requises pour chaque point de terminaison jusqu'à la limite de cache définie par `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="a356e-119">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="a356e-120">Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.</span><span class="sxs-lookup"><span data-stu-id="a356e-120">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="a356e-121">Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.</span><span class="sxs-lookup"><span data-stu-id="a356e-121">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="a356e-122">`idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.</span><span class="sxs-lookup"><span data-stu-id="a356e-122">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="a356e-123">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="a356e-123">The default is 10.</span></span><br /><br /> <span data-ttu-id="a356e-124">Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.</span><span class="sxs-lookup"><span data-stu-id="a356e-124">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="a356e-125">Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.</span><span class="sxs-lookup"><span data-stu-id="a356e-125">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="a356e-126">Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="a356e-126">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a356e-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a356e-127">Child Elements</span></span>  

 <span data-ttu-id="a356e-128">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a356e-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a356e-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a356e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a356e-130">Élément</span><span class="sxs-lookup"><span data-stu-id="a356e-130">Element</span></span>|<span data-ttu-id="a356e-131">Description</span><span class="sxs-lookup"><span data-stu-id="a356e-131">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="a356e-132">Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="a356e-132">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a356e-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a356e-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a356e-134">Transports</span><span class="sxs-lookup"><span data-stu-id="a356e-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a356e-135">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="a356e-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a356e-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a356e-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a356e-137">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a356e-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a356e-138">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a356e-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
