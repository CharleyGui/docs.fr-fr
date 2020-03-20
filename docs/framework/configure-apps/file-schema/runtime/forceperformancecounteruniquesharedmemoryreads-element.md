---
title: Élément <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154138"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
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
|`enabled`|Attribut requis.<br /><br /> Indique si PerfCounter.dll utilise le paramètre du registre CatégorieOptions pour déterminer s’il y a lieu de charger les données de compteur de performance de la mémoire partagée spécifique à la catégorie ou de la mémoire globale.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|PerfCounter.dll n’utilise pas le paramètre de registre CatégorieOptions C’est la valeur par défaut.|  
|`true`|PerfCounter.dll utilise le paramètre de registre CatégorieOptions.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 Dans les versions du cadre .NET avant le cadre .NET 4, la version de PerfCounter.dll qui a été chargée correspondait au temps d’exécution qui a été chargé dans le processus. Si un ordinateur avait à la fois la version cadre .NET 1.1 et le cadre .NET 2.0 installé, une application .NET Framework 1.1 chargerait la version .NET Framework 1.1 de PerfCounter.dll. En commençant par le cadre .NET 4, la nouvelle version installée de PerfCounter.dll est chargée. Cela signifie qu’une application .NET Framework 1.1 chargera la version .NET Framework 4 de PerfCounter.dll si le cadre .NET 4 est installé sur l’ordinateur.  
  
 En commençant par le cadre .NET 4, lors de la consommation de compteurs de performance, PerfCounter.dll vérifie l’entrée de registre CatégorieOptions pour chaque fournisseur pour déterminer s’il doit lire à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire partagée globale. Le cadre .NET 1.1 PerfCounter.dll ne lit pas cette inscription au registre, parce qu’il n’est pas au courant de la mémoire partagée spécifique à la catégorie; il lit toujours de mémoire partagée globale.  
  
 Pour la compatibilité rétrograde, le .NET Framework 4 PerfCounter.dll ne vérifie pas l’entrée du registre CatégorieOptions lors de l’exécution dans une application .NET Framework 1.1. Il utilise simplement la mémoire partagée globale, tout comme le cadre .NET 1.1 PerfCounter.dll. Toutefois, vous pouvez demander au cadre .NET 4 PerfCounter.dll `<forcePerformanceCounterUniqueSharedMemoryReads>` de vérifier le paramètre du registre en permettant l’élément.  
  
> [!NOTE]
> L’activation de l’élément `<forcePerformanceCounterUniqueSharedMemoryReads>` ne garantit pas que la mémoire partagée spécifique à la catégorie sera utilisée. Le paramètre activé ne fait que référencer `true` perfCounter.dll au paramètre de registre CatégorieOptions. Le paramètre par défaut pour CategoryOptions est d’utiliser la mémoire partagée spécifique à la catégorie ; cependant, vous pouvez modifier CatégorieOptions pour indiquer que la mémoire partagée globale doit être utilisée.  
  
 La clé de registre qui contient le paramètre CategoryOptions est HKEY_LOCAL_MACHINE-Système-CurrentControlSet-Services\\<catégorieName\>'Performance. Par défaut, CategoryOptions est réglé à 3, qui ordonne à PerfCounter.dll d’utiliser la mémoire partagée spécifique à la catégorie. Si CategoryOptions est réglé à 0, PerfCounter.dll utilise la mémoire partagée globale. Les données de instance ne seront réutilisées que si le nom de l’instance créée est identique à l’instance réutilisée. Toutes les versions pourront écrire à la catégorie. Si CatégorieOptions est définie à 1, la mémoire partagée globale est utilisée, mais les données d’instance peuvent être réutilisées si le nom de la catégorie est de la même longueur que la catégorie réutilisée.  
  
 Les réglages 0 et 1 peuvent entraîner des fuites de mémoire et le remplissage de la mémoire de compteur de performance.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment spécifier que PerfCounter.dll devrait faire référence à l’entrée du registre CatégorieOptions pour déterminer s’il doit utiliser la mémoire partagée spécifique à la catégorie.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
