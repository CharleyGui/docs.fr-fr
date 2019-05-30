---
title: Élément <gcServer>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5df7ab070cc0a40f4e2f3d0545c5bc40ccb07f4d
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378034"
---
# <a name="gcserver-element"></a>\<< gcServer > élément
Spécifie si le common language runtime exécute le garbage collection côté serveur.  
  
 \<configuration>  
\<runtime>  
\<gcServer>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime exécute le garbage collection côté serveur.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|N'exécute pas le garbage collection côté serveur. Il s'agit de la valeur par défaut.|  
|`true`|Exécute le garbage collection côté serveur.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Le common language runtime (ou CLR) prend en charge deux types de garbage collection : le garbage collection côté station de travail, qui est disponible sur tous les systèmes, et le garbage collection côté serveur, qui est disponible sur les systèmes multiprocesseurs. Utilisez l’élément `<gcServer>` pour contrôler le type de garbage collection effectué par le CLR. Utilisez la propriété <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> pour déterminer si le garbage collection côté serveur est activé.  
  
 Pour les ordinateurs monoprocesseurs, le garbage collection côté station de travail configuré par défaut représente normalement l'option la plus rapide. L'option station de travail ou serveur peut être utilisée pour les ordinateurs biprocesseurs. Le garbage collection côté serveur est normalement l'option la plus rapide pour les ordinateurs comptant plus de deux processeurs.  
  
 Cet élément peut être défini uniquement dans le fichier de configuration de l'application (il est ignoré s'il est défini dans le fichier de configuration de l'ordinateur).  
  
> [!NOTE]
>  Dans .NET Framework 4 et les versions antérieures, le garbage collection simultané n'est pas disponible si le garbage collection côté serveur est activé. À compter de .NET Framework 4.5, garbage collection côté serveur est simultané. Pour utiliser le garbage collection de serveur non simultané, définissez le `<gcServer>` élément `true` et [ \<gcConcurrent > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) à `false`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant active le garbage collection côté serveur.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Pour désactiver le garbage collection simultané](gcconcurrent-element.md#to-disable-background-garbage-collection)
