---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 7fa72d233d6489ab6a2c534f69c66a55a22d0f59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429835"
---
# <a name="udpbinding"></a><span data-ttu-id="60ed6-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="60ed6-101">\<udpBinding></span></span>
<span data-ttu-id="60ed6-102">Élément de configuration utilisé pour configurer la liaison <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="60ed6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60ed6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="60ed6-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="60ed6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="60ed6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<></span><span class="sxs-lookup"><span data-stu-id="60ed6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="60ed6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**udpBinding >**</span><span class="sxs-lookup"><span data-stu-id="60ed6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ed6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60ed6-107">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60ed6-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="60ed6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="60ed6-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="60ed6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60ed6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="60ed6-110">Attributes</span></span>  
  
|<span data-ttu-id="60ed6-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="60ed6-111">Attribute</span></span>|<span data-ttu-id="60ed6-112">Description</span><span class="sxs-lookup"><span data-stu-id="60ed6-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="60ed6-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="60ed6-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="60ed6-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="60ed6-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="60ed6-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="60ed6-116">Valeur entière qui spécifie la longueur d'historique de messages dupliqués.</span><span class="sxs-lookup"><span data-stu-id="60ed6-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="60ed6-117">Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire de tampons des messages qui reçoivent des messages du canal.</span><span class="sxs-lookup"><span data-stu-id="60ed6-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="60ed6-118">La valeur par défaut est de 524 288 (0x80000) octets.</span><span class="sxs-lookup"><span data-stu-id="60ed6-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="60ed6-119">Entier qui spécifie la taille maximale, en octets, d’une mémoire tampon qui stocke des messages pendant qu’ils sont traités pour un point de terminaison configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="60ed6-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="60ed6-120">La valeur par défaut est de 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="60ed6-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="60ed6-121">Valeur entière qui spécifie le nombre maximal de messages reçus qui n'ont pas encore été supprimés dans la file d'entrée pour une instance de canal individuelle.</span><span class="sxs-lookup"><span data-stu-id="60ed6-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="60ed6-122">Entier positif qui définit la taille maximale du message, en octets, y compris les en-têtes d’un message pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="60ed6-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="60ed6-123">L'expéditeur reçoit une erreur SOAP si le message est trop grand pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="60ed6-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="60ed6-124">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="60ed6-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="60ed6-125">La valeur par défaut est 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="60ed6-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="60ed6-126">Valeur entière qui spécifie le nombre maximal de retransmissions de messages.</span><span class="sxs-lookup"><span data-stu-id="60ed6-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="60ed6-127">Valeur entière qui spécifie l'ID d'interface de multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="60ed6-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="60ed6-128">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="60ed6-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="60ed6-129">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="60ed6-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="60ed6-130">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="60ed6-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="60ed6-131">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="60ed6-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="60ed6-132"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="60ed6-132">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="60ed6-133">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-133">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="60ed6-134">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="60ed6-134">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="60ed6-135"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="60ed6-135">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="60ed6-136">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-136">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="60ed6-137">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="60ed6-137">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="60ed6-138"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="60ed6-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="60ed6-139">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="60ed6-140">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="60ed6-140">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="60ed6-141">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="60ed6-141">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="60ed6-142">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="60ed6-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="60ed6-143">-BigEndianUnicode : encodage BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="60ed6-143">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="60ed6-144">-Unicode : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="60ed6-144">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="60ed6-145">-UTF8 : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="60ed6-145">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="60ed6-146">Le jeu de caractères par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="60ed6-146">The default is UTF8.</span></span> <span data-ttu-id="60ed6-147">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-147">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="60ed6-148">Une valeur de période qui spécifie la durée de vie de la liaison.</span><span class="sxs-lookup"><span data-stu-id="60ed6-148">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60ed6-149">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="60ed6-149">Child Elements</span></span>  
  
|<span data-ttu-id="60ed6-150">Élément</span><span class="sxs-lookup"><span data-stu-id="60ed6-150">Element</span></span>|<span data-ttu-id="60ed6-151">Description</span><span class="sxs-lookup"><span data-stu-id="60ed6-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60ed6-152">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="60ed6-152">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="60ed6-153">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="60ed6-153">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="60ed6-154">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-154">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60ed6-155">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="60ed6-155">Parent Elements</span></span>  
  
|<span data-ttu-id="60ed6-156">Élément</span><span class="sxs-lookup"><span data-stu-id="60ed6-156">Element</span></span>|<span data-ttu-id="60ed6-157">Description</span><span class="sxs-lookup"><span data-stu-id="60ed6-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ed6-158">liaisons de \<></span><span class="sxs-lookup"><span data-stu-id="60ed6-158">\<bindings></span></span>](bindings.md)|<span data-ttu-id="60ed6-159">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="60ed6-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60ed6-160">Notes</span><span class="sxs-lookup"><span data-stu-id="60ed6-160">Remarks</span></span>  
 <span data-ttu-id="60ed6-161">UdpBinding permet aux services WCF de communiquer sur le transport UDP.</span><span class="sxs-lookup"><span data-stu-id="60ed6-161">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="60ed6-162">Cela permet l’échange de messages « incendie et oubli » où un client envoie un message à un service et n’attend aucune réponse.</span><span class="sxs-lookup"><span data-stu-id="60ed6-162">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60ed6-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="60ed6-163">Example</span></span>  
 <span data-ttu-id="60ed6-164">L’exemple suivant montre comment configurer le <xref:System.ServiceModel.UdpBinding> à l’aide de l’élément <`udpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="60ed6-164">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="60ed6-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60ed6-165">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="60ed6-166">Liaisons</span><span class="sxs-lookup"><span data-stu-id="60ed6-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="60ed6-167">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="60ed6-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="60ed6-168">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="60ed6-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="60ed6-169">liaison de \<></span><span class="sxs-lookup"><span data-stu-id="60ed6-169">\<binding></span></span>](bindings.md)
