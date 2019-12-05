---
title: Paramètres de configuration de thread
description: En savoir plus sur les paramètres d’exécution qui configurent les threads pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802763"
---
# <a name="run-time-configuration-options-for-threading"></a>Options de configuration au moment de l’exécution pour le Threading

## <a name="cpu-groups"></a>Groupes de PROCESSEURs

- Configure si les threads sont automatiquement distribués entre les groupes de PROCESSEURs.
- Valeur par défaut : désactivé (`0`).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable |
| **Variable d'environnement** | `COMPlus_Thread_UseAllCpuGroups` | `0`-désactivé<br/>activé `1` |

## <a name="minimum-threads"></a>Nombre minimal de threads

- Spécifie le nombre minimal de threads pour le pool de threads de travail.
- Correspond à la méthode <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Entier qui représente le nombre minimal de threads. |
| **Variable d'environnement** | Non applicable | Non applicable |

## <a name="maximum-threads"></a>Nombre maximal de threads

- Spécifie le nombre maximal de threads pour le pool de threads de travail.
- Correspond à la méthode <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Entier qui représente le nombre maximal de threads. |
| **Variable d'environnement** | Non applicable | Non applicable |
