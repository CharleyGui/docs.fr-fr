---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854994"
---
# \<servicePrincipalName>
<span data-ttu-id="fc633-101">Spécifie l'identité d'un service par son nom de principal du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="fc633-101">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="fc633-102">Pour plus d’informations sur la définition du SPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fc633-102">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="fc633-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc633-103">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc633-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fc633-104">Attributes and Elements</span></span>  
 <span data-ttu-id="fc633-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fc633-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc633-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="fc633-106">Attributes</span></span>  
  
|<span data-ttu-id="fc633-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="fc633-107">Attribute</span></span>|<span data-ttu-id="fc633-108">Description</span><span class="sxs-lookup"><span data-stu-id="fc633-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc633-109">value</span><span class="sxs-lookup"><span data-stu-id="fc633-109">value</span></span>|<span data-ttu-id="fc633-110">Nom par lequel un client identifie de manière unique une instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="fc633-110">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="fc633-111">Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN.</span><span class="sxs-lookup"><span data-stu-id="fc633-111">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="fc633-112">Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="fc633-112">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc633-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fc633-113">Child Elements</span></span>  
 <span data-ttu-id="fc633-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fc633-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc633-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fc633-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fc633-116">Élément</span><span class="sxs-lookup"><span data-stu-id="fc633-116">Element</span></span>|<span data-ttu-id="fc633-117">Description</span><span class="sxs-lookup"><span data-stu-id="fc633-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="fc633-118">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="fc633-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc633-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="fc633-119">Remarks</span></span>  
 <span data-ttu-id="fc633-120">Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise le SPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="fc633-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc633-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc633-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="fc633-122">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="fc633-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
