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
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893158"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="11b37-102">\<issuerChannelBehaviors >, élément</span><span class="sxs-lookup"><span data-stu-id="11b37-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="11b37-103">Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) (définis dans la configuration) à utiliser lors de la communication avec les services de jeton de service spécifiés.</span><span class="sxs-lookup"><span data-stu-id="11b37-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="11b37-104">Les comportements définis ne peuvent pas inclure d' [ \<éléments > ClientCredentials](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="11b37-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="11b37-105">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="11b37-105">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="11b37-106">&nbsp;&nbsp;[\<System. serviceModel >](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="11b37-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="11b37-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<comportements >](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="11b37-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="11b37-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors >](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="11b37-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="11b37-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> de comportement](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="11b37-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="11b37-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials >](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="11b37-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="11b37-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken >](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="11b37-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="11b37-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="11b37-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="11b37-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11b37-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11b37-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="11b37-114">Attributes and elements</span></span>

<span data-ttu-id="11b37-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="11b37-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="11b37-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="11b37-116">Attributes</span></span>

<span data-ttu-id="11b37-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="11b37-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11b37-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="11b37-118">Child elements</span></span>

|<span data-ttu-id="11b37-119">Élément</span><span class="sxs-lookup"><span data-stu-id="11b37-119">Element</span></span>|<span data-ttu-id="11b37-120">Description</span><span class="sxs-lookup"><span data-stu-id="11b37-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11b37-121">\<add></span><span class="sxs-lookup"><span data-stu-id="11b37-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="11b37-122">Ajoute un comportement à la collection.</span><span class="sxs-lookup"><span data-stu-id="11b37-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="11b37-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="11b37-123">Parent elements</span></span>

|<span data-ttu-id="11b37-124">Élément</span><span class="sxs-lookup"><span data-stu-id="11b37-124">Element</span></span>|<span data-ttu-id="11b37-125">Description</span><span class="sxs-lookup"><span data-stu-id="11b37-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11b37-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="11b37-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="11b37-127">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="11b37-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11b37-128">Notes</span><span class="sxs-lookup"><span data-stu-id="11b37-128">Remarks</span></span>

<span data-ttu-id="11b37-129">Utilisez cet élément lorsque des comportements (autres que ceux qui contiennent des éléments `<clientCredentials>`) doivent être utilisés pour communiquer avec un service.</span><span class="sxs-lookup"><span data-stu-id="11b37-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="11b37-130">Par exemple, si un élément de [ \<comportement > DataContractSerializer](datacontractserializer-element.md) doit être inclus.</span><span class="sxs-lookup"><span data-stu-id="11b37-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="11b37-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11b37-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="11b37-132">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="11b37-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="11b37-133">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="11b37-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="11b37-134">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="11b37-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="11b37-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="11b37-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="11b37-136">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="11b37-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="11b37-137">Guide pratique : Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="11b37-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="11b37-138">Guide pratique : Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="11b37-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="11b37-139">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="11b37-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
