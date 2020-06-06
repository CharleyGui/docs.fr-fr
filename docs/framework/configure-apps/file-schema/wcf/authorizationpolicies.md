---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926458"
---
# \<authorizationPolicies>
<span data-ttu-id="9a736-101">Cette section de configuration contient une collection des types de stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="9a736-101">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="9a736-102">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9a736-102">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="9a736-103">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="9a736-103">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="9a736-104">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="9a736-104">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="9a736-105">Pour plus d’informations sur le fonctionnement d’une stratégie d’autorisation, consultez <xref:System.IdentityModel.Policy.IAuthorizationPolicy> et [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="9a736-105">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a736-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a736-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="9a736-107">Authorizing Access to Service Operations</span><span class="sxs-lookup"><span data-stu-id="9a736-107">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="9a736-108">Guide pratique pour créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="9a736-108">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="9a736-109">Authorization Policy</span><span class="sxs-lookup"><span data-stu-id="9a736-109">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
