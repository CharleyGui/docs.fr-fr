---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 0e56bb5c9e485559d712281a51e79f54c9661b5a
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423136"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="21c32-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="21c32-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="21c32-102">Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="21c32-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="21c32-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="21c32-103">\<system.serviceModel></span></span>  
<span data-ttu-id="21c32-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="21c32-104">\<bindings></span></span>  
<span data-ttu-id="21c32-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="21c32-105">\<customBinding></span></span>  
<span data-ttu-id="21c32-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="21c32-106">\<binding></span></span>  
<span data-ttu-id="21c32-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="21c32-107">\<namePipeTransport></span></span>  
<span data-ttu-id="21c32-108">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="21c32-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c32-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21c32-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21c32-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="21c32-110">Attributes and Elements</span></span>  
 <span data-ttu-id="21c32-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="21c32-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21c32-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="21c32-112">Attributes</span></span>  
  
|<span data-ttu-id="21c32-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="21c32-113">Attribute</span></span>|<span data-ttu-id="21c32-114">Description</span><span class="sxs-lookup"><span data-stu-id="21c32-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="21c32-115">Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.</span><span class="sxs-lookup"><span data-stu-id="21c32-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="21c32-116">En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.</span><span class="sxs-lookup"><span data-stu-id="21c32-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="21c32-117">La valeur par défaut est une chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="21c32-117">The default is a "default" string.</span></span> <span data-ttu-id="21c32-118">Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.</span><span class="sxs-lookup"><span data-stu-id="21c32-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="21c32-119"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="21c32-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="21c32-120">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="21c32-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="21c32-121">Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.</span><span class="sxs-lookup"><span data-stu-id="21c32-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="21c32-122">Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.</span><span class="sxs-lookup"><span data-stu-id="21c32-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="21c32-123">`idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.</span><span class="sxs-lookup"><span data-stu-id="21c32-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="21c32-124">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="21c32-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="21c32-125">Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.</span><span class="sxs-lookup"><span data-stu-id="21c32-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="21c32-126">Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.</span><span class="sxs-lookup"><span data-stu-id="21c32-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="21c32-127">Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="21c32-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21c32-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="21c32-128">Child Elements</span></span>  
 <span data-ttu-id="21c32-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="21c32-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21c32-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="21c32-130">Parent Elements</span></span>  
  
|<span data-ttu-id="21c32-131">Élément</span><span class="sxs-lookup"><span data-stu-id="21c32-131">Element</span></span>|<span data-ttu-id="21c32-132">Description</span><span class="sxs-lookup"><span data-stu-id="21c32-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21c32-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="21c32-133">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="21c32-134">Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="21c32-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21c32-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21c32-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="21c32-136">Transports</span><span class="sxs-lookup"><span data-stu-id="21c32-136">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="21c32-137">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="21c32-137">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="21c32-138">Liaisons</span><span class="sxs-lookup"><span data-stu-id="21c32-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="21c32-139">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="21c32-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="21c32-140">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="21c32-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="21c32-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="21c32-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
