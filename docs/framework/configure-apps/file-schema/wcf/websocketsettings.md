---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 6cfddfb9ebfc7c3447af977e14738baabebc8fe9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177849"
---
# \<webSocketSettings>

<span data-ttu-id="7fcd1-101">Élément de configuration utilisé pour spécifier des paramètres WebSocket.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="7fcd1-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fcd1-102">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fcd1-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7fcd1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7fcd1-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fcd1-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7fcd1-105">Attributes</span></span>  
  
|<span data-ttu-id="7fcd1-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="7fcd1-106">Attribute</span></span>|<span data-ttu-id="7fcd1-107">Description</span><span class="sxs-lookup"><span data-stu-id="7fcd1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fcd1-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="7fcd1-108">createNotificationOnConnection</span></span>|<span data-ttu-id="7fcd1-109">Spécifie si une notification est envoyée lors de la connexion.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="7fcd1-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="7fcd1-110">disablePayloadMasking</span></span>|<span data-ttu-id="7fcd1-111">Spécifie si le masquage WebSocket est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="7fcd1-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="7fcd1-112">keepAliveInterval</span></span>|<span data-ttu-id="7fcd1-113">Spécifie l'intervalle de maintien de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="7fcd1-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="7fcd1-114">maxPendingConnections</span></span>|<span data-ttu-id="7fcd1-115">Spécifie le nombre maximal de connexions entrantes en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="7fcd1-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="7fcd1-116">receiveBufferSize</span></span>|<span data-ttu-id="7fcd1-117">Spécifie la taille de la mémoire tampon de réception.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="7fcd1-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="7fcd1-118">sendBufferSize</span></span>|<span data-ttu-id="7fcd1-119">Spécifie la taille de la mémoire tampon d'envoi.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="7fcd1-120">subProtocol</span><span class="sxs-lookup"><span data-stu-id="7fcd1-120">subProtocol</span></span>|<span data-ttu-id="7fcd1-121">Spécifie le sous-protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="7fcd1-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="7fcd1-122">transportUsage</span></span>|<span data-ttu-id="7fcd1-123">Spécifie quand utiliser WebSocket.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="7fcd1-124">Attribut transportUsage</span><span class="sxs-lookup"><span data-stu-id="7fcd1-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="7fcd1-125">Valeur</span><span class="sxs-lookup"><span data-stu-id="7fcd1-125">Value</span></span>|<span data-ttu-id="7fcd1-126">Description</span><span class="sxs-lookup"><span data-stu-id="7fcd1-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7fcd1-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="7fcd1-127">WhenDuplex</span></span>|<span data-ttu-id="7fcd1-128">Utilisez le protocole WebSocket lorsque le contrat est en duplex.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="7fcd1-129">Toujours</span><span class="sxs-lookup"><span data-stu-id="7fcd1-129">Always</span></span>|<span data-ttu-id="7fcd1-130">Utilisez toujours le protocole WebSocket indépendamment du contrat.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="7fcd1-131">Jamais</span><span class="sxs-lookup"><span data-stu-id="7fcd1-131">Never</span></span>|<span data-ttu-id="7fcd1-132">N'utilisez jamais le protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fcd1-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7fcd1-133">Child Elements</span></span>  

 <span data-ttu-id="7fcd1-134">None</span><span class="sxs-lookup"><span data-stu-id="7fcd1-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7fcd1-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7fcd1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="7fcd1-136">Élément</span><span class="sxs-lookup"><span data-stu-id="7fcd1-136">Element</span></span>|<span data-ttu-id="7fcd1-137">Description</span><span class="sxs-lookup"><span data-stu-id="7fcd1-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="7fcd1-138">Spécifie le NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7fcd1-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7fcd1-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="7fcd1-139">Example</span></span>  

 <span data-ttu-id="7fcd1-140">L'exemple suivant montre comment utiliser l'élément \<webSocketSettings>.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="7fcd1-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fcd1-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="7fcd1-142">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7fcd1-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7fcd1-143">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="7fcd1-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7fcd1-144">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7fcd1-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
