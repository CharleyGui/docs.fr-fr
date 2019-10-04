---
title: <serviceAuthorization>, élément
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834020"
---
# <a name="serviceauthorization-element"></a>élément @no__t 0serviceAuthorization >

Spécifie les paramètres qui autorisent l'accès pour l'entretien des opérations

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<behaviors >** ](behaviors.md)\
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0behavior >** ](behavior-of-servicebehaviors.md)1
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1serviceAuthorization >**  

## <a name="syntax"></a>Syntaxe

```xml
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents :

### <a name="attributes"></a>Attributs

|Attribut|Description|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|Valeur booléenne qui spécifie si toutes les opérations du service personnifient l'appelant. La valeur par défaut est `false`.<br /><br /> Lorsqu'une opération de service spécifique personnifie l'appelant, le contexte du thread est basculé sur le contexte de l'appelant avant d'exécuter le service spécifié.|  
|principalPermissionMode|Définit la principal de sécurité utilisée pour effectuer les opérations sur le serveur. Les valeurs sont notamment les suivantes :<br /><br /> -Aucun<br />-   UseWindowsGroups<br />-   UseAspNetRoles<br />-Personnalisé<br /><br /> La valeur par défaut est UseWindowsGroups. La valeur est de type <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Pour plus d’informations sur l’utilisation de cet attribut, consultez [How à : Limitez l’accès avec la classe PrincipalPermissionAttribute @ no__t-0.|  
|roleProviderName|Chaîne qui spécifie le nom du fournisseur de rôles, qui fournit des informations de rôle pour une application de Windows Communication Foundation (WCF). La valeur par défaut est une chaîne vide.|  
|ServiceAuthorizationManagerType|Chaîne qui contient le type du gestionnaire d'autorisations de service. Pour plus d'informations, consultez <xref:System.ServiceModel.ServiceAuthorizationManager>.|  

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|  
|-------------|-----------------|  
|authorizationPolicies|Contient une collection des types de la stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`. Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne. L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications. Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération. Pour plus d'informations, consultez <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Contient une collection de paramètres pour le comportement d’un service.|  

## <a name="remarks"></a>Notes

Cette section contient des éléments qui affectent l'autorisation, les fournisseurs de rôles personnalisés et l'emprunt d'identité.  
  
L'attribut `principalPermissionMode` spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée. La valeur par défaut (`UseWindowsGroups`) spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, comme Administrateurs ou Utilisateurs. Vous pouvez également spécifier `UseAspNetRoles` pour utiliser un fournisseur de rôles personnalisé configuré sous l’élément @no__t -1system. Web >, comme indiqué dans le code suivant :

```xml
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```
  
Le code suivant illustre l' `roleProviderName` utilisé avec l’attribut `principalPermissionMode` :
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

Pour obtenir un exemple détaillé de l’utilisation de cet élément de configuration, consultez autorisation de l' [accès aux opérations de service et à](../../../wcf/samples/authorizing-access-to-service-operations.md) la [stratégie d’autorisation](../../../wcf/samples/authorization-policy.md).
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Autorisation de l’accès aux opérations de service](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Guide pratique pour Créer un gestionnaire d’autorisations personnalisé pour un service @ no__t-0
- [Guide pratique pour Restreindre l’accès avec la classe PrincipalPermissionAttribute @ no__t-0
- [Stratégie d’autorisation](../../../wcf/samples/authorization-policy.md)
