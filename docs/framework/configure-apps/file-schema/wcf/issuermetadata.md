---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 10a6d2aaad7d63d00b3a57032d0d218f756454d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175952"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="8d433-101">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d433-101">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d433-102">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8d433-102">Attributes and Elements</span></span>  

 <span data-ttu-id="8d433-103">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8d433-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d433-104">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d433-104">Attributes</span></span>  
  
|<span data-ttu-id="8d433-105">Attribut</span><span class="sxs-lookup"><span data-stu-id="8d433-105">Attribute</span></span>|<span data-ttu-id="8d433-106">Description</span><span class="sxs-lookup"><span data-stu-id="8d433-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d433-107">address</span><span class="sxs-lookup"><span data-stu-id="8d433-107">address</span></span>|<span data-ttu-id="8d433-108">Attribut `string` requis.</span><span class="sxs-lookup"><span data-stu-id="8d433-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="8d433-109">Spécifie l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8d433-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="8d433-110">L'adresse doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="8d433-110">The address must be an absolute URI.</span></span> <span data-ttu-id="8d433-111">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="8d433-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d433-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d433-112">Child Elements</span></span>  
  
|<span data-ttu-id="8d433-113">Élément</span><span class="sxs-lookup"><span data-stu-id="8d433-113">Element</span></span>|<span data-ttu-id="8d433-114">Description</span><span class="sxs-lookup"><span data-stu-id="8d433-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="8d433-115">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="8d433-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="8d433-116">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="8d433-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d433-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d433-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8d433-118">Élément</span><span class="sxs-lookup"><span data-stu-id="8d433-118">Element</span></span>|<span data-ttu-id="8d433-119">Description</span><span class="sxs-lookup"><span data-stu-id="8d433-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="8d433-120">Définit les paramètres pour la sécurité au niveau du message pour l' [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="8d433-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d433-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d433-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="8d433-122">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="8d433-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8d433-123">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="8d433-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8d433-124">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="8d433-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="8d433-125">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="8d433-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
