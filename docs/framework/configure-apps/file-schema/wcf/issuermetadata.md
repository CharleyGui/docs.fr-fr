---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: bf512c427637ca65a7271ec8300a373a38632108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913519"
---
# <a name="issuermetadata"></a><span data-ttu-id="aa61c-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="aa61c-101">\<issuerMetadata></span></span>
<span data-ttu-id="aa61c-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aa61c-102">\<system.serviceModel></span></span>  
<span data-ttu-id="aa61c-103">\<bindings></span><span class="sxs-lookup"><span data-stu-id="aa61c-103">\<bindings></span></span>  
<span data-ttu-id="aa61c-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="aa61c-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="aa61c-105">\<binding></span><span class="sxs-lookup"><span data-stu-id="aa61c-105">\<binding></span></span>  
<span data-ttu-id="aa61c-106">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="aa61c-106">\<security></span></span>  
<span data-ttu-id="aa61c-107">\<message></span><span class="sxs-lookup"><span data-stu-id="aa61c-107">\<message></span></span>  
<span data-ttu-id="aa61c-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="aa61c-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa61c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa61c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa61c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="aa61c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aa61c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="aa61c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa61c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="aa61c-112">Attributes</span></span>  
  
|<span data-ttu-id="aa61c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="aa61c-113">Attribute</span></span>|<span data-ttu-id="aa61c-114">Description</span><span class="sxs-lookup"><span data-stu-id="aa61c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa61c-115">adresse</span><span class="sxs-lookup"><span data-stu-id="aa61c-115">address</span></span>|<span data-ttu-id="aa61c-116">Attribut `string` requis.</span><span class="sxs-lookup"><span data-stu-id="aa61c-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="aa61c-117">Spécifie l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="aa61c-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="aa61c-118">L'adresse doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="aa61c-118">The address must be an absolute URI.</span></span> <span data-ttu-id="aa61c-119">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="aa61c-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa61c-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aa61c-120">Child Elements</span></span>  
  
|<span data-ttu-id="aa61c-121">Élément</span><span class="sxs-lookup"><span data-stu-id="aa61c-121">Element</span></span>|<span data-ttu-id="aa61c-122">Description</span><span class="sxs-lookup"><span data-stu-id="aa61c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa61c-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="aa61c-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="aa61c-124">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="aa61c-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="aa61c-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="aa61c-125">\<identity></span></span>](identity.md)|<span data-ttu-id="aa61c-126">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="aa61c-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa61c-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aa61c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="aa61c-128">Élément</span><span class="sxs-lookup"><span data-stu-id="aa61c-128">Element</span></span>|<span data-ttu-id="aa61c-129">Description</span><span class="sxs-lookup"><span data-stu-id="aa61c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa61c-130">\<message></span><span class="sxs-lookup"><span data-stu-id="aa61c-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="aa61c-131">Définit les paramètres pour la sécurité au niveau du message pour l' [ \<élément WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="aa61c-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa61c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa61c-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="aa61c-133">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="aa61c-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="aa61c-134">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="aa61c-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="aa61c-135">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="aa61c-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="aa61c-136">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="aa61c-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
