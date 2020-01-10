---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 11/13/2019
ms.topic: reference
ms.openlocfilehash: 41157db7770a89f4402fa6675f7031c508f33aca
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740558"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Options de configuration au moment de l’exécution pour garbage collection

Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution. Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres. Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.

Les paramètres sont organisés en groupes dans cette page. Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.

> [!NOTE]
>
> - Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.
> - Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception. Ces paramètres sont omis dans cette page.
> - Pour les valeurs numériques, utilisez la notation décimale pour les paramètres dans le fichier *runtimeconfig. JSON* et la notation hexadécimale pour les paramètres de variable d’environnement.

## <a name="flavors-of-garbage-collection"></a>Versions de garbage collection

Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur. Pour plus d’informations sur les différences entre les deux, consultez [principes de base de garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Les sous-versions de garbage collection sont en arrière-plan et non simultanées.

Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :

### <a name="systemgcservercomplus_gcserver"></a>System. GC. Server/COMPlus_gcServer

- Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.
- Par défaut : station de travail garbage collection (`false`).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Server` | `false`-station de travail<br/>serveur de `true` | .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_gcServer` | `0`-station de travail<br/>serveur de `1` | .NET Core 1.0 |
| **App. config pour .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`-station de travail<br/>serveur de `true` |  |

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System. GC. concurrent/COMPlus_gcConcurrent

- Configure si l’garbage collection d’arrière-plan (simultanée) est activée.
- Valeur par défaut : activé (`true`).
- Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) et [garbage collection de serveur d’arrière-plan](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Concurrent` | `true`-arrière-plan GC<br/>`false`-GC non simultané | .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_gcConcurrent` | `true`-arrière-plan GC<br/>`false`-GC non simultané | .NET Core 1.0 |
| **App. config pour .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`-arrière-plan GC<br/>`false`-GC non simultané |  |

## <a name="manage-resource-usage"></a>Gérer l’utilisation des ressources

Utilisez les paramètres décrits dans cette section pour gérer la mémoire et l’utilisation du processeur du garbage collector.

Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System. GC. HeapCount/COMPlus_GCHeapCount

- Limite le nombre de segments de mémoire créés par le garbage collector.
- S’applique uniquement aux garbage collection serveur (GC).
- Si l’affinité du processeur GC est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers processeurs `n`. (Utilisez les paramètres affinité Mask ou affinité Ranges pour spécifier exactement les processeurs à affinité.)
- Si l’affinité du processeur GC est désactivée, ce paramètre limite le nombre de tas GC.
- Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapCount` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapCount` | *valeur hexadécimale* | .NET Core 3.0 |
| **App. config pour .NET Framework** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *valeur décimale* | 4.6.2 |

> [!TIP]
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 10 pour la variable d’environnement.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.
- Si l’affinité du processeur est désactivée en définissant `System.GC.NoAffinitize` sur `true`, ce paramètre est ignoré.
- S’applique uniquement aux garbage collection serveur (GC).
- La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus. Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire. Cela spécifie que les 10 premiers processeurs doivent être utilisés. Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapAffinitizeMask` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapAffinitizeMask` | *valeur hexadécimale* | .NET Core 3.0 |
| **App. config pour .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *valeur décimale* | 4.6.2 |

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.
- Ce paramètre est similaire à `System.GC.HeapAffinitizeMask`, sauf qu’il vous permet de spécifier plus de 64 processeurs.
- Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».
- Si l’affinité du processeur est désactivée en définissant `System.GC.NoAffinitize` sur `true`, ce paramètre est ignoré.
- S’applique uniquement aux garbage collection serveur (GC).
- Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.GCHeapAffinitizeRanges` | Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.<br/>Exemple UNIX : "1-10, 12, 50-52, 70"<br/>Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 » | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapAffinitizeRanges` | Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.<br/>Exemple UNIX : "1-10, 12, 50-52, 70"<br/>Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 » | .NET Core 3.0 |

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .

  Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs. Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.

- S’applique aux garbage collection de serveur (GC) sur les systèmes d’exploitation Windows 64 bits uniquement.
- Valeur par défaut : désactivé (`0`).
- Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_GCCpuGroup` | `0`-désactivé<br/>activé `1` | .NET Core 1.0 |
| **App. config pour .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`-désactivé<br/>activé `true` |  |

> [!NOTE]
> Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) . Pour les applications .NET Core, vous pouvez activer cette option en définissant la valeur de la variable d’environnement `COMPlus_Thread_UseAllCpuGroups` sur `1`.

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System. GC. NoAffinitize/COMPlus_GCNoAffinitize

- Spécifie s’il faut *affinité* garbage collection threads avec des processeurs. La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique. Un segment de mémoire est créé pour chaque thread GC.
- S’applique uniquement aux garbage collection serveur (GC).
- Par défaut : affinité garbage collection threads avec processeurs (`false`).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.NoAffinitize` | `false` affinité<br/>`true`-ne pas affinité | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCNoAffinitize` | `0` affinité<br/>`1`-ne pas affinité | .NET Core 3.0 |
| **App. config pour .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false` affinité<br/>`true`-ne pas affinité | 4.6.2 |

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit

- Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimit` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapHardLimit` | *valeur hexadécimale* | .NET Core 3.0 |

> [!TIP]
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 80 000 octets, les valeurs sont 80000 pour le fichier JSON et 13880 pour la variable d’environnement.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Spécifie l’utilisation du tas GC comme pourcentage de la mémoire totale.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimitPercent` | *valeur décimale* | .NET Core 3.0 |
| **Variable d'environnement** | `COMPlus_GCHeapHardLimitPercent` | *valeur hexadécimale* | .NET Core 3.0 |

> [!TIP]
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 1E pour la variable d’environnement.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System. GC. RetainVM/COMPlus_GCRetainVM

- Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.
- Valeur par défaut : relâcher les segments sur le système d’exploitation (`false`).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.RetainVM` | `false`-version du système d’exploitation<br/>`true`-mettre en veille| .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_GCRetainVM` | `0`-version du système d’exploitation<br/>`1`-mettre en veille | .NET Core 1.0 |

## <a name="large-pages"></a>Grandes pages

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.
- Valeur par défaut : désactivé (`0`).
- Il s’agit d’un paramètre expérimental.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_GCLargePages` | `0`-désactivé<br/>activé `1` | .NET Core 3.0 |

## <a name="large-objects"></a>Objets volumineux

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).
- Valeur par défaut : activé (`1`).
- Cette option peut devenir obsolète dans une future version de .NET.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_gcAllowVeryLargeObjects` | activé `1`<br/> `0`-désactivé | .NET Core 1.0 |
| **App. config pour .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | activé `1`<br/> `0`-désactivé | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Seuil du tas des objets volumineux

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System. GC. LOHThreshold/COMPlus_GCLOHThreshold

- Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).
- Le seuil par défaut est de 85 000 octets.
- La valeur que vous spécifiez doit être supérieure au seuil par défaut.

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.LOHThreshold` | *valeur décimale* | .NET Core 1.0 |
| **Variable d'environnement** | `COMPlus_GCLOHThreshold` | *valeur hexadécimale* | .NET Core 1.0 |
| **App. config pour .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *valeur décimale* | .NET Framework 4.8 |

> [!TIP]
> Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale. Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale. Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 1D4C0 pour la variable d’environnement.

## <a name="standalone-gc"></a>GC autonome

### <a name="complus_gcname"></a>COMPlus_GCName

- Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.
- Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nom du paramètre | Valeurs | Version introduite |
| - | - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
