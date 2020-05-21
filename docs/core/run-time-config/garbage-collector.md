---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: d7e3d040cd634eeb020beff806c60f834cc02585
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761978"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Options de configuration au moment de l’exécution pour garbage collection

Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution. Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres. Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.

Les paramètres sont organisés en groupes dans cette page. Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.

> [!NOTE]
>
> - Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.
> - Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception. Ces paramètres sont omis dans cette page.
> - Pour les valeurs numériques, utilisez la notation décimale pour les paramètres dans le fichier *runtimeconfig. JSON* et la notation hexadécimale pour les paramètres de variable d’environnement. Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».

## <a name="flavors-of-garbage-collection"></a>Versions de garbage collection

Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur. Pour plus d’informations sur les différences entre les deux, consultez [station de travail et serveur garbage collection](../../standard/garbage-collection/workstation-server-gc.md).

Les sous-versions de garbage collection sont en arrière-plan et non simultanées.

Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :

### <a name="systemgcservercomplus_gcserver"></a>System. GC. Server/COMPlus_gcServer

- Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.
- Par défaut : station de travail garbage collection. Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Server` | `false`-station de travail<br/>`true`-serveur | .NET Core 1.0 |
| **MSBuild, propriété** | `ServerGarbageCollection` | `false`-station de travail<br/>`true`-serveur | .NET Core 1.0 |
| **Variable d’environnement** | `COMPlus_gcServer` | `0`-station de travail<br/>`1`-serveur | .NET Core 1.0 |
| **App. config pour .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`-station de travail<br/>`true`-serveur |  |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

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

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System. GC. concurrent/COMPlus_gcConcurrent

- Configure si l’garbage collection d’arrière-plan (simultanée) est activée.
- Valeur par défaut : utilisez GC d’arrière-plan. Cela équivaut à définir la valeur sur `true` .
- Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/background-gc.md).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Concurrent` | `true`-arrière-plan GC<br/>`false`-GC non simultané | .NET Core 1.0 |
| **MSBuild, propriété** | `ConcurrentGarbageCollection` | `true`-arrière-plan GC<br/>`false`-GC non simultané | .NET Core 1.0 |
| **Variable d’environnement** | `COMPlus_gcConcurrent` | `true`-arrière-plan GC<br/>`false`-GC non simultané | .NET Core 1.0 |
| **App. config pour .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`-arrière-plan GC<br/>`false`-GC non simultané |  |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

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

Utilisez les paramètres décrits dans cette section pour gérer la mémoire et l’utilisation du processeur du garbage collector.

Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System. GC. HeapCount/COMPlus_GCHeapCount

- Limite le nombre de segments de mémoire créés par le garbage collector.
- S’applique uniquement aux garbage collection serveur.
- Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers `n` processeurs. (Utilisez les paramètres [affinité Mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [affinité Ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) pour spécifier exactement les processeurs à affinité.)
- Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre limite le nombre de tas gc.
- Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapCount` | *valeur décimale* | .NET Core 3.0 |
| **Variable d’environnement** | `COMPlus_GCHeapCount` | *valeur hexadécimale* | .NET Core 3.0 |
| **App. config pour .NET Framework** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *valeur décimale* | .NET Framework 4.6.2 |

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
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.
- Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.
- S’applique uniquement aux garbage collection serveur.
- La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus. Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire. Cela spécifie que les 10 premiers processeurs doivent être utilisés. Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapAffinitizeMask` | *valeur décimale* | .NET Core 3.0 |
| **Variable d’environnement** | `COMPlus_GCHeapAffinitizeMask` | *valeur hexadécimale* | .NET Core 3.0 |
| **App. config pour .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *valeur décimale* | .NET Framework 4.6.2 |

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

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.
- Ce paramètre est similaire à [System. gc. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), sauf qu’il vous permet de spécifier plus de 64 processeurs.
- Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».
- Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.
- S’applique uniquement aux garbage collection serveur.
- Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.GCHeapAffinitizeRanges` | Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.<br/>Exemple UNIX : "1-10, 12, 50-52, 70"<br/>Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 » | .NET Core 3.0 |
| **Variable d’environnement** | `COMPlus_GCHeapAffinitizeRanges` | Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.<br/>Exemple UNIX : "1-10, 12, 50-52, 70"<br/>Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 » | .NET Core 3.0 |

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

- Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .

  Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs. Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.

- S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.
- Valeur par défaut : GC ne s’étend pas au-delà des groupes de PROCESSEURs. Cela équivaut à définir la valeur sur `0` .
- Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | N/A | N/A | N/A |
| **Variable d’environnement** | `COMPlus_GCCpuGroup` | `0`-désactivé<br/>`1`-activé | .NET Core 1.0 |
| **App. config pour .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`-désactivé<br/>`true`-activé |  |

> [!NOTE]
> Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) . Pour les applications .NET Core, vous pouvez activer cette option en affectant à la `COMPlus_Thread_UseAllCpuGroups` variable d’environnement la valeur `1` .

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System. GC. NoAffinitize/COMPlus_GCNoAffinitize

