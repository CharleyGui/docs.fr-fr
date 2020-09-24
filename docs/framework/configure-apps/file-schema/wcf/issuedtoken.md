---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9f3feb11fbe45cbb4b952c70feaa99f9c481dd2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157367"
---
# \<issuedToken>

<span data-ttu-id="a20e3-101">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="a20e3-101">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="a20e3-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a20e3-102">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a20e3-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a20e3-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a20e3-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a20e3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a20e3-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="a20e3-105">Attributes</span></span>  
  
|<span data-ttu-id="a20e3-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="a20e3-106">Attribute</span></span>|<span data-ttu-id="a20e3-107">Description</span><span class="sxs-lookup"><span data-stu-id="a20e3-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="a20e3-108">Attribut booléen facultatif indiquant si les jetons sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="a20e3-108">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="a20e3-109">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="a20e3-109">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="a20e3-110">Attribut de chaîne facultatif qui spécifie les valeurs aléatoires (entropies) utilisées pour les opérations de protocole de transfert.</span><span class="sxs-lookup"><span data-stu-id="a20e3-110">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="a20e3-111">Les valeurs comprennent `ClientEntropy`, `ServerEntropy` et `CombinedEntropy`. La valeur par défaut est `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="a20e3-111">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="a20e3-112">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="a20e3-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="a20e3-113">Attribut entier facultatif indiquant le pourcentage d'un délai valide (fourni par l'émetteur du jeton) pouvant s'écouler avant le renouvellement d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="a20e3-113">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="a20e3-114">Les valeurs sont comprises entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="a20e3-114">Values are from 0 to 100.</span></span> <span data-ttu-id="a20e3-115">La valeur par défaut est 60, c'est-à-dire que 60 % du délai s'écoule avant la tentative de renouvellement.</span><span class="sxs-lookup"><span data-stu-id="a20e3-115">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="a20e3-116">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="a20e3-116">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="a20e3-117">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="a20e3-117">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="a20e3-118">Attribut Timespan facultatif indiquant la durée de mise en cache des jetons émis lorsque l'émetteur de jeton (un STS) ne spécifie aucune durée.</span><span class="sxs-lookup"><span data-stu-id="a20e3-118">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="a20e3-119">La valeur par défaut est « 10675199.02:48:05.4775807 ».</span><span class="sxs-lookup"><span data-stu-id="a20e3-119">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a20e3-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a20e3-120">Child Elements</span></span>  
  
|<span data-ttu-id="a20e3-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a20e3-121">Element</span></span>|<span data-ttu-id="a20e3-122">Description</span><span class="sxs-lookup"><span data-stu-id="a20e3-122">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="a20e3-123">Spécifie l’adresse de l’émetteur local du jeton et la liaison utilisée pour communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a20e3-123">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="a20e3-124">Spécifie les comportements de point de terminaison à utiliser lors d'une communication avec un émetteur local.</span><span class="sxs-lookup"><span data-stu-id="a20e3-124">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a20e3-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a20e3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a20e3-126">Élément</span><span class="sxs-lookup"><span data-stu-id="a20e3-126">Element</span></span>|<span data-ttu-id="a20e3-127">Description</span><span class="sxs-lookup"><span data-stu-id="a20e3-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="a20e3-128">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="a20e3-128">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a20e3-129">Notes</span><span class="sxs-lookup"><span data-stu-id="a20e3-129">Remarks</span></span>  

 <span data-ttu-id="a20e3-130">Un jeton émis est un type d'informations d'identification personnalisé utilisé, par exemple, lors d'une authentification à l'aide d'un service STS dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="a20e3-130">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="a20e3-131">Par défaut, le jeton est un jeton SAML.</span><span class="sxs-lookup"><span data-stu-id="a20e3-131">By default, the token is a SAML token.</span></span> <span data-ttu-id="a20e3-132">Pour plus d’informations, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md), ainsi que [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="a20e3-132">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="a20e3-133">Cette section contient les éléments permettant de configurer un émetteur local de jetons ou les comportements utilisés avec un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a20e3-133">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="a20e3-134">Pour obtenir des instructions sur la configuration d’un client pour qu’il utilise un émetteur local, consultez [procédure : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="a20e3-134">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a20e3-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a20e3-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="a20e3-136">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="a20e3-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a20e3-137">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a20e3-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a20e3-138">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="a20e3-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a20e3-139">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="a20e3-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a20e3-140">Procédure : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="a20e3-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a20e3-141">Procédure : configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="a20e3-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a20e3-142">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="a20e3-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
