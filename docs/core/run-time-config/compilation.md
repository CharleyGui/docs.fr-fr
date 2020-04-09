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
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="96890-103">Options de configuration en temps d’exécution pour la compilation</span><span class="sxs-lookup"><span data-stu-id="96890-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="96890-104">Compilation hiérarchisée</span><span class="sxs-lookup"><span data-stu-id="96890-104">Tiered compilation</span></span>

- <span data-ttu-id="96890-105">Configure si le compilateur juste-à-temps (JIT) utilise [la compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="96890-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="96890-106">Méthodes de transition de compilation à plusieurs niveaux à travers deux niveaux :</span><span class="sxs-lookup"><span data-stu-id="96890-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="96890-107">Le premier niveau génère du code plus rapidement[(JIT rapide](#quick-jit)) ou charge le code pré-compilé ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="96890-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="96890-108">Le deuxième niveau génère du code optimisé en arrière-plan (« optimisation JIT »).</span><span class="sxs-lookup"><span data-stu-id="96890-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="96890-109">Dans .NET Core 3.0 et plus tard, la compilation à plusieurs niveaux est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="96890-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="96890-110">Dans .NET Core 2.1 et 2.2, la compilation à plusieurs niveaux est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="96890-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="96890-111">Pour plus d’informations, consultez le [guide de compilation Tiered](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="96890-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="96890-112">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="96890-112">Setting name</span></span> | <span data-ttu-id="96890-113">Valeurs</span><span class="sxs-lookup"><span data-stu-id="96890-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="96890-114">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="96890-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="96890-115">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-115">`true` - enabled</span></span><br/><span data-ttu-id="96890-116">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-116">`false` - disabled</span></span> |
| <span data-ttu-id="96890-117">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="96890-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="96890-118">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-118">`true` - enabled</span></span><br/><span data-ttu-id="96890-119">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-119">`false` - disabled</span></span> |
| <span data-ttu-id="96890-120">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="96890-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="96890-121">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-121">`1` - enabled</span></span><br/><span data-ttu-id="96890-122">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="96890-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="96890-123">Examples</span></span>

<span data-ttu-id="96890-124">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="96890-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="96890-125">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="96890-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="96890-126">JIT rapide</span><span class="sxs-lookup"><span data-stu-id="96890-126">Quick JIT</span></span>

- <span data-ttu-id="96890-127">Configure si le compilateur JIT utilise *JIT rapide*.</span><span class="sxs-lookup"><span data-stu-id="96890-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="96890-128">Pour les méthodes qui ne contiennent pas de boucles et pour lesquelles le code pré-compilé n’est pas disponible, JIT rapide les compile plus rapidement, mais sans optimisations.</span><span class="sxs-lookup"><span data-stu-id="96890-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="96890-129">L’activation d’un JIT rapide diminue le temps de démarrage mais peut produire du code avec des caractéristiques de performance dégradées.</span><span class="sxs-lookup"><span data-stu-id="96890-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="96890-130">Par exemple, le code peut utiliser plus d’espace de pile, allouer plus de mémoire, et courir plus lentement.</span><span class="sxs-lookup"><span data-stu-id="96890-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="96890-131">Si le JIT rapide est désactivé mais que la compilation à plusieurs niveaux est [activée,](#tiered-compilation) seul le code pré-compilé participe à une compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="96890-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="96890-132">Si une méthode n’est pas pré-compilée avec [ReadyToRun](#readytorun), le comportement JIT est le même que si la compilation à plusieurs niveaux ont été [désactivées.](#tiered-compilation)</span><span class="sxs-lookup"><span data-stu-id="96890-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="96890-133">Dans .NET Core 3.0 et plus tard, JIT rapide est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="96890-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="96890-134">Dans .NET Core 2.1 et 2.2, JIT rapide est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="96890-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="96890-135">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="96890-135">Setting name</span></span> | <span data-ttu-id="96890-136">Valeurs</span><span class="sxs-lookup"><span data-stu-id="96890-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="96890-137">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="96890-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="96890-138">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-138">`true` - enabled</span></span><br/><span data-ttu-id="96890-139">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-139">`false` - disabled</span></span> |
| <span data-ttu-id="96890-140">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="96890-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="96890-141">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-141">`true` - enabled</span></span><br/><span data-ttu-id="96890-142">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-142">`false` - disabled</span></span> |
| <span data-ttu-id="96890-143">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="96890-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="96890-144">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-144">`1` - enabled</span></span><br/><span data-ttu-id="96890-145">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="96890-146">Exemples</span><span class="sxs-lookup"><span data-stu-id="96890-146">Examples</span></span>

<span data-ttu-id="96890-147">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="96890-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="96890-148">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="96890-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="96890-149">JIT rapide pour les boucles</span><span class="sxs-lookup"><span data-stu-id="96890-149">Quick JIT for loops</span></span>

- <span data-ttu-id="96890-150">Configure si le compilateur JIT utilise JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="96890-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="96890-151">L’activation d’un JIT rapide pour les boucles peut améliorer les performances du démarrage.</span><span class="sxs-lookup"><span data-stu-id="96890-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="96890-152">Cependant, les boucles de longue durée peuvent rester coincées dans un code moins optimisé pendant de longues périodes.</span><span class="sxs-lookup"><span data-stu-id="96890-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="96890-153">Si [le JIT rapide](#quick-jit) est désactivé, ce paramètre n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="96890-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="96890-154">Défaut: Désactivé`false`( ).</span><span class="sxs-lookup"><span data-stu-id="96890-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="96890-155">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="96890-155">Setting name</span></span> | <span data-ttu-id="96890-156">Valeurs</span><span class="sxs-lookup"><span data-stu-id="96890-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="96890-157">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="96890-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="96890-158">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-158">`false` - disabled</span></span><br/><span data-ttu-id="96890-159">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-159">`true` - enabled</span></span> |
| <span data-ttu-id="96890-160">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="96890-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="96890-161">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-161">`false` - disabled</span></span><br/><span data-ttu-id="96890-162">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-162">`true` - enabled</span></span> |
| <span data-ttu-id="96890-163">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="96890-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="96890-164">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-164">`0` - disabled</span></span><br/><span data-ttu-id="96890-165">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="96890-166">Exemples</span><span class="sxs-lookup"><span data-stu-id="96890-166">Examples</span></span>

<span data-ttu-id="96890-167">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="96890-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="96890-168">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="96890-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="96890-169">ReadyToRun (en)</span><span class="sxs-lookup"><span data-stu-id="96890-169">ReadyToRun</span></span>

- <span data-ttu-id="96890-170">Configure si le temps d’exécution .NET Core utilise le code pré-compilé pour les images avec les données ReadyToRun disponibles.</span><span class="sxs-lookup"><span data-stu-id="96890-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="96890-171">La désactivation de cette option oblige le temps d’exécution au code-cadre de compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="96890-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="96890-172">Pour plus d’informations, voir [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="96890-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="96890-173">Défaut: Activé`1`( ).</span><span class="sxs-lookup"><span data-stu-id="96890-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="96890-174">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="96890-174">Setting name</span></span> | <span data-ttu-id="96890-175">Valeurs</span><span class="sxs-lookup"><span data-stu-id="96890-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="96890-176">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="96890-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="96890-177">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="96890-177">`1` - enabled</span></span><br/><span data-ttu-id="96890-178">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="96890-178">`0` - disabled</span></span> |
