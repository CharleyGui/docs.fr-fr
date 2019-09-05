---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252092"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Inscrit un gestionnaire d’authentification des revendications pour les revendications entrantes.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**  
  
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
|type|Spécifie un type personnalisé qui dérive de <xref:System.Security.Claims.ClaimsAuthenticationManager> la classe. Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés].|  
  
### <a name="child-elements"></a>Éléments enfants  
 S’il n’y `type` a aucun attribut, ou `type` si l’attribut <xref:System.Security.Claims.ClaimsAuthenticationManager> fait référence à `<claimsAuthenticationManager>` la classe, l’élément ne prend pas d’éléments enfants ; <xref:System.Security.Claims.ClaimsAuthenticationManager> Toutefois, les classes dérivées de peuvent définir des éléments de configuration enfants.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
  
## <a name="remarks"></a>Notes  
 Le comportement par défaut fourni par <xref:System.Security.Claims.ClaimsAuthenticationManager> la classe renvoie en écho les revendications entrantes. Si aucun `type` attribut n’est spécifié ou si `type` l’attribut spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe `<claimsAuthenticationManager>` , l’élément ne prend pas d’éléments enfants. Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe afin d’implémenter un comportement personnalisé. Les classes dérivées peuvent prendre en charge la configuration `<claimsAuthenticationManager>` par le biais d’éléments <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> enfants de l’élément en substituant la méthode pour gérer ces éléments. Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.  
  
 L' `<claimsAuthenticationManager>` élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemple  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
