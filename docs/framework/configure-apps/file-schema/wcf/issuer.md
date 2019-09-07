---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397918"
---
# <a name="issuer"></a><span data-ttu-id="ad40f-101">\<émetteur ></span><span class="sxs-lookup"><span data-stu-id="ad40f-101">\<issuer></span></span>
<span data-ttu-id="ad40f-102">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ad40f-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="ad40f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad40f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ad40f-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ad40f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ad40f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ad40f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ad40f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ad40f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="ad40f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="ad40f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ad40f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ad40f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="ad40f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de messages**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ad40f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="ad40f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<émetteur >**</span><span class="sxs-lookup"><span data-stu-id="ad40f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad40f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad40f-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad40f-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ad40f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ad40f-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ad40f-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad40f-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ad40f-114">Attributes</span></span>  
  
|<span data-ttu-id="ad40f-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="ad40f-115">Attribute</span></span>|<span data-ttu-id="ad40f-116">Description</span><span class="sxs-lookup"><span data-stu-id="ad40f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad40f-117">adresse</span><span class="sxs-lookup"><span data-stu-id="ad40f-117">address</span></span>|<span data-ttu-id="ad40f-118">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="ad40f-118">Required string.</span></span> <span data-ttu-id="ad40f-119">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="ad40f-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad40f-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ad40f-120">Child Elements</span></span>  
  
|<span data-ttu-id="ad40f-121">Élément</span><span class="sxs-lookup"><span data-stu-id="ad40f-121">Element</span></span>|<span data-ttu-id="ad40f-122">Description</span><span class="sxs-lookup"><span data-stu-id="ad40f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad40f-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="ad40f-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="ad40f-124">Collection d'en-têtes d'adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="ad40f-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="ad40f-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="ad40f-125">\<identity></span></span>](identity.md)|<span data-ttu-id="ad40f-126">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="ad40f-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad40f-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ad40f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ad40f-128">Élément</span><span class="sxs-lookup"><span data-stu-id="ad40f-128">Element</span></span>|<span data-ttu-id="ad40f-129">Description</span><span class="sxs-lookup"><span data-stu-id="ad40f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad40f-130">\<message></span><span class="sxs-lookup"><span data-stu-id="ad40f-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="ad40f-131">Définit les paramètres pour la sécurité au niveau du message pour l' [ \<élément WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ad40f-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad40f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad40f-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="ad40f-133">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="ad40f-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ad40f-134">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ad40f-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ad40f-135">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="ad40f-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ad40f-136">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ad40f-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ad40f-137">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="ad40f-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ad40f-138">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ad40f-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
