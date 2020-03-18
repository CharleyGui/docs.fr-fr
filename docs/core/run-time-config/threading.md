---
title: Réglages de config de threading
description: Découvrez les paramètres en temps d’exécution qui configurent le threading pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789851"
---
# <a name="run-time-configuration-options-for-threading"></a>Options de configuration en temps d’exécution pour le threading

## <a name="cpu-groups"></a>Groupes CPU

- Configure si les threads sont automatiquement distribués entre les groupes CPU.
- Défaut: Désactivé`0`( ).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | N/A | N/A |
| **Variable de l’environnement** | `COMPlus_Thread_UseAllCpuGroups` | `0`- désactivé<br/>`1`- activé |

## <a name="minimum-threads"></a>Fils minimums

- Spécifie le nombre minimum de threads pour le pool de threads du travailleur.
- Correspond à <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> la méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MinThreads` | Un intégrant qui représente le nombre minimum de fils |
| **Propriété MSBuild** | `ThreadPoolMinThreads` | Un intégrant qui représente le nombre minimum de fils |
| **Variable de l’environnement** | N/A | N/A |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

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

## <a name="maximum-threads"></a>Fils maximums

- Spécifie le nombre maximum de threads pour le pool de thread du travailleur.
- Correspond à <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> la méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MaxThreads` | Un intégrant qui représente le nombre maximum de fils |
| **Propriété MSBuild** | `ThreadPoolMaxThreads` | Un intégrant qui représente le nombre maximum de fils |
| **Variable de l’environnement** | N/A | N/A |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

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
