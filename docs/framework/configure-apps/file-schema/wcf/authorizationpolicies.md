---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926458"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="5dc44-101">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="5dc44-101">\<authorizationPolicies></span></span>
<span data-ttu-id="5dc44-102">Cette section de configuration contient une collection des types de stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="5dc44-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="5dc44-103">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5dc44-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="5dc44-104">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="5dc44-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="5dc44-105">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="5dc44-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="5dc44-106">Pour plus d’informations sur le fonctionnement d’une stratégie d' <xref:System.IdentityModel.Policy.IAuthorizationPolicy> autorisation, consultez et [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="5dc44-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc44-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dc44-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="5dc44-108">Autorisation de l’accès aux opérations de service</span><span class="sxs-lookup"><span data-stu-id="5dc44-108">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="5dc44-109">Guide pratique : Créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="5dc44-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="5dc44-110">\<add></span><span class="sxs-lookup"><span data-stu-id="5dc44-110">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="5dc44-111">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="5dc44-111">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
