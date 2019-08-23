---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: fe952dfe9ce51e23d1ba46975026799dfe8b5b39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915260"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="a9bce-101">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a9bce-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="a9bce-102">Une liaison sécurisée et interopérable qui dérive de [ \<WSFederationHttpBinding >](wsfederationhttpbinding.md) et prend en charge la sécurité fédérée.</span><span class="sxs-lookup"><span data-stu-id="a9bce-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <ws2007FederationHttpBinding>
```

## <a name="syntax"></a><span data-ttu-id="a9bce-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9bce-103">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a9bce-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a9bce-104">Attributes and Elements</span></span>

<span data-ttu-id="a9bce-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a9bce-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9bce-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="a9bce-106">Attributes</span></span>

|<span data-ttu-id="a9bce-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="a9bce-107">Attribute</span></span>|<span data-ttu-id="a9bce-108">Description</span><span class="sxs-lookup"><span data-stu-id="a9bce-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="a9bce-109">Valeur indiquant s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="a9bce-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="a9bce-110">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="a9bce-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="a9bce-111"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="a9bce-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a9bce-112">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a9bce-113">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a9bce-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="a9bce-114">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="a9bce-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="a9bce-115">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="a9bce-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a9bce-116">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="a9bce-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="a9bce-117">Taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a9bce-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="a9bce-118">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="a9bce-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="a9bce-119">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="a9bce-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="a9bce-120">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="a9bce-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="a9bce-121">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="a9bce-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="a9bce-122">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="a9bce-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="a9bce-123">Taille maximale du message (en octets), en-têtes compris, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a9bce-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a9bce-124">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="a9bce-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="a9bce-125">Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="a9bce-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a9bce-126">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="a9bce-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="a9bce-127">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="a9bce-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="a9bce-128">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9bce-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a9bce-129">Financière Utilisez un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="a9bce-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="a9bce-130">MTOM Utilisez un encodeur de transmission de message (MTOM) message transmission Organization 1,0.</span><span class="sxs-lookup"><span data-stu-id="a9bce-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="a9bce-131">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="a9bce-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="a9bce-132">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="a9bce-133">Nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a9bce-133">The configuration name of the binding.</span></span> <span data-ttu-id="a9bce-134">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="a9bce-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a9bce-135">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="a9bce-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a9bce-136">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a9bce-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="a9bce-137"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="a9bce-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a9bce-138">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a9bce-139">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a9bce-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="a9bce-140">URI d'emplacement de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="a9bce-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="a9bce-141">Numéro de version de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="a9bce-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="a9bce-142">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9bce-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="a9bce-143">Si `useDefaultWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="a9bce-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="a9bce-144">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="a9bce-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="a9bce-145"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="a9bce-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a9bce-146">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a9bce-147">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a9bce-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="a9bce-148"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a9bce-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a9bce-149">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a9bce-150">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a9bce-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="a9bce-151">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="a9bce-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a9bce-152">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9bce-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a9bce-153">BigEndianUnicode Encodage Unicode Big endian.</span><span class="sxs-lookup"><span data-stu-id="a9bce-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="a9bce-154">Unicode encodage 16 bits.</span><span class="sxs-lookup"><span data-stu-id="a9bce-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="a9bce-155">UTF8 encodage 8 bits.</span><span class="sxs-lookup"><span data-stu-id="a9bce-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="a9bce-156">La valeur par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="a9bce-156">The default is UTF8.</span></span> <span data-ttu-id="a9bce-157">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="a9bce-158">Valeur indiquant si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="a9bce-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="a9bce-159">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="a9bce-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="a9bce-160">Valeur indiquant si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a9bce-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="a9bce-161">L'adresse proxy doit être `null` (autrement dit, pas de jeu) si cet attribut est `true`.</span><span class="sxs-lookup"><span data-stu-id="a9bce-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="a9bce-162">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="a9bce-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a9bce-163">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a9bce-163">Child Elements</span></span>

|<span data-ttu-id="a9bce-164">Élément</span><span class="sxs-lookup"><span data-stu-id="a9bce-164">Element</span></span>|<span data-ttu-id="a9bce-165">Description</span><span class="sxs-lookup"><span data-stu-id="a9bce-165">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9bce-166">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="a9bce-166">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="a9bce-167">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="a9bce-167">Defines the security settings for the message.</span></span> <span data-ttu-id="a9bce-168">Cet élément est de type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-168">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="a9bce-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bce-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a9bce-170">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a9bce-170">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a9bce-171">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a9bce-171">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="a9bce-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a9bce-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="a9bce-173">Indique si des sessions fiables sont établies entre les points de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="a9bce-173">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a9bce-174">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a9bce-174">Parent Elements</span></span>

|<span data-ttu-id="a9bce-175">Élément</span><span class="sxs-lookup"><span data-stu-id="a9bce-175">Element</span></span>|<span data-ttu-id="a9bce-176">Description</span><span class="sxs-lookup"><span data-stu-id="a9bce-176">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9bce-177">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a9bce-177">\<bindings></span></span>](bindings.md)|<span data-ttu-id="a9bce-178">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a9bce-178">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9bce-179">Notes</span><span class="sxs-lookup"><span data-stu-id="a9bce-179">Remarks</span></span>

<span data-ttu-id="a9bce-180">La fédération est la capacité à partager des identités entre plusieurs entreprises ou domaines approuvés à des fins d'authentification et d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="a9bce-180">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="a9bce-181">Elle utilise le protocole WS-Trust pour mapper la représentation d'identité entre domaines approuvés.</span><span class="sxs-lookup"><span data-stu-id="a9bce-181">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="a9bce-182">Une liaison HTTP fédérée prend en charge la sécurité SOAP ainsi que la sécurité en mode mixte, mais pas la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="a9bce-182">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="a9bce-183">Les services configurés avec cette liaison doivent utiliser le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9bce-183">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="a9bce-184">Pour plus d’informations, consultez [ \<WSFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a9bce-184">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="a9bce-185">Exemple</span><span class="sxs-lookup"><span data-stu-id="a9bce-185">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a9bce-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9bce-186">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="a9bce-187">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a9bce-187">\<wsFederationHttpBinding></span></span>](wsfederationhttpbinding.md)
- [<span data-ttu-id="a9bce-188">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a9bce-188">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a9bce-189">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a9bce-189">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a9bce-190">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a9bce-190">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a9bce-191">\<binding></span><span class="sxs-lookup"><span data-stu-id="a9bce-191">\<binding></span></span>](../../../misc/binding.md)
