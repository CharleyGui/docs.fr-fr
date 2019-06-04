---
title: Élément <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff8c91680a0c3049fa9bc2f7e9c1bf3f654a19b9
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487773"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly> Element
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
|`value`|Attribut requis. Spécifie le nom complet de l’assembly qui fournit le Gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Pour spécifier le type du Gestionnaire de domaine, vous devez spécifier cet élément et le [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) élément. Si un de ces éléments n’est pas spécifié, l’autre est ignorée.  
  
 Lorsque le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est levée si l’assembly spécifié n’existe pas ou si l’assembly ne contient pas le type spécifié par le [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) élément ; et le processus ne parvient pas à démarrer. Si l’assembly est trouvé, mais les informations de version ne correspondent pas, un <xref:System.IO.FileLoadException> est levée.  
  
 Lorsque vous spécifiez le type de gestionnaire de domaine application pour le domaine d’application par défaut, les autres domaines d’application créés à partir du domaine d’application par défaut héritent le type de gestionnaire de domaine application. Utilisez le <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> et <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriétés pour spécifier un type de gestionnaire de domaine d’application pour un nouveau domaine d’application.  
  
 En spécifiant le type de gestionnaire de domaine application nécessite l’application ait une confiance totale. (Par exemple, une application en cours d’exécution sur le bureau a une confiance totale.) Si l’application n’a pas une confiance totale, un <xref:System.TypeLoadException> est levée.  
  
 Pour le format du nom complet d’assembly, consultez le <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> propriété.  
  
 Cet élément de configuration est disponible uniquement dans le .NET Framework 4 et versions ultérieures.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que le Gestionnaire de domaine d’application pour le domaine d’application par défaut d’un processus est le `MyMgr` tapez dans le `AdMgrExample` assembly.  
  
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
- [\<appDomainManagerType > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [SetAppDomainManagerType, méthode](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
