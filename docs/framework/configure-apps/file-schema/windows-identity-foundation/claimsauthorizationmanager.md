---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 74ca031f7017d51adaa7a71593f537b64abbeae6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942888"
---
# <a name="claimsauthorizationmanager"></a>\<claimsAuthorizationManager>
Inscrit un gestionnaire d’autorisations des revendications pour les revendications entrantes.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthorizationManager>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe. Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 S’il n’y `type` a aucun attribut, ou `type` si l’attribut <xref:System.Security.Claims.ClaimsAuthenticationManager> fait référence à `<claimsAuthorizationManager>` la classe, l’élément ne prend pas d’éléments enfants; <xref:System.Security.Claims.ClaimsAuthorizationManager> Toutefois, les classes dérivées de peuvent définir des éléments de configuration enfants.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
  
## <a name="remarks"></a>Notes  
 Le comportement par défaut fourni par <xref:System.Security.Claims.ClaimsAuthorizationManager> la classe autorise toujours les revendications entrantes. Si aucun `type` attribut n’est spécifié ou si `type` l’attribut spécifie la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe `<claimsAuthorizationManager>` , l’élément ne prend pas d’éléments enfants. Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe afin d’implémenter un comportement personnalisé. Les classes dérivées peuvent prendre en charge la configuration `<claimsAuthorizationManager>` par le biais d’éléments <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> enfants de l’élément en substituant la méthode pour gérer ces éléments. Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.  
  
> [!IMPORTANT]
> Lors de l' <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisation de <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> la classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, la configuration d’identité `<federationConfiguration>` référencée par l’élément configure le gestionnaire d’autorisation des revendications et la stratégie utilisée pour effectuer décisions d’autorisation. Cela est vrai, même dans les scénarios qui ne sont pas des scénarios Web passifs, par exemple des applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive `<claimsAuthorizationManager>` , l’élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration d’identité référencée sont les seuls paramètres appliqués. Tous les autres paramètres sont ignorés. Pour plus d’informations, consultez l' [ \<élément federationConfiguration >](federationconfiguration.md) .  
  
 Cet élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemples  
 Le code XML suivant montre la configuration d’un gestionnaire d’autorisations pour les revendications qui implémente une stratégie composée de paires ressource-action chacune spécifiant des combinaisons booléennes des revendications qu’un demandeur doit posséder pour exécuter l’action sur la ressource. Le code qui implémente le gestionnaire d’autorisations des revendications capable d’utiliser cette stratégie est disponible dans `ClaimsBasedAuthorization` l’exemple.  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
