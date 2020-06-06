---
title: Élément <performanceCounters>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697153"
---
# <a name="performancecounters-element"></a>Élément \<performanceCounters>

Spécifie la taille de la mémoire globale partagée par les compteurs de performances.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a>Syntaxe

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|FileMappingSize|Attribut requis.<br /><br /> Spécifie la taille, en octets, de la mémoire globale partagée par les compteurs de performance. La valeur par défaut est 524288.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`Configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|

## <a name="remarks"></a>Remarques

Les compteurs de performance utilisent un fichier mappé en mémoire, ou mémoire partagée, pour publier les données de performances.  La taille de la mémoire partagée détermine le nombre d’instances qui peuvent être utilisées à la fois.  Il existe deux types de mémoire partagée : la mémoire partagée globale et la mémoire partagée séparée.  La mémoire partagée globale est utilisée par toutes les catégories de compteurs de performance installées avec les versions .NET Framework 1,0 ou 1,1.  Les catégories de compteurs de performance installées avec la version de .NET Framework 2,0 utilisent une mémoire partagée distincte, chaque catégorie de compteur de performances ayant sa propre mémoire.

La taille de la mémoire partagée globale ne peut être définie qu’avec un fichier de configuration.  La taille par défaut est de 524 288 octets, la taille maximale est de 33 554 432 octets et la taille minimale est de 32 768 octets.  Étant donné que la mémoire partagée globale est partagée par tous les processus et toutes les catégories, le premier créateur spécifie la taille.  Si vous définissez la taille dans votre fichier de configuration de l’application, cette taille est utilisée uniquement si votre application est la première application qui provoque l’exécution des compteurs de performances.  Par conséquent, l’emplacement correct pour spécifier la `filemappingsize` valeur est le fichier machine. config.  La mémoire dans la mémoire partagée globale ne peut pas être libérée par des compteurs de performances individuels. par conséquent, la mémoire partagée globale finit par être épuisée si un grand nombre d’instances de compteur de performance avec des noms différents sont créés.

Pour la taille de la mémoire partagée séparée, la valeur DWORD FileMappingSize dans la clé de Registre HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services \\ *\<category name>* \Performance est référencée en premier, suivie de la valeur spécifiée pour la mémoire partagée globale dans le fichier de configuration. Si la valeur FileMappingSize n’existe pas, la taille de la mémoire partagée séparée est définie sur un quatrième (1/4) du paramètre global dans le fichier de configuration.

## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
