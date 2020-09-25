---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: d8787bc2ef8da4fdc01237ac9b041dfdd66fce03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175991"
---
# \<connectionPoolSettings>

<span data-ttu-id="e9e5b-101">Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-101">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="e9e5b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9e5b-102">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9e5b-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e9e5b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e9e5b-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9e5b-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e9e5b-105">Attributes</span></span>  
  
|<span data-ttu-id="e9e5b-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e9e5b-106">Attribute</span></span>|<span data-ttu-id="e9e5b-107">Description</span><span class="sxs-lookup"><span data-stu-id="e9e5b-107">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="e9e5b-108">Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-108">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="e9e5b-109">En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-109">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="e9e5b-110">La valeur par défaut est une chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-110">The default is a "default" string.</span></span> <span data-ttu-id="e9e5b-111">Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-111">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="e9e5b-112"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-112">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="e9e5b-113">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-113">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="e9e5b-114">Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-114">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="e9e5b-115">Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-115">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="e9e5b-116">`idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-116">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="e9e5b-117">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-117">The default is 10.</span></span><br /><br /> <span data-ttu-id="e9e5b-118">Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-118">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="e9e5b-119">Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-119">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="e9e5b-120">Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-120">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9e5b-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e9e5b-121">Child Elements</span></span>  

 <span data-ttu-id="e9e5b-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9e5b-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e9e5b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e9e5b-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e9e5b-124">Element</span></span>|<span data-ttu-id="e9e5b-125">Description</span><span class="sxs-lookup"><span data-stu-id="e9e5b-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="e9e5b-126">Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="e9e5b-126">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9e5b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9e5b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e9e5b-128">Transports</span><span class="sxs-lookup"><span data-stu-id="e9e5b-128">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="e9e5b-129">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="e9e5b-129">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="e9e5b-130">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e9e5b-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9e5b-131">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="e9e5b-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e9e5b-132">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="e9e5b-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
