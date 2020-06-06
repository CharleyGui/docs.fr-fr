---
title: <add> de <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400700"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="45efc-102">\<add> de \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="45efc-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="45efc-103">Spécifie une stratégie d'autorisation pour la transformation de revendications.</span><span class="sxs-lookup"><span data-stu-id="45efc-103">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="45efc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45efc-104">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="45efc-105">Type</span><span class="sxs-lookup"><span data-stu-id="45efc-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45efc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="45efc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="45efc-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="45efc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45efc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="45efc-108">Attributes</span></span>  
  
|<span data-ttu-id="45efc-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="45efc-109">Attribute</span></span>|<span data-ttu-id="45efc-110">Description</span><span class="sxs-lookup"><span data-stu-id="45efc-110">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="45efc-111">Attribut String requis.</span><span class="sxs-lookup"><span data-stu-id="45efc-111">A required String attribute.</span></span><br /><br /> <span data-ttu-id="45efc-112">Le modèle de contrôle d’accès Windows Communication Foundation (WCF) prend en charge l’approvisionnement d’un ensemble de stratégies d’autorisation en tant que types.</span><span class="sxs-lookup"><span data-stu-id="45efc-112">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="45efc-113">Cet attribut spécifie une stratégie d'autorisation qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="45efc-113">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="45efc-114">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="45efc-114">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45efc-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="45efc-115">Child Elements</span></span>  
 <span data-ttu-id="45efc-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="45efc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45efc-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="45efc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="45efc-118">Élément</span><span class="sxs-lookup"><span data-stu-id="45efc-118">Element</span></span>|<span data-ttu-id="45efc-119">Description</span><span class="sxs-lookup"><span data-stu-id="45efc-119">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="45efc-120">Indique une collection de types de stratégie d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="45efc-120">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45efc-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="45efc-121">Remarks</span></span>  
 <span data-ttu-id="45efc-122">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="45efc-122">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="45efc-123">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="45efc-123">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="45efc-124">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="45efc-124">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="45efc-125">Pour plus d’informations sur le fonctionnement d’une stratégie d’autorisation, consultez <xref:System.IdentityModel.Policy.IAuthorizationPolicy> et [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="45efc-125">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45efc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45efc-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="45efc-127">Authorizing Access to Service Operations</span><span class="sxs-lookup"><span data-stu-id="45efc-127">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="45efc-128">Guide pratique pour créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="45efc-128">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="45efc-129">Authorization Policy</span><span class="sxs-lookup"><span data-stu-id="45efc-129">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
