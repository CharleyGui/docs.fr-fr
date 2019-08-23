---
title: Élément <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29fbe951b955c97e39ebaf80885729a45c1a3fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927393"
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
|`enabled`|Attribut requis.<br /><br /> Indique si PerfCounter. dll utilise le paramètre de Registre CategoryOptions pour déterminer s’il faut charger les données du compteur de performance à partir de la mémoire partagée ou de la mémoire globale spécifique à la catégorie.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|`Value`|Description|  
|-----------|-----------------|  
|`false`|PerfCounter. dll n’utilise pas le paramètre de Registre CategoryOptions. il s’agit de la valeur par défaut.|  
|`true`|PerfCounter. dll utilise le paramètre de Registre CategoryOptions.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Dans les versions du .NET Framework avant le .NET Framework 4, la version de PerfCounter. dll qui a été chargée correspond au runtime qui a été chargé dans le processus. Si le .NET Framework version 1,1 et le .NET Framework 2,0 ont été installés sur un ordinateur, une application .NET Framework 1,1 chargera la version .NET Framework 1,1 de PerfCounter. dll. À partir du .NET Framework 4, la dernière version installée de PerfCounter. dll est chargée. Cela signifie qu’une application .NET Framework 1,1 chargera la version .NET Framework 4 de PerfCounter. dll si le .NET Framework 4 est installé sur l’ordinateur.  
  
 À partir du .NET Framework 4, lors de l’utilisation de compteurs de performance, PerfCounter. dll vérifie l’entrée de Registre CategoryOptions pour chaque fournisseur afin de déterminer si elle doit lire à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire partagée globale. Le .NET Framework 1,1 PerfCounter. dll ne lit pas cette entrée de Registre, car il n’est pas conscient de la mémoire partagée propre à la catégorie; Il lit toujours à partir de la mémoire partagée globale.  
  
 Pour la compatibilité descendante, le .NET Framework 4 PerfCounter. dll ne vérifie pas l’entrée de Registre CategoryOptions lors de l’exécution dans une application .NET Framework 1,1. Elle utilise simplement la mémoire partagée globale, comme le .NET Framework 1,1 PerfCounter. dll. Toutefois, vous pouvez indiquer au .NET Framework 4 PerfCounter. dll de vérifier le paramètre de registre en activant `<forcePerformanceCounterUniqueSharedMemoryReads>` l’élément.  
  
> [!NOTE]
> L’activation `<forcePerformanceCounterUniqueSharedMemoryReads>` de l’élément ne garantit pas que la mémoire partagée propre à la catégorie sera utilisée. Si vous affectez la valeur à `true` activé, PerfCounter. dll fait référence au paramètre de Registre CategoryOptions. Le paramètre par défaut pour CategoryOptions consiste à utiliser la mémoire partagée propre à la catégorie. Toutefois, vous pouvez modifier CategoryOptions pour indiquer que la mémoire partagée globale doit être utilisée.  
  
 La clé de Registre qui contient le paramètre CategoryOptions est\\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services <\>CategoryName \Performance. Par défaut, CategoryOptions a la valeur 3, ce qui indique à PerfCounter. dll d’utiliser la mémoire partagée propre à la catégorie. Si CategoryOptions a la valeur 0, PerfCounter. dll utilise la mémoire partagée globale. Les données d’instance sont réutilisées uniquement si le nom de l’instance en cours de création est identique à l’instance réutilisée. Toutes les versions seront en mesure d’écrire dans la catégorie. Si CategoryOptions a la valeur 1, la mémoire partagée globale est utilisée, mais les données d’instance peuvent être réutilisées si le nom de la catégorie a la même longueur que la catégorie réutilisée.  
  
 Les paramètres 0 et 1 peuvent entraîner des fuites de mémoire et la saturation de la mémoire du compteur de performances.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que PerfCounter. dll doit faire référence à l’entrée du Registre CategoryOptions pour déterminer si elle doit utiliser la mémoire partagée propre à la catégorie.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
