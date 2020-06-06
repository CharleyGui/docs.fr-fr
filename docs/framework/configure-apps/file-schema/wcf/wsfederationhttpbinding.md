---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 0a77c791d55c6009cf59d5a4b15f3b2a63b7ccf9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140475"
---
# \<wsFederationHttpBinding>

<span data-ttu-id="4cd88-101">Définit une liaison qui prend en charge WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="4cd88-101">Defines a binding that supports WS-Federation.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**  

## <a name="syntax"></a><span data-ttu-id="4cd88-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cd88-102">Syntax</span></span>

```xml
<wsFederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
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
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4cd88-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4cd88-103">Attributes and Elements</span></span>

<span data-ttu-id="4cd88-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4cd88-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4cd88-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="4cd88-105">Attributes</span></span>

|<span data-ttu-id="4cd88-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="4cd88-106">Attribute</span></span>|<span data-ttu-id="4cd88-107">Description</span><span class="sxs-lookup"><span data-stu-id="4cd88-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="4cd88-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="4cd88-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="4cd88-109">Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="4cd88-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="4cd88-110">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="4cd88-110">The default is `false`.</span></span>|
|<span data-ttu-id="4cd88-111">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="4cd88-111">closeTimeout</span></span>|<span data-ttu-id="4cd88-112"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="4cd88-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4cd88-113">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4cd88-114">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4cd88-114">The default is 00:01:00.</span></span>|
|<span data-ttu-id="4cd88-115">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="4cd88-115">hostnameComparisonMode</span></span>|<span data-ttu-id="4cd88-116">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="4cd88-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4cd88-117">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="4cd88-117">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4cd88-118">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="4cd88-118">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="4cd88-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4cd88-119">maxBufferPoolSize</span></span>|<span data-ttu-id="4cd88-120">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4cd88-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4cd88-121">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="4cd88-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="4cd88-122">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="4cd88-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4cd88-123">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="4cd88-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4cd88-124">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="4cd88-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4cd88-125">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="4cd88-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="4cd88-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4cd88-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="4cd88-127">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4cd88-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4cd88-128">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="4cd88-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4cd88-129">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="4cd88-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4cd88-130">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="4cd88-130">The default is 65536.</span></span>|
|<span data-ttu-id="4cd88-131">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="4cd88-131">messageEncoding</span></span>|<span data-ttu-id="4cd88-132">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="4cd88-132">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="4cd88-133">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4cd88-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4cd88-134">-Text : utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="4cd88-134">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="4cd88-135">-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4cd88-135">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="4cd88-136">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="4cd88-136">The default is Text.</span></span><br /><br /> <span data-ttu-id="4cd88-137">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-137">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="4cd88-138">name</span><span class="sxs-lookup"><span data-stu-id="4cd88-138">name</span></span>|<span data-ttu-id="4cd88-139">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="4cd88-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4cd88-140">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="4cd88-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4cd88-141">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="4cd88-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4cd88-142">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4cd88-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="4cd88-143">openTimeout</span><span class="sxs-lookup"><span data-stu-id="4cd88-143">openTimeout</span></span>|<span data-ttu-id="4cd88-144"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="4cd88-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4cd88-145">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4cd88-146">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4cd88-146">The default is 00:01:00.</span></span>|
|<span data-ttu-id="4cd88-147">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="4cd88-147">privacyNoticeAt</span></span>|<span data-ttu-id="4cd88-148">Chaîne qui spécifie un URI dans lequel l'information préalable de confidentialité est située.</span><span class="sxs-lookup"><span data-stu-id="4cd88-148">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="4cd88-149">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="4cd88-149">privacyNoticeVersion</span></span>|<span data-ttu-id="4cd88-150">Entier qui spécifie la version de l'avis de confidentialité actuel.</span><span class="sxs-lookup"><span data-stu-id="4cd88-150">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="4cd88-151">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="4cd88-151">proxyAddress</span></span>|<span data-ttu-id="4cd88-152">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="4cd88-152">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="4cd88-153">Si `useDefaultWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="4cd88-153">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="4cd88-154">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="4cd88-154">The default is `null`.</span></span>|
|<span data-ttu-id="4cd88-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="4cd88-155">receiveTimeout</span></span>|<span data-ttu-id="4cd88-156"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="4cd88-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4cd88-157">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4cd88-158">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="4cd88-158">The default is 00:10:00.</span></span>|
|<span data-ttu-id="4cd88-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="4cd88-159">sendTimeout</span></span>|<span data-ttu-id="4cd88-160"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="4cd88-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4cd88-161">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4cd88-162">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4cd88-162">The default is 00:01:00.</span></span>|
|<span data-ttu-id="4cd88-163">textEncoding</span><span class="sxs-lookup"><span data-stu-id="4cd88-163">textEncoding</span></span>|<span data-ttu-id="4cd88-164">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="4cd88-164">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4cd88-165">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4cd88-165">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4cd88-166">-BigEndianUnicode : encodage BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="4cd88-166">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="4cd88-167">-Unicode : encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="4cd88-167">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="4cd88-168">-UTF8 : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="4cd88-168">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4cd88-169">La valeur par défaut est UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4cd88-169">The default is UTF8.</span></span> <span data-ttu-id="4cd88-170">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-170">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="4cd88-171">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="4cd88-171">transactionFlow</span></span>|<span data-ttu-id="4cd88-172">Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="4cd88-172">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="4cd88-173">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="4cd88-173">The default is `false`.</span></span>|
|<span data-ttu-id="4cd88-174">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="4cd88-174">useDefaultWebProxy</span></span>|<span data-ttu-id="4cd88-175">Valeur booléenne qui indique si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4cd88-175">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="4cd88-176">L'adresse proxy doit être `null` (autrement dit, pas de jeu) si cet attribut est `true`.</span><span class="sxs-lookup"><span data-stu-id="4cd88-176">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="4cd88-177">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="4cd88-177">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4cd88-178">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4cd88-178">Child Elements</span></span>

