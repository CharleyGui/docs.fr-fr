---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: f1be0997fc7b2b884c7ec90ea6a02ea0af96ab4c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431024"
---
# <a name="basichttpbinding"></a><span data-ttu-id="0565f-101">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0565f-101">\<basicHttpBinding></span></span>
<span data-ttu-id="0565f-102">Représente une liaison qu’un service Windows Communication Foundation (WCF) peut utiliser pour configurer et exposer des points de terminaison capables de communiquer avec des clients et services web basés sur ASMX, ainsi qu’avec d’autres services conformes au profil WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="0565f-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
<span data-ttu-id="0565f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0565f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0565f-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0565f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0565f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<></span><span class="sxs-lookup"><span data-stu-id="0565f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0565f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**basicHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="0565f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0565f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0565f-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
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
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0565f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0565f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0565f-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0565f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0565f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0565f-110">Attributes</span></span>  
  
|<span data-ttu-id="0565f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="0565f-111">Attribute</span></span>|<span data-ttu-id="0565f-112">Description</span><span class="sxs-lookup"><span data-stu-id="0565f-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="0565f-113">Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes.</span><span class="sxs-lookup"><span data-stu-id="0565f-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="0565f-114">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="0565f-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0565f-115">Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies.</span><span class="sxs-lookup"><span data-stu-id="0565f-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="0565f-116">De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.</span><span class="sxs-lookup"><span data-stu-id="0565f-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="0565f-117">Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="0565f-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="0565f-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="0565f-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0565f-119">Une ressource Internet est locale si elle dispose d'une adresse locale.</span><span class="sxs-lookup"><span data-stu-id="0565f-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="0565f-120">Une adresse locale est une adresse sur le même ordinateur, le réseau local ou l’intranet et est identifiée, syntaxiquement, par l’absence de point (.) comme dans les URI « http://webserver/» et « http://localhost/».</span><span class="sxs-lookup"><span data-stu-id="0565f-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="0565f-121">La définition de cet attribut détermine si les points de terminaison configurés avec le BasicHttpBinding utilisent le serveur proxy lors de l'accès aux ressources locales.</span><span class="sxs-lookup"><span data-stu-id="0565f-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="0565f-122">Si cet attribut est `true`, les demandes adressées à des ressources Internet locales n'utilisent pas le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="0565f-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="0565f-123">Utilisez le nom d'hôte (plutôt que localhost) si vous souhaitez que les clients traversent un proxy lorsqu'ils parlent aux services sur le même ordinateur et que cet attribut a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0565f-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="0565f-124">Si cet attribut est `false`, toutes les demandes Internet sont exécutées par le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="0565f-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="0565f-125"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="0565f-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0565f-126">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0565f-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0565f-127">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0565f-127">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="0565f-128">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="0565f-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0565f-129">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="0565f-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0565f-130">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="0565f-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="0565f-131">Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire de tampons des messages qui reçoivent des messages du canal.</span><span class="sxs-lookup"><span data-stu-id="0565f-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="0565f-132">La valeur par défaut est de 524 288 (0x80000) octets.</span><span class="sxs-lookup"><span data-stu-id="0565f-132">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="0565f-133">Le gestionnaire de tampons réduit le coût d'utilisation des mémoires tampons à l'aide d'un pool de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="0565f-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="0565f-134">Les mémoires tampons sont requises par le service pour traiter des messages lorsqu'ils sortent du canal.</span><span class="sxs-lookup"><span data-stu-id="0565f-134">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="0565f-135">S’il n’y a pas mémoire suffisante dans le pool de mémoires tampons pour traiter la charge de message, le gestionnaire de mémoires tampons doit allouer de la mémoire additionnelle dans le segment de mémoire CLR, ce qui augmente le traitement du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0565f-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="0565f-136">Une allocation importante de mémoire issue du tas de garbage CLR indique que la taille du pool de mémoires tampons est insuffisante et qu'il est possible d'améliorer les performances en augmentant la limite spécifiée par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="0565f-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="0565f-137">Entier qui spécifie la taille maximale, en octets, d’une mémoire tampon qui stocke des messages pendant qu’ils sont traités pour un point de terminaison configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="0565f-138">La valeur par défaut est de 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="0565f-138">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="0565f-139">Entier positif qui définit la taille maximale du message, en octets, y compris les en-têtes d’un message pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0565f-140">L'expéditeur reçoit une erreur SOAP si le message est trop grand pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="0565f-140">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="0565f-141">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="0565f-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0565f-142">La valeur par défaut est 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="0565f-142">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="0565f-143">Définit l'encodeur utilisé pour encoder le message SOAP.</span><span class="sxs-lookup"><span data-stu-id="0565f-143">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="0565f-144">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0565f-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0565f-145">-Text : utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="0565f-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="0565f-146">-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="0565f-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="0565f-147">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="0565f-147">The default is Text.</span></span> <span data-ttu-id="0565f-148">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="0565f-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="0565f-149">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0565f-150">Cette valeur doit être unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="0565f-150">This value should be unique among bindings of the same type.</span></span> <span data-ttu-id="0565f-151">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="0565f-151">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0565f-152">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0565f-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="0565f-153"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="0565f-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0565f-154">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0565f-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0565f-155">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0565f-155">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="0565f-156">URI qui contient l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="0565f-156">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="0565f-157">Si `useSystemWebProxy` a la valeur `true` ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="0565f-157">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="0565f-158">La valeur par défaut est `null`.</span><span class="sxs-lookup"><span data-stu-id="0565f-158">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0565f-159"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="0565f-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0565f-160">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0565f-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0565f-161">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0565f-161">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0565f-162"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="0565f-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0565f-163">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0565f-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0565f-164">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0565f-164">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="0565f-165">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0565f-166">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0565f-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0565f-167">-BigEndianUnicode : encodage BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="0565f-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0565f-168">-Unicode : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="0565f-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0565f-169">-UTF8 : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="0565f-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0565f-170">Le jeu de caractères par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="0565f-170">The default is UTF8.</span></span> <span data-ttu-id="0565f-171">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="0565f-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="0565f-172">Valeur <xref:System.ServiceModel.TransferMode> valide qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu dans une demande ou une réponse.</span><span class="sxs-lookup"><span data-stu-id="0565f-172">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="0565f-173">Valeur booléenne qui spécifie si le proxy HTTP du système, configuré automatiquement, doit être utilisé, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="0565f-173">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="0565f-174">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="0565f-174">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0565f-175">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0565f-175">Child Elements</span></span>  
  
