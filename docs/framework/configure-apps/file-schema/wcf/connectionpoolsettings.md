---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400479"
---
# \<connectionPoolSettings>
<span data-ttu-id="a744c-101">Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="a744c-101">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="a744c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a744c-102">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a744c-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a744c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a744c-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a744c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a744c-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="a744c-105">Attributes</span></span>  
  
|<span data-ttu-id="a744c-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="a744c-106">Attribute</span></span>|<span data-ttu-id="a744c-107">Description</span><span class="sxs-lookup"><span data-stu-id="a744c-107">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="a744c-108">Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.</span><span class="sxs-lookup"><span data-stu-id="a744c-108">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="a744c-109">En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a744c-109">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="a744c-110">La valeur par défaut est une chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="a744c-110">The default is a "default" string.</span></span> <span data-ttu-id="a744c-111">Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.</span><span class="sxs-lookup"><span data-stu-id="a744c-111">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="a744c-112"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="a744c-112">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="a744c-113">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="a744c-113">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="a744c-114">Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.</span><span class="sxs-lookup"><span data-stu-id="a744c-114">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="a744c-115">Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.</span><span class="sxs-lookup"><span data-stu-id="a744c-115">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="a744c-116">`idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.</span><span class="sxs-lookup"><span data-stu-id="a744c-116">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="a744c-117">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="a744c-117">The default is 10.</span></span><br /><br /> <span data-ttu-id="a744c-118">Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.</span><span class="sxs-lookup"><span data-stu-id="a744c-118">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="a744c-119">Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.</span><span class="sxs-lookup"><span data-stu-id="a744c-119">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="a744c-120">Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="a744c-120">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a744c-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a744c-121">Child Elements</span></span>  
 <span data-ttu-id="a744c-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a744c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a744c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a744c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a744c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="a744c-124">Element</span></span>|<span data-ttu-id="a744c-125">Description</span><span class="sxs-lookup"><span data-stu-id="a744c-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="a744c-126">Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="a744c-126">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a744c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a744c-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a744c-128">Transports</span><span class="sxs-lookup"><span data-stu-id="a744c-128">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a744c-129">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="a744c-129">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a744c-130">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a744c-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a744c-131">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a744c-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a744c-132">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a744c-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
