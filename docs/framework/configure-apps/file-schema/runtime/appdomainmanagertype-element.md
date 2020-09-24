---
title: Élément <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: e21384de6ca07c637a79ee54207d1e3ddfbf20e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170309"
---
# <a name="appdomainmanagertype-element"></a>Élément \<appDomainManagerType>

Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
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
|`value`|Attribut requis. Spécifie le nom du type, y compris l’espace de noms, qui sert de gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  

 Pour spécifier le type du gestionnaire de domaine d’application, vous devez spécifier à la fois cet élément et l' [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) élément. Si l’un de ces éléments n’est pas spécifié, l’autre est ignorée.  
  
 Quand le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est levé si le type spécifié n’existe pas dans l’assembly spécifié par l' [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) élément et que le processus ne démarre pas.  
  
 Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine d’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application. Utilisez les <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Propriétés et pour spécifier un autre type de gestionnaire de domaine d’application pour un nouveau domaine d’application.  
  
 Si vous spécifiez le type de gestionnaire de domaine d’application, l’application doit avoir une confiance totale. (Par exemple, une application qui s’exécute sur le bureau bénéficie d’une confiance totale.) Si l’application ne dispose pas d’une confiance totale, une <xref:System.TypeLoadException> exception est levée.  
  
 Le format du type et de l’espace de noms est le même que celui utilisé pour la <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriété.  
  
 Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment spécifier que le gestionnaire de domaine d’application pour le domaine d’application par défaut d’un processus est le `MyMgr` type dans l' `AdMgrExample` assembly.  
  
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
- [\<appDomainManagerAssembly> Appartient](appdomainmanagerassembly-element.md)
- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
- [SetAppDomainManagerType, méthode](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
