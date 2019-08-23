---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 0b6f26c7b9e9d02b3ff20b53f42b09d671699ea5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919389"
---
# <a name="custombinding"></a><span data-ttu-id="33fef-101">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="33fef-101">\<customBinding></span></span>

<span data-ttu-id="33fef-102">Fournit le contrôle total sur la pile de messagerie pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="33fef-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="33fef-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="33fef-103">\<system.serviceModel></span></span>\
<span data-ttu-id="33fef-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="33fef-104">\<bindings></span></span>\
<span data-ttu-id="33fef-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="33fef-105">\<customBinding></span></span>

## <a name="syntax"></a><span data-ttu-id="33fef-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33fef-106">Syntax</span></span>

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33fef-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="33fef-107">Attributes and Elements</span></span>

<span data-ttu-id="33fef-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="33fef-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="33fef-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="33fef-109">Attributes</span></span>

|<span data-ttu-id="33fef-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="33fef-110">Attribute</span></span>|<span data-ttu-id="33fef-111">Description</span><span class="sxs-lookup"><span data-stu-id="33fef-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="33fef-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="33fef-112">closeTimeout</span></span>|<span data-ttu-id="33fef-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="33fef-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="33fef-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="33fef-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33fef-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="33fef-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="33fef-116">name</span><span class="sxs-lookup"><span data-stu-id="33fef-116">name</span></span>|<span data-ttu-id="33fef-117">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="33fef-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="33fef-118">Cette valeur est une chaîne définie par l'utilisateur qui sert de chaîne d'identification à la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="33fef-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="33fef-119">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="33fef-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="33fef-120">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="33fef-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="33fef-121">openTimeout</span><span class="sxs-lookup"><span data-stu-id="33fef-121">openTimeout</span></span>|<span data-ttu-id="33fef-122"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="33fef-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="33fef-123">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="33fef-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33fef-124">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="33fef-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="33fef-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="33fef-125">receiveTimeout</span></span>|<span data-ttu-id="33fef-126"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="33fef-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="33fef-127">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="33fef-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33fef-128">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="33fef-128">The default is 00:01:00.</span></span>|
|<span data-ttu-id="33fef-129">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="33fef-129">sendTimeout</span></span>|<span data-ttu-id="33fef-130"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="33fef-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="33fef-131">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="33fef-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33fef-132">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="33fef-132">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="33fef-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="33fef-133">Child Elements</span></span>

|<span data-ttu-id="33fef-134">Élément</span><span class="sxs-lookup"><span data-stu-id="33fef-134">Element</span></span>|<span data-ttu-id="33fef-135">Description</span><span class="sxs-lookup"><span data-stu-id="33fef-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33fef-136">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="33fef-136">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="33fef-137">Spécifie la messagerie bidirectionnelle pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="33fef-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="33fef-138">Il est utilisé avec les transports qui n'autorisent pas nativement les communications duplex, comme HTTP.</span><span class="sxs-lookup"><span data-stu-id="33fef-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="33fef-139">En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.</span><span class="sxs-lookup"><span data-stu-id="33fef-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="33fef-140">Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="33fef-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="33fef-141">Cette adresse cliente est fournie par l'attribut `ClientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="33fef-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="33fef-142">Cet élément est de type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="33fef-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="33fef-143">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="33fef-143">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="33fef-144">Spécifie un programme de résolution de nom d’homologue PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="33fef-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="33fef-145">Cet élément est de type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="33fef-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="33fef-146">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="33fef-146">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="33fef-147">Spécifie le paramètre de WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="33fef-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="33fef-148">Lorsque cet élément est ajouté à une liaison personnalisée, le canal résultant peut prendre en charge des assurances de remise EOD (Exactly-Once-Delivery).</span><span class="sxs-lookup"><span data-stu-id="33fef-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="33fef-149">Cet élément est de type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="33fef-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="33fef-150">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="33fef-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="33fef-151">Spécifie les options de sécurité de la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="33fef-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="33fef-152">Cet élément est de type <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="33fef-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="33fef-153">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="33fef-153">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="33fef-154">Spécifie les paramètres de sécurité pour une liaison de flux de données SSL.</span><span class="sxs-lookup"><span data-stu-id="33fef-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="33fef-155">Cet élément est de type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="33fef-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="33fef-156">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="33fef-156">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="33fef-157">Spécifie que le flux de la transaction des prises en charge de la liaison, ainsi que le protocole à utiliser par l’attribut `transactionProtocol`.</span><span class="sxs-lookup"><span data-stu-id="33fef-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="33fef-158">Cet élément est de type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="33fef-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="33fef-159">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="33fef-159">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="33fef-160">Spécifie les options permettant de transmettre en continu la sécurité de la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="33fef-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="33fef-161">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="33fef-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33fef-162">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="33fef-162">Parent Elements</span></span>

