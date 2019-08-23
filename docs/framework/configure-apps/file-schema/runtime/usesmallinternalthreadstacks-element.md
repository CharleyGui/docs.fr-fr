---
title: Élément <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ee4df12a017429de333dd4e93df27973b658dad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920678"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks >, élément
Demande que le common language runtime (CLR) réduit l’utilisation de la mémoire en spécifiant des tailles de pile explicites lorsqu’il crée certains threads qu’il utilise en interne, au lieu d’utiliser la taille de pile par défaut pour ces threads.  
  
 \<Élément de > de configuration  
\<Élément > du Runtime  
\<UseSmallInternalThreadStacks >, élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie s’il faut demander que le CLR utilise des tailles de pile explicites au lieu de la taille de la pile par défaut lorsqu’il crée certains threads qu’il utilise en interne. Les tailles de pile explicites sont inférieures à la taille de pile par défaut de 1 Mo.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|true|Demander des tailles de pile explicites.|  
|false|Utilisez la taille de pile par défaut. Il s’agit de la valeur par défaut pour le .NET Framework 4.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Cet élément de configuration est utilisé pour demander une utilisation réduite de la mémoire virtuelle dans un processus, car les tailles de thread explicites utilisées par le CLR pour ses threads internes, si la demande est honorée, sont inférieures à la taille par défaut.  
  
> [!IMPORTANT]
> Cet élément de configuration est une demande au CLR plutôt qu’une exigence absolue. Dans le .NET Framework 4, la demande est honorée uniquement pour l’architecture x86. Cet élément peut être complètement ignoré dans les futures versions du CLR ou remplacé par des tailles de pile explicites qui sont toujours utilisées pour les threads internes sélectionnés.  
  
 La spécification de cet élément de configuration pour la fiabilité pour une plus petite utilisation de la mémoire virtuelle si le CLR honore la demande, parce que les plus petites tailles de pile peuvent potentiellement rendre les débordements de pile plus probables.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment demander que le CLR utilise des tailles de pile explicites pour certains threads qu’il utilise en interne.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
