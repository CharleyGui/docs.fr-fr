---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 20ba643fddbac8a488e5457f0195cc253d4d23f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139317"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="1db10-101">Liaison sécurisée et interopérable qui dérive de [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) et prend en charge la sécurité fédérée.</span><span class="sxs-lookup"><span data-stu-id="1db10-101">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1db10-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db10-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="1db10-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1db10-103">Attributes and Elements</span></span>

<span data-ttu-id="1db10-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1db10-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1db10-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="1db10-105">Attributes</span></span>

|<span data-ttu-id="1db10-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="1db10-106">Attribute</span></span>|<span data-ttu-id="1db10-107">Description</span><span class="sxs-lookup"><span data-stu-id="1db10-107">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="1db10-108">Valeur indiquant s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="1db10-108">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="1db10-109">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="1db10-109">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="1db10-110"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="1db10-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1db10-111">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1db10-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1db10-112">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1db10-112">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="1db10-113">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="1db10-113">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="1db10-114">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="1db10-114">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1db10-115">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="1db10-115">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="1db10-116">Taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="1db10-116">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="1db10-117">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="1db10-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="1db10-118">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="1db10-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="1db10-119">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="1db10-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="1db10-120">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="1db10-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="1db10-121">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="1db10-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="1db10-122">Taille maximale du message (en octets), en-têtes compris, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="1db10-122">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1db10-123">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="1db10-123">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="1db10-124">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="1db10-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1db10-125">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="1db10-125">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="1db10-126">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="1db10-126">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="1db10-127">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1db10-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1db10-128">-Text : utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="1db10-128">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="1db10-129">-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="1db10-129">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="1db10-130">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="1db10-130">The default is Text.</span></span><br /><br /> <span data-ttu-id="1db10-131">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="1db10-131">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="1db10-132">Nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="1db10-132">The configuration name of the binding.</span></span> <span data-ttu-id="1db10-133">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="1db10-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1db10-134">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="1db10-134">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1db10-135">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1db10-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="1db10-136"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="1db10-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1db10-137">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1db10-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1db10-138">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1db10-138">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="1db10-139">URI d'emplacement de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="1db10-139">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="1db10-140">Numéro de version de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="1db10-140">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="1db10-141">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="1db10-141">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="1db10-142">Si `useDefaultWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="1db10-142">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="1db10-143">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="1db10-143">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="1db10-144"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="1db10-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1db10-145">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1db10-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1db10-146">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1db10-146">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="1db10-147"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1db10-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1db10-148">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1db10-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1db10-149">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1db10-149">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="1db10-150">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="1db10-150">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="1db10-151">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1db10-151">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1db10-152">-BigEndianUnicode : encodage Unicode Big endian.</span><span class="sxs-lookup"><span data-stu-id="1db10-152">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="1db10-153">-Unicode : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="1db10-153">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="1db10-154">-UTF8 : encodage 8 bits.</span><span class="sxs-lookup"><span data-stu-id="1db10-154">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="1db10-155">La valeur par défaut est UTF-8.</span><span class="sxs-lookup"><span data-stu-id="1db10-155">The default is UTF8.</span></span> <span data-ttu-id="1db10-156">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="1db10-156">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="1db10-157">Valeur indiquant si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="1db10-157">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="1db10-158">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="1db10-158">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="1db10-159">Valeur indiquant si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="1db10-159">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="1db10-160">L'adresse proxy doit être `null` (autrement dit, pas de jeu) si cet attribut est `true`.</span><span class="sxs-lookup"><span data-stu-id="1db10-160">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="1db10-161">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="1db10-161">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1db10-162">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1db10-162">Child Elements</span></span>

|<span data-ttu-id="1db10-163">Élément</span><span class="sxs-lookup"><span data-stu-id="1db10-163">Element</span></span>|<span data-ttu-id="1db10-164">Description</span><span class="sxs-lookup"><span data-stu-id="1db10-164">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="1db10-165">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="1db10-165">Defines the security settings for the message.</span></span> <span data-ttu-id="1db10-166">Cet élément est de type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1db10-166">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="1db10-167">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="1db10-167">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1db10-168">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1db10-168">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="1db10-169">Indique si des sessions fiables sont établies entre les points de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="1db10-169">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1db10-170">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1db10-170">Parent Elements</span></span>

|<span data-ttu-id="1db10-171">Élément</span><span class="sxs-lookup"><span data-stu-id="1db10-171">Element</span></span>|<span data-ttu-id="1db10-172">Description</span><span class="sxs-lookup"><span data-stu-id="1db10-172">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="1db10-173">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1db10-173">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1db10-174">Remarques</span><span class="sxs-lookup"><span data-stu-id="1db10-174">Remarks</span></span>

<span data-ttu-id="1db10-175">La fédération est la capacité à partager des identités entre plusieurs entreprises ou domaines approuvés à des fins d'authentification et d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="1db10-175">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="1db10-176">Elle utilise le protocole WS-Trust pour mapper la représentation d'identité entre domaines approuvés.</span><span class="sxs-lookup"><span data-stu-id="1db10-176">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="1db10-177">Une liaison HTTP fédérée prend en charge la sécurité SOAP ainsi que la sécurité en mode mixte, mais pas la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="1db10-177">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="1db10-178">Les services configurés avec cette liaison doivent utiliser le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="1db10-178">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="1db10-179">Pour plus d’informations, consultez [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1db10-179">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="1db10-180">Exemple</span><span class="sxs-lookup"><span data-stu-id="1db10-180">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1db10-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1db10-181">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="1db10-182">Liaisons</span><span class="sxs-lookup"><span data-stu-id="1db10-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1db10-183">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="1db10-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1db10-184">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="1db10-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