|<span data-ttu-id="4cd88-179">Élément</span><span class="sxs-lookup"><span data-stu-id="4cd88-179">Element</span></span>|<span data-ttu-id="4cd88-180">Description</span><span class="sxs-lookup"><span data-stu-id="4cd88-180">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="4cd88-181">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="4cd88-181">Defines the security settings for the message.</span></span> <span data-ttu-id="4cd88-182">Cet élément est de type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-182">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="4cd88-183">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4cd88-183">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4cd88-184">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4cd88-184">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="4cd88-185">Spécifie si des sessions fiables sont établies entre les points de terminaison du canal.</span><span class="sxs-lookup"><span data-stu-id="4cd88-185">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4cd88-186">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4cd88-186">Parent Elements</span></span>

|<span data-ttu-id="4cd88-187">Élément</span><span class="sxs-lookup"><span data-stu-id="4cd88-187">Element</span></span>|<span data-ttu-id="4cd88-188">Description</span><span class="sxs-lookup"><span data-stu-id="4cd88-188">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="4cd88-189">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="4cd88-189">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4cd88-190">Remarques</span><span class="sxs-lookup"><span data-stu-id="4cd88-190">Remarks</span></span>

<span data-ttu-id="4cd88-191">La fédération est la capacité à partager des identités sur plusieurs systèmes pour authentification et autorisation.</span><span class="sxs-lookup"><span data-stu-id="4cd88-191">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="4cd88-192">Ces identités peuvent faire référence à des utilisateurs ou des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="4cd88-192">These identities can refer to users or to machines.</span></span> <span data-ttu-id="4cd88-193">Le protocole HTTP fédéré prend en charge la sécurité SOAP, ainsi que la sécurité en mode mixte, mais il ne prend pas en charge exclusivement à l'aide de la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="4cd88-193">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="4cd88-194">Cette liaison fournit la prise en charge de Windows Communication Foundation (WCF) pour le protocole WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="4cd88-194">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="4cd88-195">Les services configurés avec cette liaison doivent utiliser le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="4cd88-195">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="4cd88-196">Les liaisons se composent d’une pile d’éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="4cd88-196">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="4cd88-197">La pile d’éléments de liaison dans</span><span class="sxs-lookup"><span data-stu-id="4cd88-197">The stack of binding elements in</span></span>

<span data-ttu-id="4cd88-198">`wsFederationHttpBinding` est la même que celle contenue dans `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="4cd88-198">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="4cd88-199">Lorsque [\<security>](security-of-wsfederationhttpbinding.md) est défini sur la valeur par défaut de <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="4cd88-199">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="4cd88-200">`wsFederationHttpBinding`Contrôle les détails des paramètres de sécurité de message dans [\<message>](message-element-of-wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4cd88-200">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="4cd88-201">Notez que l' [\<security>](security-of-wsfederationhttpbinding.md) élément fournit l’accès uniquement lorsque la sécurité utilisée par la liaison ne peut pas être modifiée une fois que la liaison est créée.</span><span class="sxs-lookup"><span data-stu-id="4cd88-201">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="4cd88-202">Le `wsFederationHttpBinding` fournit également un attribut privacyNoticeAt pour définir et récupérer l’URI où se trouve l’avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="4cd88-202">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="4cd88-203">Maintenir la sécurité de la stratégie est particulièrement important dans les scénarios de fédération.</span><span class="sxs-lookup"><span data-stu-id="4cd88-203">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="4cd88-204">Il est recommandé d'utiliser un type de sécurité, tel que HTTPS, pour protéger la stratégie d'utilisateurs malveillants.</span><span class="sxs-lookup"><span data-stu-id="4cd88-204">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="4cd88-205">Dans les scénarios de fédération utilisant cette liaison, la stratégie de service comporte potentiellement des informations importantes, telles que la clé à utiliser pour chiffrer le jeton émis (SAML), le type de revendications à mettre dans le jeton, etc.</span><span class="sxs-lookup"><span data-stu-id="4cd88-205">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="4cd88-206">Si cette stratégie était falsifiée, un intrus pourrait découvrir la clé du jeton émis, entraînant davantage de falsification, de divulgation d'informations et autres comportements malveillants.</span><span class="sxs-lookup"><span data-stu-id="4cd88-206">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="4cd88-207">Pour que ce type de problème puisse être évité, la stratégie doit être obtenue de manière sécurisée auprès du service (par exemple à l'aide de HTTPS).</span><span class="sxs-lookup"><span data-stu-id="4cd88-207">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="4cd88-208">Pour plus d’informations sur cette liaison, consultez [How to : Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4cd88-208">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="4cd88-209">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cd88-209">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4cd88-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cd88-210">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="4cd88-211">Guide pratique pour créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4cd88-211">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="4cd88-212">Liaisons</span><span class="sxs-lookup"><span data-stu-id="4cd88-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4cd88-213">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="4cd88-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4cd88-214">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="4cd88-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
