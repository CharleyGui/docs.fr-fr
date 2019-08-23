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
# <a name="add-of-authorizationpolicies"></a>\<Ajouter > de \<la > AuthorizationPolicies
Spécifie une stratégie d'autorisation pour la transformation de revendications.  
  
 \<system.ServiceModel>  
\<behaviors>  
\<> de comportement  
\<serviceAuthorization>  
\<authorizationPolicies>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`policyType`|Attribut String requis.<br /><br /> Le modèle de contrôle d’accès Windows Communication Foundation (WCF) prend en charge l’approvisionnement d’un ensemble de stratégies d’autorisation en tant que types. Cet attribut spécifie une stratégie d'autorisation qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications. Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|Indique une collection de types de stratégie d’autorisation.|  
  
## <a name="remarks"></a>Notes  
 Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne. L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications. Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération. Pour plus d’informations sur le fonctionnement d’une stratégie d' <xref:System.IdentityModel.Policy.IAuthorizationPolicy> autorisation, consultez et [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Autorisation de l’accès aux opérations de service](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Guide pratique pour Créer un gestionnaire d’autorisations personnalisé pour un service](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [Stratégie d’autorisation](../../../wcf/samples/authorization-policy.md)
