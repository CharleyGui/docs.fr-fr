---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 91d155b638c7e69b3d2c0216266a7c0c0410db4c
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915995"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Options de configuration au moment de l’exécution pour garbage collection

Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution. Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres. Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.

Les paramètres sont organisés en groupes dans cette page. Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.

> [!NOTE]
>
> - Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.
> - Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception. Ces paramètres sont omis dans cette page.
> - Pour les valeurs numériques, utilisez la notation décimale pour les paramètres de la *runtimeconfig.jssur* fichier et notation hexadécimale pour les paramètres de variable d’environnement. Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».

## <a name="flavors-of-garbage-collection"></a>Versions de garbage collection

Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur. Pour plus d’informations sur les différences entre les deux, consultez [station de travail et serveur garbage collection](../../standard/garbage-collection/workstation-server-gc.md).

Les sous-versions de garbage collection sont en arrière-plan et non simultanées.

Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :

- [Station de travail et GC de serveur](#workstation-vs-server)
- [GC d’arrière-plan](#background-gc)

### <a name="workstation-vs-server"></a>Station de travail et serveur

- Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.
- Par défaut : station de travail garbage collection. Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.Server` | `false`-station de travail<br/>`true`-serveur | .NET Core 1.0 |
| **MSBuild, propriété** | `ServerGarbageCollection` | `false`-station de travail<br/>`true`-serveur | .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_gcServer` | `0`-station de travail<br/>`1`-serveur | .NET Core 1.0 |
| **app.config pour .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`-station de travail<br/>`true`-serveur |  |

#### <a name="examples"></a>Exemples

*runtimeconfig.jssur le* fichier :

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

### <a name="background-gc"></a>GC d’arrière-plan

- Configure si l’garbage collection d’arrière-plan (simultanée) est activée.
- Valeur par défaut : utilisez GC d’arrière-plan. Cela équivaut à définir la valeur sur `true` .
- Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/background-gc.md).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.Concurrent` | `true`-arrière-plan GC<br/>`false`-GC non simultané | .NET Core 1.0 |
| **MSBuild, propriété** | `ConcurrentGarbageCollection` | `true`-arrière-plan GC<br/>`false`-GC non simultané | .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_gcConcurrent` | `1`-arrière-plan GC<br/>`0`-GC non simultané | .NET Core 1.0 |
| **app.config pour .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`-arrière-plan GC<br/>`false`-GC non simultané |  |

#### <a name="examples"></a>Exemples

*runtimeconfig.jssur le* fichier :

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

Utilisez les paramètres suivants pour gérer la mémoire et l’utilisation du processeur du garbage collector :

- [Affinité](#affinitize)
- [Masque affinité](#affinitize-mask)
- [Plages affinité](#affinitize-ranges)
- [Groupes de PROCESSEURs](#cpu-groups)
- [Nombre de tas](#heap-count)
- [Limite du tas](#heap-limit)
- [Pourcentage de la limite du tas](#heap-limit-percent)
- [Pourcentage de mémoire élevé](#high-memory-percent)
- [Limites par objet-tas](#per-object-heap-limits)
- [Pourcentages de limites de tas par objet](#per-object-heap-limit-percents)
- [Conserver la machine virtuelle](#retain-vm)

Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .

### <a name="heap-count"></a>Nombre de tas

- Limite le nombre de segments de mémoire créés par le garbage collector.
- S’applique uniquement aux garbage collection serveur.
- Si l' [affinité du processeur GC](#affinitize) est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers `n` processeurs. (Utilisez les paramètres [affinité Mask](#affinitize-mask) ou [affinité Ranges](#affinitize-ranges) pour spécifier exactement les processeurs à affinité.)
- Si l' [affinité du processeur GC](#affinitize) est désactivée, ce paramètre limite le nombre de tas gc.
- Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapCount` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapCount` | *valeur hexadécimale* | .NET Core 3.0 |
| **app.config pour .NET Framework** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *valeur décimale* | .NET Framework 4.6.2 |

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
> Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.

### <a name="affinitize-mask"></a>Masque affinité

- Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.
- Si l' [affinité du processeur GC](#affinitize) est désactivée, ce paramètre est ignoré.
- S’applique uniquement aux garbage collection serveur.
- La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus. Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire. Cela spécifie que les 10 premiers processeurs doivent être utilisés. Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapAffinitizeMask` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapAffinitizeMask` | *valeur hexadécimale* | .NET Core 3.0 |
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

### <a name="affinitize-ranges"></a>Plages affinité

- Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.
- Ce paramètre est similaire à [System. gc. HeapAffinitizeMask](#affinitize-mask), sauf qu’il vous permet de spécifier plus de 64 processeurs.
- Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».
- Si l' [affinité du processeur GC](#affinitize) est désactivée, ce paramètre est ignoré.
- S’applique uniquement aux garbage collection serveur.
- Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.GCHeapAffinitizeRanges` | Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.<br/>Exemple UNIX : "1-10, 12, 50-52, 70"<br/>Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 » | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapAffinitizeRanges` | Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.<br/>Exemple UNIX : "1-10, 12, 50-52, 70"<br/>Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 » | .NET Core 3.0 |

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

### <a name="cpu-groups"></a>Groupes de PROCESSEURs

- Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .

  Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs. Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.

- S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.
- Valeur par défaut : GC ne s’étend pas au-delà des groupes de PROCESSEURs. Cela équivaut à définir la valeur sur `0` .
- Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.CpuGroup` | `0`-désactivé<br/>`1`-activé | .NET 5,0 |
| **Variable d'environnement** | `COMPlus_GCCpuGroup` | `0`-désactivé<br/>`1`-activé | .NET Core 1.0 |
| **app.config pour .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`-désactivé<br/>`true`-activé |  |

> [!NOTE]
> Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) . Pour les applications .NET Core, vous pouvez activer cette option en affectant à la `COMPlus_Thread_UseAllCpuGroups` variable d’environnement la valeur `1` .

### <a name="affinitize"></a>Affinité

- Spécifie s’il faut *affinité* garbage collection threads avec des processeurs. La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique. Un segment de mémoire est créé pour chaque thread GC.
- S’applique uniquement aux garbage collection serveur.
- Par défaut : affinité garbage collection les threads avec des processeurs. Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.NoAffinitize` | `false`-affinité<br/>`true`-ne affinité | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCNoAffinitize` | `0`-affinité<br/>`1`-ne affinité | .NET Core 3.0 |
| **app.config pour .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`-affinité<br/>`true`-ne affinité | .NET Framework 4.6.2 |

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

### <a name="heap-limit"></a>Limite du tas

- Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.
- Ce paramètre s’applique uniquement aux ordinateurs 64 bits.
- Ce paramètre est ignoré si les [limites par objet/tas](#per-object-heap-limits) sont configurées.
- La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus grande de 20 Mo ou 75% de la limite de mémoire sur le conteneur. La valeur par défaut s’applique dans les cas suivants :

  - Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.
  - [System. gc. HeapHardLimitPercent](#heap-limit-percent) n’est pas défini.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimit` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapHardLimit` | *valeur hexadécimale* | .NET Core 3.0 |

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
> Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.

### <a name="heap-limit-percent"></a>Pourcentage de la limite du tas

- Spécifie l’utilisation autorisée du tas GC comme pourcentage de la mémoire physique totale.
- Si [System. gc. HeapHardLimit](#heap-limit) est également défini, ce paramètre est ignoré.
- Ce paramètre s’applique uniquement aux ordinateurs 64 bits.
- Si le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé sous la forme d’un pourcentage de cette limite de mémoire.
- Ce paramètre est ignoré si les [limites par objet/tas](#per-object-heap-limits) sont configurées.
- La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus petite de 20 Mo ou 75% de la limite de mémoire sur le conteneur. La valeur par défaut s’applique dans les cas suivants :

  - Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.
  - [System. gc. HeapHardLimit](#heap-limit) n’est pas défini.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimitPercent` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapHardLimitPercent` | *valeur hexadécimale* | .NET Core 3.0 |

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
> Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.

### <a name="per-object-heap-limits"></a>Limites par objet-tas

Vous pouvez spécifier l’utilisation autorisée du tas du GC pour chaque segment de mémoire. Les différents tas sont le tas d’objets volumineux (LOH), le tas de petits objets (SOH) et le tas d’objets épinglés (POH).

- Si vous spécifiez une valeur pour l’un `COMPLUS_GCHeapHardLimitSOH` des `COMPLUS_GCHeapHardLimitLOH` paramètres, ou `COMPLUS_GCHeapHardLimitPOH` , vous devez également spécifier une valeur pour `COMPLUS_GCHeapHardLimitSOH` et `COMPLUS_GCHeapHardLimitLOH` . Si ce n’est pas le cas, l’initialisation du runtime échoue.
- La valeur par défaut pour `COMPLUS_GCHeapHardLimitPOH` est 0. `COMPLUS_GCHeapHardLimitSOH`et `COMPLUS_GCHeapHardLimitLOH` n’ont pas de valeurs par défaut.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimitSOH` | *valeur décimale* | .NET 5,0 |
| **Variable d'environnement** | `COMPLUS_GCHeapHardLimitSOH` | *valeur hexadécimale* | .NET 5,0 |

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimitLOH` | *valeur décimale* | .NET 5,0 |
| **Variable d'environnement** | `COMPLUS_GCHeapHardLimitLOH` | *valeur hexadécimale* | .NET 5,0 |

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimitPOH` | *valeur décimale* | .NET 5,0 |
| **Variable d'environnement** | `COMPLUS_GCHeapHardLimitPOH` | *valeur hexadécimale* | .NET 5,0 |

> [!TIP]
> Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.

### <a name="per-object-heap-limit-percents"></a>Pourcentages de limites de tas par objet

Vous pouvez spécifier l’utilisation autorisée du tas du GC pour chaque segment de mémoire. Les différents tas sont le tas d’objets volumineux (LOH), le tas de petits objets (SOH) et le tas d’objets épinglés (POH).

- Si vous spécifiez une valeur pour l’un `COMPLUS_GCHeapHardLimitSOHPercent` des `COMPLUS_GCHeapHardLimitLOHPercent` paramètres, ou `COMPLUS_GCHeapHardLimitPOHPercent` , vous devez également spécifier une valeur pour `COMPLUS_GCHeapHardLimitSOHPercent` et `COMPLUS_GCHeapHardLimitLOHPercent` . Si ce n’est pas le cas, l’initialisation du runtime échoue.
- Ces paramètres sont ignorés si `COMPLUS_GCHeapHardLimitSOH` , `COMPLUS_GCHeapHardLimitLOH` et `COMPLUS_GCHeapHardLimitPOH` sont spécifiés.
- La valeur 1 signifie que GC utilise 1% de la mémoire physique totale pour ce tas d’objets.
- Chaque valeur doit être supérieure à zéro et inférieure à 100. En outre, la somme des trois valeurs de pourcentage doit être inférieure à 100. Dans le cas contraire, le runtime ne pourra pas s’initialiser.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimitSOHPercent` | *valeur décimale* | .NET 5,0 |
| **Variable d'environnement** | `COMPLUS_GCHeapHardLimitSOHPercent` | *valeur hexadécimale* | .NET 5,0 |

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimitLOHPercent` | *valeur décimale* | .NET 5,0 |
| **Variable d'environnement** | `COMPLUS_GCHeapHardLimitLOHPercent` | *valeur hexadécimale* | .NET 5,0 |

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HeapHardLimitPOHPercent` | *valeur décimale* | .NET 5,0 |
| **Variable d'environnement** | `COMPLUS_GCHeapHardLimitPOHPercent` | *valeur hexadécimale* | .NET 5,0 |

> [!TIP]
> Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.

### <a name="high-memory-percent"></a>Pourcentage de mémoire élevé

La charge de mémoire est indiquée par le pourcentage de mémoire physique en cours d’utilisation. Par défaut, lorsque la charge de mémoire physique atteint **90%**, garbage collection devient plus agressive pour effectuer des garbage collections de compactage complets afin d’éviter la pagination. Lorsque la charge de mémoire est inférieure à 90%, GC privilégie les collections d’arrière-plan pour les garbage collections complets, qui ont des pauses plus courtes, mais ne réduisent pas de manière importante la taille totale du tas. Sur les ordinateurs disposant d’une quantité importante de mémoire (80 Go ou plus), le seuil de charge par défaut est compris entre 90% et 97%.

Le seuil de charge de mémoire élevé peut être ajusté par la `COMPlus_GCHighMemPercent` variable d’environnement ou le `System.GC.HighMemoryPercent` paramètre de configuration JSON. Envisagez d’ajuster le seuil si vous souhaitez contrôler la taille du tas. Par exemple, pour le processus dominant sur un ordinateur avec 64 Go de mémoire, il est raisonnable que GC commence à réagir lorsqu’il y a 10% de mémoire disponible. Toutefois, pour les processus plus petits, par exemple, un processus qui consomme uniquement 1 Go de mémoire, le garbage collector peut s’exécuter confortablement avec moins de 10% de la mémoire disponible. Pour ces processus plus petits, envisagez de définir le seuil plus haut. En revanche, si vous souhaitez que les plus grands processus aient des tailles de tas plus petites (même si la mémoire physique disponible est importante), le fait de réduire ce seuil est un moyen efficace pour que GC réagisse plus tôt pour compacter le tas.

> [!NOTE]
> Pour les processus en cours d’exécution dans un conteneur, GC prend en compte la mémoire physique en fonction de la limite du conteneur.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.HighMemoryPercent` | *valeur décimale* | .NET 5,0 |
| **Variable d'environnement** | `COMPlus_GCHighMemPercent` | *valeur hexadécimale* | |

> [!TIP]
> Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour définir le seuil de mémoire élevé sur 75%, les valeurs sont 75 pour le fichier JSON et 0x4B ou 4B pour la variable d’environnement.

### <a name="retain-vm"></a>Conserver la machine virtuelle

- Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.
- Valeur par défaut : relâcher les segments sur le système d’exploitation. Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.RetainVM` | `false`-version finale du système d’exploitation<br/>`true`-mise en veille | .NET Core 1.0 |
| **MSBuild, propriété** | `RetainVMGarbageCollection` | `false`-version finale du système d’exploitation<br/>`true`-mise en veille | .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_GCRetainVM` | `0`-version finale du système d’exploitation<br/>`1`-mise en veille | .NET Core 1.0 |

#### <a name="examples"></a>Exemples

*runtimeconfig.jssur le* fichier :

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

- Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.
- Valeur par défaut : n’utilisez pas de grandes pages lorsqu’une limite matérielle de tas est définie. Cela équivaut à définir la valeur sur `0` .
- Il s’agit d’un paramètre expérimental.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | N/A | N/A | N/A |
| **Variable d'environnement** | `COMPlus_GCLargePages` | `0`-désactivé<br/>`1`-activé | .NET Core 3.0 |

## <a name="allow-large-objects"></a>Autoriser les objets volumineux

- Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).
- Valeur par défaut : GC prend en charge les tableaux supérieurs à 2 Go. Cela équivaut à définir la valeur sur `1` .
- Cette option peut devenir obsolète dans une future version de .NET.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | N/A | N/A | N/A |
| **Variable d'environnement** | `COMPlus_gcAllowVeryLargeObjects` | `1`-activé<br/> `0`-désactivé | .NET Core 1.0 |
| **app.config pour .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`-activé<br/> `0`-désactivé | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Seuil du tas des objets volumineux

- Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).
- Le seuil par défaut est de 85 000 octets.
- La valeur que vous spécifiez doit être supérieure au seuil par défaut.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | `System.GC.LOHThreshold` | *valeur décimale* | .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_GCLOHThreshold` | *valeur hexadécimale* | .NET Core 1.0 |
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
> Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.

## <a name="standalone-gc"></a>GC autonome

- Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.
- Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig.js** | N/A | N/A | N/A |
| **Variable d'environnement** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
