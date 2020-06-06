---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732553"
---
# \<webSocketSettings>
<span data-ttu-id="2528e-101">Élément de configuration utilisé pour spécifier des paramètres WebSocket.</span><span class="sxs-lookup"><span data-stu-id="2528e-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="2528e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2528e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2528e-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2528e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2528e-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2528e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2528e-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="2528e-105">Attributes</span></span>  
  
|<span data-ttu-id="2528e-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="2528e-106">Attribute</span></span>|<span data-ttu-id="2528e-107">Description</span><span class="sxs-lookup"><span data-stu-id="2528e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2528e-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="2528e-108">createNotificationOnConnection</span></span>|<span data-ttu-id="2528e-109">Spécifie si une notification est envoyée lors de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2528e-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="2528e-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="2528e-110">disablePayloadMasking</span></span>|<span data-ttu-id="2528e-111">Spécifie si le masquage WebSocket est désactivé.</span><span class="sxs-lookup"><span data-stu-id="2528e-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="2528e-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="2528e-112">keepAliveInterval</span></span>|<span data-ttu-id="2528e-113">Spécifie l'intervalle de maintien de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2528e-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="2528e-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="2528e-114">maxPendingConnections</span></span>|<span data-ttu-id="2528e-115">Spécifie le nombre maximal de connexions entrantes en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="2528e-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="2528e-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="2528e-116">receiveBufferSize</span></span>|<span data-ttu-id="2528e-117">Spécifie la taille de la mémoire tampon de réception.</span><span class="sxs-lookup"><span data-stu-id="2528e-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="2528e-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="2528e-118">sendBufferSize</span></span>|<span data-ttu-id="2528e-119">Spécifie la taille de la mémoire tampon d'envoi.</span><span class="sxs-lookup"><span data-stu-id="2528e-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="2528e-120">subProtocol</span><span class="sxs-lookup"><span data-stu-id="2528e-120">subProtocol</span></span>|<span data-ttu-id="2528e-121">Spécifie le sous-protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="2528e-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="2528e-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="2528e-122">transportUsage</span></span>|<span data-ttu-id="2528e-123">Spécifie quand utiliser WebSocket.</span><span class="sxs-lookup"><span data-stu-id="2528e-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="2528e-124">Attribut transportUsage</span><span class="sxs-lookup"><span data-stu-id="2528e-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="2528e-125">Valeur</span><span class="sxs-lookup"><span data-stu-id="2528e-125">Value</span></span>|<span data-ttu-id="2528e-126">Description</span><span class="sxs-lookup"><span data-stu-id="2528e-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2528e-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="2528e-127">WhenDuplex</span></span>|<span data-ttu-id="2528e-128">Utilisez le protocole WebSocket lorsque le contrat est en duplex.</span><span class="sxs-lookup"><span data-stu-id="2528e-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="2528e-129">Always (Toujours)</span><span class="sxs-lookup"><span data-stu-id="2528e-129">Always</span></span>|<span data-ttu-id="2528e-130">Utilisez toujours le protocole WebSocket indépendamment du contrat.</span><span class="sxs-lookup"><span data-stu-id="2528e-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="2528e-131">Jamais</span><span class="sxs-lookup"><span data-stu-id="2528e-131">Never</span></span>|<span data-ttu-id="2528e-132">N'utilisez jamais le protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="2528e-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2528e-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2528e-133">Child Elements</span></span>  
 <span data-ttu-id="2528e-134">Aucune</span><span class="sxs-lookup"><span data-stu-id="2528e-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2528e-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2528e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2528e-136">Élément</span><span class="sxs-lookup"><span data-stu-id="2528e-136">Element</span></span>|<span data-ttu-id="2528e-137">Description</span><span class="sxs-lookup"><span data-stu-id="2528e-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="2528e-138">Spécifie le NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2528e-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2528e-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="2528e-139">Example</span></span>  
 <span data-ttu-id="2528e-140">L'exemple suivant montre comment utiliser l'élément \<webSocketSettings>.</span><span class="sxs-lookup"><span data-stu-id="2528e-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2528e-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2528e-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="2528e-142">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2528e-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2528e-143">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="2528e-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2528e-144">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="2528e-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
