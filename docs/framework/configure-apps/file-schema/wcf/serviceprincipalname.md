---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936151"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="2fc99-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="2fc99-101">\<servicePrincipalName></span></span>
<span data-ttu-id="2fc99-102">Spécifie l'identité d'un service par son nom de principal du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="2fc99-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="2fc99-103">Pour plus d’informations sur la définition du SPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2fc99-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="2fc99-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="2fc99-104">\<identity></span></span>  
<span data-ttu-id="2fc99-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="2fc99-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc99-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fc99-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fc99-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2fc99-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2fc99-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2fc99-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fc99-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2fc99-109">Attributes</span></span>  
  
|<span data-ttu-id="2fc99-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2fc99-110">Attribute</span></span>|<span data-ttu-id="2fc99-111">Description</span><span class="sxs-lookup"><span data-stu-id="2fc99-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fc99-112">value</span><span class="sxs-lookup"><span data-stu-id="2fc99-112">value</span></span>|<span data-ttu-id="2fc99-113">Nom par lequel un client identifie de manière unique une instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="2fc99-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="2fc99-114">Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN.</span><span class="sxs-lookup"><span data-stu-id="2fc99-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="2fc99-115">Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="2fc99-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fc99-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2fc99-116">Child Elements</span></span>  
 <span data-ttu-id="2fc99-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2fc99-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fc99-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2fc99-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2fc99-119">Élément</span><span class="sxs-lookup"><span data-stu-id="2fc99-119">Element</span></span>|<span data-ttu-id="2fc99-120">Description</span><span class="sxs-lookup"><span data-stu-id="2fc99-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fc99-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="2fc99-121">\<identity></span></span>](identity.md)|<span data-ttu-id="2fc99-122">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="2fc99-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fc99-123">Notes</span><span class="sxs-lookup"><span data-stu-id="2fc99-123">Remarks</span></span>  
 <span data-ttu-id="2fc99-124">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise le SPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2fc99-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc99-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fc99-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="2fc99-126">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="2fc99-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2fc99-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="2fc99-127">\<identity></span></span>](identity.md)
