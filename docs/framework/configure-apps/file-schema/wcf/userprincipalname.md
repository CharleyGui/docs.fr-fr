---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854823"
---
# <a name="userprincipalname"></a><span data-ttu-id="bed88-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="bed88-101">\<userPrincipalName></span></span>
<span data-ttu-id="bed88-102">Indique le nom d'utilisateur principal (UPN) d'un service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="bed88-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="bed88-103">Pour plus d’informations sur la définition de l’UPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bed88-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="bed88-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bed88-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bed88-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bed88-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bed88-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="bed88-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="bed88-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<point de terminaison >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="bed88-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="bed88-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’identité**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="bed88-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="bed88-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="bed88-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed88-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bed88-110">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bed88-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bed88-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bed88-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bed88-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bed88-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="bed88-113">Attributes</span></span>  
  
|<span data-ttu-id="bed88-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="bed88-114">Attribute</span></span>|<span data-ttu-id="bed88-115">Description</span><span class="sxs-lookup"><span data-stu-id="bed88-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bed88-116">value</span><span class="sxs-lookup"><span data-stu-id="bed88-116">value</span></span>|<span data-ttu-id="bed88-117">Nom de compte d'utilisateur (parfois connu sous le nom de connexion d'utilisateur) et nom de domaine identifiant le domaine dans lequel se trouve le compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bed88-117">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="bed88-118">Il s'agit de la méthode de connexion standard à un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="bed88-118">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="bed88-119">Le format est le someone@example.com suivant : (comme pour une adresse de messagerie).</span><span class="sxs-lookup"><span data-stu-id="bed88-119">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bed88-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bed88-120">Child Elements</span></span>  
 <span data-ttu-id="bed88-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bed88-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bed88-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bed88-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bed88-123">Élément</span><span class="sxs-lookup"><span data-stu-id="bed88-123">Element</span></span>|<span data-ttu-id="bed88-124">Description</span><span class="sxs-lookup"><span data-stu-id="bed88-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bed88-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="bed88-125">\<identity></span></span>](identity.md)|<span data-ttu-id="bed88-126">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="bed88-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bed88-127">Notes</span><span class="sxs-lookup"><span data-stu-id="bed88-127">Remarks</span></span>  
 <span data-ttu-id="bed88-128">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise l’UPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="bed88-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bed88-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="bed88-129">Example</span></span>  
 <span data-ttu-id="bed88-130">Le code de configuration suivant indique le nom UPN du service devant être authentifié par le client.</span><span class="sxs-lookup"><span data-stu-id="bed88-130">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="bed88-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bed88-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="bed88-132">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="bed88-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="bed88-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="bed88-133">\<identity></span></span>](identity.md)