|<span data-ttu-id="33fef-163">Élément</span><span class="sxs-lookup"><span data-stu-id="33fef-163">Element</span></span>|<span data-ttu-id="33fef-164">Description</span><span class="sxs-lookup"><span data-stu-id="33fef-164">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="33fef-165">liaisons</span><span class="sxs-lookup"><span data-stu-id="33fef-165">bindings</span></span>|<span data-ttu-id="33fef-166">Contient toutes les liaisons pour les applications de Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="33fef-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33fef-167">Notes</span><span class="sxs-lookup"><span data-stu-id="33fef-167">Remarks</span></span>

<span data-ttu-id="33fef-168">Les liaisons personnalisées permettent d'exercer un contrôle total sur la pile de messagerie WCF.</span><span class="sxs-lookup"><span data-stu-id="33fef-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="33fef-169">Les liaisons spécialement conçues peuvent être créées en ajoutant des éléments de configuration pour des entités spécifiques.</span><span class="sxs-lookup"><span data-stu-id="33fef-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="33fef-170">Par exemple, l’utilisateur peut associer les sections `httpsTransport`, `reliableSession` et `security` pour créer une liaison fiable et sécurisée basée sur https.</span><span class="sxs-lookup"><span data-stu-id="33fef-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="33fef-171">Une liaison individuelle définit la pile de messages en spécifiant les éléments de configuration des éléments de la pile suivant leur l'ordre d'apparition dans cette pile.</span><span class="sxs-lookup"><span data-stu-id="33fef-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="33fef-172">Chaque élément définit et configure l'élément de la pile.</span><span class="sxs-lookup"><span data-stu-id="33fef-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="33fef-173">Il doit y avoir un seul élément de transport dans chaque liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="33fef-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="33fef-174">Sans cet élément, la pile de messagerie est incomplète.</span><span class="sxs-lookup"><span data-stu-id="33fef-174">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="33fef-175">L'ordre dans lequel les éléments apparaissent dans la pile est important car il s'agit de l'ordre dans lequel les opérations sont appliquées au message.</span><span class="sxs-lookup"><span data-stu-id="33fef-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="33fef-176">Voici l'ordre recommandé des éléments de la pile :</span><span class="sxs-lookup"><span data-stu-id="33fef-176">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="33fef-177">Transactions (facultatif)</span><span class="sxs-lookup"><span data-stu-id="33fef-177">Transactions (optional)</span></span>

2. <span data-ttu-id="33fef-178">Messagerie fiable (facultatif)</span><span class="sxs-lookup"><span data-stu-id="33fef-178">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="33fef-179">Sécurité (facultatif)</span><span class="sxs-lookup"><span data-stu-id="33fef-179">Security (optional)</span></span>

4. <span data-ttu-id="33fef-180">Transport</span><span class="sxs-lookup"><span data-stu-id="33fef-180">Transport</span></span>

5. <span data-ttu-id="33fef-181">Encodeur (facultatif)</span><span class="sxs-lookup"><span data-stu-id="33fef-181">Encoder (optional)</span></span>

