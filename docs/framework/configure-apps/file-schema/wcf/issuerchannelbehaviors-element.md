---
title: Élément <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 2c0e0d8d041565edd25c4b2c2802bfd2a589b4f7
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397899"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="0a41a-102">\<issuerChannelBehaviors >, élément</span><span class="sxs-lookup"><span data-stu-id="0a41a-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="0a41a-103">Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) (définis dans la configuration) à utiliser lors de la communication avec les services de jeton de service spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0a41a-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="0a41a-104">Les comportements définis ne peuvent pas inclure d' [ \<éléments > ClientCredentials](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="0a41a-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="0a41a-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0a41a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0a41a-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0a41a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0a41a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0a41a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="0a41a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0a41a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="0a41a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0a41a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="0a41a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="0a41a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="0a41a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="0a41a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="0a41a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerChannelBehaviors >**</span><span class="sxs-lookup"><span data-stu-id="0a41a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerChannelBehaviors>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="0a41a-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a41a-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a41a-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0a41a-114">Attributes and Elements</span></span>

<span data-ttu-id="0a41a-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0a41a-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a41a-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="0a41a-116">Attributes</span></span>

<span data-ttu-id="0a41a-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0a41a-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a41a-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0a41a-118">Child Elements</span></span>

|<span data-ttu-id="0a41a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="0a41a-119">Element</span></span>|<span data-ttu-id="0a41a-120">Description</span><span class="sxs-lookup"><span data-stu-id="0a41a-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a41a-121">\<add></span><span class="sxs-lookup"><span data-stu-id="0a41a-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="0a41a-122">Ajoute un comportement à la collection.</span><span class="sxs-lookup"><span data-stu-id="0a41a-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0a41a-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0a41a-123">Parent Elements</span></span>

|<span data-ttu-id="0a41a-124">Élément</span><span class="sxs-lookup"><span data-stu-id="0a41a-124">Element</span></span>|<span data-ttu-id="0a41a-125">Description</span><span class="sxs-lookup"><span data-stu-id="0a41a-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a41a-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="0a41a-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="0a41a-127">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="0a41a-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0a41a-128">Notes</span><span class="sxs-lookup"><span data-stu-id="0a41a-128">Remarks</span></span>

<span data-ttu-id="0a41a-129">Utilisez cet élément lorsque des comportements (autres que ceux qui contiennent des éléments `<clientCredentials>`) doivent être utilisés pour communiquer avec un service.</span><span class="sxs-lookup"><span data-stu-id="0a41a-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="0a41a-130">Par exemple, si un élément de [ \<comportement > DataContractSerializer](datacontractserializer-element.md) doit être inclus.</span><span class="sxs-lookup"><span data-stu-id="0a41a-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a41a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a41a-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="0a41a-132">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="0a41a-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0a41a-133">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="0a41a-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0a41a-134">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="0a41a-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0a41a-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0a41a-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0a41a-136">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="0a41a-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0a41a-137">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="0a41a-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="0a41a-138">Guide pratique : Configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="0a41a-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="0a41a-139">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="0a41a-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
