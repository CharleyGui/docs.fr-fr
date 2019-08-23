---
title: <add> de <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920276"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="3b8e5-102">\<Ajouter > de \<la > AuthorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="3b8e5-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="3b8e5-103">Spécifie une stratégie d'autorisation pour la transformation de revendications.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="3b8e5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3b8e5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3b8e5-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="3b8e5-105">\<behaviors></span></span>  
<span data-ttu-id="3b8e5-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="3b8e5-106">\<behavior></span></span>  
<span data-ttu-id="3b8e5-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="3b8e5-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="3b8e5-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="3b8e5-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="3b8e5-109">\<add></span><span class="sxs-lookup"><span data-stu-id="3b8e5-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b8e5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b8e5-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="3b8e5-111">Type</span><span class="sxs-lookup"><span data-stu-id="3b8e5-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b8e5-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3b8e5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3b8e5-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b8e5-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="3b8e5-114">Attributes</span></span>  
  
|<span data-ttu-id="3b8e5-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="3b8e5-115">Attribute</span></span>|<span data-ttu-id="3b8e5-116">Description</span><span class="sxs-lookup"><span data-stu-id="3b8e5-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="3b8e5-117">Attribut String requis.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="3b8e5-118">Le modèle de contrôle d’accès Windows Communication Foundation (WCF) prend en charge l’approvisionnement d’un ensemble de stratégies d’autorisation en tant que types.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="3b8e5-119">Cet attribut spécifie une stratégie d'autorisation qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3b8e5-120">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b8e5-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3b8e5-121">Child Elements</span></span>  
 <span data-ttu-id="3b8e5-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b8e5-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3b8e5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3b8e5-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3b8e5-124">Element</span></span>|<span data-ttu-id="3b8e5-125">Description</span><span class="sxs-lookup"><span data-stu-id="3b8e5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b8e5-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="3b8e5-126">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="3b8e5-127">Indique une collection de types de stratégie d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b8e5-128">Notes</span><span class="sxs-lookup"><span data-stu-id="3b8e5-128">Remarks</span></span>  
 <span data-ttu-id="3b8e5-129">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="3b8e5-130">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3b8e5-131">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="3b8e5-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="3b8e5-132">Pour plus d’informations sur le fonctionnement d’une stratégie d' <xref:System.IdentityModel.Policy.IAuthorizationPolicy> autorisation, consultez et [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="3b8e5-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b8e5-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b8e5-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="3b8e5-134">Autorisation de l’accès aux opérations de service</span><span class="sxs-lookup"><span data-stu-id="3b8e5-134">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="3b8e5-135">Guide pratique pour Créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="3b8e5-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="3b8e5-136">\<add></span><span class="sxs-lookup"><span data-stu-id="3b8e5-136">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="3b8e5-137">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="3b8e5-137">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
