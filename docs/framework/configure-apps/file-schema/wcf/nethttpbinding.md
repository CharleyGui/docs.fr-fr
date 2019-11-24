---
title: <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: 537cbd03e55615bcda2a0ab8e41a171e22a94344
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430857"
---
# <a name="nethttpbinding"></a><span data-ttu-id="0447f-101">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0447f-101">\<netHttpBinding></span></span>
<span data-ttu-id="0447f-102">Représente une liaison qu’un service Windows Communication Foundation (WCF) peut utiliser pour configurer et exposer des points de terminaison qui sont en mesure de communiquer sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="0447f-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTP.</span></span> <span data-ttu-id="0447f-103">Lorsqu'elle est utilisée avec un contrat duplex, WebSocket est utilisé, sinon HTTP est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0447f-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTP will be used.</span></span>  
  
<span data-ttu-id="0447f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0447f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0447f-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0447f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0447f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<></span><span class="sxs-lookup"><span data-stu-id="0447f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0447f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**netHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="0447f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0447f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0447f-108">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="0447f-109">Type</span><span class="sxs-lookup"><span data-stu-id="0447f-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0447f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0447f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0447f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0447f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0447f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0447f-112">Attributes</span></span>  
  
|<span data-ttu-id="0447f-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="0447f-113">Attribute</span></span>|<span data-ttu-id="0447f-114">Description</span><span class="sxs-lookup"><span data-stu-id="0447f-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="0447f-115">Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes.</span><span class="sxs-lookup"><span data-stu-id="0447f-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="0447f-116">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="0447f-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0447f-117">Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies.</span><span class="sxs-lookup"><span data-stu-id="0447f-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="0447f-118">De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.</span><span class="sxs-lookup"><span data-stu-id="0447f-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="0447f-119">Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="0447f-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="0447f-120">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="0447f-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0447f-121">Une ressource Internet est locale si elle dispose d'une adresse locale.</span><span class="sxs-lookup"><span data-stu-id="0447f-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="0447f-122">Une adresse locale est une adresse sur le même ordinateur, le réseau local ou l’intranet et est identifiée, syntaxiquement, par l’absence de point (.) comme dans les URI « http://webserver/» et « http://localhost/».</span><span class="sxs-lookup"><span data-stu-id="0447f-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="0447f-123">La définition de cet attribut détermine si les points de terminaison configurés avec le BasicHttpBinding utilisent le serveur proxy lors de l'accès aux ressources locales.</span><span class="sxs-lookup"><span data-stu-id="0447f-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="0447f-124">Si cet attribut est `true`, les demandes adressées à des ressources Internet locales n'utilisent pas le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="0447f-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="0447f-125">Utilisez le nom d'hôte (plutôt que localhost) si vous souhaitez que les clients traversent un proxy lorsqu'ils parlent aux services sur le même ordinateur et que cet attribut a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0447f-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="0447f-126">Si cet attribut est `false`, toutes les demandes Internet sont exécutées par le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="0447f-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="0447f-127"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="0447f-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0447f-128">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0447f-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0447f-129">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0447f-129">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="0447f-130">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="0447f-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0447f-131">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="0447f-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0447f-132">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="0447f-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="0447f-133">Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire de tampons des messages qui reçoivent des messages du canal.</span><span class="sxs-lookup"><span data-stu-id="0447f-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="0447f-134">La valeur par défaut est de 524 288 (0x80000) octets.</span><span class="sxs-lookup"><span data-stu-id="0447f-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="0447f-135">Le gestionnaire de tampons réduit le coût d'utilisation des mémoires tampons à l'aide d'un pool de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="0447f-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="0447f-136">Les mémoires tampons sont requises par le service pour traiter des messages lorsqu'ils sortent du canal.</span><span class="sxs-lookup"><span data-stu-id="0447f-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="0447f-137">S’il n’y a pas mémoire suffisante dans le pool de mémoires tampons pour traiter la charge de message, le gestionnaire de mémoires tampons doit allouer de la mémoire additionnelle dans le segment de mémoire CLR, ce qui augmente le traitement du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0447f-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="0447f-138">Une allocation importante de mémoire issue du tas de garbage CLR indique que la taille du pool de mémoires tampons est insuffisante et qu'il est possible d'améliorer les performances en augmentant la limite spécifiée par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="0447f-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="0447f-139">Entier qui spécifie la taille maximale, en octets, d’une mémoire tampon qui stocke des messages pendant qu’ils sont traités pour un point de terminaison configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="0447f-140">La valeur par défaut est de 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="0447f-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="0447f-141">Entier positif qui définit la taille maximale du message, en octets, y compris les en-têtes d’un message pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0447f-142">L'expéditeur reçoit une erreur SOAP si le message est trop grand pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="0447f-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="0447f-143">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="0447f-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0447f-144">La valeur par défaut est 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="0447f-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="0447f-145">Définit l'encodeur utilisé pour encoder le message SOAP.</span><span class="sxs-lookup"><span data-stu-id="0447f-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="0447f-146">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0447f-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0447f-147">-Text : utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="0447f-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="0447f-148">-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="0447f-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="0447f-149">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="0447f-149">The default is Text.</span></span> <span data-ttu-id="0447f-150">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="0447f-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="0447f-151">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0447f-152">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0447f-153">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="0447f-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0447f-154">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0447f-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="0447f-155"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="0447f-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0447f-156">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0447f-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0447f-157">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0447f-157">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="0447f-158">URI qui contient l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="0447f-158">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="0447f-159">Si `useSystemWebProxy` a la valeur `true` ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="0447f-159">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="0447f-160">La valeur par défaut est `null`.</span><span class="sxs-lookup"><span data-stu-id="0447f-160">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0447f-161"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="0447f-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0447f-162">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0447f-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0447f-163">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0447f-163">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0447f-164"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="0447f-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0447f-165">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0447f-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0447f-166">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0447f-166">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="0447f-167">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-167">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0447f-168">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0447f-168">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0447f-169">-BigEndianUnicode : encodage BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="0447f-169">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0447f-170">-Unicode : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="0447f-170">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0447f-171">-UTF8 : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="0447f-171">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0447f-172">La valeur par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="0447f-172">The default is UTF8.</span></span> <span data-ttu-id="0447f-173">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="0447f-173">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="0447f-174">Valeur <xref:System.ServiceModel.TransferMode> valide qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu dans une demande ou une réponse.</span><span class="sxs-lookup"><span data-stu-id="0447f-174">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="0447f-175">Valeur booléenne qui spécifie si le proxy HTTP du système, configuré automatiquement, doit être utilisé, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="0447f-175">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="0447f-176">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="0447f-176">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="0447f-177">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0447f-177">Child Elements</span></span>  
  
