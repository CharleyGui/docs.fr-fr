---
title: Paramètres de configuration de compilation
description: En savoir plus sur les paramètres d’exécution qui configurent le fonctionnement du compilateur JIT pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: e5f9e1245b749864787fb808527d022665197edf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654840"
---
# <a name="run-time-configuration-options-for-compilation"></a>Options de configuration au moment de l’exécution pour la compilation

## <a name="tiered-compilation"></a>Compilation hiérarchisée

- Configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation). Méthodes de transition de compilation hiérarchisée via deux niveaux :
  - Le premier niveau génère du code plus rapidement ([JIT rapide](#quick-jit)) ou charge du code pré-compilé ([ReadyToRun](#readytorun)).
  - Le deuxième niveau génère du code optimisé en arrière-plan (« optimisation du JIT »).
- Dans .NET Core 3,0 et versions ultérieures, la compilation à plusieurs niveaux est activée par défaut.
- Dans .NET Core 2,1 et 2,2, la compilation à plusieurs niveaux est désactivée par défaut.
- Pour plus d’informations, consultez le [Guide de compilation à plusieurs niveaux](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `System.Runtime.TieredCompilation` | `true` -activé<br/>`false` -désactivé |
| **MSBuild, propriété** | `TieredCompilation` | `true` -activé<br/>`false` -désactivé |
| **Variable d'environnement** | `COMPlus_TieredCompilation` | `1` -activé<br/>`0` -désactivé |

### <a name="examples"></a>Exemples

*runtimeconfig.jssur le* fichier :

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
- Si le JIT rapide est désactivé mais que la [compilation hiérarchisée](#tiered-compilation) est activée, seul le code précompilé participe à la compilation hiérarchisée. Si une méthode n’est pas précompilée avec [ReadyToRun](#readytorun), le comportement JIT est le même que si la [compilation à plusieurs niveaux](#tiered-compilation) était désactivée.
- Dans .NET Core 3,0 et versions ultérieures, le JIT rapide est activé par défaut.
- Dans .NET Core 2,1 et 2,2, le JIT rapide est désactivé par défaut.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `System.Runtime.TieredCompilation.QuickJit` | `true` -activé<br/>`false` -désactivé |
| **MSBuild, propriété** | `TieredCompilationQuickJit` | `true` -activé<br/>`false` -désactivé |
| **Variable d'environnement** | `COMPlus_TC_QuickJit` | `1` -activé<br/>`0` -désactivé |

### <a name="examples"></a>Exemples

*runtimeconfig.jssur le* fichier :

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
- Si vous omettez ce paramètre, le JIT rapide n’est pas utilisé pour les méthodes qui contiennent des boucles. Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false` -désactivé<br/>`true` -activé |
| **MSBuild, propriété** | `TieredCompilationQuickJitForLoops` | `false` -désactivé<br/>`true` -activé |
| **Variable d'environnement** | `COMPlus_TC_QuickJitForLoops` | `0` -désactivé<br/>`1` -activé |

### <a name="examples"></a>Exemples

*runtimeconfig.jssur le* fichier :

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
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun

- Configure si le Runtime .NET Core utilise du code précompilé pour les images avec les données ReadyToRun disponibles. La désactivation de cette option force le runtime à compiler le code d’infrastructure juste-à-temps.
- Pour plus d’informations, consultez [prêt pour l’exécution](../deploying/ready-to-run.md).
- Si vous omettez ce paramètre, .NET utilise les données ReadyToRun lorsqu’elles sont disponibles. Cela équivaut à définir la valeur sur `1` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **Variable d'environnement** | `COMPlus_ReadyToRun` | `1` -activé<br/>`0` -désactivé |
