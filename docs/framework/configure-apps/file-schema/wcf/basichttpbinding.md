---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 2ae8a9d2ad7bf3607394e65570b8961fd2d58606
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919880"
---
# <a name="basichttpbinding"></a><span data-ttu-id="a73e5-101">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a73e5-101">\<basicHttpBinding></span></span>
<span data-ttu-id="a73e5-102">Représente une liaison qu’un service Windows Communication Foundation (WCF) peut utiliser pour configurer et exposer des points de terminaison capables de communiquer avec des clients et services web basés sur ASMX, ainsi qu’avec d’autres services conformes au profil WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="a73e5-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="a73e5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a73e5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a73e5-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a73e5-104">\<bindings></span></span>  
<span data-ttu-id="a73e5-105">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a73e5-105">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73e5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a73e5-106">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           envelopeVersion="None/Soap11/Soap12"
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a73e5-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a73e5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a73e5-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a73e5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a73e5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a73e5-109">Attributes</span></span>  
  
|<span data-ttu-id="a73e5-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a73e5-110">Attribute</span></span>|<span data-ttu-id="a73e5-111">Description</span><span class="sxs-lookup"><span data-stu-id="a73e5-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="a73e5-112">Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes.</span><span class="sxs-lookup"><span data-stu-id="a73e5-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="a73e5-113">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="a73e5-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a73e5-114">Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies.</span><span class="sxs-lookup"><span data-stu-id="a73e5-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="a73e5-115">De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.</span><span class="sxs-lookup"><span data-stu-id="a73e5-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="a73e5-116">Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="a73e5-116">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="a73e5-117">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="a73e5-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a73e5-118">Une ressource Internet est locale si elle dispose d'une adresse locale.</span><span class="sxs-lookup"><span data-stu-id="a73e5-118">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="a73e5-119">Une adresse locale est une adresse sur le même ordinateur, le réseau local ou l’intranet et est identifiée, syntaxiquement, par l’absence de point (.) comme dans les URI http://webserver/ «» et http://localhost/ «».</span><span class="sxs-lookup"><span data-stu-id="a73e5-119">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="a73e5-120">La définition de cet attribut détermine si les points de terminaison configurés avec le BasicHttpBinding utilisent le serveur proxy lors de l'accès aux ressources locales.</span><span class="sxs-lookup"><span data-stu-id="a73e5-120">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="a73e5-121">Si cet attribut est `true`, les demandes adressées à des ressources Internet locales n'utilisent pas le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="a73e5-121">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="a73e5-122">Utilisez le nom d'hôte (plutôt que localhost) si vous souhaitez que les clients traversent un proxy lorsqu'ils parlent aux services sur le même ordinateur et que cet attribut a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="a73e5-122">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="a73e5-123">Si cet attribut est `false`, toutes les demandes Internet sont exécutées par le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="a73e5-123">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="a73e5-124"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="a73e5-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a73e5-125">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a73e5-126">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a73e5-126">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="a73e5-127">Spécifie la version de SOAP utilisée pour les messages traités par cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-127">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="a73e5-128">La seule valeur valide est Soap11.</span><span class="sxs-lookup"><span data-stu-id="a73e5-128">The only valid value is Soap11.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="a73e5-129">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="a73e5-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="a73e5-130">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="a73e5-130">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a73e5-131">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="a73e5-131">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="a73e5-132">Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire de tampons des messages qui reçoivent des messages du canal.</span><span class="sxs-lookup"><span data-stu-id="a73e5-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="a73e5-133">La valeur par défaut est de 524 288 (0x80000) octets.</span><span class="sxs-lookup"><span data-stu-id="a73e5-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="a73e5-134">Le gestionnaire de tampons réduit le coût d'utilisation des mémoires tampons à l'aide d'un pool de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="a73e5-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="a73e5-135">Les mémoires tampons sont requises par le service pour traiter des messages lorsqu'ils sortent du canal.</span><span class="sxs-lookup"><span data-stu-id="a73e5-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="a73e5-136">S’il n’y a pas mémoire suffisante dans le pool de mémoires tampons pour traiter la charge de message, le gestionnaire de mémoires tampons doit allouer de la mémoire additionnelle dans le segment de mémoire CLR, ce qui augmente le traitement du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a73e5-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="a73e5-137">Une allocation importante de mémoire issue du tas de garbage CLR indique que la taille du pool de mémoires tampons est insuffisante et qu'il est possible d'améliorer les performances en augmentant la limite spécifiée par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="a73e5-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="a73e5-138">Entier qui spécifie la taille maximale, en octets, d’une mémoire tampon qui stocke des messages pendant qu’ils sont traités pour un point de terminaison configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="a73e5-139">La valeur par défaut est de 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="a73e5-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="a73e5-140">Entier positif qui définit la taille maximale du message, en octets, y compris les en-têtes d’un message pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a73e5-141">L'expéditeur reçoit une erreur SOAP si le message est trop grand pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="a73e5-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="a73e5-142">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="a73e5-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a73e5-143">La valeur par défaut est 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="a73e5-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="a73e5-144">Définit l'encodeur utilisé pour encoder le message SOAP.</span><span class="sxs-lookup"><span data-stu-id="a73e5-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="a73e5-145">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a73e5-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a73e5-146">Financière Utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="a73e5-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="a73e5-147">MTOM Utilisez un encodeur de transmission de message (MTOM) message transmission Organization 1,0.</span><span class="sxs-lookup"><span data-stu-id="a73e5-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="a73e5-148">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="a73e5-148">The default is Text.</span></span> <span data-ttu-id="a73e5-149">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="a73e5-150">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a73e5-151">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a73e5-152">Chaque liaison porte un `name` et a un attribut `namespace` qui l’identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="a73e5-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="a73e5-153">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="a73e5-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="a73e5-154">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="a73e5-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a73e5-155">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a73e5-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="a73e5-156">Spécifie l'espace de noms XML de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="a73e5-157">La valeur par défaut est « http://tempuri.org/Bindings  ».</span><span class="sxs-lookup"><span data-stu-id="a73e5-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="a73e5-158">Chaque liaison porte un `name` et a un attribut `namespace` qui l’identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="a73e5-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="a73e5-159"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="a73e5-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a73e5-160">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a73e5-161">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a73e5-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="a73e5-162">URI qui contient l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="a73e5-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="a73e5-163">Si `useSystemWebProxy` a la valeur `true` ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="a73e5-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="a73e5-164">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="a73e5-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a73e5-165"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="a73e5-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a73e5-166">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a73e5-167">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a73e5-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a73e5-168"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a73e5-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a73e5-169">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a73e5-170">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a73e5-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="a73e5-171">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a73e5-172">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a73e5-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a73e5-173">BigEndianUnicode Encodage BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="a73e5-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="a73e5-174">Unicode encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="a73e5-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="a73e5-175">UTF8 encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="a73e5-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a73e5-176">La valeur par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="a73e5-176">The default is UTF8.</span></span> <span data-ttu-id="a73e5-177">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="a73e5-178">Valeur <xref:System.ServiceModel.TransferMode> valide qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu dans une demande ou une réponse.</span><span class="sxs-lookup"><span data-stu-id="a73e5-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="a73e5-179">Valeur booléenne qui spécifie si le proxy HTTP du système, configuré automatiquement, doit être utilisé, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="a73e5-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="a73e5-180">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="a73e5-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a73e5-181">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a73e5-181">Child Elements</span></span>  
  
