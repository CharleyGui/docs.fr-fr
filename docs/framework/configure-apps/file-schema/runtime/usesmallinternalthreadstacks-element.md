---
title: Élément <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f098065cc005c59ec558ffa1f95202715624e7d
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456115"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks > élément
Les demandes que le common language runtime (CLR) réduire la mémoire utilisent en spécifiant des tailles de pile explicites lorsqu’il crée certains threads qu’il utilise en interne, au lieu d’utiliser la taille de pile par défaut pour ces threads.  
  
 \<configuration > élément  
\<runtime > élément  
\<UseSmallInternalThreadStacks > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie s’il faut demander que les tailles de pile explicites d’utilisation CLR au lieu de la taille de pile par défaut lorsqu’il crée certains threads qu’il utilise en interne. Les tailles de pile explicites sont inférieures à la taille de pile par défaut de 1 Mo.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|true|Demander des tailles de pile explicites.|  
|False|Utiliser la taille de pile par défaut. Il s’agit par défaut pour le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Cet élément de configuration est utilisé pour demander l’utilisation réduite de la mémoire virtuelle dans un processus, étant donné que les tailles de thread explicites que le CLR utilise pour ses threads internes, si la demande est honorée, sont plus petites que la taille par défaut.  
  
> [!IMPORTANT]
>  Cet élément de configuration est une demande au CLR plutôt qu’une exigence absolue. Dans le .NET Framework 4, la demande est honorée uniquement pour le x86 architecture. Cet élément peut complètement ignoré dans les futures versions du CLR ou remplacé par des tailles de pile explicites qui sont toujours utilisés pour les threads internes sélectionnés.  
  
 Spécification de que cet élément de configuration entretient des relations fiabilité pour une utilisation de mémoire virtuelle plus petits si le CLR répond à la requête, car il est plus petite taille de pile peut augmenter les débordements plus probablement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment demander que la CLR utilisation tailles de pile explicites pour certains threads qu’il utilise en interne.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
