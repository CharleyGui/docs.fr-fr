---
title: Élément <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154423"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType> Element
Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`value`|Attribut requis. Spécifie le nom du type, y compris l’espace de nom, qui sert de gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 Pour spécifier le type de gestionnaire de domaine d’application, vous devez spécifier à la fois cet élément et [ \<l’élément>appDomainManagerAssembly.](appdomainmanagerassembly-element.md) Si l’un ou l’autre de ces éléments n’est pas spécifié, l’autre est ignoré.  
  
 Lorsque le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est lancé si le type spécifié n’existe pas dans l’assemblage qui est spécifié par [ \<l’appDomainManagerAssembly>](appdomainmanagerassembly-element.md) élément; et le processus ne démarre pas.  
  
 Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine de l’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application. Utilisez <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> les <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriétés et les propriétés pour spécifier un type de gestionnaire de domaine d’application différent pour un nouveau domaine d’application.  
  
 Spécifier le type de gestionnaire de domaine d’application nécessite que l’application ait une pleine confiance. (Par exemple, une application fonctionnant sur le bureau a une confiance totale.) Si l’application n’a <xref:System.TypeLoadException> pas la pleine confiance, a est lancée.  
  
 Le format du type et de l’espace de <xref:System.Type.FullName%2A?displayProperty=nameWithType> nom est le même format qui est utilisé pour la propriété.  
  
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
- [\<appDomainManagerAssembly> Element](appdomainmanagerassembly-element.md)
- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
- [SetAppDomainManagerType, méthode](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