<span data-ttu-id="33fef-182">Utilisez une liaison personnalisée lorsque l’une des liaisons fournies par le système ne répond pas aux exigences de votre service.</span><span class="sxs-lookup"><span data-stu-id="33fef-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="33fef-183">Une liaison personnalisée peut être utilisée, par exemple, pour activer l’utilisation d’un nouveau transport ou d’un nouvel encodeur à un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="33fef-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="33fef-184">Une liaison personnalisée est construite à l'aide d'une collection <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> d'éléments de liaison « empilés » dans un ordre spécifique :</span><span class="sxs-lookup"><span data-stu-id="33fef-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="33fef-185">Tout en haut de cette pile figure un <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> facultatif qui autorise des transactions de flux.</span><span class="sxs-lookup"><span data-stu-id="33fef-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="33fef-186">Puis figure un <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> facultatif qui fournit une session et un mécanisme de classement tel que défini dans la spécification WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="33fef-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="33fef-187">Cette notion de session peut traverser les intermédiaires SOAP et de transport.</span><span class="sxs-lookup"><span data-stu-id="33fef-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="33fef-188">Puis figure un élément de liaison facultatif qui fournit des fonctionnalités de sécurité telles que l'autorisation, l'authentification, la protection et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="33fef-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="33fef-189">Les éléments de liaison de sécurité suivants sont fournis par Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="33fef-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="33fef-190">Les modèles de messages facultatifs spécifiés par des éléments de liaison figurent ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="33fef-190">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="33fef-191">Les éléments de liaison d’assistance/de mises à niveau de transport facultatifs sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="33fef-191">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="33fef-192">L’élément suivant est un message obligatoire qui encode l’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="33fef-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="33fef-193">Vous pouvez utiliser votre propre transport ou utiliser l’une des liaisons d’encodage des messages suivantes :</span><span class="sxs-lookup"><span data-stu-id="33fef-193">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="33fef-194">Au bas de la pile se trouve un élément de transport obligatoire.</span><span class="sxs-lookup"><span data-stu-id="33fef-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="33fef-195">Vous pouvez utiliser votre propre transport ou utiliser l’un des éléments de liaison de transport fournis par Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="33fef-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="33fef-196">Le tableau suivant récapitule les options de chaque couche.</span><span class="sxs-lookup"><span data-stu-id="33fef-196">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="33fef-197">Couche</span><span class="sxs-lookup"><span data-stu-id="33fef-197">Layer</span></span>|<span data-ttu-id="33fef-198">Options</span><span class="sxs-lookup"><span data-stu-id="33fef-198">Options</span></span>|<span data-ttu-id="33fef-199">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="33fef-199">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="33fef-200">Flux de transaction</span><span class="sxs-lookup"><span data-stu-id="33fef-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="33fef-201">Non</span><span class="sxs-lookup"><span data-stu-id="33fef-201">No</span></span>|
|<span data-ttu-id="33fef-202">Fiabilité</span><span class="sxs-lookup"><span data-stu-id="33fef-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="33fef-203">Non</span><span class="sxs-lookup"><span data-stu-id="33fef-203">No</span></span>|
|<span data-ttu-id="33fef-204">Sécurité</span><span class="sxs-lookup"><span data-stu-id="33fef-204">Security</span></span>|<span data-ttu-id="33fef-205">Symétrique, asymétrique, au niveau du transport</span><span class="sxs-lookup"><span data-stu-id="33fef-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="33fef-206">Non</span><span class="sxs-lookup"><span data-stu-id="33fef-206">No</span></span>|
|<span data-ttu-id="33fef-207">Modification de la forme</span><span class="sxs-lookup"><span data-stu-id="33fef-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="33fef-208">Non</span><span class="sxs-lookup"><span data-stu-id="33fef-208">No</span></span>|
|<span data-ttu-id="33fef-209">Mises à niveau de transport</span><span class="sxs-lookup"><span data-stu-id="33fef-209">Transport Upgrades</span></span>|<span data-ttu-id="33fef-210">Flux SSL, flux Windows, programme de résolution d'homologue</span><span class="sxs-lookup"><span data-stu-id="33fef-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="33fef-211">Non</span><span class="sxs-lookup"><span data-stu-id="33fef-211">No</span></span>|
|<span data-ttu-id="33fef-212">Encodage</span><span class="sxs-lookup"><span data-stu-id="33fef-212">Encoding</span></span>|<span data-ttu-id="33fef-213">Text, Binary, MTOM, Custom</span><span class="sxs-lookup"><span data-stu-id="33fef-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="33fef-214">Oui</span><span class="sxs-lookup"><span data-stu-id="33fef-214">Yes</span></span>|
|<span data-ttu-id="33fef-215">Transport</span><span class="sxs-lookup"><span data-stu-id="33fef-215">Transport</span></span>|<span data-ttu-id="33fef-216">TCP, canaux nommés, HTTP, HTTPS, versions de MSMQ, personnalisé</span><span class="sxs-lookup"><span data-stu-id="33fef-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="33fef-217">Oui</span><span class="sxs-lookup"><span data-stu-id="33fef-217">Yes</span></span>|

<span data-ttu-id="33fef-218">De plus, vous pouvez définir vos propres éléments de liaison et les insérer entre chacune des couches définies précédentes.</span><span class="sxs-lookup"><span data-stu-id="33fef-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="33fef-219">Pour plus d’informations sur l’utilisation d’une liaison personnalisée pour modifier une liaison fournie par le système [, consultez Procédure: Personnaliser une liaison](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="33fef-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33fef-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33fef-220">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="33fef-221">\<binding></span><span class="sxs-lookup"><span data-stu-id="33fef-221">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="33fef-222">Liaisons</span><span class="sxs-lookup"><span data-stu-id="33fef-222">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="33fef-223">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="33fef-223">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="33fef-224">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="33fef-224">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="33fef-225">customBinding, élément</span><span class="sxs-lookup"><span data-stu-id="33fef-225">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="33fef-226">Liaisons</span><span class="sxs-lookup"><span data-stu-id="33fef-226">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="33fef-227">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="33fef-227">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="33fef-228">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="33fef-228">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
