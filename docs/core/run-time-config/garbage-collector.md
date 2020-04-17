---
title: Arrangements de config de collecteur d’ordures
description: Découvrez les paramètres de course pour configurer comment le collecteur d’ordures gère la mémoire des applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607808"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Options de configuration en temps d’exécution pour la collecte des ordures

Cette page contient des informations sur les paramètres de collecteur d’ordures (GC) qui peuvent être modifiés au moment de l’exécution. Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres. Cependant, les défauts offrent des performances optimales pour la plupart des applications dans des situations typiques.

Les paramètres sont disposés en groupes sur cette page. Les paramètres de chaque groupe sont couramment utilisés en conjonction les uns avec les autres pour obtenir un résultat spécifique.

> [!NOTE]
>
> - Ces paramètres peuvent également être modifiés dynamiquement par l’application au fur et à mesure qu’elle est en cours d’exécution, de sorte que tous les paramètres de temps d’exécution que vous définissez peuvent être annulés.
> - Certains paramètres, tels que [le niveau de latence,](../../standard/garbage-collection/latency.md)ne sont généralement définis que par l’API au moment de la conception. Ces paramètres sont omis à partir de cette page.
> - Pour les valeurs de nombre, utilisez la notation décimale pour les paramètres du fichier *runtimeconfig.json* et la notation hexadecimal pour les paramètres variables de l’environnement. Pour les valeurs hexadecimales, vous pouvez les spécifier avec ou sans le préfixe "0x".

## <a name="flavors-of-garbage-collection"></a>Saveurs de collecte des ordures

