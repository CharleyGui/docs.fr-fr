---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140799"
---
# \<customBinding>

<span data-ttu-id="1ee2f-101">Fournit le contrôle total sur la pile de messagerie pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-101">Provides full control over the messaging stack for the user.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a><span data-ttu-id="1ee2f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ee2f-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="1ee2f-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1ee2f-103">Attributes and Elements</span></span>

<span data-ttu-id="1ee2f-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-104">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="1ee2f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="1ee2f-105">Attributes</span></span>

|<span data-ttu-id="1ee2f-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="1ee2f-106">Attribute</span></span>|<span data-ttu-id="1ee2f-107">Description</span><span class="sxs-lookup"><span data-stu-id="1ee2f-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="1ee2f-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="1ee2f-108">closeTimeout</span></span>|<span data-ttu-id="1ee2f-109"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1ee2f-110">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ee2f-111">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-111">The default is 00:01:00.</span></span>|
|<span data-ttu-id="1ee2f-112">name</span><span class="sxs-lookup"><span data-stu-id="1ee2f-112">name</span></span>|<span data-ttu-id="1ee2f-113">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-113">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1ee2f-114">Cette valeur est une chaîne définie par l'utilisateur qui sert de chaîne d'identification à la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-114">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="1ee2f-115">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-115">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1ee2f-116">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1ee2f-116">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="1ee2f-117">openTimeout</span><span class="sxs-lookup"><span data-stu-id="1ee2f-117">openTimeout</span></span>|<span data-ttu-id="1ee2f-118"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1ee2f-119">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ee2f-120">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-120">The default is 00:01:00.</span></span>|
|<span data-ttu-id="1ee2f-121">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="1ee2f-121">receiveTimeout</span></span>|<span data-ttu-id="1ee2f-122"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1ee2f-123">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ee2f-124">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="1ee2f-125">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="1ee2f-125">sendTimeout</span></span>|<span data-ttu-id="1ee2f-126"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1ee2f-127">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ee2f-128">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-128">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1ee2f-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1ee2f-129">Child Elements</span></span>

|<span data-ttu-id="1ee2f-130">Élément</span><span class="sxs-lookup"><span data-stu-id="1ee2f-130">Element</span></span>|<span data-ttu-id="1ee2f-131">Description</span><span class="sxs-lookup"><span data-stu-id="1ee2f-131">Description</span></span>|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|<span data-ttu-id="1ee2f-132">Spécifie la messagerie bidirectionnelle pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-132">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="1ee2f-133">Il est utilisé avec les transports qui n'autorisent pas nativement les communications duplex, comme HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-133">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="1ee2f-134">En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-134">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="1ee2f-135">Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-135">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="1ee2f-136">Cette adresse cliente est fournie par l'attribut `ClientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-136">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="1ee2f-137">Cet élément est de type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-137">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|<span data-ttu-id="1ee2f-138">Spécifie un programme de résolution de nom d’homologue PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="1ee2f-138">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="1ee2f-139">Cet élément est de type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-139">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[\<reliableSession>](reliablesession.md)|<span data-ttu-id="1ee2f-140">Spécifie le paramètre de WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-140">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="1ee2f-141">Lorsque cet élément est ajouté à une liaison personnalisée, le canal résultant peut prendre en charge des assurances de remise EOD (Exactly-Once-Delivery).</span><span class="sxs-lookup"><span data-stu-id="1ee2f-141">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="1ee2f-142">Cet élément est de type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-142">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="1ee2f-143">Spécifie les options de sécurité de la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-143">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="1ee2f-144">Cet élément est de type <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-144">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|<span data-ttu-id="1ee2f-145">Spécifie les paramètres de sécurité pour une liaison de flux de données SSL.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-145">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="1ee2f-146">Cet élément est de type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-146">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[\<transactionFlow>](transactionflow.md)|<span data-ttu-id="1ee2f-147">Spécifie que le flux de la transaction des prises en charge de la liaison, ainsi que le protocole à utiliser par l’attribut `transactionProtocol`.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-147">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="1ee2f-148">Cet élément est de type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-148">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|<span data-ttu-id="1ee2f-149">Spécifie les options permettant de transmettre en continu la sécurité de la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-149">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="1ee2f-150">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-150">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1ee2f-151">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1ee2f-151">Parent Elements</span></span>

