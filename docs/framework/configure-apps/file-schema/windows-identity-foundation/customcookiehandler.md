---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252015"
---
# <a name="customcookiehandler"></a>\<customCookieHandler>
Définit le type de gestionnaire de cookies personnalisé. Cet élément ne peut être présent que si `mode` l’attribut de `<cookieHandler>` l’élément est « Custom ». Le type personnalisé doit être dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel. services >** ](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customCookieHandler >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Spécifie un type personnalisé qui dérive de <xref:System.IdentityModel.Services.CookieHandler> la classe. Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Configure le <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> que utilise pour lire et écrire des cookies.|  
  
## <a name="remarks"></a>Notes  
 Quand vous spécifiez un gestionnaire de cookies personnalisé en `mode` affectant à `<cookieHandler>` l’attribut de l’élément la valeur « Custom », vous devez spécifier le type du gestionnaire de `<customCookieHandler>` cookies personnalisé en incluant un élément enfant qui référence le type de gestionnaire de cookie. Cet élément ne peut pas être spécifié `mode` lorsque l’attribut a la valeur « chunked » ou « default ». Les gestionnaires de cookies personnalisés doivent dériver <xref:System.IdentityModel.Services.CookieHandler> de la classe.  
  
 L' `<customCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant configure le SAM pour utiliser un gestionnaire de cookies personnalisé de type `MyNamespace.MyCustomCookieHandler`.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Services.CookieHandler>
