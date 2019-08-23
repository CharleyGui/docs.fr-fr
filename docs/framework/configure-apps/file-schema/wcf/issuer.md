---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929371"
---
# <a name="issuer"></a><span data-ttu-id="ca653-101">\<émetteur ></span><span class="sxs-lookup"><span data-stu-id="ca653-101">\<issuer></span></span>
<span data-ttu-id="ca653-102">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ca653-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="ca653-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ca653-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ca653-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ca653-104">\<bindings></span></span>  
<span data-ttu-id="ca653-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ca653-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="ca653-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="ca653-106">\<binding></span></span>  
<span data-ttu-id="ca653-107">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="ca653-107">\<security></span></span>  
<span data-ttu-id="ca653-108">\<message></span><span class="sxs-lookup"><span data-stu-id="ca653-108">\<message></span></span>  
<span data-ttu-id="ca653-109">\<émetteur ></span><span class="sxs-lookup"><span data-stu-id="ca653-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca653-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca653-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca653-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ca653-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca653-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ca653-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca653-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="ca653-113">Attributes</span></span>  
  
|<span data-ttu-id="ca653-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="ca653-114">Attribute</span></span>|<span data-ttu-id="ca653-115">Description</span><span class="sxs-lookup"><span data-stu-id="ca653-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca653-116">adresse</span><span class="sxs-lookup"><span data-stu-id="ca653-116">address</span></span>|<span data-ttu-id="ca653-117">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="ca653-117">Required string.</span></span> <span data-ttu-id="ca653-118">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="ca653-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca653-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca653-119">Child Elements</span></span>  
  
|<span data-ttu-id="ca653-120">Élément</span><span class="sxs-lookup"><span data-stu-id="ca653-120">Element</span></span>|<span data-ttu-id="ca653-121">Description</span><span class="sxs-lookup"><span data-stu-id="ca653-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca653-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="ca653-122">\<headers></span></span>](headers-element.md)|<span data-ttu-id="ca653-123">Collection d'en-têtes d'adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="ca653-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="ca653-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="ca653-124">\<identity></span></span>](identity.md)|<span data-ttu-id="ca653-125">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="ca653-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca653-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca653-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ca653-127">Élément</span><span class="sxs-lookup"><span data-stu-id="ca653-127">Element</span></span>|<span data-ttu-id="ca653-128">Description</span><span class="sxs-lookup"><span data-stu-id="ca653-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca653-129">\<message></span><span class="sxs-lookup"><span data-stu-id="ca653-129">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="ca653-130">Définit les paramètres pour la sécurité au niveau du message pour l' [ \<élément WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ca653-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca653-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca653-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="ca653-132">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="ca653-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ca653-133">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ca653-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ca653-134">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="ca653-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ca653-135">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ca653-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ca653-136">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="ca653-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ca653-137">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ca653-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