|<span data-ttu-id="1ee2f-152">Élément</span><span class="sxs-lookup"><span data-stu-id="1ee2f-152">Element</span></span>|<span data-ttu-id="1ee2f-153">Description</span><span class="sxs-lookup"><span data-stu-id="1ee2f-153">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="1ee2f-154">liaisons</span><span class="sxs-lookup"><span data-stu-id="1ee2f-154">bindings</span></span>|<span data-ttu-id="1ee2f-155">Contient toutes les liaisons pour les applications de Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-155">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1ee2f-156">Remarques</span><span class="sxs-lookup"><span data-stu-id="1ee2f-156">Remarks</span></span>

<span data-ttu-id="1ee2f-157">Les liaisons personnalisées permettent d'exercer un contrôle total sur la pile de messagerie WCF.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-157">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="1ee2f-158">Les liaisons spécialement conçues peuvent être créées en ajoutant des éléments de configuration pour des entités spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-158">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="1ee2f-159">Par exemple, l’utilisateur peut associer les sections `httpsTransport`, `reliableSession` et `security` pour créer une liaison fiable et sécurisée basée sur https.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-159">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="1ee2f-160">Une liaison individuelle définit la pile de messages en spécifiant les éléments de configuration des éléments de la pile suivant leur l'ordre d'apparition dans cette pile.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-160">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="1ee2f-161">Chaque élément définit et configure l'élément de la pile.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-161">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="1ee2f-162">Il doit y avoir un seul élément de transport dans chaque liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-162">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="1ee2f-163">Sans cet élément, la pile de messagerie est incomplète.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-163">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="1ee2f-164">L'ordre dans lequel les éléments apparaissent dans la pile est important car il s'agit de l'ordre dans lequel les opérations sont appliquées au message.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-164">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="1ee2f-165">Voici l'ordre recommandé des éléments de la pile :</span><span class="sxs-lookup"><span data-stu-id="1ee2f-165">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="1ee2f-166">Transactions (facultatif)</span><span class="sxs-lookup"><span data-stu-id="1ee2f-166">Transactions (optional)</span></span>

2. <span data-ttu-id="1ee2f-167">Messagerie fiable (facultatif)</span><span class="sxs-lookup"><span data-stu-id="1ee2f-167">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="1ee2f-168">Sécurité (facultatif)</span><span class="sxs-lookup"><span data-stu-id="1ee2f-168">Security (optional)</span></span>

4. <span data-ttu-id="1ee2f-169">Transport</span><span class="sxs-lookup"><span data-stu-id="1ee2f-169">Transport</span></span>

5. <span data-ttu-id="1ee2f-170">Encodeur (facultatif)</span><span class="sxs-lookup"><span data-stu-id="1ee2f-170">Encoder (optional)</span></span>

