---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940516"
---
# <a name="userprincipalname"></a><span data-ttu-id="75b9a-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="75b9a-101">\<userPrincipalName></span></span>
<span data-ttu-id="75b9a-102">Indique le nom d'utilisateur principal (UPN) d'un service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="75b9a-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="75b9a-103">Pour plus d’informations sur la définition de l’UPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="75b9a-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="75b9a-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="75b9a-104">\<identity></span></span>  
<span data-ttu-id="75b9a-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="75b9a-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b9a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75b9a-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75b9a-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75b9a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="75b9a-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="75b9a-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75b9a-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="75b9a-109">Attributes</span></span>  
  
|<span data-ttu-id="75b9a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="75b9a-110">Attribute</span></span>|<span data-ttu-id="75b9a-111">Description</span><span class="sxs-lookup"><span data-stu-id="75b9a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75b9a-112">value</span><span class="sxs-lookup"><span data-stu-id="75b9a-112">value</span></span>|<span data-ttu-id="75b9a-113">Nom de compte d'utilisateur (parfois connu sous le nom de connexion d'utilisateur) et nom de domaine identifiant le domaine dans lequel se trouve le compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="75b9a-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="75b9a-114">Il s'agit de la méthode de connexion standard à un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="75b9a-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="75b9a-115">Le format est le someone@example.com suivant: (comme pour une adresse de messagerie).</span><span class="sxs-lookup"><span data-stu-id="75b9a-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75b9a-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75b9a-116">Child Elements</span></span>  
 <span data-ttu-id="75b9a-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="75b9a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75b9a-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75b9a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="75b9a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="75b9a-119">Element</span></span>|<span data-ttu-id="75b9a-120">Description</span><span class="sxs-lookup"><span data-stu-id="75b9a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75b9a-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="75b9a-121">\<identity></span></span>](identity.md)|<span data-ttu-id="75b9a-122">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="75b9a-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75b9a-123">Notes</span><span class="sxs-lookup"><span data-stu-id="75b9a-123">Remarks</span></span>  
 <span data-ttu-id="75b9a-124">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise l’UPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="75b9a-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75b9a-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="75b9a-125">Example</span></span>  
 <span data-ttu-id="75b9a-126">Le code de configuration suivant indique le nom UPN du service devant être authentifié par le client.</span><span class="sxs-lookup"><span data-stu-id="75b9a-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="75b9a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75b9a-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="75b9a-128">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="75b9a-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="75b9a-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="75b9a-129">\<identity></span></span>](identity.md)
