---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925380"
---
# <a name="issuedtoken"></a><span data-ttu-id="d7324-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="d7324-101">\<issuedToken></span></span>
<span data-ttu-id="d7324-102">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="d7324-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="d7324-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d7324-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7324-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="d7324-104">\<behaviors></span></span>  
<span data-ttu-id="d7324-105">section endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="d7324-105">endpointBehaviors section</span></span>  
<span data-ttu-id="d7324-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="d7324-106">\<behavior></span></span>  
<span data-ttu-id="d7324-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d7324-107">\<clientCredentials></span></span>  
<span data-ttu-id="d7324-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="d7324-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7324-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7324-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7324-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d7324-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d7324-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d7324-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7324-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="d7324-112">Attributes</span></span>  
  
|<span data-ttu-id="d7324-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="d7324-113">Attribute</span></span>|<span data-ttu-id="d7324-114">Description</span><span class="sxs-lookup"><span data-stu-id="d7324-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="d7324-115">Attribut booléen facultatif indiquant si les jetons sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="d7324-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="d7324-116">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="d7324-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="d7324-117">Attribut de chaîne facultatif qui spécifie les valeurs aléatoires (entropies) utilisées pour les opérations de protocole de transfert.</span><span class="sxs-lookup"><span data-stu-id="d7324-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="d7324-118">Les valeurs comprennent `ClientEntropy`, `ServerEntropy` et `CombinedEntropy`. La valeur par défaut est `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="d7324-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="d7324-119">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="d7324-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="d7324-120">Attribut entier facultatif indiquant le pourcentage d'un délai valide (fourni par l'émetteur du jeton) pouvant s'écouler avant le renouvellement d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="d7324-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="d7324-121">Les valeurs sont comprises entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="d7324-121">Values are from 0 to 100.</span></span> <span data-ttu-id="d7324-122">La valeur par défaut est 60, c'est-à-dire que 60 % du délai s'écoule avant la tentative de renouvellement.</span><span class="sxs-lookup"><span data-stu-id="d7324-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="d7324-123">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="d7324-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="d7324-124">Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="d7324-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="d7324-125">Attribut Timespan facultatif indiquant la durée de mise en cache des jetons émis lorsque l'émetteur de jeton (un STS) ne spécifie aucune durée.</span><span class="sxs-lookup"><span data-stu-id="d7324-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="d7324-126">La valeur par défaut est «10675199.02:48:05.4775807».</span><span class="sxs-lookup"><span data-stu-id="d7324-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7324-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d7324-127">Child Elements</span></span>  
  
|<span data-ttu-id="d7324-128">Élément</span><span class="sxs-lookup"><span data-stu-id="d7324-128">Element</span></span>|<span data-ttu-id="d7324-129">Description</span><span class="sxs-lookup"><span data-stu-id="d7324-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7324-130">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="d7324-130">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="d7324-131">Spécifie l’adresse de l’émetteur local du jeton et la liaison utilisée pour communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d7324-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="d7324-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="d7324-132">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="d7324-133">Spécifie les comportements de point de terminaison à utiliser lors d'une communication avec un émetteur local.</span><span class="sxs-lookup"><span data-stu-id="d7324-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7324-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d7324-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d7324-135">Élément</span><span class="sxs-lookup"><span data-stu-id="d7324-135">Element</span></span>|<span data-ttu-id="d7324-136">Description</span><span class="sxs-lookup"><span data-stu-id="d7324-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7324-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d7324-137">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="d7324-138">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="d7324-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7324-139">Notes</span><span class="sxs-lookup"><span data-stu-id="d7324-139">Remarks</span></span>  
 <span data-ttu-id="d7324-140">Un jeton émis est un type d'informations d'identification personnalisé utilisé, par exemple, lors d'une authentification à l'aide d'un service STS dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="d7324-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="d7324-141">Par défaut, le jeton est un jeton SAML.</span><span class="sxs-lookup"><span data-stu-id="d7324-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="d7324-142">Pour plus d’informations, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="d7324-142">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="d7324-143">et la [Fédération et les jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="d7324-143">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="d7324-144">Cette section contient les éléments permettant de configurer un émetteur local de jetons ou les comportements utilisés avec un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d7324-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="d7324-145">Pour obtenir des instructions sur la configuration d’un client pour qu’il utilise un [émetteur local, consultez Procédure: Configurez un émetteur](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="d7324-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7324-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7324-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="d7324-147">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="d7324-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d7324-148">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d7324-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d7324-149">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="d7324-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d7324-150">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="d7324-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d7324-151">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="d7324-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d7324-152">Guide pratique pour Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="d7324-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d7324-153">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="d7324-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