<span data-ttu-id="1ee2f-171">Utilisez une liaison personnalisée lorsque l’une des liaisons fournies par le système ne répond pas aux exigences de votre service.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-171">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="1ee2f-172">Une liaison personnalisée peut être utilisée, par exemple, pour activer l’utilisation d’un nouveau transport ou d’un nouvel encodeur à un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-172">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="1ee2f-173">Une liaison personnalisée est construite à l'aide d'une collection <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> d'éléments de liaison « empilés » dans un ordre spécifique :</span><span class="sxs-lookup"><span data-stu-id="1ee2f-173">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="1ee2f-174">Tout en haut de cette pile figure un <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> facultatif qui autorise des transactions de flux.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-174">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="1ee2f-175">Puis figure un <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> facultatif qui fournit une session et un mécanisme de classement tel que défini dans la spécification WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-175">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="1ee2f-176">Cette notion de session peut traverser les intermédiaires SOAP et de transport.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-176">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="1ee2f-177">Puis figure un élément de liaison facultatif qui fournit des fonctionnalités de sécurité telles que l'autorisation, l'authentification, la protection et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-177">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="1ee2f-178">Les éléments de liaison de sécurité suivants sont fournis par Windows Communication Foundation (WCF) :</span><span class="sxs-lookup"><span data-stu-id="1ee2f-178">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="1ee2f-179">Les modèles de messages facultatifs spécifiés par des éléments de liaison figurent ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1ee2f-179">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="1ee2f-180">Les éléments de liaison d’assistance/de mises à niveau de transport facultatifs sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="1ee2f-180">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="1ee2f-181">L’élément suivant est un message obligatoire qui encode l’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-181">Next is a required message encoding binding element.</span></span> <span data-ttu-id="1ee2f-182">Vous pouvez utiliser votre propre transport ou utiliser l’une des liaisons d’encodage des messages suivantes :</span><span class="sxs-lookup"><span data-stu-id="1ee2f-182">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="1ee2f-183">Au bas de la pile se trouve un élément de transport obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-183">At the bottom is a required transport element.</span></span> <span data-ttu-id="1ee2f-184">Vous pouvez utiliser votre propre transport ou utiliser l’un des éléments de liaison de transport fournis par Windows Communication Foundation (WCF) :</span><span class="sxs-lookup"><span data-stu-id="1ee2f-184">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="1ee2f-185">Le tableau suivant récapitule les options de chaque couche.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-185">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="1ee2f-186">Couche</span><span class="sxs-lookup"><span data-stu-id="1ee2f-186">Layer</span></span>|<span data-ttu-id="1ee2f-187">Options</span><span class="sxs-lookup"><span data-stu-id="1ee2f-187">Options</span></span>|<span data-ttu-id="1ee2f-188">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="1ee2f-188">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="1ee2f-189">Flux de transaction</span><span class="sxs-lookup"><span data-stu-id="1ee2f-189">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="1ee2f-190">No</span><span class="sxs-lookup"><span data-stu-id="1ee2f-190">No</span></span>|
|<span data-ttu-id="1ee2f-191">Fiabilité</span><span class="sxs-lookup"><span data-stu-id="1ee2f-191">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="1ee2f-192">No</span><span class="sxs-lookup"><span data-stu-id="1ee2f-192">No</span></span>|
|<span data-ttu-id="1ee2f-193">Sécurité</span><span class="sxs-lookup"><span data-stu-id="1ee2f-193">Security</span></span>|<span data-ttu-id="1ee2f-194">Symétrique, asymétrique, au niveau du transport</span><span class="sxs-lookup"><span data-stu-id="1ee2f-194">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="1ee2f-195">No</span><span class="sxs-lookup"><span data-stu-id="1ee2f-195">No</span></span>|
|<span data-ttu-id="1ee2f-196">Modification de la forme</span><span class="sxs-lookup"><span data-stu-id="1ee2f-196">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="1ee2f-197">No</span><span class="sxs-lookup"><span data-stu-id="1ee2f-197">No</span></span>|
|<span data-ttu-id="1ee2f-198">Mises à niveau de transport</span><span class="sxs-lookup"><span data-stu-id="1ee2f-198">Transport Upgrades</span></span>|<span data-ttu-id="1ee2f-199">Flux SSL, flux Windows, programme de résolution d'homologue</span><span class="sxs-lookup"><span data-stu-id="1ee2f-199">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="1ee2f-200">No</span><span class="sxs-lookup"><span data-stu-id="1ee2f-200">No</span></span>|
|<span data-ttu-id="1ee2f-201">Encodage</span><span class="sxs-lookup"><span data-stu-id="1ee2f-201">Encoding</span></span>|<span data-ttu-id="1ee2f-202">Text, Binary, MTOM, Custom</span><span class="sxs-lookup"><span data-stu-id="1ee2f-202">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="1ee2f-203">Yes</span><span class="sxs-lookup"><span data-stu-id="1ee2f-203">Yes</span></span>|
|<span data-ttu-id="1ee2f-204">Transport</span><span class="sxs-lookup"><span data-stu-id="1ee2f-204">Transport</span></span>|<span data-ttu-id="1ee2f-205">TCP, canaux nommés, HTTP, HTTPS, versions de MSMQ, personnalisé</span><span class="sxs-lookup"><span data-stu-id="1ee2f-205">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="1ee2f-206">Yes</span><span class="sxs-lookup"><span data-stu-id="1ee2f-206">Yes</span></span>|

<span data-ttu-id="1ee2f-207">De plus, vous pouvez définir vos propres éléments de liaison et les insérer entre chacune des couches définies précédentes.</span><span class="sxs-lookup"><span data-stu-id="1ee2f-207">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="1ee2f-208">Pour plus d’informations sur l’utilisation d’une liaison personnalisée pour modifier une liaison fournie par le système, consultez Guide pratique [pour personnaliser une liaison fournie par le système](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="1ee2f-208">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ee2f-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ee2f-209">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="1ee2f-210">Liaisons</span><span class="sxs-lookup"><span data-stu-id="1ee2f-210">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ee2f-211">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="1ee2f-211">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1ee2f-212">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="1ee2f-212">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1ee2f-213">customBinding, élément</span><span class="sxs-lookup"><span data-stu-id="1ee2f-213">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="1ee2f-214">Liaisons</span><span class="sxs-lookup"><span data-stu-id="1ee2f-214">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ee2f-215">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="1ee2f-215">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1ee2f-216">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="1ee2f-216">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
