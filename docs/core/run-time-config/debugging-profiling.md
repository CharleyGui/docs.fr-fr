---
title: Débogage des paramètres de configuration du profilage
description: En savoir plus sur les paramètres d’exécution qui configurent le débogage et le profilage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761991"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Options de configuration au moment de l’exécution pour le débogage et le profilage

## <a name="enable-diagnostics"></a>Activation des diagnostics

- Configure si le débogueur, le profileur et les diagnostics EventPipe sont activés ou désactivés.
- Si vous omettez ce paramètre, les diagnostics sont activés. Cela équivaut à définir la valeur sur `1` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | N/A | N/A |
| **Variable d’environnement** | `COMPlus_EnableDiagnostics` | `1`-activé<br/>`0`-désactivé |

## <a name="enable-profiling"></a>Activer le profilage

- Configure si le profilage est activé pour le processus en cours d’exécution.
- Si vous omettez ce paramètre, le profilage est désactivé. Cela équivaut à définir la valeur sur `0` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | N/A | N/A |
| **Variable d’environnement** | `CORECLR_ENABLE_PROFILING` | `0`-désactivé<br/>`1`-activé |

## <a name="profiler-guid"></a>GUID du profileur

- Spécifie le GUID du profileur à charger dans le processus en cours d’exécution.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | N/A | N/A |
| **Variable d’environnement** | `CORECLR_PROFILER` | *GUID de chaîne* |

## <a name="profiler-location"></a>Emplacement du profileur

- Spécifie le chemin d’accès à la DLL du profileur à charger dans le processus en cours d’exécution (processus 32 bits ou 64 bits).
- Si plusieurs variables sont définies, les variables spécifiques au nombre de bits sont prioritaires. Ils spécifient le nombre de bits du profileur à charger.
- Pour plus d’informations, consultez [recherche de la bibliothèque du profileur](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **Variable d’environnement** | `CORECLR_PROFILER_PATH` | *chaîne-chemin d’accès* |
| **Variable d’environnement** | `CORECLR_PROFILER_PATH_32` | *chaîne-chemin d’accès* |
| **Variable d’environnement** | `CORECLR_PROFILER_PATH_64` | *chaîne-chemin d’accès* |

## <a name="write-perf-map"></a>Écrire le mappage des performances

- Active ou désactive l’écriture de */tmp/perf-$PID. map* sur les systèmes Linux.
- Si vous omettez ce paramètre, l’écriture de la carte de performances est désactivée. Cela équivaut à définir la valeur sur `0` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | N/A | N/A |
| **Variable d’environnement** | `COMPlus_PerfMapEnabled` | `0`-désactivé<br/>`1`-activé |

## <a name="perf-log-markers"></a>Marqueurs de journaux de performances

- Active ou désactive l’acceptation et l’ignorance du signal spécifié en tant que marqueur dans les journaux de performances.
- Si vous omettez ce paramètre, le signal spécifié n’est pas ignoré. Cela équivaut à définir la valeur sur `0` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | N/A | N/A |
| **Variable d’environnement** | `COMPlus_PerfMapIgnoreSignal` | `0`-désactivé<br/>`1`-activé |

> [!NOTE]
> Ce paramètre est ignoré si [COMPlus_PerfMapEnabled](#write-perf-map) est omis ou défini sur `0` (autrement dit, désactivé).
