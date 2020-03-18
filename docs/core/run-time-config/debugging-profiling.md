---
title: Réglages de profilage de débogage
description: Renseignez-vous sur les paramètres de course qui configurent le débogage et le profilage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802798"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Options de configuration en temps d’exécution pour le débogage et le profilage

## <a name="enable-diagnostics"></a>Activation des diagnostics

- Configure si le débbuggeur, le profileur et les diagnostics EventPipe sont activés ou désactivés.
- Défaut: Activé`1`( ).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_EnableDiagnostics` | `1`- activé<br/>`0`- désactivé |

## <a name="enable-profiling"></a>Activer le profilage

- Configure si le profilage est activé pour le processus en cours d’exécution.
- Défaut: Désactivé`0`( ).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | N/A | N/A |
| **Variable de l’environnement** | `CORECLR_ENABLE_PROFILING` | `0`- désactivé<br/>`1`- activé |

## <a name="profiler-guid"></a>Profiler GUID

- Spécifie le GUID du profileur à charger dans le processus en cours d’exécution.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | N/A | N/A |
| **Variable de l’environnement** | `CORECLR_PROFILER` | *chaîne-guid* |

## <a name="profiler-location"></a>Emplacement profileur

- Spécifie le chemin vers le profileur DLL pour charger dans le processus en cours d’exécution (ou 32 bits ou 64 bits processus).
- Si plus d’une variable est réglée, les variables spécifiques à la bits ont préséance. Ils spécifient quelle bitté de profiler à charger.
- Pour plus d’informations, voir [Trouver la bibliothèque de profileur](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **Variable de l’environnement** | `CORECLR_PROFILER_PATH` | *corde-chemin* |
| **Variable de l’environnement** | `CORECLR_PROFILER_PATH_32` | *corde-chemin* |
| **Variable de l’environnement** | `CORECLR_PROFILER_PATH_64` | *corde-chemin* |

## <a name="write-perf-map"></a>Écrire la carte de perf

- Permet ou désactive l’écriture */tmp/perf-$pid.map* sur les systèmes Linux.
- Défaut: Désactivé`0`( ).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_PerfMapEnabled` | `0`- désactivé<br/>`1`- activé |

## <a name="perf-log-markers"></a>Marqueurs de journal Perf

- Quand `COMPlus_PerfMapEnabled` est `1`réglé à , permet ou désactive le signal spécifié d’être accepté et ignoré comme un marqueur dans les journaux perf.
- Défaut: Désactivé`0`( ).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_PerfMapIgnoreSignal` | `0`- désactivé<br/>`1`- activé |
