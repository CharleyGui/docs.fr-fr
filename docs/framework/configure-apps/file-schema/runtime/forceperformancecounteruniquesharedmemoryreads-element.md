---
title: Élément <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26fed0a10b9a25f25a580c7ac9a468cbedeb3671
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489472"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.  
  
 \<configuration>  
\<runtime>  
\<forcePerformanceCounterUniqueSharedMemoryReads>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions pour déterminer s’il faut charger des données de compteur de performances à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire globale.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|PerfCounter.dll n’utilise pas les CategoryOptions ce paramètre de Registre est la valeur par défaut.|  
|`true`|PerfCounter.dll n’utilise pas le paramètre de Registre CategoryOptions.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Dans les versions du .NET Framework antérieures au .NET Framework 4, la version de PerfCounter.dll chargée correspondait à l’exécution qui a été chargée dans le processus. Si un ordinateur avait à la fois le .NET Framework version 1.1 et le [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installé, une application .NET Framework 1.1 chargerait le .NET Framework version 1.1 de PerfCounter.dll. À compter de .NET Framework 4, la dernière version installée de PerfCounter.dll est chargée. Cela signifie qu’une application .NET Framework 1.1 chargera la version de .NET Framework 4 de PerfCounter.dll si le .NET Framework 4 est installé sur l’ordinateur.  
  
 À compter de .NET Framework 4, lors de l’utilisation des compteurs de performance, PerfCounter.dll vérifie l’entrée de Registre CategoryOptions pour chaque fournisseur pour déterminer s’il doit lire à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire partagée globale. Le PerfCounter.dll .NET Framework 1.1 ne lit pas cette entrée de Registre, car elle n’a pas connaissance de la mémoire partagée spécifique à la catégorie ; Il lit toujours à partir de la mémoire partagée globale.  
  
 Pour la compatibilité descendante, le PerfCounter.dll de 4 de .NET Framework ne vérifie pas l’entrée de Registre CategoryOptions lors de l’exécution dans une application .NET Framework 1.1. Elle utilise simplement la mémoire partagée globale, comme le PerfCounter.dll .NET Framework 1.1. Toutefois, vous pouvez indiquer le PerfCounter.dll de 4 .NET Framework pour vérifier le paramètre de Registre en activant le `<forcePerformanceCounterUniqueSharedMemoryReads>` élément.  
  
> [!NOTE]
>  L’activation de la `<forcePerformanceCounterUniqueSharedMemoryReads>` élément ne garantit pas que la mémoire partagée spécifique à la catégorie sera utilisée. Paramètre est activé à `true` uniquement, PerfCounter.dll référence le paramètre du Registre CategoryOptions. Le paramètre par défaut CategoryOptions consiste à utiliser la mémoire partagée spécifique à la catégorie ; Toutefois, vous pouvez modifier CategoryOptions pour indiquer que la mémoire partagée globale doit être utilisée.  
  
 La clé de Registre qui contient le paramètre CategoryOptions est HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. Par défaut, CategoryOptions a la valeur 3, qui indique à PerfCounter.dll d’utiliser la mémoire partagée spécifique à la catégorie. Si CategoryOptions est définie sur 0, PerfCounter.dll utilise la mémoire partagée globale. Données d’instance seront réutilisées uniquement si le nom de l’instance en cours de création est identique à l’instance est réutilisé. Toutes les versions seront en mesure d’écrire à la catégorie. Si CategoryOptions est définie sur 1, mémoire partagée globale est utilisée, mais les données d’instance peuvent être réutilisées si le nom de catégorie est la même longueur que la catégorie est réutilisée.  
  
 Les paramètres 0 et 1 peuvent entraîner des fuites de mémoire et la saturation de mémoire de compteur de performances.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que PerfCounter.dll doit référencer l’entrée de Registre CategoryOptions pour déterminer s’il doit utiliser la mémoire partagée spécifique à la catégorie.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
