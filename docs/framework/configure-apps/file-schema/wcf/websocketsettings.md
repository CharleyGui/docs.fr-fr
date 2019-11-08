---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732553"
---
# <a name="websocketsettings"></a><span data-ttu-id="9d7c6-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="9d7c6-101">\<webSocketSettings></span></span>
<span data-ttu-id="9d7c6-102">Élément de configuration utilisé pour spécifier des paramètres WebSocket.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="9d7c6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d7c6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9d7c6-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9d7c6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9d7c6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="9d7c6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="9d7c6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetHttpBinding**](nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="9d7c6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="9d7c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="9d7c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="9d7c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="9d7c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7c6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d7c6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d7c6-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9d7c6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9d7c6-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d7c6-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="9d7c6-112">Attributes</span></span>  
  
|<span data-ttu-id="9d7c6-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="9d7c6-113">Attribute</span></span>|<span data-ttu-id="9d7c6-114">Description</span><span class="sxs-lookup"><span data-stu-id="9d7c6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d7c6-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="9d7c6-115">createNotificationOnConnection</span></span>|<span data-ttu-id="9d7c6-116">Spécifie si une notification est envoyée lors de la connexion.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="9d7c6-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="9d7c6-117">disablePayloadMasking</span></span>|<span data-ttu-id="9d7c6-118">Spécifie si le masquage WebSocket est désactivé.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="9d7c6-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="9d7c6-119">keepAliveInterval</span></span>|<span data-ttu-id="9d7c6-120">Spécifie l'intervalle de maintien de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="9d7c6-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="9d7c6-121">maxPendingConnections</span></span>|<span data-ttu-id="9d7c6-122">Spécifie le nombre maximal de connexions entrantes en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="9d7c6-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="9d7c6-123">receiveBufferSize</span></span>|<span data-ttu-id="9d7c6-124">Spécifie la taille de la mémoire tampon de réception.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="9d7c6-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="9d7c6-125">sendBufferSize</span></span>|<span data-ttu-id="9d7c6-126">Spécifie la taille de la mémoire tampon d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="9d7c6-127">subProtocol</span><span class="sxs-lookup"><span data-stu-id="9d7c6-127">subProtocol</span></span>|<span data-ttu-id="9d7c6-128">Spécifie le sous-protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="9d7c6-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="9d7c6-129">transportUsage</span></span>|<span data-ttu-id="9d7c6-130">Spécifie quand utiliser WebSocket.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="9d7c6-131">Attribut transportUsage</span><span class="sxs-lookup"><span data-stu-id="9d7c6-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="9d7c6-132">valeur</span><span class="sxs-lookup"><span data-stu-id="9d7c6-132">Value</span></span>|<span data-ttu-id="9d7c6-133">Description</span><span class="sxs-lookup"><span data-stu-id="9d7c6-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d7c6-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="9d7c6-134">WhenDuplex</span></span>|<span data-ttu-id="9d7c6-135">Utilisez le protocole WebSocket lorsque le contrat est en duplex.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="9d7c6-136">Always</span><span class="sxs-lookup"><span data-stu-id="9d7c6-136">Always</span></span>|<span data-ttu-id="9d7c6-137">Utilisez toujours le protocole WebSocket indépendamment du contrat.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="9d7c6-138">Never</span><span class="sxs-lookup"><span data-stu-id="9d7c6-138">Never</span></span>|<span data-ttu-id="9d7c6-139">N'utilisez jamais le protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d7c6-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9d7c6-140">Child Elements</span></span>  
 <span data-ttu-id="9d7c6-141">aucune.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d7c6-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9d7c6-142">Parent Elements</span></span>  
  
|<span data-ttu-id="9d7c6-143">Élément</span><span class="sxs-lookup"><span data-stu-id="9d7c6-143">Element</span></span>|<span data-ttu-id="9d7c6-144">Description</span><span class="sxs-lookup"><span data-stu-id="9d7c6-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d7c6-145">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9d7c6-145">\<netHttpBinding></span></span>|<span data-ttu-id="9d7c6-146">Spécifie le NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9d7c6-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d7c6-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d7c6-147">Example</span></span>  
 <span data-ttu-id="9d7c6-148">L’exemple suivant montre comment utiliser l’élément \<webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="9d7c6-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d7c6-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d7c6-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="9d7c6-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9d7c6-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9d7c6-151">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="9d7c6-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9d7c6-152">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="9d7c6-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9d7c6-153">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="9d7c6-153">\<binding></span></span>](bindings.md)