Les deux principales saveurs de la collecte des ordures sont le poste de travail GC et le serveur GC. Pour plus d’informations sur les différences entre les deux, voir [Fondamentaux de la collecte des ordures](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Les sous-composants de la collecte des ordures sont de fond et non simultanés.

Utilisez les paramètres suivants pour sélectionner les saveurs de la collecte des ordures :

### <a name="systemgcservercomplus_gcserver"></a>System.GC.Server/COMPlus_gcServer

- Configure si l’application utilise la collecte des ordures de poste de travail ou la collecte des ordures du serveur.
- Défaut : Collecte des`false`ordures de poste de travail ().

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false`- poste de travail<br/>`true`- serveur | .NET Core 1.0 |
| **Propriété MSBuild** | `ServerGarbageCollection` | `false`- poste de travail<br/>`true`- serveur | .NET Core 1.0 |
| **Variable de l’environnement** | `COMPlus_gcServer` | `0`- poste de travail<br/>`1`- serveur | .NET Core 1.0 |
| **app.config pour .NET Framework** | [GCServer (en)](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`- poste de travail<br/>`true`- serveur |  |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.GC.Concurrent/COMPlus_gcConcurrent

- Configure si la collecte des ordures de fond (concurrente) est activée.
- Défaut: Activé`true`( ).
- Pour plus d’informations, voir [Collection d’ordures Background](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) et [collecte des ordures serveur De fond](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true`- fond GC<br/>`false`- GC non concomitant | .NET Core 1.0 |
| **Propriété MSBuild** | `ConcurrentGarbageCollection` | `true`- fond GC<br/>`false`- GC non concomitant | .NET Core 1.0 |
| **Variable de l’environnement** | `COMPlus_gcConcurrent` | `true`- fond GC<br/>`false`- GC non concomitant | .NET Core 1.0 |
| **app.config pour .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`- fond GC<br/>`false`- GC non concomitant |  |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>Gérer l’utilisation des ressources

Utilisez les paramètres décrits dans cette section pour gérer la mémoire du collecteur d’ordures et l’utilisation du processeur.

Pour plus d’informations sur certains de ces paramètres, voir le [terrain intermédiaire entre la poste de travail et l’entrée de blog serveur GC.](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System.GC.HeapCount/COMPlus_GCHeapCount

- Limite le nombre de tas créés par le collecteur d’ordures.
- S’applique uniquement à la collecte des ordures du serveur.
- Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est activée, ce qui `n` est la valeur par défaut, `n` le réglage du nombre de tas affinitise les tas/threads GC aux premiers processeurs. (Utilisez le [masque affinitize](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [affinitisez](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) les paramètres des plages pour spécifier exactement les processeurs à affinitiser.)
- Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre limite le nombre de tas de GC.
- Pour plus d’informations, voir les [remarques GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | *valeur décimale* | .NET Core 3.0 |
| **Variable de l’environnement** | `COMPlus_GCHeapCount` | *valeur hexadecimal* | .NET Core 3.0 |
| **app.config pour .NET Framework** | [GCHeapCount (en)](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *valeur décimale* | .NET Framework 4.6.2 |

Exemple :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale. Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal. Par exemple, pour limiter le nombre de tas à 16, les valeurs seraient de 16 pour le fichier JSON et de 0x10 ou 10 pour la variable environnement.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Spécifie les processeurs exacts que les fils de collecteur d’ordures devraient utiliser.
- Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.
- S’applique uniquement à la collecte des ordures du serveur.
- La valeur est un masque peu qui définit les processeurs qui sont disponibles pour le processus. Par exemple, une valeur décimale de 1023 (ou une valeur hexadecimale de 0x3FF ou 3FF si vous utilisez la variable de l’environnement) est 0011 1111 1111 en notation binaire. Cela spécifie que les 10 premiers processeurs doivent être utilisés. Pour spécifier les 10 processeurs suivants, c’est-à-dire les processeurs 10-19, spécifient une valeur décimale de 1047552 (ou une valeur hexadecimale de 0xFFC00 ou FFC00), ce qui équivaut à une valeur binaire de 1111 1111 1100 000 0000.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | *valeur décimale* | .NET Core 3.0 |
| **Variable de l’environnement** | `COMPlus_GCHeapAffinitizeMask` | *valeur hexadecimal* | .NET Core 3.0 |
| **app.config pour .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *valeur décimale* | .NET Framework 4.6.2 |

Exemple :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Spécifie la liste des processeurs à utiliser pour les fils de collecteur d’ordures.
- Ce paramètre est similaire à [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), sauf qu’il vous permet de spécifier plus de 64 processeurs.
- Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe CPU](/windows/win32/procthread/processor-groups)correspondant, par exemple, "0:1-10,0:12,1:50-52,1:70".
- Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.
- S’applique uniquement à la collecte des ordures du serveur.
- Pour plus d’informations, voir [Faire la configuration CPU mieux pour GC sur les machines avec > 64 processeurs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de Maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.GCHeapAffinitizeRanges` | Liste séparée par comma des numéros de processeur ou des gammes de numéros de processeur.<br/>Exemple d’Unix : « 1-10,12,50-52,70 »<br/>Exemple windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |
| **Variable de l’environnement** | `COMPlus_GCHeapAffinitizeRanges` | Liste séparée par comma des numéros de processeur ou des gammes de numéros de processeur.<br/>Exemple d’Unix : « 1-10,12,50-52,70 »<br/>Exemple windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |

Exemple :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- Configure si le collecteur d’ordures utilise ou non [des groupes de processeurs.](/windows/win32/procthread/processor-groups)

  Lorsqu’un ordinateur Windows 64 bits a plusieurs groupes de processeurs, c’est-à-dire qu’il y a plus de 64 processeurs, ce qui permet à cet élément d’étendre la collecte des ordures dans tous les groupes de processeurs. Le collecteur d’ordures utilise tous les noyaux pour créer et équilibrer les tas.

- S’applique uniquement à la collecte des ordures du serveur sur les systèmes d’exploitation Windows 64 bits.
- Défaut: Désactivé`0`( ).
- Pour plus d’informations, voir [Faire la configuration CPU mieux pour GC sur les machines avec > 64 processeurs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de Maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | N/A | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_GCCpuGroup` | `0`- désactivé<br/>`1`- activé | .NET Core 1.0 |
| **app.config pour .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`- désactivé<br/>`true`- activé |  |

> [!NOTE]
> Pour configurer l’heure de l’exécution de la langue commune (CLR) pour également distribuer les fils du pool de threads dans tous les groupes de processeur, activez [l’option Thread_UseAllCpuGroups élément.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) Pour les applications .NET Core, vous pouvez activer cette option en définissant la valeur de la variable de l’environnement `COMPlus_Thread_UseAllCpuGroups` à `1`.

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System.GC.NoAffinitize/COMPlus_GCNoAffinitize

- Précise s’il faut *affinitiser les* fils de collecte des ordures avec les transformateurs. Pour affinitiser un thread GC signifie qu’il ne peut fonctionner que sur son processeur spécifique. Un tas est créé pour chaque thread GC.
- S’applique uniquement à la collecte des ordures du serveur.
- Défaut : Affinitiser les fils de`false`collecte des ordures avec les transformateurs ( ).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false`- affinitiser<br/>`true`- n’affinitez pas | .NET Core 3.0 |
| **Variable de l’environnement** | `COMPlus_GCNoAffinitize` | `0`- affinitiser<br/>`1`- n’affinitez pas | .NET Core 3.0 |
| **app.config pour .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`- affinitiser<br/>`true`- n’affinitez pas | .NET Framework 4.6.2 |

Exemple :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit

- Spécifie la taille maximale de commit, dans les octets, pour le tas GC et la comptabilité GC.
- Ce paramètre ne s’applique qu’aux ordinateurs 64 bits.
- La valeur par défaut, qui ne s’applique que dans certains cas, est la moindre de 20 Mo ou 75% de la limite de mémoire sur le conteneur. La valeur par défaut s’applique si :

  - Le processus est en cours d’exécution à l’intérieur d’un conteneur qui a une limite de mémoire spécifiée.
  - [System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) n’est pas défini.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimit` | *valeur décimale* | .NET Core 3.0 |
| **Variable de l’environnement** | `COMPlus_GCHeapHardLimit` | *valeur hexadecimal* | .NET Core 3.0 |

Exemple :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale. Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal. Par exemple, pour spécifier une limite de 200 mebioctets (MiB), les valeurs seraient 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable environnement.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Spécifie l’utilisation autorisée de tas de GC en pourcentage de la mémoire physique totale.
- Si [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) est également défini, ce paramètre est ignoré.
- Ce paramètre ne s’applique qu’aux ordinateurs 64 bits.
- Si le processus est en cours d’exécution à l’intérieur d’un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé comme un pourcentage de cette limite de mémoire.
- La valeur par défaut, qui ne s’applique que dans certains cas, est la moindre de 20 Mo ou 75% de la limite de mémoire sur le conteneur. La valeur par défaut s’applique si :

  - Le processus est en cours d’exécution à l’intérieur d’un conteneur qui a une limite de mémoire spécifiée.
  - [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) n’est pas défini.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPercent` | *valeur décimale* | .NET Core 3.0 |
| **Variable de l’environnement** | `COMPlus_GCHeapHardLimitPercent` | *valeur hexadecimal* | .NET Core 3.0 |

Exemple :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale. Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal. Par exemple, pour limiter l’utilisation du tas à 30 %, les valeurs seraient de 30 pour le fichier JSON et de 0x1E ou 1E pour la variable de l’environnement.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System.GC.RetainVM/COMPlus_GCRetainVM

- Configure si les segments qui doivent être supprimés sont mis sur une liste de veille pour une utilisation future ou sont libérés vers le système d’exploitation (OS).
- Défaut : Les segments de`false`sortie retournent au système d’exploitation ().

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false`- sortie à OS<br/>`true`- mis en veille | .NET Core 1.0 |
| **Propriété MSBuild** | `RetainVMGarbageCollection` | `false`- sortie à OS<br/>`true`- mis en veille | .NET Core 1.0 |
| **Variable de l’environnement** | `COMPlus_GCRetainVM` | `0`- sortie à OS<br/>`1`- mis en veille | .NET Core 1.0 |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>Grandes pages

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Précise si de grandes pages doivent être utilisées lorsqu’une limite de tas est définie.
- Défaut: Désactivé`0`( ).
- C’est un cadre expérimental.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | N/A | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_GCLargePages` | `0`- désactivé<br/>`1`- activé | .NET Core 3.0 |

## <a name="large-objects"></a>Grands objets

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Configure le support des collecteurs d’ordures sur les plates-formes 64 bits pour les tableaux de plus de 2 gigaoctets (GB) en taille totale.
- Défaut: Activé`1`( ).
- Cette option peut devenir obsolète dans une future version de .NET.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | N/A | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_gcAllowVeryLargeObjects` | `1`- activé<br/> `0`- désactivé | .NET Core 1.0 |
| **app.config pour .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`- activé<br/> `0`- désactivé | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Grand seuil de tas d’objets

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System.GC.LOHThreshold/COMPlus_GCLOHThreshold

- Spécifie la taille du seuil, dans les octets, qui provoque des objets à aller sur le tas de gros objets (LOH).
- Le seuil par défaut est de 85 000 octets.
- La valeur que vous spécifiez doit être supérieure au seuil par défaut.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | *valeur décimale* | .NET Core 1.0 |
| **Variable de l’environnement** | `COMPlus_GCLOHThreshold` | *valeur hexadecimal* | .NET Core 1.0 |
| **app.config pour .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *valeur décimale* | .NET Framework 4.8 |

Exemple :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale. Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal. Par exemple, pour fixer un seuil de 120 000 octets, les valeurs seraient de 120000 pour le fichier JSON et de 0x1D4C0 ou 1D4C0 pour la variable environnement.

## <a name="standalone-gc"></a>GC autonome

### <a name="complus_gcname"></a>COMPlus_GCName

- Spécifie un chemin vers la bibliothèque contenant le éboueur que le temps d’exécution a l’intention de charger.
- Pour plus d’informations, voir [La conception de chargeur Standalone GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.json** | N/A | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
