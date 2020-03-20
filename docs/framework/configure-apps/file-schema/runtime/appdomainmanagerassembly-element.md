---
title: Élément <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154422"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly> Element
Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`value`|Attribut requis. Spécifie le nom d’affichage de l’assemblage qui fournit au gestionnaire de domaine d’application le domaine de l’application par défaut dans le processus.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 Pour spécifier le type de gestionnaire de domaine d’application, vous devez spécifier à la fois cet élément et [ \<l’élément appDomainManagerType>.](appdomainmanagertype-element.md) Si l’un ou l’autre de ces éléments n’est pas spécifié, l’autre est ignoré.  
  
 Lorsque le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est lancé si l’assemblage spécifié n’existe pas ou si l’assemblage ne contient pas le type spécifié par [ \<l’appDomainManagerType>](appdomainmanagertype-element.md) élément; et le processus ne démarre pas. Si l’assemblage est trouvé mais que <xref:System.IO.FileLoadException> l’information de la version ne correspond pas, a est lancée.  
  
 Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine de l’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application. Utilisez <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> les <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriétés et les propriétés pour spécifier un type de gestionnaire de domaine d’application différent pour un nouveau domaine d’application.  
  
 Spécifier le type de gestionnaire de domaine d’application nécessite que l’application ait une pleine confiance. (Par exemple, une application fonctionnant sur le bureau a une confiance totale.) Si l’application n’a <xref:System.TypeLoadException> pas la pleine confiance, a est lancée.  
  
 Pour le format du nom d’affichage de l’assemblage, voir la <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> propriété.  
  
 Cet élément de configuration n’est disponible que dans le cadre .NET 4 et plus tard.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment spécifier que le gestionnaire de `MyMgr` domaine `AdMgrExample` d’application pour le domaine d’application par défaut d’un processus est le type dans l’assemblage.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<appDomainManagerType> Element](appdomainmanagertype-element.md)
- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
- [SetAppDomainManagerType, méthode](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
