---
title: Élément <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893158"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="b2073-102">Élément \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="b2073-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="b2073-103">Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) (définis dans la configuration) à utiliser lors de la communication avec les services de jeton de service spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b2073-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="b2073-104">Les comportements définis ne peuvent pas inclure d' [\<clientCredentials>](clientcredentials.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="b2073-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a><span data-ttu-id="b2073-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2073-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2073-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b2073-106">Attributes and elements</span></span>

<span data-ttu-id="b2073-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b2073-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2073-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="b2073-108">Attributes</span></span>

<span data-ttu-id="b2073-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b2073-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2073-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b2073-110">Child elements</span></span>

|<span data-ttu-id="b2073-111">Élément</span><span class="sxs-lookup"><span data-stu-id="b2073-111">Element</span></span>|<span data-ttu-id="b2073-112">Description</span><span class="sxs-lookup"><span data-stu-id="b2073-112">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="b2073-113">Ajoute un comportement à la collection.</span><span class="sxs-lookup"><span data-stu-id="b2073-113">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b2073-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b2073-114">Parent elements</span></span>

|<span data-ttu-id="b2073-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b2073-115">Element</span></span>|<span data-ttu-id="b2073-116">Description</span><span class="sxs-lookup"><span data-stu-id="b2073-116">Description</span></span>|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="b2073-117">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="b2073-117">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2073-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="b2073-118">Remarks</span></span>

<span data-ttu-id="b2073-119">Utilisez cet élément lorsque des comportements (autres que ceux qui contiennent des éléments `<clientCredentials>`) doivent être utilisés pour communiquer avec un service.</span><span class="sxs-lookup"><span data-stu-id="b2073-119">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="b2073-120">Par exemple, si un [\<dataContractSerializer>](datacontractserializer-element.md) élément de comportement doit être inclus.</span><span class="sxs-lookup"><span data-stu-id="b2073-120">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2073-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2073-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="b2073-122">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="b2073-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b2073-123">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="b2073-123">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b2073-124">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="b2073-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b2073-125">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="b2073-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b2073-126">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="b2073-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b2073-127">Comment : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="b2073-127">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="b2073-128">Comment : configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="b2073-128">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="b2073-129">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="b2073-129">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
