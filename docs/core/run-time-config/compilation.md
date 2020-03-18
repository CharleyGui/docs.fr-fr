---
title: Compilation config paramètres
description: Découvrez les paramètres de run-time qui configurent le fonctionnement du compilateur JIT pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092887"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="c3b02-103">Options de configuration en temps d’exécution pour la compilation</span><span class="sxs-lookup"><span data-stu-id="c3b02-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="c3b02-104">Compilation hiérarchisée</span><span class="sxs-lookup"><span data-stu-id="c3b02-104">Tiered compilation</span></span>

- <span data-ttu-id="c3b02-105">Configure si le compilateur juste-à-temps (JIT) utilise [la compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="c3b02-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="c3b02-106">Méthodes de transition de compilation à plusieurs niveaux à travers deux niveaux :</span><span class="sxs-lookup"><span data-stu-id="c3b02-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="c3b02-107">Le premier niveau génère du code plus rapidement[(JIT rapide](#quick-jit)) ou charge le code pré-compilé ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="c3b02-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="c3b02-108">Le deuxième niveau génère du code optimisé en arrière-plan (« optimisation JIT »).</span><span class="sxs-lookup"><span data-stu-id="c3b02-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="c3b02-109">Dans .NET Core 3.0 et plus tard, la compilation à plusieurs niveaux est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3b02-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="c3b02-110">Dans .NET Core 2.1 et 2.2, la compilation à plusieurs niveaux est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3b02-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="c3b02-111">Pour plus d’informations, consultez le [guide de compilation Tiered](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span><span class="sxs-lookup"><span data-stu-id="c3b02-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="c3b02-112">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c3b02-112">Setting name</span></span> | <span data-ttu-id="c3b02-113">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c3b02-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c3b02-114">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="c3b02-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="c3b02-115">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-115">`true` - enabled</span></span><br/><span data-ttu-id="c3b02-116">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-116">`false` - disabled</span></span> |
| <span data-ttu-id="c3b02-117">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c3b02-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="c3b02-118">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-118">`true` - enabled</span></span><br/><span data-ttu-id="c3b02-119">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-119">`false` - disabled</span></span> |
| <span data-ttu-id="c3b02-120">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="c3b02-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="c3b02-121">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-121">`1` - enabled</span></span><br/><span data-ttu-id="c3b02-122">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="c3b02-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="c3b02-123">Examples</span></span>

<span data-ttu-id="c3b02-124">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="c3b02-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="c3b02-125">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c3b02-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="c3b02-126">JIT rapide</span><span class="sxs-lookup"><span data-stu-id="c3b02-126">Quick JIT</span></span>

- <span data-ttu-id="c3b02-127">Configure si le compilateur JIT utilise *JIT rapide*.</span><span class="sxs-lookup"><span data-stu-id="c3b02-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="c3b02-128">Pour les méthodes qui ne contiennent pas de boucles et pour lesquelles le code pré-compilé n’est pas disponible, JIT rapide les compile plus rapidement, mais sans optimisations.</span><span class="sxs-lookup"><span data-stu-id="c3b02-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="c3b02-129">L’activation d’un JIT rapide diminue le temps de démarrage mais peut produire du code avec des caractéristiques de performance dégradées.</span><span class="sxs-lookup"><span data-stu-id="c3b02-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="c3b02-130">Par exemple, le code peut utiliser plus d’espace de pile, allouer plus de mémoire, et courir plus lentement.</span><span class="sxs-lookup"><span data-stu-id="c3b02-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="c3b02-131">Si le JIT rapide est désactivé mais que la compilation à plusieurs niveaux est [activée,](#tiered-compilation) seul le code pré-compilé participe à une compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="c3b02-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="c3b02-132">Si une méthode n’est pas pré-compilée avec [ReadyToRun](#readytorun), le comportement JIT est le même que si la compilation à plusieurs niveaux ont été [désactivées.](#tiered-compilation)</span><span class="sxs-lookup"><span data-stu-id="c3b02-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="c3b02-133">Dans .NET Core 3.0 et plus tard, JIT rapide est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3b02-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="c3b02-134">Dans .NET Core 2.1 et 2.2, JIT rapide est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3b02-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="c3b02-135">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c3b02-135">Setting name</span></span> | <span data-ttu-id="c3b02-136">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c3b02-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c3b02-137">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="c3b02-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="c3b02-138">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-138">`true` - enabled</span></span><br/><span data-ttu-id="c3b02-139">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-139">`false` - disabled</span></span> |
| <span data-ttu-id="c3b02-140">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c3b02-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="c3b02-141">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-141">`true` - enabled</span></span><br/><span data-ttu-id="c3b02-142">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-142">`false` - disabled</span></span> |
| <span data-ttu-id="c3b02-143">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="c3b02-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="c3b02-144">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-144">`1` - enabled</span></span><br/><span data-ttu-id="c3b02-145">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="c3b02-146">Exemples</span><span class="sxs-lookup"><span data-stu-id="c3b02-146">Examples</span></span>

<span data-ttu-id="c3b02-147">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="c3b02-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="c3b02-148">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c3b02-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="c3b02-149">JIT rapide pour les boucles</span><span class="sxs-lookup"><span data-stu-id="c3b02-149">Quick JIT for loops</span></span>

- <span data-ttu-id="c3b02-150">Configure si le compilateur JIT utilise JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="c3b02-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="c3b02-151">L’activation d’un JIT rapide pour les boucles peut améliorer les performances du démarrage.</span><span class="sxs-lookup"><span data-stu-id="c3b02-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="c3b02-152">Cependant, les boucles de longue durée peuvent rester coincées dans un code moins optimisé pendant de longues périodes.</span><span class="sxs-lookup"><span data-stu-id="c3b02-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="c3b02-153">Si [le JIT rapide](#quick-jit) est désactivé, ce paramètre n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="c3b02-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="c3b02-154">Défaut: Désactivé`false`( ).</span><span class="sxs-lookup"><span data-stu-id="c3b02-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="c3b02-155">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c3b02-155">Setting name</span></span> | <span data-ttu-id="c3b02-156">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c3b02-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c3b02-157">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="c3b02-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="c3b02-158">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-158">`false` - disabled</span></span><br/><span data-ttu-id="c3b02-159">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-159">`true` - enabled</span></span> |
| <span data-ttu-id="c3b02-160">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c3b02-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="c3b02-161">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-161">`false` - disabled</span></span><br/><span data-ttu-id="c3b02-162">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-162">`true` - enabled</span></span> |
| <span data-ttu-id="c3b02-163">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="c3b02-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="c3b02-164">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-164">`0` - disabled</span></span><br/><span data-ttu-id="c3b02-165">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="c3b02-166">Exemples</span><span class="sxs-lookup"><span data-stu-id="c3b02-166">Examples</span></span>

<span data-ttu-id="c3b02-167">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="c3b02-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="c3b02-168">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c3b02-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="c3b02-169">ReadyToRun (en)</span><span class="sxs-lookup"><span data-stu-id="c3b02-169">ReadyToRun</span></span>

- <span data-ttu-id="c3b02-170">Configure si le temps d’exécution .NET Core utilise le code pré-compilé pour les images avec les données ReadyToRun disponibles.</span><span class="sxs-lookup"><span data-stu-id="c3b02-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="c3b02-171">La désactivation de cette option oblige le temps d’exécution au code-cadre de compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="c3b02-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="c3b02-172">Pour plus d’informations, voir [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="c3b02-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="c3b02-173">Défaut: Activé`1`( ).</span><span class="sxs-lookup"><span data-stu-id="c3b02-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="c3b02-174">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c3b02-174">Setting name</span></span> | <span data-ttu-id="c3b02-175">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c3b02-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c3b02-176">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="c3b02-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="c3b02-177">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="c3b02-177">`1` - enabled</span></span><br/><span data-ttu-id="c3b02-178">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="c3b02-178">`0` - disabled</span></span> |
