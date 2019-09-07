---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: b5ab3c3ad070499d686ea74b9fd459e89f380cfa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397964"
---
# <a name="issuedtoken"></a><span data-ttu-id="5ca6d-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="5ca6d-101">\<issuedToken></span></span>
<span data-ttu-id="5ca6d-102">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="5ca6d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ca6d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ca6d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5ca6d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5ca6d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ca6d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5ca6d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ca6d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="5ca6d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ca6d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="5ca6d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5ca6d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="5ca6d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedToken >**</span><span class="sxs-lookup"><span data-stu-id="5ca6d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca6d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ca6d-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ca6d-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5ca6d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5ca6d-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ca6d-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="5ca6d-113">Attributes</span></span>  
  
|<span data-ttu-id="5ca6d-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ca6d-114">Attribute</span></span>|<span data-ttu-id="5ca6d-115">Description</span><span class="sxs-lookup"><span data-stu-id="5ca6d-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="5ca6d-116">Attribut booléen facultatif indiquant si les jetons sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="5ca6d-117">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="5ca6d-118">Attribut de chaîne facultatif qui spécifie les valeurs aléatoires (entropies) utilisées pour les opérations de protocole de transfert.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="5ca6d-119">Les valeurs comprennent `ClientEntropy`, `ServerEntropy` et `CombinedEntropy`. La valeur par défaut est `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="5ca6d-120">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="5ca6d-121">Attribut entier facultatif indiquant le pourcentage d'un délai valide (fourni par l'émetteur du jeton) pouvant s'écouler avant le renouvellement d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="5ca6d-122">Les valeurs sont comprises entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-122">Values are from 0 to 100.</span></span> <span data-ttu-id="5ca6d-123">La valeur par défaut est 60, c'est-à-dire que 60 % du délai s'écoule avant la tentative de renouvellement.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="5ca6d-124">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="5ca6d-125">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="5ca6d-126">Attribut Timespan facultatif indiquant la durée de mise en cache des jetons émis lorsque l'émetteur de jeton (un STS) ne spécifie aucune durée.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="5ca6d-127">La valeur par défaut est « 10675199.02:48:05.4775807 ».</span><span class="sxs-lookup"><span data-stu-id="5ca6d-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ca6d-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ca6d-128">Child Elements</span></span>  
  
|<span data-ttu-id="5ca6d-129">Élément</span><span class="sxs-lookup"><span data-stu-id="5ca6d-129">Element</span></span>|<span data-ttu-id="5ca6d-130">Description</span><span class="sxs-lookup"><span data-stu-id="5ca6d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ca6d-131">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="5ca6d-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="5ca6d-132">Spécifie l’adresse de l’émetteur local du jeton et la liaison utilisée pour communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="5ca6d-133">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="5ca6d-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="5ca6d-134">Spécifie les comportements de point de terminaison à utiliser lors d'une communication avec un émetteur local.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ca6d-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ca6d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5ca6d-136">Élément</span><span class="sxs-lookup"><span data-stu-id="5ca6d-136">Element</span></span>|<span data-ttu-id="5ca6d-137">Description</span><span class="sxs-lookup"><span data-stu-id="5ca6d-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ca6d-138">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5ca6d-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="5ca6d-139">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca6d-140">Notes</span><span class="sxs-lookup"><span data-stu-id="5ca6d-140">Remarks</span></span>  
 <span data-ttu-id="5ca6d-141">Un jeton émis est un type d'informations d'identification personnalisé utilisé, par exemple, lors d'une authentification à l'aide d'un service STS dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="5ca6d-142">Par défaut, le jeton est un jeton SAML.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="5ca6d-143">Pour plus d’informations, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5ca6d-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="5ca6d-144">et la [Fédération et les jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5ca6d-144">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="5ca6d-145">Cette section contient les éléments permettant de configurer un émetteur local de jetons ou les comportements utilisés avec un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="5ca6d-146">Pour obtenir des instructions sur la configuration d’un client pour qu’il utilise un [émetteur local, consultez Procédure : Configurez un émetteur](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="5ca6d-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca6d-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ca6d-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="5ca6d-148">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="5ca6d-148">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5ca6d-149">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="5ca6d-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5ca6d-150">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="5ca6d-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5ca6d-151">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="5ca6d-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5ca6d-152">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="5ca6d-152">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="5ca6d-153">Guide pratique pour Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="5ca6d-153">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="5ca6d-154">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="5ca6d-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
