---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 80784f40130e572ae374bd9b26e701360dbfcaa5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399134"
---
# <a name="websocketsettings"></a><span data-ttu-id="fe99c-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="fe99c-101">\<webSocketSettings></span></span>
<span data-ttu-id="fe99c-102">Élément de configuration utilisé pour spécifier des paramètres WebSocket.</span><span class="sxs-lookup"><span data-stu-id="fe99c-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="fe99c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe99c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe99c-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fe99c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fe99c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="fe99c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="fe99c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fe99c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="fe99c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="fe99c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="fe99c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="fe99c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe99c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe99c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe99c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fe99c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe99c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fe99c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe99c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="fe99c-112">Attributes</span></span>  
  
|<span data-ttu-id="fe99c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="fe99c-113">Attribute</span></span>|<span data-ttu-id="fe99c-114">Description</span><span class="sxs-lookup"><span data-stu-id="fe99c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe99c-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="fe99c-115">createNotificationOnConnection</span></span>|<span data-ttu-id="fe99c-116">Spécifie si une notification est envoyée lors de la connexion.</span><span class="sxs-lookup"><span data-stu-id="fe99c-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="fe99c-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="fe99c-117">disablePayloadMasking</span></span>|<span data-ttu-id="fe99c-118">Spécifie si le masquage WebSocket est désactivé.</span><span class="sxs-lookup"><span data-stu-id="fe99c-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="fe99c-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="fe99c-119">keepAliveInterval</span></span>|<span data-ttu-id="fe99c-120">Spécifie l'intervalle de maintien de l'activité.</span><span class="sxs-lookup"><span data-stu-id="fe99c-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="fe99c-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="fe99c-121">maxPendingConnections</span></span>|<span data-ttu-id="fe99c-122">Spécifie le nombre maximal de connexions entrantes en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="fe99c-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="fe99c-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="fe99c-123">receiveBufferSize</span></span>|<span data-ttu-id="fe99c-124">Spécifie la taille de la mémoire tampon de réception.</span><span class="sxs-lookup"><span data-stu-id="fe99c-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="fe99c-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="fe99c-125">sendBufferSize</span></span>|<span data-ttu-id="fe99c-126">Spécifie la taille de la mémoire tampon d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fe99c-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="fe99c-127">subProtocol</span><span class="sxs-lookup"><span data-stu-id="fe99c-127">subProtocol</span></span>|<span data-ttu-id="fe99c-128">Spécifie le sous-protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="fe99c-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="fe99c-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="fe99c-129">transportUsage</span></span>|<span data-ttu-id="fe99c-130">Spécifie quand utiliser WebSocket.</span><span class="sxs-lookup"><span data-stu-id="fe99c-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="fe99c-131">Attribut transportUsage</span><span class="sxs-lookup"><span data-stu-id="fe99c-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="fe99c-132">`Value`</span><span class="sxs-lookup"><span data-stu-id="fe99c-132">Value</span></span>|<span data-ttu-id="fe99c-133">Description</span><span class="sxs-lookup"><span data-stu-id="fe99c-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe99c-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="fe99c-134">WhenDuplex</span></span>|<span data-ttu-id="fe99c-135">Utilisez le protocole WebSocket lorsque le contrat est en duplex.</span><span class="sxs-lookup"><span data-stu-id="fe99c-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="fe99c-136">Always</span><span class="sxs-lookup"><span data-stu-id="fe99c-136">Always</span></span>|<span data-ttu-id="fe99c-137">Utilisez toujours le protocole WebSocket indépendamment du contrat.</span><span class="sxs-lookup"><span data-stu-id="fe99c-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="fe99c-138">Never</span><span class="sxs-lookup"><span data-stu-id="fe99c-138">Never</span></span>|<span data-ttu-id="fe99c-139">N'utilisez jamais le protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="fe99c-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe99c-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fe99c-140">Child Elements</span></span>  
 <span data-ttu-id="fe99c-141">Aucun</span><span class="sxs-lookup"><span data-stu-id="fe99c-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe99c-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fe99c-142">Parent Elements</span></span>  
  
|<span data-ttu-id="fe99c-143">Élément</span><span class="sxs-lookup"><span data-stu-id="fe99c-143">Element</span></span>|<span data-ttu-id="fe99c-144">Description</span><span class="sxs-lookup"><span data-stu-id="fe99c-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe99c-145">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="fe99c-145">\<netHttpBinding></span></span>|<span data-ttu-id="fe99c-146">Spécifie le NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fe99c-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe99c-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="fe99c-147">Example</span></span>  
 <span data-ttu-id="fe99c-148">L’exemple suivant montre comment utiliser l' \<élément webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="fe99c-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe99c-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe99c-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="fe99c-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="fe99c-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fe99c-151">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="fe99c-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fe99c-152">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="fe99c-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fe99c-153">\<binding></span><span class="sxs-lookup"><span data-stu-id="fe99c-153">\<binding></span></span>](../../../misc/binding.md)
