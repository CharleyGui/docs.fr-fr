---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 0718f789ff4d99fb4e2651a9a704da4248cd5f49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158433"
---
# \<claimsAuthorizationManager>

Inscrit un gestionnaire d’autorisations des revendications pour les revendications entrantes.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
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
|type|Type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe. Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Éléments enfants  

 S’il n’y a aucun `type` attribut, ou si l' `type` attribut fait référence <xref:System.Security.Claims.ClaimsAuthenticationManager> à la classe, l' `<claimsAuthorizationManager>` élément ne prend pas d’éléments enfants ; Toutefois, les classes dérivées de <xref:System.Security.Claims.ClaimsAuthorizationManager> peuvent définir des éléments de configuration enfants.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
  
## <a name="remarks"></a>Notes  

 Le comportement par défaut fourni par la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe autorise toujours les revendications entrantes. Si aucun `type` attribut n’est spécifié ou si l' `type` attribut spécifie la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe, l' `<claimsAuthorizationManager>` élément ne prend pas d’éléments enfants. Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe afin d’implémenter un comportement personnalisé. Les classes dérivées peuvent prendre en charge la configuration par le biais d’éléments enfants de l' `<claimsAuthorizationManager>` élément en substituant la <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> méthode pour gérer ces éléments. Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.  
  
> [!IMPORTANT]
> Lors de l’utilisation de la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, la configuration d’identité référencée par l' `<federationConfiguration>` élément configure le gestionnaire d’autorisation des revendications et la stratégie utilisée pour prendre des décisions d’autorisation. Cela est vrai, même dans les scénarios qui ne sont pas des scénarios Web passifs, par exemple des applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive, l' `<claimsAuthorizationManager>` élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration d’identité référencée sont les seuls paramètres appliqués. Tous les autres paramètres sont ignorés. Pour plus d’informations, consultez l' [\<federationConfiguration>](federationconfiguration.md) élément.  
  
 Cet élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemple  

 Le code XML suivant montre la configuration d’un gestionnaire d’autorisations pour les revendications qui implémente une stratégie composée de paires ressource-action chacune spécifiant des combinaisons booléennes des revendications qu’un demandeur doit posséder pour exécuter l’action sur la ressource. Le code qui implémente le gestionnaire d’autorisations des revendications capable d’utiliser cette stratégie est disponible dans l' `ClaimsBasedAuthorization` exemple.  
  
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
