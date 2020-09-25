---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 353d3e2d88e3515e54deadab85c37ce3be26ef29
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203863"
---
# \<userPrincipalName>

<span data-ttu-id="bfcc5-101">Indique le nom d'utilisateur principal (UPN) d'un service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="bfcc5-102">Pour plus d’informations sur la définition de l’UPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bfcc5-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="bfcc5-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfcc5-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfcc5-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bfcc5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bfcc5-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfcc5-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="bfcc5-106">Attributes</span></span>  
  
|<span data-ttu-id="bfcc5-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="bfcc5-107">Attribute</span></span>|<span data-ttu-id="bfcc5-108">Description</span><span class="sxs-lookup"><span data-stu-id="bfcc5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bfcc5-109">value</span><span class="sxs-lookup"><span data-stu-id="bfcc5-109">value</span></span>|<span data-ttu-id="bfcc5-110">Nom de compte d'utilisateur (parfois connu sous le nom de connexion d'utilisateur) et nom de domaine identifiant le domaine dans lequel se trouve le compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="bfcc5-111">Il s'agit de la méthode de connexion standard à un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="bfcc5-112">Le format est le suivant : someone@example.com (comme pour une adresse de messagerie).</span><span class="sxs-lookup"><span data-stu-id="bfcc5-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfcc5-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bfcc5-113">Child Elements</span></span>  

 <span data-ttu-id="bfcc5-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfcc5-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bfcc5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bfcc5-116">Élément</span><span class="sxs-lookup"><span data-stu-id="bfcc5-116">Element</span></span>|<span data-ttu-id="bfcc5-117">Description</span><span class="sxs-lookup"><span data-stu-id="bfcc5-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="bfcc5-118">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfcc5-119">Notes</span><span class="sxs-lookup"><span data-stu-id="bfcc5-119">Remarks</span></span>  

 <span data-ttu-id="bfcc5-120">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise l’UPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfcc5-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="bfcc5-121">Example</span></span>  

 <span data-ttu-id="bfcc5-122">Le code de configuration suivant indique le nom UPN du service devant être authentifié par le client.</span><span class="sxs-lookup"><span data-stu-id="bfcc5-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="bfcc5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfcc5-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="bfcc5-124">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="bfcc5-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
