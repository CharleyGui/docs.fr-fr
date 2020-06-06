---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398329"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="841fa-102">\<add> de \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="841fa-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="841fa-103">Ajoute un comportement de point de terminaison à utiliser lors de la communication avec un service STS.</span><span class="sxs-lookup"><span data-stu-id="841fa-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="841fa-104">Si un comportement de point de terminaison contient un [\<clientCredentials>](clientcredentials.md) élément, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="841fa-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="841fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="841fa-105">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="841fa-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="841fa-106">Attributes and Elements</span></span>

<span data-ttu-id="841fa-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="841fa-107">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="841fa-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="841fa-108">Attributes</span></span>

|<span data-ttu-id="841fa-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="841fa-109">Attribute</span></span>|<span data-ttu-id="841fa-110">Description</span><span class="sxs-lookup"><span data-stu-id="841fa-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="841fa-111">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="841fa-111">issuerAddress</span></span>|<span data-ttu-id="841fa-112">URI de l'émetteur de jeton de sécurité avec lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="841fa-112">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="841fa-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="841fa-113">behaviorConfiguration</span></span>|<span data-ttu-id="841fa-114">Nom d'un comportement de point de terminaison défini dans le même fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="841fa-114">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="841fa-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="841fa-115">Child Elements</span></span>

<span data-ttu-id="841fa-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="841fa-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="841fa-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="841fa-117">Parent Elements</span></span>

|<span data-ttu-id="841fa-118">Élément</span><span class="sxs-lookup"><span data-stu-id="841fa-118">Element</span></span>|<span data-ttu-id="841fa-119">Description</span><span class="sxs-lookup"><span data-stu-id="841fa-119">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="841fa-120">Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) à utiliser lors de la communication avec les services de jeton de service spécifiés.</span><span class="sxs-lookup"><span data-stu-id="841fa-120">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="841fa-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="841fa-121">Remarks</span></span>

<span data-ttu-id="841fa-122">`issuerAddress` contient l'URI du service d'émission de jeton de sécurité avec lequel le client souhaite communiquer.</span><span class="sxs-lookup"><span data-stu-id="841fa-122">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="841fa-123">`behaviorConfiguration`pointe vers un comportement de point de terminaison que l’application utilise dans les canaux créés par Windows Communication Foundation (WCF) pour récupérer les jetons émis à partir des services d’émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="841fa-123">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="841fa-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="841fa-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="841fa-125">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="841fa-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="841fa-126">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="841fa-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="841fa-127">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="841fa-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="841fa-128">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="841fa-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="841fa-129">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="841fa-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="841fa-130">Comment : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="841fa-130">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="841fa-131">Comment : configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="841fa-131">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="841fa-132">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="841fa-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
