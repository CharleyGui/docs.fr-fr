---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846857"
---
# <a name="issuedtoken"></a><span data-ttu-id="0937a-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="0937a-101">\<issuedToken></span></span>
<span data-ttu-id="0937a-102">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="0937a-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="0937a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0937a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0937a-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0937a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0937a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**comportements**](behaviors.md)\<</span><span class="sxs-lookup"><span data-stu-id="0937a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\</span></span>
<span data-ttu-id="0937a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**endpointBehaviors**](endpointbehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="0937a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="0937a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](behavior-of-endpointbehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="0937a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="0937a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="0937a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="0937a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuedToken** ></span><span class="sxs-lookup"><span data-stu-id="0937a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0937a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0937a-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0937a-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0937a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0937a-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0937a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0937a-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="0937a-113">Attributes</span></span>  
  
|<span data-ttu-id="0937a-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="0937a-114">Attribute</span></span>|<span data-ttu-id="0937a-115">Description</span><span class="sxs-lookup"><span data-stu-id="0937a-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="0937a-116">Attribut booléen facultatif indiquant si les jetons sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="0937a-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="0937a-117">La valeur par défaut est `true`,</span><span class="sxs-lookup"><span data-stu-id="0937a-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="0937a-118">Attribut de chaîne facultatif qui spécifie les valeurs aléatoires (entropies) utilisées pour les opérations de protocole de transfert.</span><span class="sxs-lookup"><span data-stu-id="0937a-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="0937a-119">Les valeurs comprennent `ClientEntropy`, `ServerEntropy` et `CombinedEntropy`. La valeur par défaut est `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="0937a-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="0937a-120">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="0937a-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="0937a-121">Attribut entier facultatif indiquant le pourcentage d'un délai valide (fourni par l'émetteur du jeton) pouvant s'écouler avant le renouvellement d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="0937a-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="0937a-122">Les valeurs sont comprises entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="0937a-122">Values are from 0 to 100.</span></span> <span data-ttu-id="0937a-123">La valeur par défaut est 60, c'est-à-dire que 60 % du délai s'écoule avant la tentative de renouvellement.</span><span class="sxs-lookup"><span data-stu-id="0937a-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="0937a-124">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="0937a-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="0937a-125">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="0937a-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="0937a-126">Attribut Timespan facultatif indiquant la durée de mise en cache des jetons émis lorsque l'émetteur de jeton (un STS) ne spécifie aucune durée.</span><span class="sxs-lookup"><span data-stu-id="0937a-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="0937a-127">La valeur par défaut est « 10675199.02:48:05.4775807 ».</span><span class="sxs-lookup"><span data-stu-id="0937a-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0937a-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0937a-128">Child Elements</span></span>  
  
|<span data-ttu-id="0937a-129">Élément</span><span class="sxs-lookup"><span data-stu-id="0937a-129">Element</span></span>|<span data-ttu-id="0937a-130">Description</span><span class="sxs-lookup"><span data-stu-id="0937a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0937a-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="0937a-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="0937a-132">Spécifie l’adresse de l’émetteur local du jeton et la liaison utilisée pour communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0937a-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="0937a-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0937a-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="0937a-134">Spécifie les comportements de point de terminaison à utiliser lors d'une communication avec un émetteur local.</span><span class="sxs-lookup"><span data-stu-id="0937a-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0937a-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0937a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="0937a-136">Élément</span><span class="sxs-lookup"><span data-stu-id="0937a-136">Element</span></span>|<span data-ttu-id="0937a-137">Description</span><span class="sxs-lookup"><span data-stu-id="0937a-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0937a-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="0937a-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="0937a-139">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="0937a-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0937a-140">Notes</span><span class="sxs-lookup"><span data-stu-id="0937a-140">Remarks</span></span>  
 <span data-ttu-id="0937a-141">Un jeton émis est un type d'informations d'identification personnalisé utilisé, par exemple, lors d'une authentification à l'aide d'un service STS dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="0937a-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="0937a-142">Par défaut, le jeton est un jeton SAML.</span><span class="sxs-lookup"><span data-stu-id="0937a-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="0937a-143">Pour plus d’informations, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md), ainsi que [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="0937a-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="0937a-144">Cette section contient les éléments permettant de configurer un émetteur local de jetons ou les comportements utilisés avec un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0937a-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="0937a-145">Pour obtenir des instructions sur la configuration d’un client pour qu’il utilise un émetteur local, consultez [procédure : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="0937a-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0937a-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0937a-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="0937a-147">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="0937a-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0937a-148">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0937a-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0937a-149">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="0937a-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0937a-150">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="0937a-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0937a-151">Guide pratique pour créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="0937a-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="0937a-152">Guide pratique pour configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="0937a-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="0937a-153">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="0937a-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
