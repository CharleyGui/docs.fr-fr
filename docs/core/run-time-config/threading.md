---
title: Paramètres de configuration de thread
description: En savoir plus sur les paramètres d’exécution qui configurent les threads pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733433"
---
# <a name="run-time-configuration-options-for-threading"></a>Options de configuration au moment de l’exécution pour le Threading

## <a name="cpu-groups"></a>Groupes de PROCESSEURs

- Configure si les threads sont automatiquement distribués entre les groupes de PROCESSEURs.
- Valeur par défaut : désactivé (`0`).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | Non applicable | Non applicable |
| **Variable d’environnement** | `COMPlus_Thread_UseAllCpuGroups` | `0`-désactivé<br/>activé `1` |

## <a name="minimum-threads"></a>Nombre minimal de threads

- Spécifie le nombre minimal de threads pour le pool de threads de travail.
- Correspond à la méthode <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Entier qui représente le nombre minimal de threads. |
| **MSBuild, propriété** | `ThreadPoolMinThreads` | Entier qui représente le nombre minimal de threads. |
| **Variable d’environnement** | Non applicable | Non applicable |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a>Nombre maximal de threads

- Spécifie le nombre maximal de threads pour le pool de threads de travail.
- Correspond à la méthode <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Entier qui représente le nombre maximal de threads. |
| **MSBuild, propriété** | `ThreadPoolMaxThreads` | Entier qui représente le nombre maximal de threads. |
| **Variable d’environnement** | Non applicable | Non applicable |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