|<span data-ttu-id="0565f-176">Élément</span><span class="sxs-lookup"><span data-stu-id="0565f-176">Element</span></span>|<span data-ttu-id="0565f-177">Description</span><span class="sxs-lookup"><span data-stu-id="0565f-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0565f-178">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="0565f-178">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="0565f-179">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="0565f-180">Cet élément est de type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0565f-180">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="0565f-181">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0565f-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="0565f-182">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0565f-183">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0565f-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0565f-184">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0565f-184">Parent Elements</span></span>  
  
|<span data-ttu-id="0565f-185">Élément</span><span class="sxs-lookup"><span data-stu-id="0565f-185">Element</span></span>|<span data-ttu-id="0565f-186">Description</span><span class="sxs-lookup"><span data-stu-id="0565f-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0565f-187">liaisons de \<></span><span class="sxs-lookup"><span data-stu-id="0565f-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0565f-188">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0565f-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0565f-189">Notes</span><span class="sxs-lookup"><span data-stu-id="0565f-189">Remarks</span></span>  
 <span data-ttu-id="0565f-190">Le BasicHttpBinding utilise HTTP en guise de transport pour envoyer des messages SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="0565f-190">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="0565f-191">Un service peut utiliser cette liaison pour exposer des points de terminaison qui se conforment à WS-I BP 1.1, tels que ceux que les clients ASMX consomment.</span><span class="sxs-lookup"><span data-stu-id="0565f-191">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="0565f-192">De la même façon, un client peut utiliser le BasicHttpBinding pour communiquer avec les services qui exposent des points de terminaison qui se conforment à WS-I BP 1.1, tel que les services Web ASMX ou les services configurés avec le BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="0565f-192">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="0565f-193">La sécurité est désactivée par défaut, mais peut être ajoutée en affectant à l’attribut mode de l’élément enfant [\<security >](security-of-basichttpbinding.md) la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="0565f-193">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="0565f-194">Par défaut, il utilise un encodage de message "Texte" et un encodage texte UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0565f-194">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0565f-195">Exemple</span><span class="sxs-lookup"><span data-stu-id="0565f-195">Example</span></span>  
 <span data-ttu-id="0565f-196">L'exemple suivant montre l'utilisation de <xref:System.ServiceModel.BasicHttpBinding> qui fournit la communication HTTP et l'interopérabilité maximale avec les services Web de première et seconde génération.</span><span class="sxs-lookup"><span data-stu-id="0565f-196">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="0565f-197">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="0565f-197">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0565f-198">Le type de liaison est spécifié à l’aide de l’attribut `binding` de l’élément `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="0565f-198">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="0565f-199">Si vous souhaitez configurer la liaison de base et modifier certains de ses paramètres, vous devez définir une configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-199">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="0565f-200">Le point de terminaison doit référencer la configuration de liaison par nom en utilisant l’attribut `bindingConfiguration` de l’élément `<endpoint>`, comme présenté dans le code de configuration suivant pour le service.</span><span class="sxs-lookup"><span data-stu-id="0565f-200">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="0565f-201">Exemple</span><span class="sxs-lookup"><span data-stu-id="0565f-201">Example</span></span>  
 <span data-ttu-id="0565f-202">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="0565f-202">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0565f-203">Les fonctionnalités de l’exemple précédent peuvent être obtenues en supprimant le bindingConfiguration de l’adresse du point de terminaison et le nom de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0565f-203">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="0565f-204">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0565f-204">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0565f-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0565f-205">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="0565f-206">Liaisons</span><span class="sxs-lookup"><span data-stu-id="0565f-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0565f-207">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="0565f-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0565f-208">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0565f-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0565f-209">liaison de \<></span><span class="sxs-lookup"><span data-stu-id="0565f-209">\<binding></span></span>](bindings.md)
