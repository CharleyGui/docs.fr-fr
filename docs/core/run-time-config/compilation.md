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
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="366de-103">Options de configuration au moment de l’exécution pour la compilation</span><span class="sxs-lookup"><span data-stu-id="366de-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="366de-104">Compilation hiérarchisée</span><span class="sxs-lookup"><span data-stu-id="366de-104">Tiered compilation</span></span>

- <span data-ttu-id="366de-105">Configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="366de-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="366de-106">Méthodes de transition de compilation hiérarchisée via deux niveaux :</span><span class="sxs-lookup"><span data-stu-id="366de-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="366de-107">Le premier niveau génère du code plus rapidement ([JIT rapide](#quick-jit)) ou charge du code pré-compilé ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="366de-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="366de-108">Le deuxième niveau génère du code optimisé en arrière-plan (« optimisation du JIT »).</span><span class="sxs-lookup"><span data-stu-id="366de-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="366de-109">Dans .NET Core 3,0 et versions ultérieures, la compilation à plusieurs niveaux est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="366de-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="366de-110">Dans .NET Core 2,1 et 2,2, la compilation à plusieurs niveaux est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="366de-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="366de-111">Pour plus d’informations, consultez le [Guide de compilation à plusieurs niveaux](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="366de-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="366de-112">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="366de-112">Setting name</span></span> | <span data-ttu-id="366de-113">Valeurs</span><span class="sxs-lookup"><span data-stu-id="366de-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="366de-114">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="366de-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="366de-115">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-115">`true` - enabled</span></span><br/><span data-ttu-id="366de-116">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-116">`false` - disabled</span></span> |
| <span data-ttu-id="366de-117">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="366de-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="366de-118">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-118">`true` - enabled</span></span><br/><span data-ttu-id="366de-119">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-119">`false` - disabled</span></span> |
| <span data-ttu-id="366de-120">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="366de-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="366de-121">`1` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-121">`1` - enabled</span></span><br/><span data-ttu-id="366de-122">`0` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="366de-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="366de-123">Examples</span></span>

<span data-ttu-id="366de-124">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="366de-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="366de-125">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="366de-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="366de-126">JIT rapide</span><span class="sxs-lookup"><span data-stu-id="366de-126">Quick JIT</span></span>

- <span data-ttu-id="366de-127">Configure si le compilateur JIT utilise *Quick JIT*.</span><span class="sxs-lookup"><span data-stu-id="366de-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="366de-128">Pour les méthodes qui ne contiennent pas de boucles et pour lesquelles du code précompilé n’est pas disponible, le JIT rapide les compile plus rapidement, mais sans optimisation.</span><span class="sxs-lookup"><span data-stu-id="366de-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="366de-129">L’activation du JIT rapide réduit le temps de démarrage, mais peut produire du code avec des caractéristiques de performances dégradées.</span><span class="sxs-lookup"><span data-stu-id="366de-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="366de-130">Par exemple, le code peut utiliser plus d’espace de pile, allouer davantage de mémoire et s’exécuter plus lentement.</span><span class="sxs-lookup"><span data-stu-id="366de-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="366de-131">Si le JIT rapide est désactivé mais que la [compilation hiérarchisée](#tiered-compilation) est activée, seul le code précompilé participe à la compilation hiérarchisée.</span><span class="sxs-lookup"><span data-stu-id="366de-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="366de-132">Si une méthode n’est pas précompilée avec [ReadyToRun](#readytorun), le comportement JIT est le même que si la [compilation à plusieurs niveaux](#tiered-compilation) était désactivée.</span><span class="sxs-lookup"><span data-stu-id="366de-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="366de-133">Dans .NET Core 3,0 et versions ultérieures, le JIT rapide est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="366de-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="366de-134">Dans .NET Core 2,1 et 2,2, le JIT rapide est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="366de-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="366de-135">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="366de-135">Setting name</span></span> | <span data-ttu-id="366de-136">Valeurs</span><span class="sxs-lookup"><span data-stu-id="366de-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="366de-137">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="366de-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="366de-138">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-138">`true` - enabled</span></span><br/><span data-ttu-id="366de-139">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-139">`false` - disabled</span></span> |
| <span data-ttu-id="366de-140">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="366de-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="366de-141">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-141">`true` - enabled</span></span><br/><span data-ttu-id="366de-142">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-142">`false` - disabled</span></span> |
| <span data-ttu-id="366de-143">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="366de-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="366de-144">`1` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-144">`1` - enabled</span></span><br/><span data-ttu-id="366de-145">`0` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="366de-146">Exemples</span><span class="sxs-lookup"><span data-stu-id="366de-146">Examples</span></span>

<span data-ttu-id="366de-147">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="366de-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="366de-148">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="366de-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="366de-149">JIT rapide pour les boucles</span><span class="sxs-lookup"><span data-stu-id="366de-149">Quick JIT for loops</span></span>

- <span data-ttu-id="366de-150">Configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="366de-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="366de-151">L’activation du JIT rapide pour les boucles peut améliorer les performances de démarrage.</span><span class="sxs-lookup"><span data-stu-id="366de-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="366de-152">Toutefois, les boucles longues peuvent être bloquées dans du code moins optimisé pendant de longues périodes.</span><span class="sxs-lookup"><span data-stu-id="366de-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="366de-153">Si le [JIT rapide](#quick-jit) est désactivé, ce paramètre n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="366de-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="366de-154">Si vous omettez ce paramètre, le JIT rapide n’est pas utilisé pour les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="366de-154">If you omit this setting, quick JIT is not used for methods that contain loops.</span></span> <span data-ttu-id="366de-155">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="366de-155">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="366de-156">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="366de-156">Setting name</span></span> | <span data-ttu-id="366de-157">Valeurs</span><span class="sxs-lookup"><span data-stu-id="366de-157">Values</span></span> |
| - | - | - |
| <span data-ttu-id="366de-158">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="366de-158">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="366de-159">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-159">`false` - disabled</span></span><br/><span data-ttu-id="366de-160">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-160">`true` - enabled</span></span> |
| <span data-ttu-id="366de-161">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="366de-161">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="366de-162">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-162">`false` - disabled</span></span><br/><span data-ttu-id="366de-163">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-163">`true` - enabled</span></span> |
| <span data-ttu-id="366de-164">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="366de-164">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="366de-165">`0` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-165">`0` - disabled</span></span><br/><span data-ttu-id="366de-166">`1` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-166">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="366de-167">Exemples</span><span class="sxs-lookup"><span data-stu-id="366de-167">Examples</span></span>

<span data-ttu-id="366de-168">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="366de-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="366de-169">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="366de-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="366de-170">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="366de-170">ReadyToRun</span></span>

- <span data-ttu-id="366de-171">Configure si le Runtime .NET Core utilise du code précompilé pour les images avec les données ReadyToRun disponibles.</span><span class="sxs-lookup"><span data-stu-id="366de-171">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="366de-172">La désactivation de cette option force le runtime à compiler le code d’infrastructure juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="366de-172">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="366de-173">Pour plus d’informations, consultez [prêt pour l’exécution](../deploying/ready-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="366de-173">For more information, see [Ready to Run](../deploying/ready-to-run.md).</span></span>
- <span data-ttu-id="366de-174">Si vous omettez ce paramètre, .NET utilise les données ReadyToRun lorsqu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="366de-174">If you omit this setting, .NET uses ReadyToRun data when it's available.</span></span> <span data-ttu-id="366de-175">Cela équivaut à définir la valeur sur `1` .</span><span class="sxs-lookup"><span data-stu-id="366de-175">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="366de-176">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="366de-176">Setting name</span></span> | <span data-ttu-id="366de-177">Valeurs</span><span class="sxs-lookup"><span data-stu-id="366de-177">Values</span></span> |
| - | - | - |
| <span data-ttu-id="366de-178">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="366de-178">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="366de-179">`1` -activé</span><span class="sxs-lookup"><span data-stu-id="366de-179">`1` - enabled</span></span><br/><span data-ttu-id="366de-180">`0` -désactivé</span><span class="sxs-lookup"><span data-stu-id="366de-180">`0` - disabled</span></span> |