- Spécifie s’il faut *affinité* garbage collection threads avec des processeurs. La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique. Un segment de mémoire est créé pour chaque thread GC.
- S’applique uniquement aux garbage collection serveur.
- Par défaut : affinité garbage collection les threads avec des processeurs. Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.NoAffinitize` | `false`-affinité<br/>`true`-ne affinité | .NET Core 3.0 |
| **Variable d’environnement** | `COMPlus_GCNoAffinitize` | `0`-affinité<br/>`1`-ne affinité | .NET Core 3.0 |
| **App. config pour .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`-affinité<br/>`true`-ne affinité | .NET Framework 4.6.2 |

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

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit

- Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.
- Ce paramètre s’applique uniquement aux ordinateurs 64 bits.
- La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus grande de 20 Mo ou 75% de la limite de mémoire sur le conteneur. La valeur par défaut s’applique dans les cas suivants :

  - Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.
  - [System. gc. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) n’est pas défini.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimit` | *valeur décimale* | .NET Core 3.0 |
| **Variable d’environnement** | `COMPlus_GCHeapHardLimit` | *valeur hexadécimale* | .NET Core 3.0 |

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
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Spécifie l’utilisation autorisée du tas GC comme pourcentage de la mémoire physique totale.
- Si [System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) est également défini, ce paramètre est ignoré.
- Ce paramètre s’applique uniquement aux ordinateurs 64 bits.
- Si le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé sous la forme d’un pourcentage de cette limite de mémoire.
- La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus petite de 20 Mo ou 75% de la limite de mémoire sur le conteneur. La valeur par défaut s’applique dans les cas suivants :

  - Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.
  - [System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) n’est pas défini.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimitPercent` | *valeur décimale* | .NET Core 3.0 |
| **Variable d’environnement** | `COMPlus_GCHeapHardLimitPercent` | *valeur hexadécimale* | .NET Core 3.0 |

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
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System. GC. RetainVM/COMPlus_GCRetainVM

- Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.
- Valeur par défaut : relâcher les segments sur le système d’exploitation. Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.RetainVM` | `false`-version finale du système d’exploitation<br/>`true`-mise en veille | .NET Core 1.0 |
| **MSBuild, propriété** | `RetainVMGarbageCollection` | `false`-version finale du système d’exploitation<br/>`true`-mise en veille | .NET Core 1.0 |
| **Variable d’environnement** | `COMPlus_GCRetainVM` | `0`-version finale du système d’exploitation<br/>`1`-mise en veille | .NET Core 1.0 |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

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

- Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.
- Valeur par défaut : n’utilisez pas de grandes pages lorsqu’une limite matérielle de tas est définie. Cela équivaut à définir la valeur sur `0` .
- Il s’agit d’un paramètre expérimental.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | N/A | N/A | N/A |
| **Variable d’environnement** | `COMPlus_GCLargePages` | `0`-désactivé<br/>`1`-activé | .NET Core 3.0 |

## <a name="large-objects"></a>Objets volumineux

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).
- Valeur par défaut : GC prend en charge les tableaux supérieurs à 2 Go. Cela équivaut à définir la valeur sur `1` .
- Cette option peut devenir obsolète dans une future version de .NET.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | N/A | N/A | N/A |
| **Variable d’environnement** | `COMPlus_gcAllowVeryLargeObjects` | `1`-activé<br/> `0`-désactivé | .NET Core 1.0 |
| **App. config pour .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`-activé<br/> `0`-désactivé | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Seuil du tas des objets volumineux

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System. GC. LOHThreshold/COMPlus_GCLOHThreshold

- Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).
- Le seuil par défaut est de 85 000 octets.
- La valeur que vous spécifiez doit être supérieure au seuil par défaut.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.LOHThreshold` | *valeur décimale* | .NET Core 1.0 |
| **Variable d’environnement** | `COMPlus_GCLOHThreshold` | *valeur hexadécimale* | .NET Core 1.0 |
| **App. config pour .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *valeur décimale* | .NET Framework 4.8 |

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
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.

## <a name="standalone-gc"></a>GC autonome

### <a name="complus_gcname"></a>COMPlus_GCName

- Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.
- Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | N/A | N/A | N/A |
| **Variable d’environnement** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
