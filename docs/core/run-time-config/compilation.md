---
title: Paramètres de configuration de compilation
description: En savoir plus sur les paramètres d’exécution qui configurent le fonctionnement du compilateur JIT pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733536"
---
# <a name="run-time-configuration-options-for-compilation"></a>Options de configuration au moment de l’exécution pour la compilation

## <a name="tiered-compilation"></a>Compilation hiérarchisée

- Configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation). Méthodes de transition de compilation hiérarchisée via deux niveaux :
  - Le premier niveau génère du code plus rapidement ([JIT rapide](#quick-jit)) ou charge du code pré-compilé ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).
  - Le deuxième niveau génère du code optimisé en arrière-plan (« optimisation du JIT »).
- Dans .NET Core 3,0 et versions ultérieures, la compilation à plusieurs niveaux est activée par défaut.
- Dans .NET Core 2,1 et 2,2, la compilation à plusieurs niveaux est désactivée par défaut.
- Pour plus d’informations, consultez le [Guide de compilation à plusieurs niveaux](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | activé `true`<br/>`false`-désactivé |
| **MSBuild, propriété** | `TieredCompilation` | activé `true`<br/>`false`-désactivé |
| **Variable d'environnement** | `COMPlus_TieredCompilation` | activé `1`<br/>`0`-désactivé |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

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

- Configure si le compilateur JIT utilise *Quick JIT*. Pour les méthodes qui ne contiennent pas de boucles et pour lesquelles du code précompilé n’est pas disponible, le JIT rapide les compile plus rapidement, mais sans optimisation.
- L’activation du JIT rapide réduit le temps de démarrage, mais peut produire du code avec des caractéristiques de performances dégradées. Par exemple, le code peut utiliser plus d’espace de pile, allouer davantage de mémoire et s’exécuter plus lentement.
- Si le JIT rapide est désactivé mais que la [compilation hiérarchisée](#tiered-compilation) est activée, seul le code précompilé participe à la compilation hiérarchisée. Si une méthode n’est pas précompilée avec [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), le comportement JIT est le même que si la [compilation à plusieurs niveaux](#tiered-compilation) était désactivée.
- Dans .NET Core 3,0 et versions ultérieures, le JIT rapide est activé par défaut.
- Dans .NET Core 2,1 et 2,2, le JIT rapide est désactivé par défaut.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJit` | activé `true`<br/>`false`-désactivé |
| **MSBuild, propriété** | `TieredCompilationQuickJit` | activé `true`<br/>`false`-désactivé |
| **Variable d'environnement** | `COMPlus_TC_QuickJit` | activé `1`<br/>`0`-désactivé |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

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

- Configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.
- L’activation du JIT rapide pour les boucles peut améliorer les performances de démarrage. Toutefois, les boucles longues peuvent être bloquées dans du code moins optimisé pendant de longues périodes.
- Si le [JIT rapide](#quick-jit) est désactivé, ce paramètre n’a aucun effet.
- Valeur par défaut : désactivé (`false`).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`-désactivé<br/>activé `true` |
| **MSBuild, propriété** | `TieredCompilationQuickJitForLoops` | `false`-désactivé<br/>activé `true` |
| **Variable d'environnement** | `COMPlus_TC_QuickJitForLoops` | `0`-désactivé<br/>activé `1` |

### <a name="examples"></a>Exemples

fichier *runtimeconfig. JSON* :

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
