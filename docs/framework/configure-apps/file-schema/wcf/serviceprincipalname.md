---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 0d03844a58de5b4af93f276de75c88af6efed3f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153792"
---
# \<servicePrincipalName>

<span data-ttu-id="552d0-101">Spécifie l'identité d'un service par son nom de principal du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="552d0-101">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="552d0-102">Pour plus d’informations sur la définition du SPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="552d0-102">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="552d0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="552d0-103">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="552d0-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="552d0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="552d0-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="552d0-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="552d0-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="552d0-106">Attributes</span></span>  
  
|<span data-ttu-id="552d0-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="552d0-107">Attribute</span></span>|<span data-ttu-id="552d0-108">Description</span><span class="sxs-lookup"><span data-stu-id="552d0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="552d0-109">value</span><span class="sxs-lookup"><span data-stu-id="552d0-109">value</span></span>|<span data-ttu-id="552d0-110">Nom par lequel un client identifie de manière unique une instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="552d0-110">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="552d0-111">Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN.</span><span class="sxs-lookup"><span data-stu-id="552d0-111">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="552d0-112">Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="552d0-112">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="552d0-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="552d0-113">Child Elements</span></span>  

 <span data-ttu-id="552d0-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="552d0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="552d0-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="552d0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="552d0-116">Élément</span><span class="sxs-lookup"><span data-stu-id="552d0-116">Element</span></span>|<span data-ttu-id="552d0-117">Description</span><span class="sxs-lookup"><span data-stu-id="552d0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="552d0-118">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="552d0-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="552d0-119">Notes</span><span class="sxs-lookup"><span data-stu-id="552d0-119">Remarks</span></span>  

 <span data-ttu-id="552d0-120">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise le SPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="552d0-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="552d0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="552d0-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="552d0-122">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="552d0-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
