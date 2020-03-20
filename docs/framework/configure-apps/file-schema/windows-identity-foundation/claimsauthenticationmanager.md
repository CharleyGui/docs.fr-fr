---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152747"
---
# <a name="claimsauthenticationmanager"></a>\<revendicationsAuthenticationManager>
Enregistre un gestionnaire d’authentification des réclamations pour les réclamations entrantes.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<revendicationsAuthenticationManager>**  
  
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
|type|Spécifie un type personnalisé <xref:System.Security.Claims.ClaimsAuthenticationManager> qui dérive de la classe. Pour plus d’informations `type` sur la façon de spécifier l’attribut, voir [Références de type personnalisé].|  
  
### <a name="child-elements"></a>Éléments enfants  
 S’il `type` n’y a `type` pas <xref:System.Security.Claims.ClaimsAuthenticationManager> d’attribut, ou si l’attribut fait référence à la classe, l’élément `<claimsAuthenticationManager>` ne prend pas d’éléments pour enfants; cependant, les <xref:System.Security.Claims.ClaimsAuthenticationManager> classes dérivées peuvent définir des éléments de configuration de l’enfant.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identitéConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
  
## <a name="remarks"></a>Notes   
 Le comportement par <xref:System.Security.Claims.ClaimsAuthenticationManager> défaut fourni par la classe fait écho aux réclamations entrantes. Si `type` aucun attribut n’est spécifié ou si l’attribut `type` spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, l’élément `<claimsAuthenticationManager>` ne prend pas d’éléments pour enfants. Vous pouvez `type` spécifier l’attribut <xref:System.Security.Claims.ClaimsAuthenticationManager> pour enregistrer un type dérivé de la classe pour implémenter un comportement personnalisé. Les classes dérivées peuvent soutenir `<claimsAuthenticationManager>` la configuration par <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> des éléments enfantaux de l’élément en l’emporteant sur la méthode de manutention de ces éléments. Le schéma défini pour les éléments de l’enfant est à la designer de la classe.  
  
 L’élément `<claimsAuthenticationManager>` <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> définit la propriété.  
  
## <a name="example"></a> Exemple  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
