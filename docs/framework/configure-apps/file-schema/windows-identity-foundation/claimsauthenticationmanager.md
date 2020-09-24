---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 9e099b8de486631702548b8a035a46a7e0f4eb30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158472"
---
# \<claimsAuthenticationManager>

Inscrit un gestionnaire d’authentification des revendications pour les revendications entrantes.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Spécifie un type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe. Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés].|  
  
### <a name="child-elements"></a>Éléments enfants  

 S’il n’y a aucun `type` attribut, ou si l' `type` attribut fait référence <xref:System.Security.Claims.ClaimsAuthenticationManager> à la classe, l' `<claimsAuthenticationManager>` élément ne prend pas d’éléments enfants ; Toutefois, les classes dérivées de <xref:System.Security.Claims.ClaimsAuthenticationManager> peuvent définir des éléments de configuration enfants.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
  
## <a name="remarks"></a>Notes  

 Le comportement par défaut fourni par la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe renvoie en écho les revendications entrantes. Si aucun `type` attribut n’est spécifié ou si l' `type` attribut spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, l' `<claimsAuthenticationManager>` élément ne prend pas d’éléments enfants. Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe afin d’implémenter un comportement personnalisé. Les classes dérivées peuvent prendre en charge la configuration par le biais d’éléments enfants de l' `<claimsAuthenticationManager>` élément en substituant la <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> méthode pour gérer ces éléments. Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.  
  
 L' `<claimsAuthenticationManager>` élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemple  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
