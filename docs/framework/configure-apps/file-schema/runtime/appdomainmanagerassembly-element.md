---
title: Élément <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a293af73fde5ee72ba02c7e6613e9c57eae1b9b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658948"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly >, élément
Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.  
  
 \<configuration>  
\<runtime>  
\<appDomainManagerAssembly>  
  
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
|`value`|Attribut requis. Spécifie le nom complet de l’assembly qui fournit le gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Pour spécifier le type du gestionnaire de domaine d’application, vous devez spécifier cet élément et l' [ \<élément AppDomainManagerType >](appdomainmanagertype-element.md) . Si l’un de ces éléments n’est pas spécifié, l’autre est ignorée.  
  
 Quand le domaine d’application par défaut est <xref:System.TypeLoadException> chargé, est levé si l’assembly spécifié n’existe pas ou si l’assembly ne contient pas le type spécifié par l' [ \<élément AppDomainManagerType >](appdomainmanagertype-element.md) ; et si le processus échoue à activer. Si l’assembly est trouvé, mais que les informations de version ne <xref:System.IO.FileLoadException> correspondent pas, une exception est levée.  
  
 Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine d’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application. Utilisez les <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> propriétés <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> et pour spécifier un autre type de gestionnaire de domaine d’application pour un nouveau domaine d’application.  
  
 Si vous spécifiez le type de gestionnaire de domaine d’application, l’application doit avoir une confiance totale. (Par exemple, une application qui s’exécute sur le bureau bénéficie d’une confiance totale.) Si l’application ne dispose pas d’une confiance totale <xref:System.TypeLoadException> , une exception est levée.  
  
 Pour connaître le format du nom complet de l’assembly <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> , consultez la propriété.  
  
 Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que le gestionnaire de domaine d’application pour le domaine d’application par défaut d’un `MyMgr` processus est le `AdMgrExample` type dans l’assembly.  
  
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
- [\<appDomainManagerType >, élément](appdomainmanagertype-element.md)
- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [SetAppDomainManagerType, méthode](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
