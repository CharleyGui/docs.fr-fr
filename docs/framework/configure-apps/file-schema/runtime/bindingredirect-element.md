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
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154294"
---
# <a name="bindingredirect-element"></a>\<bindingRedirect> Element
Redirige une version d'assembly vers une autre.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dépendantAssembly>**](dependentassembly-element.md)\
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
|`oldVersion`|Attribut requis.<br /><br /> Spécifie la version de l'assembly demandée initialement. Le format d’un numéro de version d’assemblage est *major.minor.build.revision*. Les valeurs valides pour chaque partie de ce numéro de version vont de 0 à 65535.<br /><br /> Vous pouvez également spécifier une plage de versions en respectant le format suivant :<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|Attribut requis.<br /><br /> Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*<br /><br /> Cette valeur peut spécifier une version antérieure à `oldVersion`.|  
  
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
 Lorsque vous générez une application .NET Framework basée sur un assembly avec nom fort, l'application utilise par défaut cette version de l'assembly au moment de l'exécution, même si une nouvelle version est disponible. Vous pouvez toutefois configurer l'application pour faire en sorte qu'elle s'exécute en utilisant une version plus récente de l'assembly. Pour plus de détails sur la façon dont le temps d’exécution utilise ces fichiers pour déterminer quelle version d’assemblage utiliser, voir [Comment les assemblages De localisation de runtime](../../../deployment/how-the-runtime-locates-assemblies.md).  
  
 Vous pouvez rediriger plusieurs versions d'assembly en incluant plusieurs éléments `bindingRedirect` dans un élément `dependentAssembly`. Vous pouvez également rediriger une version plus récente vers une version antérieure de l'assembly.  
  
 La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité. Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers. La permission est accordée <xref:System.Security.Permissions.SecurityPermissionFlag> en <xref:System.Security.Permissions.SecurityPermission>fixant le drapeau sur le . Pour plus d’informations, voir [l’autorisation de sécurité de réorientation contraignante de l’Assemblée](../../assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a> Exemple  
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
- [Configuration Fichier Schema](../index.md)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
