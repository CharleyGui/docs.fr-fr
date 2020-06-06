---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854823"
---
# \<userPrincipalName>
<span data-ttu-id="cfdd0-101">Indique le nom d'utilisateur principal (UPN) d'un service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="cfdd0-102">Pour plus d’informations sur la définition de l’UPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="cfdd0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfdd0-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfdd0-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cfdd0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="cfdd0-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfdd0-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="cfdd0-106">Attributes</span></span>  
  
|<span data-ttu-id="cfdd0-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="cfdd0-107">Attribute</span></span>|<span data-ttu-id="cfdd0-108">Description</span><span class="sxs-lookup"><span data-stu-id="cfdd0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfdd0-109">value</span><span class="sxs-lookup"><span data-stu-id="cfdd0-109">value</span></span>|<span data-ttu-id="cfdd0-110">Nom de compte d'utilisateur (parfois connu sous le nom de connexion d'utilisateur) et nom de domaine identifiant le domaine dans lequel se trouve le compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="cfdd0-111">Il s'agit de la méthode de connexion standard à un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="cfdd0-112">Le format est le suivant : someone@example.com (comme pour une adresse de messagerie).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfdd0-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cfdd0-113">Child Elements</span></span>  
 <span data-ttu-id="cfdd0-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfdd0-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cfdd0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="cfdd0-116">Élément</span><span class="sxs-lookup"><span data-stu-id="cfdd0-116">Element</span></span>|<span data-ttu-id="cfdd0-117">Description</span><span class="sxs-lookup"><span data-stu-id="cfdd0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="cfdd0-118">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfdd0-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="cfdd0-119">Remarks</span></span>  
 <span data-ttu-id="cfdd0-120">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise l’UPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfdd0-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="cfdd0-121">Example</span></span>  
 <span data-ttu-id="cfdd0-122">Le code de configuration suivant indique le nom UPN du service devant être authentifié par le client.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="cfdd0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfdd0-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="cfdd0-124">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="cfdd0-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