|<span data-ttu-id="0447f-178">Élément</span><span class="sxs-lookup"><span data-stu-id="0447f-178">Element</span></span>|<span data-ttu-id="0447f-179">Description</span><span class="sxs-lookup"><span data-stu-id="0447f-179">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0447f-180">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="0447f-180">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="0447f-181">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-181">Defines the security settings for the binding.</span></span> <span data-ttu-id="0447f-182">Cet élément est de type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0447f-182">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="0447f-183">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0447f-183">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="0447f-184">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0447f-185">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0447f-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0447f-186">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0447f-186">Parent Elements</span></span>  
  
|<span data-ttu-id="0447f-187">Élément</span><span class="sxs-lookup"><span data-stu-id="0447f-187">Element</span></span>|<span data-ttu-id="0447f-188">Description</span><span class="sxs-lookup"><span data-stu-id="0447f-188">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0447f-189">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0447f-189">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0447f-190">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0447f-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0447f-191">Notes</span><span class="sxs-lookup"><span data-stu-id="0447f-191">Remarks</span></span>  
 <span data-ttu-id="0447f-192">Le NetHttpBinding utilise HTTP en guise de transport pour envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="0447f-192">The NetHttpBinding uses HTTP as the transport for sending messages.</span></span> <span data-ttu-id="0447f-193">Lorsqu'elle est utilisée avec un contrat duplex, WebSocket est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0447f-193">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="0447f-194">Lorsqu'elle est utilisée avec un contrat de demande-réponse, NetHttpBinding se comporte comme un BasicHttpBinding avec un encodeur binaire.</span><span class="sxs-lookup"><span data-stu-id="0447f-194">When used with a request-reply contract NetHttpBinding will behave like a BasicHttpBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="0447f-195">La sécurité est désactivée par défaut, mais peut être ajoutée en affectant à l’attribut mode de l’élément enfant [\<security >](security-of-basichttpbinding.md) la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="0447f-195">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="0447f-196">Par défaut, il utilise un encodage de message "Texte" et un encodage texte UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0447f-196">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0447f-197">Exemple</span><span class="sxs-lookup"><span data-stu-id="0447f-197">Example</span></span>  
 <span data-ttu-id="0447f-198">L'exemple suivant montre l'utilisation de <xref:System.ServiceModel.NetHttpBinding> qui fournit la communication HTTP et l'interopérabilité maximale avec les services Web de première et seconde génération.</span><span class="sxs-lookup"><span data-stu-id="0447f-198">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="0447f-199">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="0447f-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0447f-200">Le type de liaison est spécifié à l’aide de l’attribut `binding` de l’élément `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="0447f-200">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="0447f-201">Si vous souhaitez configurer la liaison de base et modifier certains de ses paramètres, vous devez définir une configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-201">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="0447f-202">Le point de terminaison doit référencer la configuration de liaison par nom en utilisant l’attribut `bindingConfiguration` de l’élément `<endpoint>`, comme présenté dans le code de configuration suivant pour le service.</span><span class="sxs-lookup"><span data-stu-id="0447f-202">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="0447f-203">Exemple</span><span class="sxs-lookup"><span data-stu-id="0447f-203">Example</span></span>  
 <span data-ttu-id="0447f-204">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="0447f-204">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0447f-205">Les fonctionnalités de l’exemple précédent peuvent être obtenues en supprimant le bindingConfiguration de l’adresse du point de terminaison et le nom de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0447f-205">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="0447f-206">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0447f-206">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0447f-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0447f-207">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="0447f-208">Liaisons</span><span class="sxs-lookup"><span data-stu-id="0447f-208">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0447f-209">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="0447f-209">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0447f-210">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0447f-210">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0447f-211">\<binding></span><span class="sxs-lookup"><span data-stu-id="0447f-211">\<binding></span></span>](bindings.md)
