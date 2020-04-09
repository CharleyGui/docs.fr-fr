---
title: Compilation config paramètres
description: Découvrez les paramètres de run-time qui configurent le fonctionnement du compilateur JIT pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ac51aa13254b2f2b1fdd8d1dd9c52559831a1659
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989114"
---
# <a name="run-time-configuration-options-for-compilation"></a>Options de configuration en temps d’exécution pour la compilation

## <a name="tiered-compilation"></a>Compilation hiérarchisée

- Configure si le compilateur juste-à-temps (JIT) utilise [la compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation). Méthodes de transition de compilation à plusieurs niveaux à travers deux niveaux :
  - Le premier niveau génère du code plus rapidement[(JIT rapide](#quick-jit)) ou charge le code pré-compilé ([ReadyToRun](#readytorun)).
  - Le deuxième niveau génère du code optimisé en arrière-plan (« optimisation JIT »).
- Dans .NET Core 3.0 et plus tard, la compilation à plusieurs niveaux est activée par défaut.
- Dans .NET Core 2.1 et 2.2, la compilation à plusieurs niveaux est désactivée par défaut.
- Pour plus d’informations, consultez le [guide de compilation Tiered](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation` | `true`- activé<br/>`false`- désactivé |
| **Propriété MSBuild** | `TieredCompilation` | `true`- activé<br/>`false`- désactivé |
| **Variable d’environnement** | `COMPlus_TieredCompilation` | `1`- activé<br/>`0`- désactivé |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a>JIT rapide

- Configure si le compilateur JIT utilise *JIT rapide*. Pour les méthodes qui ne contiennent pas de boucles et pour lesquelles le code pré-compilé n’est pas disponible, JIT rapide les compile plus rapidement, mais sans optimisations.
- L’activation d’un JIT rapide diminue le temps de démarrage mais peut produire du code avec des caractéristiques de performance dégradées. Par exemple, le code peut utiliser plus d’espace de pile, allouer plus de mémoire, et courir plus lentement.
- Si le JIT rapide est désactivé mais que la compilation à plusieurs niveaux est [activée,](#tiered-compilation) seul le code pré-compilé participe à une compilation à plusieurs niveaux. Si une méthode n’est pas pré-compilée avec [ReadyToRun](#readytorun), le comportement JIT est le même que si la compilation à plusieurs niveaux ont été [désactivées.](#tiered-compilation)
- Dans .NET Core 3.0 et plus tard, JIT rapide est activé par défaut.
- Dans .NET Core 2.1 et 2.2, JIT rapide est désactivé par défaut.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJit` | `true`- activé<br/>`false`- désactivé |
| **Propriété MSBuild** | `TieredCompilationQuickJit` | `true`- activé<br/>`false`- désactivé |
| **Variable d’environnement** | `COMPlus_TC_QuickJit` | `1`- activé<br/>`0`- désactivé |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a>JIT rapide pour les boucles

- Configure si le compilateur JIT utilise JIT rapide sur les méthodes qui contiennent des boucles.
- L’activation d’un JIT rapide pour les boucles peut améliorer les performances du démarrage. Cependant, les boucles de longue durée peuvent rester coincées dans un code moins optimisé pendant de longues périodes.
- Si [le JIT rapide](#quick-jit) est désactivé, ce paramètre n’a aucun effet.
- Défaut: Désactivé`false`( ).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`- désactivé<br/>`true`- activé |
| **Propriété MSBuild** | `TieredCompilationQuickJitForLoops` | `false`- désactivé<br/>`true`- activé |
| **Variable d’environnement** | `COMPlus_TC_QuickJitForLoops` | `0`- désactivé<br/>`1`- activé |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun (en)

- Configure si le temps d’exécution .NET Core utilise le code pré-compilé pour les images avec les données ReadyToRun disponibles. La désactivation de cette option oblige le temps d’exécution au code-cadre de compilation JIT.
- Pour plus d’informations, voir [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Défaut: Activé`1`( ).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **Variable d’environnement** | `COMPlus_ReadyToRun` | `1`- activé<br/>`0`- désactivé |
