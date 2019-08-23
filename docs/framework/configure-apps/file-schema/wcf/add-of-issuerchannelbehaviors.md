---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920109"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="caf1b-102">\<Ajouter > de \<la > issuerChannelBehaviors</span><span class="sxs-lookup"><span data-stu-id="caf1b-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="caf1b-103">Ajoute un comportement de point de terminaison à utiliser lors de la communication avec un service STS.</span><span class="sxs-lookup"><span data-stu-id="caf1b-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="caf1b-104">Si un comportement de point de terminaison contient un [ \<élément ClientCredentials >](clientcredentials.md) , une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="caf1b-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="caf1b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="caf1b-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="caf1b-106">\<comportements > </span><span class="sxs-lookup"><span data-stu-id="caf1b-106">\<behaviors></span></span>\
<span data-ttu-id="caf1b-107">comportement de \<la section endpointBehaviors > </span><span class="sxs-lookup"><span data-stu-id="caf1b-107">endpointBehaviors section \<behavior></span></span>\
<span data-ttu-id="caf1b-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="caf1b-108">\<clientCredentials></span></span>\
<span data-ttu-id="caf1b-109">\<issuedToken > </span><span class="sxs-lookup"><span data-stu-id="caf1b-109">\<issuedToken></span></span>\
<span data-ttu-id="caf1b-110">\<issuerChannelBehaviors >, élément </span><span class="sxs-lookup"><span data-stu-id="caf1b-110">\<issuerChannelBehaviors> Element</span></span>\
<span data-ttu-id="caf1b-111">\<add></span><span class="sxs-lookup"><span data-stu-id="caf1b-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="caf1b-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caf1b-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="caf1b-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="caf1b-113">Attributes and Elements</span></span>

<span data-ttu-id="caf1b-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="caf1b-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="caf1b-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="caf1b-115">Attributes</span></span>

|<span data-ttu-id="caf1b-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="caf1b-116">Attribute</span></span>|<span data-ttu-id="caf1b-117">Description</span><span class="sxs-lookup"><span data-stu-id="caf1b-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="caf1b-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="caf1b-118">issuerAddress</span></span>|<span data-ttu-id="caf1b-119">URI de l'émetteur de jeton de sécurité avec lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="caf1b-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="caf1b-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="caf1b-120">behaviorConfiguration</span></span>|<span data-ttu-id="caf1b-121">Nom d'un comportement de point de terminaison défini dans le même fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="caf1b-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="caf1b-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="caf1b-122">Child Elements</span></span>

<span data-ttu-id="caf1b-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="caf1b-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="caf1b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="caf1b-124">Parent Elements</span></span>

|<span data-ttu-id="caf1b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="caf1b-125">Element</span></span>|<span data-ttu-id="caf1b-126">Description</span><span class="sxs-lookup"><span data-stu-id="caf1b-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="caf1b-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="caf1b-127">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="caf1b-128">Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) à utiliser lors de la communication avec les services de jeton de service spécifiés.</span><span class="sxs-lookup"><span data-stu-id="caf1b-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="caf1b-129">Notes</span><span class="sxs-lookup"><span data-stu-id="caf1b-129">Remarks</span></span>

<span data-ttu-id="caf1b-130">`issuerAddress` contient l'URI du service d'émission de jeton de sécurité avec lequel le client souhaite communiquer.</span><span class="sxs-lookup"><span data-stu-id="caf1b-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="caf1b-131">`behaviorConfiguration`pointe vers un comportement de point de terminaison que l’application utilise dans les canaux créés par Windows Communication Foundation (WCF) pour récupérer les jetons émis à partir des services d’émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="caf1b-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="caf1b-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caf1b-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="caf1b-133">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="caf1b-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="caf1b-134">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="caf1b-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="caf1b-135">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="caf1b-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="caf1b-136">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="caf1b-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="caf1b-137">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="caf1b-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="caf1b-138">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="caf1b-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="caf1b-139">Guide pratique pour Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="caf1b-139">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="caf1b-140">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="caf1b-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="caf1b-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="caf1b-141">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
