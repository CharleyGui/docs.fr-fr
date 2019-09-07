---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397894"
---
# <a name="issuermetadata"></a><span data-ttu-id="1246b-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="1246b-101">\<issuerMetadata></span></span>

<span data-ttu-id="1246b-102">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1246b-102">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1246b-103">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1246b-103">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1246b-104">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1246b-104">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1246b-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1246b-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1246b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="1246b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1246b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1246b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1246b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de messages**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1246b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1246b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="1246b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1246b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1246b-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
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
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1246b-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1246b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1246b-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1246b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1246b-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="1246b-113">Attributes</span></span>  
  
|<span data-ttu-id="1246b-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="1246b-114">Attribute</span></span>|<span data-ttu-id="1246b-115">Description</span><span class="sxs-lookup"><span data-stu-id="1246b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1246b-116">adresse</span><span class="sxs-lookup"><span data-stu-id="1246b-116">address</span></span>|<span data-ttu-id="1246b-117">Attribut `string` requis.</span><span class="sxs-lookup"><span data-stu-id="1246b-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="1246b-118">Spécifie l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1246b-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="1246b-119">L'adresse doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="1246b-119">The address must be an absolute URI.</span></span> <span data-ttu-id="1246b-120">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="1246b-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1246b-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1246b-121">Child Elements</span></span>  
  
|<span data-ttu-id="1246b-122">Élément</span><span class="sxs-lookup"><span data-stu-id="1246b-122">Element</span></span>|<span data-ttu-id="1246b-123">Description</span><span class="sxs-lookup"><span data-stu-id="1246b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1246b-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="1246b-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="1246b-125">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="1246b-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="1246b-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="1246b-126">\<identity></span></span>](identity.md)|<span data-ttu-id="1246b-127">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="1246b-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1246b-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1246b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="1246b-129">Élément</span><span class="sxs-lookup"><span data-stu-id="1246b-129">Element</span></span>|<span data-ttu-id="1246b-130">Description</span><span class="sxs-lookup"><span data-stu-id="1246b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1246b-131">\<message></span><span class="sxs-lookup"><span data-stu-id="1246b-131">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="1246b-132">Définit les paramètres pour la sécurité au niveau du message pour l' [ \<élément WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1246b-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1246b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1246b-133">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="1246b-134">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="1246b-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1246b-135">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="1246b-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1246b-136">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="1246b-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="1246b-137">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="1246b-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
