---
title: <wsHttpBinding>
description: Définit une liaison HTTP sécurisée, fiable et interopérable adaptée aux contrats de service non duplex, qui implémente WS-Reliable Messaging et WS-Security.
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 27b506a53aba3e7c58f850c7b3adb8a763c80b39
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557266"
---
# \<wsHttpBinding>
<span data-ttu-id="fa568-102">Définit une liaison sécurisée, fiable, interopérable adaptée aux contrats de service non duplex.</span><span class="sxs-lookup"><span data-stu-id="fa568-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="fa568-103">La liaison implémente les spécifications suivantes : WS-ReliableMessaging pour la fiabilité et WS-Security pour la sécurité et l'authentification des messages.</span><span class="sxs-lookup"><span data-stu-id="fa568-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="fa568-104">Le protocole de transport est HTTP et l'encodage de message est Text/XML.</span><span class="sxs-lookup"><span data-stu-id="fa568-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="fa568-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa568-105">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa568-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fa568-106">Attributes and Elements</span></span>  
 <span data-ttu-id="fa568-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fa568-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa568-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="fa568-108">Attributes</span></span>  
  
|<span data-ttu-id="fa568-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="fa568-109">Attribute</span></span>|<span data-ttu-id="fa568-110">Description</span><span class="sxs-lookup"><span data-stu-id="fa568-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa568-111">allowCookies</span><span class="sxs-lookup"><span data-stu-id="fa568-111">allowCookies</span></span>|<span data-ttu-id="fa568-112">Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes.</span><span class="sxs-lookup"><span data-stu-id="fa568-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="fa568-113">La valeur par défaut est false.</span><span class="sxs-lookup"><span data-stu-id="fa568-113">The default is false.</span></span><br /><br /> <span data-ttu-id="fa568-114">Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies.</span><span class="sxs-lookup"><span data-stu-id="fa568-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="fa568-115">De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.</span><span class="sxs-lookup"><span data-stu-id="fa568-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="fa568-116">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="fa568-116">bypassProxyOnLocal</span></span>|<span data-ttu-id="fa568-117">Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="fa568-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="fa568-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="fa568-118">The default is `false`.</span></span>|  
|<span data-ttu-id="fa568-119">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="fa568-119">closeTimeout</span></span>|<span data-ttu-id="fa568-120"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="fa568-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="fa568-121">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fa568-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fa568-122">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fa568-122">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fa568-123">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="fa568-123">hostnameComparisonMode</span></span>|<span data-ttu-id="fa568-124">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="fa568-124">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="fa568-125">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="fa568-125">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="fa568-126">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="fa568-126">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="fa568-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="fa568-127">maxBufferPoolSize</span></span>|<span data-ttu-id="fa568-128">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="fa568-128">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="fa568-129">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="fa568-129">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="fa568-130">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="fa568-130">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="fa568-131">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="fa568-131">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="fa568-132">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="fa568-132">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="fa568-133">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="fa568-133">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="fa568-134">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="fa568-134">maxReceivedMessageSize</span></span>|<span data-ttu-id="fa568-135">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="fa568-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="fa568-136">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="fa568-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="fa568-137">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="fa568-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="fa568-138">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="fa568-138">The default is 65536.</span></span>|  
|<span data-ttu-id="fa568-139">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="fa568-139">messageEncoding</span></span>|<span data-ttu-id="fa568-140">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="fa568-140">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="fa568-141">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa568-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fa568-142">-Text : utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="fa568-142">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="fa568-143">-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="fa568-143">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="fa568-144">-La valeur par défaut est texte.</span><span class="sxs-lookup"><span data-stu-id="fa568-144">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="fa568-145">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="fa568-145">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="fa568-146">name</span><span class="sxs-lookup"><span data-stu-id="fa568-146">name</span></span>|<span data-ttu-id="fa568-147">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa568-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="fa568-148">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa568-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="fa568-149">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="fa568-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="fa568-150">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fa568-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="fa568-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="fa568-151">openTimeout</span></span>|<span data-ttu-id="fa568-152"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="fa568-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="fa568-153">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fa568-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fa568-154">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fa568-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fa568-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="fa568-155">proxyAddress</span></span>|<span data-ttu-id="fa568-156">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="fa568-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="fa568-157">Si `useSystemWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="fa568-157">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="fa568-158">La valeur par défaut est `null`.</span><span class="sxs-lookup"><span data-stu-id="fa568-158">The default is `null`.</span></span>|  
|<span data-ttu-id="fa568-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="fa568-159">receiveTimeout</span></span>|<span data-ttu-id="fa568-160"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="fa568-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="fa568-161">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fa568-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fa568-162">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fa568-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fa568-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="fa568-163">sendTimeout</span></span>|<span data-ttu-id="fa568-164"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fa568-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="fa568-165">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fa568-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fa568-166">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fa568-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="fa568-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="fa568-167">textEncoding</span></span>|<span data-ttu-id="fa568-168">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa568-168">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="fa568-169">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa568-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fa568-170">-UnicodeFffeTextEncoding : encodage BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="fa568-170">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="fa568-171">-Utf16TextEncoding : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="fa568-171">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="fa568-172">-Utf8TextEncoding : encodage 8 bits.</span><span class="sxs-lookup"><span data-stu-id="fa568-172">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="fa568-173">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="fa568-173">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="fa568-174">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="fa568-174">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="fa568-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="fa568-175">transactionFlow</span></span>|<span data-ttu-id="fa568-176">Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="fa568-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="fa568-177">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="fa568-177">The default is `false`.</span></span>|  
|<span data-ttu-id="fa568-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="fa568-178">useDefaultWebProxy</span></span>|<span data-ttu-id="fa568-179">Valeur booléenne qui spécifie si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fa568-179">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="fa568-180">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="fa568-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa568-181">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fa568-181">Child Elements</span></span>  
  
|<span data-ttu-id="fa568-182">Élément</span><span class="sxs-lookup"><span data-stu-id="fa568-182">Element</span></span>|<span data-ttu-id="fa568-183">Description</span><span class="sxs-lookup"><span data-stu-id="fa568-183">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="fa568-184">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa568-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="fa568-185">Cet élément est de type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="fa568-185">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="fa568-186">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="fa568-186">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fa568-187">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fa568-187">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="fa568-188">Spécifie si des sessions fiables sont établies entre les points de terminaison du canal.</span><span class="sxs-lookup"><span data-stu-id="fa568-188">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa568-189">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fa568-189">Parent Elements</span></span>  
  
|<span data-ttu-id="fa568-190">Élément</span><span class="sxs-lookup"><span data-stu-id="fa568-190">Element</span></span>|<span data-ttu-id="fa568-191">Description</span><span class="sxs-lookup"><span data-stu-id="fa568-191">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="fa568-192">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="fa568-192">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa568-193">Notes</span><span class="sxs-lookup"><span data-stu-id="fa568-193">Remarks</span></span>  
 <span data-ttu-id="fa568-194">`WSHttpBinding` est semblable à `BasicHttpBinding` mais fournit plus de fonctionnalités de service Web.</span><span class="sxs-lookup"><span data-stu-id="fa568-194">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="fa568-195">Il utilise le transport HTTP et assure la sécurité des messages, comme BasicHttpBinding, mais il fournit également des transactions, une messagerie fiable et WS-Addressing, qu’il soit actif par défaut ou disponible par l’intermédiaire d’un paramètre de contrôle unique.</span><span class="sxs-lookup"><span data-stu-id="fa568-195">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa568-196">Exemple</span><span class="sxs-lookup"><span data-stu-id="fa568-196">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="fa568-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa568-197">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="fa568-198">Liaisons</span><span class="sxs-lookup"><span data-stu-id="fa568-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fa568-199">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="fa568-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fa568-200">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="fa568-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
