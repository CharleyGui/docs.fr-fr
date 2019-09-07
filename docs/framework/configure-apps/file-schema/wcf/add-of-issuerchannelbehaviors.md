---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398329"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="fd28e-102">\<Ajouter > de \<la > issuerChannelBehaviors</span><span class="sxs-lookup"><span data-stu-id="fd28e-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="fd28e-103">Ajoute un comportement de point de terminaison à utiliser lors de la communication avec un service STS.</span><span class="sxs-lookup"><span data-stu-id="fd28e-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="fd28e-104">Si un comportement de point de terminaison contient un [ \<élément ClientCredentials >](clientcredentials.md) , une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="fd28e-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="fd28e-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fd28e-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fd28e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fd28e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="fd28e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="fd28e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="fd28e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="fd28e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerChannelBehaviors >** ](issuerchannelbehaviors-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd28e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)</span></span>\
<span data-ttu-id="fd28e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="fd28e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="fd28e-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd28e-114">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd28e-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd28e-115">Attributes and Elements</span></span>

<span data-ttu-id="fd28e-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fd28e-116">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="fd28e-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd28e-117">Attributes</span></span>

|<span data-ttu-id="fd28e-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="fd28e-118">Attribute</span></span>|<span data-ttu-id="fd28e-119">Description</span><span class="sxs-lookup"><span data-stu-id="fd28e-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fd28e-120">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="fd28e-120">issuerAddress</span></span>|<span data-ttu-id="fd28e-121">URI de l'émetteur de jeton de sécurité avec lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="fd28e-121">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="fd28e-122">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fd28e-122">behaviorConfiguration</span></span>|<span data-ttu-id="fd28e-123">Nom d'un comportement de point de terminaison défini dans le même fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="fd28e-123">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fd28e-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd28e-124">Child Elements</span></span>

<span data-ttu-id="fd28e-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd28e-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd28e-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd28e-126">Parent Elements</span></span>

|<span data-ttu-id="fd28e-127">Élément</span><span class="sxs-lookup"><span data-stu-id="fd28e-127">Element</span></span>|<span data-ttu-id="fd28e-128">Description</span><span class="sxs-lookup"><span data-stu-id="fd28e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd28e-129">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="fd28e-129">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="fd28e-130">Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) à utiliser lors de la communication avec les services de jeton de service spécifiés.</span><span class="sxs-lookup"><span data-stu-id="fd28e-130">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fd28e-131">Notes</span><span class="sxs-lookup"><span data-stu-id="fd28e-131">Remarks</span></span>

<span data-ttu-id="fd28e-132">`issuerAddress` contient l'URI du service d'émission de jeton de sécurité avec lequel le client souhaite communiquer.</span><span class="sxs-lookup"><span data-stu-id="fd28e-132">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="fd28e-133">`behaviorConfiguration`pointe vers un comportement de point de terminaison que l’application utilise dans les canaux créés par Windows Communication Foundation (WCF) pour récupérer les jetons émis à partir des services d’émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="fd28e-133">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd28e-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd28e-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="fd28e-135">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="fd28e-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fd28e-136">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="fd28e-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="fd28e-137">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="fd28e-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fd28e-138">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="fd28e-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fd28e-139">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="fd28e-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="fd28e-140">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="fd28e-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="fd28e-141">Guide pratique pour Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="fd28e-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="fd28e-142">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="fd28e-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fd28e-143">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="fd28e-143">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
