---
title: Élément <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c8f8744d3ef1ca30eb05a4c8c3290d8a514714b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663510"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy >, élément
Spécifie si le runtime applique la stratégie de l'éditeur.  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<dependentAssembly>  
\<publisherPolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`apply`|Spécifie s’il faut appliquer la stratégie d’éditeur.|  
  
## <a name="apply-attribute"></a>appliquer l’attribut  
  
|`Value`|Description|  
|-----------|-----------------|  
|`yes`|Applique la stratégie d’éditeur. Il s’agit du paramètre par défaut.|  
|`no`|N’applique pas la stratégie d’éditeur.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un fournisseur de composant publie une nouvelle version d’un assembly, le fournisseur peut inclure une stratégie d’éditeur pour que les applications qui utilisent l’ancienne version utilisent désormais la nouvelle version. Pour spécifier s’il faut appliquer la stratégie d’éditeur pour un assembly particulier, placez l'  **\<élément publisherPolicy >** dans l'  **\<élément de > dependentAssembly** .  
  
 La valeur par défaut de l’attribut **apply** est **Oui**. La définition de l’attribut **apply** sur **no** remplace tous les paramètres **Yes** précédents d’un assembly.  
  
 Une autorisation est requise pour qu’une application ignore explicitement la stratégie de l’éditeur à l’aide de l' [ \<élément publisherPolicy Apply = "no"/>](publisherpolicy-element.md) dans le fichier de configuration de l’application. L’autorisation est accordée en définissant <xref:System.Security.Permissions.SecurityPermissionFlag> l’indicateur <xref:System.Security.Permissions.SecurityPermission>sur. Pour plus d’informations, consultez [autorisation de sécurité pour la redirection des liaisons](../../assembly-binding-redirection-security-permission.md)d’assembly.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant désactive la stratégie d’éditeur pour l’assembly, `myAssembly`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Méthode de localisation des assemblys par le runtime](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
