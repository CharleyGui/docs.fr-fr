---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 0a5090166efd90efa7537f87d5fa47b8c9d078cb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735756"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="51a71-101">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="51a71-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="51a71-102">Liaison sécurisée et interopérable qui dérive de [\<wsFederationHttpBinding >](wsfederationhttpbinding.md) et prend en charge la sécurité fédérée.</span><span class="sxs-lookup"><span data-stu-id="51a71-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

<span data-ttu-id="51a71-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="51a71-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="51a71-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="51a71-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="51a71-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="51a71-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="51a71-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**ws2007FederationHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="51a71-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51a71-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51a71-107">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51a71-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="51a71-108">Attributes and Elements</span></span>

<span data-ttu-id="51a71-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="51a71-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="51a71-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="51a71-110">Attributes</span></span>

|<span data-ttu-id="51a71-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="51a71-111">Attribute</span></span>|<span data-ttu-id="51a71-112">Description</span><span class="sxs-lookup"><span data-stu-id="51a71-112">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="51a71-113">Valeur indiquant s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="51a71-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="51a71-114">La valeur par défaut est `false`,</span><span class="sxs-lookup"><span data-stu-id="51a71-114">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="51a71-115"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="51a71-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="51a71-116">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="51a71-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="51a71-117">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="51a71-117">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="51a71-118">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="51a71-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="51a71-119">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="51a71-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="51a71-120">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="51a71-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="51a71-121">Taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="51a71-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="51a71-122">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="51a71-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="51a71-123">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="51a71-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="51a71-124">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="51a71-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="51a71-125">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="51a71-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="51a71-126">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="51a71-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="51a71-127">Taille maximale du message (en octets), en-têtes compris, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="51a71-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="51a71-128">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="51a71-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="51a71-129">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="51a71-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="51a71-130">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="51a71-130">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="51a71-131">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="51a71-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="51a71-132">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="51a71-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="51a71-133">-Text : utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="51a71-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="51a71-134">-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="51a71-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="51a71-135">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="51a71-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="51a71-136">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="51a71-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="51a71-137">Nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="51a71-137">The configuration name of the binding.</span></span> <span data-ttu-id="51a71-138">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="51a71-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="51a71-139">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="51a71-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="51a71-140">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="51a71-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="51a71-141"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="51a71-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="51a71-142">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="51a71-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="51a71-143">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="51a71-143">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="51a71-144">URI d'emplacement de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="51a71-144">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="51a71-145">Numéro de version de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="51a71-145">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="51a71-146">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="51a71-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="51a71-147">Si `useDefaultWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="51a71-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="51a71-148">La valeur par défaut est `null`,</span><span class="sxs-lookup"><span data-stu-id="51a71-148">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="51a71-149"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="51a71-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="51a71-150">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="51a71-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="51a71-151">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="51a71-151">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="51a71-152"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="51a71-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="51a71-153">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="51a71-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="51a71-154">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="51a71-154">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="51a71-155">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="51a71-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="51a71-156">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="51a71-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="51a71-157">-BigEndianUnicode : encodage Unicode Big endian.</span><span class="sxs-lookup"><span data-stu-id="51a71-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="51a71-158">-Unicode : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="51a71-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="51a71-159">-UTF8 : encodage 8 bits.</span><span class="sxs-lookup"><span data-stu-id="51a71-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="51a71-160">La valeur par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="51a71-160">The default is UTF8.</span></span> <span data-ttu-id="51a71-161">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="51a71-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="51a71-162">Valeur indiquant si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="51a71-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="51a71-163">La valeur par défaut est `false`,</span><span class="sxs-lookup"><span data-stu-id="51a71-163">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="51a71-164">Valeur indiquant si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="51a71-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="51a71-165">L'adresse proxy doit être `null` (autrement dit, pas de jeu) si cet attribut est `true`.</span><span class="sxs-lookup"><span data-stu-id="51a71-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="51a71-166">La valeur par défaut est `true`,</span><span class="sxs-lookup"><span data-stu-id="51a71-166">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="51a71-167">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="51a71-167">Child Elements</span></span>

|<span data-ttu-id="51a71-168">Élément</span><span class="sxs-lookup"><span data-stu-id="51a71-168">Element</span></span>|<span data-ttu-id="51a71-169">Description</span><span class="sxs-lookup"><span data-stu-id="51a71-169">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51a71-170">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="51a71-170">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="51a71-171">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="51a71-171">Defines the security settings for the message.</span></span> <span data-ttu-id="51a71-172">Cet élément est de type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="51a71-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="51a71-173">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="51a71-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="51a71-174">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="51a71-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="51a71-175">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="51a71-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="51a71-176">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="51a71-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="51a71-177">Indique si des sessions fiables sont établies entre les points de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="51a71-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="51a71-178">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="51a71-178">Parent Elements</span></span>

|<span data-ttu-id="51a71-179">Élément</span><span class="sxs-lookup"><span data-stu-id="51a71-179">Element</span></span>|<span data-ttu-id="51a71-180">Description</span><span class="sxs-lookup"><span data-stu-id="51a71-180">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51a71-181">liaisons de\<</span><span class="sxs-lookup"><span data-stu-id="51a71-181">\<bindings></span></span>](bindings.md)|<span data-ttu-id="51a71-182">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="51a71-182">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="51a71-183">Notes</span><span class="sxs-lookup"><span data-stu-id="51a71-183">Remarks</span></span>

<span data-ttu-id="51a71-184">La fédération est la capacité à partager des identités entre plusieurs entreprises ou domaines approuvés à des fins d'authentification et d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="51a71-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="51a71-185">Elle utilise le protocole WS-Trust pour mapper la représentation d'identité entre domaines approuvés.</span><span class="sxs-lookup"><span data-stu-id="51a71-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="51a71-186">Une liaison HTTP fédérée prend en charge la sécurité SOAP ainsi que la sécurité en mode mixte, mais pas la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="51a71-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="51a71-187">Les services configurés avec cette liaison doivent utiliser le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="51a71-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="51a71-188">Pour plus d’informations, consultez [\<wsFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="51a71-188">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="51a71-189">Exemple</span><span class="sxs-lookup"><span data-stu-id="51a71-189">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="51a71-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51a71-190">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="51a71-191">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="51a71-191">\<wsFederationHttpBinding></span></span>](wsfederationhttpbinding.md)
- [<span data-ttu-id="51a71-192">Liaisons</span><span class="sxs-lookup"><span data-stu-id="51a71-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="51a71-193">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="51a71-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="51a71-194">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="51a71-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="51a71-195">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="51a71-195">\<binding></span></span>](bindings.md)
