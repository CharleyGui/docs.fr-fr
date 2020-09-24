---
title: Élément <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: 7667f78d2c341990585526fd153c0b230658a2ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167247"
---
# <a name="bindingredirect-element"></a>Élément \<bindingRedirect>

Redirige une version d'assembly vers une autre.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`oldVersion`|Attribut requis.<br /><br /> Spécifie la version de l'assembly demandée initialement. Le format d’un numéro de version d’assembly est *major. minor. Build. Revision*. Les valeurs valides pour chaque partie de ce numéro de version vont de 0 à 65535.<br /><br /> Vous pouvez également spécifier une plage de versions en respectant le format suivant :<br /><br /> *n. n. n. n-n. n. n*|  
|`newVersion`|Attribut requis.<br /><br /> Spécifie la version de l’assembly à utiliser à la place de la version initialement demandée au format : *n. n. n. n*<br /><br /> Cette valeur peut spécifier une version antérieure à `oldVersion`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`dependentAssembly`|Encapsule la stratégie de liaisons et l’emplacement de chaque assembly. Utilisez un élément dependentAssembly pour chaque assembly.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  

 Lorsque vous générez une application .NET Framework basée sur un assembly avec nom fort, l'application utilise par défaut cette version de l'assembly au moment de l'exécution, même si une nouvelle version est disponible. Vous pouvez toutefois configurer l'application pour faire en sorte qu'elle s'exécute en utilisant une version plus récente de l'assembly. Pour plus d’informations sur la façon dont le runtime utilise ces fichiers pour déterminer la version de l’assembly à utiliser, consultez [la manière dont le runtime localise les assemblys](../../../deployment/how-the-runtime-locates-assemblies.md).  
  
 Vous pouvez rediriger plusieurs versions d'assembly en incluant plusieurs éléments `bindingRedirect` dans un élément `dependentAssembly`. Vous pouvez également rediriger une version plus récente vers une version antérieure de l'assembly.  
  
 La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité. Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers. L’autorisation est accordée en définissant l' <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur <xref:System.Security.Permissions.SecurityPermission> . Pour plus d’informations, consultez [autorisation de sécurité pour la redirection des liaisons d’assembly](../../assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment rediriger une version d'assembly vers une autre.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