|<span data-ttu-id="a73e5-182">Élément</span><span class="sxs-lookup"><span data-stu-id="a73e5-182">Element</span></span>|<span data-ttu-id="a73e5-183">Description</span><span class="sxs-lookup"><span data-stu-id="a73e5-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a73e5-184">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="a73e5-184">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="a73e5-185">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="a73e5-186">Cet élément est de type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="a73e5-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a73e5-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a73e5-188">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a73e5-189">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a73e5-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a73e5-190">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a73e5-190">Parent Elements</span></span>  
  
|<span data-ttu-id="a73e5-191">Élément</span><span class="sxs-lookup"><span data-stu-id="a73e5-191">Element</span></span>|<span data-ttu-id="a73e5-192">Description</span><span class="sxs-lookup"><span data-stu-id="a73e5-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a73e5-193">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a73e5-193">\<bindings></span></span>](bindings.md)|<span data-ttu-id="a73e5-194">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a73e5-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a73e5-195">Notes</span><span class="sxs-lookup"><span data-stu-id="a73e5-195">Remarks</span></span>  
 <span data-ttu-id="a73e5-196">Le BasicHttpBinding utilise HTTP en guise de transport pour envoyer des messages SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="a73e5-196">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="a73e5-197">Un service peut utiliser cette liaison pour exposer des points de terminaison qui se conforment à WS-I BP 1.1, tels que ceux que les clients ASMX consomment.</span><span class="sxs-lookup"><span data-stu-id="a73e5-197">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="a73e5-198">De la même façon, un client peut utiliser le BasicHttpBinding pour communiquer avec les services qui exposent des points de terminaison qui se conforment à WS-I BP 1.1, tel que les services Web ASMX ou les services configurés avec le BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="a73e5-198">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="a73e5-199">La sécurité est désactivée par défaut, mais peut être ajoutée en affectant à l’attribut mode de la [ \<sécurité >](security-of-basichttpbinding.md) élément enfant `None`une valeur autre que.</span><span class="sxs-lookup"><span data-stu-id="a73e5-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="a73e5-200">Par défaut, il utilise un encodage de message "Texte" et un encodage texte UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a73e5-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a73e5-201">Exemples</span><span class="sxs-lookup"><span data-stu-id="a73e5-201">Example</span></span>  
 <span data-ttu-id="a73e5-202">L'exemple suivant montre l'utilisation de <xref:System.ServiceModel.BasicHttpBinding> qui fournit la communication HTTP et l'interopérabilité maximale avec les services Web de première et seconde génération.</span><span class="sxs-lookup"><span data-stu-id="a73e5-202">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="a73e5-203">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="a73e5-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="a73e5-204">Le type de liaison est spécifié à l’aide de l’attribut `binding` de l’élément `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="a73e5-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="a73e5-205">Si vous souhaitez configurer la liaison de base et modifier certains de ses paramètres, vous devez définir une configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="a73e5-206">Le point de terminaison doit référencer la configuration de liaison par nom en utilisant l’attribut `bindingConfiguration` de l’élément `<endpoint>`, comme présenté dans le code de configuration suivant pour le service.</span><span class="sxs-lookup"><span data-stu-id="a73e5-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a73e5-207">Exemple</span><span class="sxs-lookup"><span data-stu-id="a73e5-207">Example</span></span>  
 <span data-ttu-id="a73e5-208">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="a73e5-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a73e5-209">Les fonctionnalités de l’exemple précédent peuvent être obtenues en supprimant le bindingConfiguration de l’adresse du point de terminaison et le nom de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a73e5-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="a73e5-210">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a73e5-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73e5-211">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a73e5-211">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="a73e5-212">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a73e5-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a73e5-213">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a73e5-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a73e5-214">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a73e5-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a73e5-215">\<binding></span><span class="sxs-lookup"><span data-stu-id="a73e5-215">\<binding></span></span>](../../../misc/binding.md)
