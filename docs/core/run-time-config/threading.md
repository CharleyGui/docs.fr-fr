---
title: Paramètres de configuration de thread
description: En savoir plus sur les paramètres d’exécution qui configurent les threads pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761926"
---
# <a name="run-time-configuration-options-for-threading"></a>Options de configuration au moment de l’exécution pour le Threading

## <a name="cpu-groups"></a>Groupes de PROCESSEURs

- Configure si les threads sont automatiquement distribués entre les groupes de PROCESSEURs.
- Si vous omettez ce paramètre, les threads ne sont pas distribués entre les groupes de PROCESSEURs. Cela équivaut à définir la valeur sur `0` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | N/A | N/A |
| **Variable d’environnement** | `COMPlus_Thread_UseAllCpuGroups` | `0`-désactivé<br/>`1`-activé |

## <a name="minimum-threads"></a>Nombre minimal de threads

- Spécifie le nombre minimal de threads pour le pool de threads de travail.
- Correspond à la <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Entier qui représente le nombre minimal de threads. |
| **MSBuild, propriété** | `ThreadPoolMinThreads` | Entier qui représente le nombre minimal de threads. |
| **Variable d’environnement** | N/A | N/A |

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
- Correspond à la <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Entier qui représente le nombre maximal de threads. |
| **MSBuild, propriété** | `ThreadPoolMaxThreads` | Entier qui représente le nombre maximal de threads. |
| **Variable d’environnement** | N/A | N/A |

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
