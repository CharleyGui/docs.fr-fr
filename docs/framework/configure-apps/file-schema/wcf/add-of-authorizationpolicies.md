---
title: <add> de <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400700"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="e79f7-102">\<Ajouter > de \<la > AuthorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="e79f7-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="e79f7-103">Spécifie une stratégie d'autorisation pour la transformation de revendications.</span><span class="sxs-lookup"><span data-stu-id="e79f7-103">Specifies an authorization policy for claim transformation.</span></span>  
  
<span data-ttu-id="e79f7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e79f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e79f7-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e79f7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e79f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e79f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e79f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e79f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="e79f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e79f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="e79f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceAuthorization >** ](serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="e79f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)</span></span>\
<span data-ttu-id="e79f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authorizationPolicies >** ](authorizationpolicies.md)</span><span class="sxs-lookup"><span data-stu-id="e79f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)</span></span>\
<span data-ttu-id="e79f7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="e79f7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e79f7-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e79f7-112">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="e79f7-113">Type</span><span class="sxs-lookup"><span data-stu-id="e79f7-113">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e79f7-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e79f7-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e79f7-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e79f7-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e79f7-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="e79f7-116">Attributes</span></span>  
  
|<span data-ttu-id="e79f7-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="e79f7-117">Attribute</span></span>|<span data-ttu-id="e79f7-118">Description</span><span class="sxs-lookup"><span data-stu-id="e79f7-118">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="e79f7-119">Attribut String requis.</span><span class="sxs-lookup"><span data-stu-id="e79f7-119">A required String attribute.</span></span><br /><br /> <span data-ttu-id="e79f7-120">Le modèle de contrôle d’accès Windows Communication Foundation (WCF) prend en charge l’approvisionnement d’un ensemble de stratégies d’autorisation en tant que types.</span><span class="sxs-lookup"><span data-stu-id="e79f7-120">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="e79f7-121">Cet attribut spécifie une stratégie d'autorisation qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="e79f7-121">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e79f7-122">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="e79f7-122">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e79f7-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e79f7-123">Child Elements</span></span>  
 <span data-ttu-id="e79f7-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e79f7-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e79f7-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e79f7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e79f7-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e79f7-126">Element</span></span>|<span data-ttu-id="e79f7-127">Description</span><span class="sxs-lookup"><span data-stu-id="e79f7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e79f7-128">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="e79f7-128">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="e79f7-129">Indique une collection de types de stratégie d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="e79f7-129">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e79f7-130">Notes</span><span class="sxs-lookup"><span data-stu-id="e79f7-130">Remarks</span></span>  
 <span data-ttu-id="e79f7-131">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e79f7-131">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="e79f7-132">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="e79f7-132">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e79f7-133">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="e79f7-133">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="e79f7-134">Pour plus d’informations sur le fonctionnement d’une stratégie d' <xref:System.IdentityModel.Policy.IAuthorizationPolicy> autorisation, consultez et [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="e79f7-134">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79f7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e79f7-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="e79f7-136">Autorisation de l’accès aux opérations de service</span><span class="sxs-lookup"><span data-stu-id="e79f7-136">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="e79f7-137">Guide pratique pour Créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="e79f7-137">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="e79f7-138">\<add></span><span class="sxs-lookup"><span data-stu-id="e79f7-138">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="e79f7-139">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="e79f7-139">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
