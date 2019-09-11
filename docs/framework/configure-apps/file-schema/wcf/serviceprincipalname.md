---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854994"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="306a7-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="306a7-101">\<servicePrincipalName></span></span>
<span data-ttu-id="306a7-102">Spécifie l'identité d'un service par son nom de principal du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="306a7-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="306a7-103">Pour plus d’informations sur la définition du SPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="306a7-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="306a7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="306a7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="306a7-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="306a7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="306a7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="306a7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="306a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<point de terminaison >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="306a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="306a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’identité**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="306a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="306a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<servicePrincipalName >**</span><span class="sxs-lookup"><span data-stu-id="306a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306a7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="306a7-110">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="306a7-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="306a7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="306a7-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="306a7-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="306a7-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="306a7-113">Attributes</span></span>  
  
|<span data-ttu-id="306a7-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="306a7-114">Attribute</span></span>|<span data-ttu-id="306a7-115">Description</span><span class="sxs-lookup"><span data-stu-id="306a7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="306a7-116">value</span><span class="sxs-lookup"><span data-stu-id="306a7-116">value</span></span>|<span data-ttu-id="306a7-117">Nom par lequel un client identifie de manière unique une instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="306a7-117">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="306a7-118">Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN.</span><span class="sxs-lookup"><span data-stu-id="306a7-118">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="306a7-119">Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="306a7-119">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="306a7-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="306a7-120">Child Elements</span></span>  
 <span data-ttu-id="306a7-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="306a7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="306a7-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="306a7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="306a7-123">Élément</span><span class="sxs-lookup"><span data-stu-id="306a7-123">Element</span></span>|<span data-ttu-id="306a7-124">Description</span><span class="sxs-lookup"><span data-stu-id="306a7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="306a7-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="306a7-125">\<identity></span></span>](identity.md)|<span data-ttu-id="306a7-126">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="306a7-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="306a7-127">Notes</span><span class="sxs-lookup"><span data-stu-id="306a7-127">Remarks</span></span>  
 <span data-ttu-id="306a7-128">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise le SPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="306a7-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306a7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="306a7-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="306a7-130">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="306a7-130">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="306a7-131">\<identity></span><span class="sxs-lookup"><span data-stu-id="306a7-131">\<identity></span></span>](identity.md)
