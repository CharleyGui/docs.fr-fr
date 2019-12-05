---
title: Débogage des paramètres de configuration du profilage
description: En savoir plus sur les paramètres d’exécution qui configurent le débogage et le profilage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802798"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Options de configuration au moment de l’exécution pour le débogage et le profilage

## <a name="enable-diagnostics"></a>Activer le diagnostic

- Configure si le débogueur, le profileur et les diagnostics EventPipe sont activés ou désactivés.
- Valeur par défaut : activé (`1`).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_EnableDiagnostics` | activé `1`<br/>`0`-désactivé |

## <a name="enable-profiling"></a>Activer le profilage

- Configure si le profilage est activé pour le processus en cours d’exécution.
- Valeur par défaut : désactivé (`0`).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable |
| **Variable d'environnement** | `CORECLR_ENABLE_PROFILING` | `0`-désactivé<br/>activé `1` |

## <a name="profiler-guid"></a>GUID du profileur

- Spécifie le GUID du profileur à charger dans le processus en cours d’exécution.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable |
| **Variable d'environnement** | `CORECLR_PROFILER` | *GUID de chaîne* |

## <a name="profiler-location"></a>Emplacement du profileur

- Spécifie le chemin d’accès à la DLL du profileur à charger dans le processus en cours d’exécution (processus 32 bits ou 64 bits).
- Si plusieurs variables sont définies, les variables spécifiques au nombre de bits sont prioritaires. Ils spécifient le nombre de bits du profileur à charger.
- Pour plus d’informations, consultez [recherche de la bibliothèque du profileur](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **Variable d'environnement** | `CORECLR_PROFILER_PATH` | *chaîne-chemin d’accès* |
| **Variable d'environnement** | `CORECLR_PROFILER_PATH_32` | *chaîne-chemin d’accès* |
| **Variable d'environnement** | `CORECLR_PROFILER_PATH_64` | *chaîne-chemin d’accès* |

## <a name="write-perf-map"></a>Écrire le mappage des performances

- Active ou désactive l’écriture de */tmp/perf-$PID. map* sur les systèmes Linux.
- Valeur par défaut : désactivé (`0`).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_PerfMapEnabled` | `0`-désactivé<br/>activé `1` |

## <a name="perf-log-markers"></a>Marqueurs de journaux de performances

- Lorsque `COMPlus_PerfMapEnabled` a la valeur `1`, active ou désactive l’acceptation et l’ignorance du signal spécifié en tant que marqueur dans les journaux de performances.
- Valeur par défaut : désactivé (`0`).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_PerfMapIgnoreSignal` | `0`-désactivé<br/>activé `1` |
