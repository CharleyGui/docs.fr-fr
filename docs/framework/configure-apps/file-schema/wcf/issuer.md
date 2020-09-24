---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 9e92bbcacf529a97e1ae936e93e38c98eab19cab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157263"
---
# \<issuer>

<span data-ttu-id="7bc3d-101">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7bc3d-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="7bc3d-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bc3d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bc3d-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7bc3d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7bc3d-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7bc3d-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bc3d-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7bc3d-105">Attributes</span></span>  
  
|<span data-ttu-id="7bc3d-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="7bc3d-106">Attribute</span></span>|<span data-ttu-id="7bc3d-107">Description</span><span class="sxs-lookup"><span data-stu-id="7bc3d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bc3d-108">address</span><span class="sxs-lookup"><span data-stu-id="7bc3d-108">address</span></span>|<span data-ttu-id="7bc3d-109">Chaîne obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7bc3d-109">Required string.</span></span> <span data-ttu-id="7bc3d-110">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="7bc3d-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bc3d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7bc3d-111">Child Elements</span></span>  
  
|<span data-ttu-id="7bc3d-112">Élément</span><span class="sxs-lookup"><span data-stu-id="7bc3d-112">Element</span></span>|<span data-ttu-id="7bc3d-113">Description</span><span class="sxs-lookup"><span data-stu-id="7bc3d-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="7bc3d-114">Collection d'en-têtes d'adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="7bc3d-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="7bc3d-115">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="7bc3d-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7bc3d-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7bc3d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7bc3d-117">Élément</span><span class="sxs-lookup"><span data-stu-id="7bc3d-117">Element</span></span>|<span data-ttu-id="7bc3d-118">Description</span><span class="sxs-lookup"><span data-stu-id="7bc3d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="7bc3d-119">Définit les paramètres pour la sécurité au niveau du message pour l' [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="7bc3d-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bc3d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bc3d-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="7bc3d-121">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="7bc3d-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7bc3d-122">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="7bc3d-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7bc3d-123">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="7bc3d-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7bc3d-124">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="7bc3d-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7bc3d-125">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="7bc3d-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7bc3d-126">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="7bc3d-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
