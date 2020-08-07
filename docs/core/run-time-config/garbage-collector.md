---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 91d155b638c7e69b3d2c0216266a7c0c0410db4c
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915995"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="f41e9-103">Options de configuration au moment de l’exécution pour garbage collection</span><span class="sxs-lookup"><span data-stu-id="f41e9-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="f41e9-104">Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f41e9-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="f41e9-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="f41e9-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="f41e9-106">Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="f41e9-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="f41e9-107">Les paramètres sont organisés en groupes dans cette page.</span><span class="sxs-lookup"><span data-stu-id="f41e9-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="f41e9-108">Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="f41e9-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="f41e9-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.</span><span class="sxs-lookup"><span data-stu-id="f41e9-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="f41e9-110">Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="f41e9-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="f41e9-111">Ces paramètres sont omis dans cette page.</span><span class="sxs-lookup"><span data-stu-id="f41e9-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="f41e9-112">Pour les valeurs numériques, utilisez la notation décimale pour les paramètres de la *runtimeconfig.jssur* fichier et notation hexadécimale pour les paramètres de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="f41e9-113">Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».</span><span class="sxs-lookup"><span data-stu-id="f41e9-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="f41e9-114">Versions de garbage collection</span><span class="sxs-lookup"><span data-stu-id="f41e9-114">Flavors of garbage collection</span></span>

<span data-ttu-id="f41e9-115">Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="f41e9-116">Pour plus d’informations sur les différences entre les deux, consultez [station de travail et serveur garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="f41e9-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="f41e9-117">Les sous-versions de garbage collection sont en arrière-plan et non simultanées.</span><span class="sxs-lookup"><span data-stu-id="f41e9-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="f41e9-118">Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :</span><span class="sxs-lookup"><span data-stu-id="f41e9-118">Use the following settings to select flavors of garbage collection:</span></span>

- [<span data-ttu-id="f41e9-119">Station de travail et GC de serveur</span><span class="sxs-lookup"><span data-stu-id="f41e9-119">Workstation vs. server GC</span></span>](#workstation-vs-server)
- [<span data-ttu-id="f41e9-120">GC d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="f41e9-120">Background GC</span></span>](#background-gc)

### <a name="workstation-vs-server"></a><span data-ttu-id="f41e9-121">Station de travail et serveur</span><span class="sxs-lookup"><span data-stu-id="f41e9-121">Workstation vs. server</span></span>

- <span data-ttu-id="f41e9-122">Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-122">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="f41e9-123">Par défaut : station de travail garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f41e9-123">Default: Workstation garbage collection.</span></span> <span data-ttu-id="f41e9-124">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-124">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f41e9-125">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-125">Setting name</span></span> | <span data-ttu-id="f41e9-126">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-126">Values</span></span> | <span data-ttu-id="f41e9-127">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-127">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-128">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-128">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="f41e9-129">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="f41e9-129">`false` - workstation</span></span><br/><span data-ttu-id="f41e9-130">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="f41e9-130">`true` - server</span></span> | <span data-ttu-id="f41e9-131">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-131">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-132">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="f41e9-132">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="f41e9-133">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="f41e9-133">`false` - workstation</span></span><br/><span data-ttu-id="f41e9-134">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="f41e9-134">`true` - server</span></span> | <span data-ttu-id="f41e9-135">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-135">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-136">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-136">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="f41e9-137">`0`-station de travail</span><span class="sxs-lookup"><span data-stu-id="f41e9-137">`0` - workstation</span></span><br/><span data-ttu-id="f41e9-138">`1`-serveur</span><span class="sxs-lookup"><span data-stu-id="f41e9-138">`1` - server</span></span> | <span data-ttu-id="f41e9-139">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-139">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-140">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-140">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-141">GCServer</span><span class="sxs-lookup"><span data-stu-id="f41e9-141">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="f41e9-142">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="f41e9-142">`false` - workstation</span></span><br/><span data-ttu-id="f41e9-143">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="f41e9-143">`true` - server</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="f41e9-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="f41e9-144">Examples</span></span>

<span data-ttu-id="f41e9-145">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="f41e9-145">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="f41e9-146">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="f41e9-146">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a><span data-ttu-id="f41e9-147">GC d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="f41e9-147">Background GC</span></span>

- <span data-ttu-id="f41e9-148">Configure si l’garbage collection d’arrière-plan (simultanée) est activée.</span><span class="sxs-lookup"><span data-stu-id="f41e9-148">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="f41e9-149">Valeur par défaut : utilisez GC d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f41e9-149">Default: Use background GC.</span></span> <span data-ttu-id="f41e9-150">Cela équivaut à définir la valeur sur `true` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-150">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="f41e9-151">Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="f41e9-151">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="f41e9-152">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-152">Setting name</span></span> | <span data-ttu-id="f41e9-153">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-153">Values</span></span> | <span data-ttu-id="f41e9-154">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-154">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-155">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-155">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="f41e9-156">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="f41e9-156">`true` - background GC</span></span><br/><span data-ttu-id="f41e9-157">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="f41e9-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f41e9-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-159">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="f41e9-159">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="f41e9-160">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="f41e9-160">`true` - background GC</span></span><br/><span data-ttu-id="f41e9-161">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="f41e9-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f41e9-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-163">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-163">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="f41e9-164">`1`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="f41e9-164">`1` - background GC</span></span><br/><span data-ttu-id="f41e9-165">`0`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="f41e9-165">`0` - non-concurrent GC</span></span> | <span data-ttu-id="f41e9-166">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-166">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-167">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-167">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-168">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="f41e9-168">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="f41e9-169">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="f41e9-169">`true` - background GC</span></span><br/><span data-ttu-id="f41e9-170">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="f41e9-170">`false` - non-concurrent GC</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="f41e9-171">Exemples</span><span class="sxs-lookup"><span data-stu-id="f41e9-171">Examples</span></span>

<span data-ttu-id="f41e9-172">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="f41e9-172">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="f41e9-173">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="f41e9-173">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="f41e9-174">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="f41e9-174">Manage resource usage</span></span>

<span data-ttu-id="f41e9-175">Utilisez les paramètres suivants pour gérer la mémoire et l’utilisation du processeur du garbage collector :</span><span class="sxs-lookup"><span data-stu-id="f41e9-175">Use the following settings to manage the garbage collector's memory and processor usage:</span></span>

- [<span data-ttu-id="f41e9-176">Affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-176">Affinitize</span></span>](#affinitize)
- [<span data-ttu-id="f41e9-177">Masque affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-177">Affinitize mask</span></span>](#affinitize-mask)
- [<span data-ttu-id="f41e9-178">Plages affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-178">Affinitize ranges</span></span>](#affinitize-ranges)
- [<span data-ttu-id="f41e9-179">Groupes de PROCESSEURs</span><span class="sxs-lookup"><span data-stu-id="f41e9-179">CPU groups</span></span>](#cpu-groups)
- [<span data-ttu-id="f41e9-180">Nombre de tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-180">Heap count</span></span>](#heap-count)
- [<span data-ttu-id="f41e9-181">Limite du tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-181">Heap limit</span></span>](#heap-limit)
- [<span data-ttu-id="f41e9-182">Pourcentage de la limite du tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-182">Heap limit percent</span></span>](#heap-limit-percent)
- [<span data-ttu-id="f41e9-183">Pourcentage de mémoire élevé</span><span class="sxs-lookup"><span data-stu-id="f41e9-183">High memory percent</span></span>](#high-memory-percent)
- [<span data-ttu-id="f41e9-184">Limites par objet-tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-184">Per-object-heap limits</span></span>](#per-object-heap-limits)
- [<span data-ttu-id="f41e9-185">Pourcentages de limites de tas par objet</span><span class="sxs-lookup"><span data-stu-id="f41e9-185">Per-object-heap limit percents</span></span>](#per-object-heap-limit-percents)
- [<span data-ttu-id="f41e9-186">Conserver la machine virtuelle</span><span class="sxs-lookup"><span data-stu-id="f41e9-186">Retain VM</span></span>](#retain-vm)

<span data-ttu-id="f41e9-187">Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="f41e9-187">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="heap-count"></a><span data-ttu-id="f41e9-188">Nombre de tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-188">Heap count</span></span>

- <span data-ttu-id="f41e9-189">Limite le nombre de segments de mémoire créés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="f41e9-189">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="f41e9-190">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-190">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f41e9-191">Si l' [affinité du processeur GC](#affinitize) est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers `n` processeurs.</span><span class="sxs-lookup"><span data-stu-id="f41e9-191">If [GC processor affinity](#affinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="f41e9-192">(Utilisez les paramètres [affinité Mask](#affinitize-mask) ou [affinité Ranges](#affinitize-ranges) pour spécifier exactement les processeurs à affinité.)</span><span class="sxs-lookup"><span data-stu-id="f41e9-192">(Use the [affinitize mask](#affinitize-mask) or [affinitize ranges](#affinitize-ranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="f41e9-193">Si l' [affinité du processeur GC](#affinitize) est désactivée, ce paramètre limite le nombre de tas gc.</span><span class="sxs-lookup"><span data-stu-id="f41e9-193">If [GC processor affinity](#affinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="f41e9-194">Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="f41e9-194">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="f41e9-195">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-195">Setting name</span></span> | <span data-ttu-id="f41e9-196">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-196">Values</span></span> | <span data-ttu-id="f41e9-197">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-197">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-198">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-198">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="f41e9-199">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-199">*decimal value*</span></span> | <span data-ttu-id="f41e9-200">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-200">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-201">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-201">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="f41e9-202">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-202">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-203">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-203">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-204">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-204">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-205">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="f41e9-205">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="f41e9-206">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-206">*decimal value*</span></span> | <span data-ttu-id="f41e9-207">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f41e9-207">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f41e9-208">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f41e9-208">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="f41e9-209">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-209">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f41e9-210">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-210">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f41e9-211">Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-211">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="affinitize-mask"></a><span data-ttu-id="f41e9-212">Masque affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-212">Affinitize mask</span></span>

- <span data-ttu-id="f41e9-213">Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.</span><span class="sxs-lookup"><span data-stu-id="f41e9-213">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="f41e9-214">Si l' [affinité du processeur GC](#affinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="f41e9-214">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f41e9-215">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-215">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f41e9-216">La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="f41e9-216">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="f41e9-217">Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="f41e9-217">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="f41e9-218">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="f41e9-218">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="f41e9-219">Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="f41e9-219">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="f41e9-220">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-220">Setting name</span></span> | <span data-ttu-id="f41e9-221">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-221">Values</span></span> | <span data-ttu-id="f41e9-222">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-222">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-223">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-223">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="f41e9-224">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-224">*decimal value*</span></span> | <span data-ttu-id="f41e9-225">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-225">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-226">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-226">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="f41e9-227">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-227">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-228">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-228">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-229">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-229">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-230">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="f41e9-230">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="f41e9-231">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-231">*decimal value*</span></span> | <span data-ttu-id="f41e9-232">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f41e9-232">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f41e9-233">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f41e9-233">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a><span data-ttu-id="f41e9-234">Plages affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-234">Affinitize ranges</span></span>

- <span data-ttu-id="f41e9-235">Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.</span><span class="sxs-lookup"><span data-stu-id="f41e9-235">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="f41e9-236">Ce paramètre est similaire à [System. gc. HeapAffinitizeMask](#affinitize-mask), sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="f41e9-236">This setting is similar to [System.GC.HeapAffinitizeMask](#affinitize-mask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="f41e9-237">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».</span><span class="sxs-lookup"><span data-stu-id="f41e9-237">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="f41e9-238">Si l' [affinité du processeur GC](#affinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="f41e9-238">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f41e9-239">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-239">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f41e9-240">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="f41e9-240">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f41e9-241">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-241">Setting name</span></span> | <span data-ttu-id="f41e9-242">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-242">Values</span></span> | <span data-ttu-id="f41e9-243">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-243">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-244">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-244">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="f41e9-245">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-245">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f41e9-246">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="f41e9-246">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f41e9-247">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="f41e9-247">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f41e9-248">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-248">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-249">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-249">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="f41e9-250">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-250">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f41e9-251">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="f41e9-251">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f41e9-252">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="f41e9-252">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f41e9-253">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-253">.NET Core 3.0</span></span> |

<span data-ttu-id="f41e9-254">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f41e9-254">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a><span data-ttu-id="f41e9-255">Groupes de PROCESSEURs</span><span class="sxs-lookup"><span data-stu-id="f41e9-255">CPU groups</span></span>

- <span data-ttu-id="f41e9-256">Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .</span><span class="sxs-lookup"><span data-stu-id="f41e9-256">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="f41e9-257">Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="f41e9-257">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="f41e9-258">Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="f41e9-258">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="f41e9-259">S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-259">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="f41e9-260">Valeur par défaut : GC ne s’étend pas au-delà des groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="f41e9-260">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="f41e9-261">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-261">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="f41e9-262">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="f41e9-262">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f41e9-263">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-263">Setting name</span></span> | <span data-ttu-id="f41e9-264">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-264">Values</span></span> | <span data-ttu-id="f41e9-265">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-265">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-266">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-266">**runtimeconfig.json**</span></span> | `System.GC.CpuGroup` | <span data-ttu-id="f41e9-267">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="f41e9-267">`0` - disabled</span></span><br/><span data-ttu-id="f41e9-268">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="f41e9-268">`1` - enabled</span></span> | <span data-ttu-id="f41e9-269">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-269">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-270">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-270">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="f41e9-271">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="f41e9-271">`0` - disabled</span></span><br/><span data-ttu-id="f41e9-272">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="f41e9-272">`1` - enabled</span></span> | <span data-ttu-id="f41e9-273">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-273">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-274">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-274">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-275">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="f41e9-275">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="f41e9-276">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="f41e9-276">`false` - disabled</span></span><br/><span data-ttu-id="f41e9-277">`true`-activé</span><span class="sxs-lookup"><span data-stu-id="f41e9-277">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="f41e9-278">Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="f41e9-278">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="f41e9-279">Pour les applications .NET Core, vous pouvez activer cette option en affectant à la `COMPlus_Thread_UseAllCpuGroups` variable d’environnement la valeur `1` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-279">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="affinitize"></a><span data-ttu-id="f41e9-280">Affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-280">Affinitize</span></span>

- <span data-ttu-id="f41e9-281">Spécifie s’il faut *affinité* garbage collection threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="f41e9-281">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="f41e9-282">La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique.</span><span class="sxs-lookup"><span data-stu-id="f41e9-282">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="f41e9-283">Un segment de mémoire est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="f41e9-283">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="f41e9-284">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-284">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f41e9-285">Par défaut : affinité garbage collection les threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="f41e9-285">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="f41e9-286">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-286">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f41e9-287">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-287">Setting name</span></span> | <span data-ttu-id="f41e9-288">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-288">Values</span></span> | <span data-ttu-id="f41e9-289">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-289">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-290">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-290">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="f41e9-291">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-291">`false` - affinitize</span></span><br/><span data-ttu-id="f41e9-292">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-292">`true` - don't affinitize</span></span> | <span data-ttu-id="f41e9-293">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-293">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-294">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-294">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="f41e9-295">`0`-affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-295">`0` - affinitize</span></span><br/><span data-ttu-id="f41e9-296">`1`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-296">`1` - don't affinitize</span></span> | <span data-ttu-id="f41e9-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-298">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-298">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-299">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="f41e9-299">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="f41e9-300">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-300">`false` - affinitize</span></span><br/><span data-ttu-id="f41e9-301">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="f41e9-301">`true` - don't affinitize</span></span> | <span data-ttu-id="f41e9-302">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f41e9-302">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f41e9-303">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f41e9-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a><span data-ttu-id="f41e9-304">Limite du tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-304">Heap limit</span></span>

- <span data-ttu-id="f41e9-305">Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.</span><span class="sxs-lookup"><span data-stu-id="f41e9-305">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="f41e9-306">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f41e9-306">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f41e9-307">Ce paramètre est ignoré si les [limites par objet/tas](#per-object-heap-limits) sont configurées.</span><span class="sxs-lookup"><span data-stu-id="f41e9-307">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="f41e9-308">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus grande de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-308">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f41e9-309">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="f41e9-309">The default value applies if:</span></span>

  - <span data-ttu-id="f41e9-310">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f41e9-310">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f41e9-311">[System. gc. HeapHardLimitPercent](#heap-limit-percent) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="f41e9-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) is not set.</span></span>

| | <span data-ttu-id="f41e9-312">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-312">Setting name</span></span> | <span data-ttu-id="f41e9-313">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-313">Values</span></span> | <span data-ttu-id="f41e9-314">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-314">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-315">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-315">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="f41e9-316">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-316">*decimal value*</span></span> | <span data-ttu-id="f41e9-317">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-317">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-318">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-318">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="f41e9-319">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-319">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-320">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-320">.NET Core 3.0</span></span> |

<span data-ttu-id="f41e9-321">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f41e9-321">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="f41e9-322">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-322">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f41e9-323">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-323">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f41e9-324">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-324">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="heap-limit-percent"></a><span data-ttu-id="f41e9-325">Pourcentage de la limite du tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-325">Heap limit percent</span></span>

- <span data-ttu-id="f41e9-326">Spécifie l’utilisation autorisée du tas GC comme pourcentage de la mémoire physique totale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-326">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="f41e9-327">Si [System. gc. HeapHardLimit](#heap-limit) est également défini, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="f41e9-327">If [System.GC.HeapHardLimit](#heap-limit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="f41e9-328">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f41e9-328">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f41e9-329">Si le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé sous la forme d’un pourcentage de cette limite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f41e9-329">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="f41e9-330">Ce paramètre est ignoré si les [limites par objet/tas](#per-object-heap-limits) sont configurées.</span><span class="sxs-lookup"><span data-stu-id="f41e9-330">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="f41e9-331">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus petite de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-331">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f41e9-332">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="f41e9-332">The default value applies if:</span></span>

  - <span data-ttu-id="f41e9-333">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f41e9-333">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f41e9-334">[System. gc. HeapHardLimit](#heap-limit) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="f41e9-334">[System.GC.HeapHardLimit](#heap-limit) is not set.</span></span>

| | <span data-ttu-id="f41e9-335">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-335">Setting name</span></span> | <span data-ttu-id="f41e9-336">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-336">Values</span></span> | <span data-ttu-id="f41e9-337">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-337">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-338">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-338">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="f41e9-339">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-339">*decimal value*</span></span> | <span data-ttu-id="f41e9-340">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-340">.NET Core 3.0</span></span> |
| <span data-ttu-id="f41e9-341">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-341">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="f41e9-342">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-342">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-343">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-343">.NET Core 3.0</span></span> |

<span data-ttu-id="f41e9-344">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f41e9-344">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="f41e9-345">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-345">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f41e9-346">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-346">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f41e9-347">Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-347">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="f41e9-348">Limites par objet-tas</span><span class="sxs-lookup"><span data-stu-id="f41e9-348">Per-object-heap limits</span></span>

<span data-ttu-id="f41e9-349">Vous pouvez spécifier l’utilisation autorisée du tas du GC pour chaque segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f41e9-349">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="f41e9-350">Les différents tas sont le tas d’objets volumineux (LOH), le tas de petits objets (SOH) et le tas d’objets épinglés (POH).</span><span class="sxs-lookup"><span data-stu-id="f41e9-350">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="f41e9-351">Si vous spécifiez une valeur pour l’un `COMPLUS_GCHeapHardLimitSOH` des `COMPLUS_GCHeapHardLimitLOH` paramètres, ou `COMPLUS_GCHeapHardLimitPOH` , vous devez également spécifier une valeur pour `COMPLUS_GCHeapHardLimitSOH` et `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-351">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="f41e9-352">Si ce n’est pas le cas, l’initialisation du runtime échoue.</span><span class="sxs-lookup"><span data-stu-id="f41e9-352">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="f41e9-353">La valeur par défaut pour `COMPLUS_GCHeapHardLimitPOH` est 0.</span><span class="sxs-lookup"><span data-stu-id="f41e9-353">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="f41e9-354">`COMPLUS_GCHeapHardLimitSOH`et `COMPLUS_GCHeapHardLimitLOH` n’ont pas de valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f41e9-354">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="f41e9-355">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-355">Setting name</span></span> | <span data-ttu-id="f41e9-356">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-356">Values</span></span> | <span data-ttu-id="f41e9-357">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-358">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-358">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOH` | <span data-ttu-id="f41e9-359">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-359">*decimal value*</span></span> | <span data-ttu-id="f41e9-360">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-360">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-361">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-361">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="f41e9-362">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-362">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-363">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-363">.NET 5.0</span></span> |

| | <span data-ttu-id="f41e9-364">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-364">Setting name</span></span> | <span data-ttu-id="f41e9-365">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-365">Values</span></span> | <span data-ttu-id="f41e9-366">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-366">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-367">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-367">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOH` | <span data-ttu-id="f41e9-368">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-368">*decimal value*</span></span> | <span data-ttu-id="f41e9-369">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-369">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-370">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-370">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="f41e9-371">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-371">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-372">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-372">.NET 5.0</span></span> |

| | <span data-ttu-id="f41e9-373">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-373">Setting name</span></span> | <span data-ttu-id="f41e9-374">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-374">Values</span></span> | <span data-ttu-id="f41e9-375">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-375">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-376">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-376">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOH` | <span data-ttu-id="f41e9-377">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-377">*decimal value*</span></span> | <span data-ttu-id="f41e9-378">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-378">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-379">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-379">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="f41e9-380">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-380">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-381">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-381">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="f41e9-382">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-382">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f41e9-383">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-383">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f41e9-384">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-384">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="per-object-heap-limit-percents"></a><span data-ttu-id="f41e9-385">Pourcentages de limites de tas par objet</span><span class="sxs-lookup"><span data-stu-id="f41e9-385">Per-object-heap limit percents</span></span>

<span data-ttu-id="f41e9-386">Vous pouvez spécifier l’utilisation autorisée du tas du GC pour chaque segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f41e9-386">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="f41e9-387">Les différents tas sont le tas d’objets volumineux (LOH), le tas de petits objets (SOH) et le tas d’objets épinglés (POH).</span><span class="sxs-lookup"><span data-stu-id="f41e9-387">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="f41e9-388">Si vous spécifiez une valeur pour l’un `COMPLUS_GCHeapHardLimitSOHPercent` des `COMPLUS_GCHeapHardLimitLOHPercent` paramètres, ou `COMPLUS_GCHeapHardLimitPOHPercent` , vous devez également spécifier une valeur pour `COMPLUS_GCHeapHardLimitSOHPercent` et `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-388">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="f41e9-389">Si ce n’est pas le cas, l’initialisation du runtime échoue.</span><span class="sxs-lookup"><span data-stu-id="f41e9-389">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="f41e9-390">Ces paramètres sont ignorés si `COMPLUS_GCHeapHardLimitSOH` , `COMPLUS_GCHeapHardLimitLOH` et `COMPLUS_GCHeapHardLimitPOH` sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f41e9-390">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="f41e9-391">La valeur 1 signifie que GC utilise 1% de la mémoire physique totale pour ce tas d’objets.</span><span class="sxs-lookup"><span data-stu-id="f41e9-391">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="f41e9-392">Chaque valeur doit être supérieure à zéro et inférieure à 100.</span><span class="sxs-lookup"><span data-stu-id="f41e9-392">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="f41e9-393">En outre, la somme des trois valeurs de pourcentage doit être inférieure à 100.</span><span class="sxs-lookup"><span data-stu-id="f41e9-393">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="f41e9-394">Dans le cas contraire, le runtime ne pourra pas s’initialiser.</span><span class="sxs-lookup"><span data-stu-id="f41e9-394">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="f41e9-395">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-395">Setting name</span></span> | <span data-ttu-id="f41e9-396">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-396">Values</span></span> | <span data-ttu-id="f41e9-397">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-397">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-398">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-398">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOHPercent` | <span data-ttu-id="f41e9-399">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-399">*decimal value*</span></span> | <span data-ttu-id="f41e9-400">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-400">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-401">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-401">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="f41e9-402">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-402">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-403">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-403">.NET 5.0</span></span> |

| | <span data-ttu-id="f41e9-404">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-404">Setting name</span></span> | <span data-ttu-id="f41e9-405">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-405">Values</span></span> | <span data-ttu-id="f41e9-406">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-406">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-407">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-407">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOHPercent` | <span data-ttu-id="f41e9-408">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-408">*decimal value*</span></span> | <span data-ttu-id="f41e9-409">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-409">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-410">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-410">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="f41e9-411">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-411">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-412">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-412">.NET 5.0</span></span> |

| | <span data-ttu-id="f41e9-413">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-413">Setting name</span></span> | <span data-ttu-id="f41e9-414">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-414">Values</span></span> | <span data-ttu-id="f41e9-415">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-416">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-416">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOHPercent` | <span data-ttu-id="f41e9-417">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-417">*decimal value*</span></span> | <span data-ttu-id="f41e9-418">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-418">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-419">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-419">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="f41e9-420">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-420">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-421">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-421">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="f41e9-422">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-422">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f41e9-423">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-423">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f41e9-424">Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-424">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="high-memory-percent"></a><span data-ttu-id="f41e9-425">Pourcentage de mémoire élevé</span><span class="sxs-lookup"><span data-stu-id="f41e9-425">High memory percent</span></span>

<span data-ttu-id="f41e9-426">La charge de mémoire est indiquée par le pourcentage de mémoire physique en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="f41e9-426">Memory load is indicated by the percentage of physical memory in use.</span></span> <span data-ttu-id="f41e9-427">Par défaut, lorsque la charge de mémoire physique atteint **90%**, garbage collection devient plus agressive pour effectuer des garbage collections de compactage complets afin d’éviter la pagination.</span><span class="sxs-lookup"><span data-stu-id="f41e9-427">By default, when the physical memory load reaches **90%**, garbage collection becomes more aggressive about doing full, compacting garbage collections to avoid paging.</span></span> <span data-ttu-id="f41e9-428">Lorsque la charge de mémoire est inférieure à 90%, GC privilégie les collections d’arrière-plan pour les garbage collections complets, qui ont des pauses plus courtes, mais ne réduisent pas de manière importante la taille totale du tas.</span><span class="sxs-lookup"><span data-stu-id="f41e9-428">When memory load is below 90%, GC favors background collections for full garbage collections, which have shorter pauses but don't reduce the total heap size by much.</span></span> <span data-ttu-id="f41e9-429">Sur les ordinateurs disposant d’une quantité importante de mémoire (80 Go ou plus), le seuil de charge par défaut est compris entre 90% et 97%.</span><span class="sxs-lookup"><span data-stu-id="f41e9-429">On machines with a significant amount of memory (80GB or more), the default load threshold is between 90% and 97%.</span></span>

<span data-ttu-id="f41e9-430">Le seuil de charge de mémoire élevé peut être ajusté par la `COMPlus_GCHighMemPercent` variable d’environnement ou le `System.GC.HighMemoryPercent` paramètre de configuration JSON.</span><span class="sxs-lookup"><span data-stu-id="f41e9-430">The high memory load threshold can be adjusted by the `COMPlus_GCHighMemPercent` environment variable or `System.GC.HighMemoryPercent` JSON configuration setting.</span></span> <span data-ttu-id="f41e9-431">Envisagez d’ajuster le seuil si vous souhaitez contrôler la taille du tas.</span><span class="sxs-lookup"><span data-stu-id="f41e9-431">Consider adjusting the threshold if you want to control heap size.</span></span> <span data-ttu-id="f41e9-432">Par exemple, pour le processus dominant sur un ordinateur avec 64 Go de mémoire, il est raisonnable que GC commence à réagir lorsqu’il y a 10% de mémoire disponible.</span><span class="sxs-lookup"><span data-stu-id="f41e9-432">For example, for the dominant process on a machine with 64GB of memory, it's reasonable for GC to start reacting when there's 10% of memory available.</span></span> <span data-ttu-id="f41e9-433">Toutefois, pour les processus plus petits, par exemple, un processus qui consomme uniquement 1 Go de mémoire, le garbage collector peut s’exécuter confortablement avec moins de 10% de la mémoire disponible.</span><span class="sxs-lookup"><span data-stu-id="f41e9-433">But for smaller processes, for example, a process that only consumes 1GB of memory, GC can comfortably run with less than 10% of memory available.</span></span> <span data-ttu-id="f41e9-434">Pour ces processus plus petits, envisagez de définir le seuil plus haut.</span><span class="sxs-lookup"><span data-stu-id="f41e9-434">For these smaller processes, consider setting the threshold higher.</span></span> <span data-ttu-id="f41e9-435">En revanche, si vous souhaitez que les plus grands processus aient des tailles de tas plus petites (même si la mémoire physique disponible est importante), le fait de réduire ce seuil est un moyen efficace pour que GC réagisse plus tôt pour compacter le tas.</span><span class="sxs-lookup"><span data-stu-id="f41e9-435">On the other hand, if you want larger processes to have smaller heap sizes (even when there's plenty of physical memory available), lowering this threshold is an effective way for GC to react sooner to compact the heap down.</span></span>

> [!NOTE]
> <span data-ttu-id="f41e9-436">Pour les processus en cours d’exécution dans un conteneur, GC prend en compte la mémoire physique en fonction de la limite du conteneur.</span><span class="sxs-lookup"><span data-stu-id="f41e9-436">For processes running in a container, GC considers the physical memory based on the container limit.</span></span>

| | <span data-ttu-id="f41e9-437">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-437">Setting name</span></span> | <span data-ttu-id="f41e9-438">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-438">Values</span></span> | <span data-ttu-id="f41e9-439">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-439">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-440">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-440">**runtimeconfig.json**</span></span> | `System.GC.HighMemoryPercent` | <span data-ttu-id="f41e9-441">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-441">*decimal value*</span></span> | <span data-ttu-id="f41e9-442">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f41e9-442">.NET 5.0</span></span> |
| <span data-ttu-id="f41e9-443">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-443">**Environment variable**</span></span> | `COMPlus_GCHighMemPercent` | <span data-ttu-id="f41e9-444">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-444">*hexadecimal value*</span></span> | |

> [!TIP]
> <span data-ttu-id="f41e9-445">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-445">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f41e9-446">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-446">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f41e9-447">Par exemple, pour définir le seuil de mémoire élevé sur 75%, les valeurs sont 75 pour le fichier JSON et 0x4B ou 4B pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-447">For example, to set the high memory threshold to 75%, the values would be 75 for the JSON file and 0x4B or 4B for the environment variable.</span></span>

### <a name="retain-vm"></a><span data-ttu-id="f41e9-448">Conserver la machine virtuelle</span><span class="sxs-lookup"><span data-stu-id="f41e9-448">Retain VM</span></span>

- <span data-ttu-id="f41e9-449">Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f41e9-449">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="f41e9-450">Valeur par défaut : relâcher les segments sur le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f41e9-450">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="f41e9-451">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-451">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f41e9-452">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-452">Setting name</span></span> | <span data-ttu-id="f41e9-453">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-453">Values</span></span> | <span data-ttu-id="f41e9-454">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-454">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-455">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-455">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="f41e9-456">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="f41e9-456">`false` - release to OS</span></span><br/><span data-ttu-id="f41e9-457">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="f41e9-457">`true` - put on standby</span></span> | <span data-ttu-id="f41e9-458">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-458">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-459">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="f41e9-459">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="f41e9-460">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="f41e9-460">`false` - release to OS</span></span><br/><span data-ttu-id="f41e9-461">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="f41e9-461">`true` - put on standby</span></span> | <span data-ttu-id="f41e9-462">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-462">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-463">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-463">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="f41e9-464">`0`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="f41e9-464">`0` - release to OS</span></span><br/><span data-ttu-id="f41e9-465">`1`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="f41e9-465">`1` - put on standby</span></span> | <span data-ttu-id="f41e9-466">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-466">.NET Core 1.0</span></span> |

#### <a name="examples"></a><span data-ttu-id="f41e9-467">Exemples</span><span class="sxs-lookup"><span data-stu-id="f41e9-467">Examples</span></span>

<span data-ttu-id="f41e9-468">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="f41e9-468">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="f41e9-469">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="f41e9-469">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="f41e9-470">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="f41e9-470">Large pages</span></span>

- <span data-ttu-id="f41e9-471">Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="f41e9-471">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="f41e9-472">Valeur par défaut : n’utilisez pas de grandes pages lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="f41e9-472">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="f41e9-473">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-473">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="f41e9-474">Il s’agit d’un paramètre expérimental.</span><span class="sxs-lookup"><span data-stu-id="f41e9-474">This is an experimental setting.</span></span>

| | <span data-ttu-id="f41e9-475">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-475">Setting name</span></span> | <span data-ttu-id="f41e9-476">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-476">Values</span></span> | <span data-ttu-id="f41e9-477">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-477">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-478">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-478">**runtimeconfig.json**</span></span> | <span data-ttu-id="f41e9-479">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-479">N/A</span></span> | <span data-ttu-id="f41e9-480">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-480">N/A</span></span> | <span data-ttu-id="f41e9-481">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-481">N/A</span></span> |
| <span data-ttu-id="f41e9-482">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-482">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="f41e9-483">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="f41e9-483">`0` - disabled</span></span><br/><span data-ttu-id="f41e9-484">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="f41e9-484">`1` - enabled</span></span> | <span data-ttu-id="f41e9-485">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-485">.NET Core 3.0</span></span> |

## <a name="allow-large-objects"></a><span data-ttu-id="f41e9-486">Autoriser les objets volumineux</span><span class="sxs-lookup"><span data-stu-id="f41e9-486">Allow large objects</span></span>

- <span data-ttu-id="f41e9-487">Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="f41e9-487">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="f41e9-488">Valeur par défaut : GC prend en charge les tableaux supérieurs à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="f41e9-488">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="f41e9-489">Cela équivaut à définir la valeur sur `1` .</span><span class="sxs-lookup"><span data-stu-id="f41e9-489">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="f41e9-490">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="f41e9-490">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="f41e9-491">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-491">Setting name</span></span> | <span data-ttu-id="f41e9-492">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-492">Values</span></span> | <span data-ttu-id="f41e9-493">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-493">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-494">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-494">**runtimeconfig.json**</span></span> | <span data-ttu-id="f41e9-495">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-495">N/A</span></span> | <span data-ttu-id="f41e9-496">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-496">N/A</span></span> | <span data-ttu-id="f41e9-497">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-497">N/A</span></span> |
| <span data-ttu-id="f41e9-498">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-498">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="f41e9-499">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="f41e9-499">`1` - enabled</span></span><br/> <span data-ttu-id="f41e9-500">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="f41e9-500">`0` - disabled</span></span> | <span data-ttu-id="f41e9-501">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-501">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-502">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-502">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-503">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="f41e9-503">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="f41e9-504">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="f41e9-504">`1` - enabled</span></span><br/> <span data-ttu-id="f41e9-505">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="f41e9-505">`0` - disabled</span></span> | <span data-ttu-id="f41e9-506">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="f41e9-506">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="f41e9-507">Seuil du tas des objets volumineux</span><span class="sxs-lookup"><span data-stu-id="f41e9-507">Large object heap threshold</span></span>

- <span data-ttu-id="f41e9-508">Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="f41e9-508">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="f41e9-509">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="f41e9-509">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="f41e9-510">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="f41e9-510">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="f41e9-511">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-511">Setting name</span></span> | <span data-ttu-id="f41e9-512">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-512">Values</span></span> | <span data-ttu-id="f41e9-513">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-513">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-514">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-514">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="f41e9-515">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-515">*decimal value*</span></span> | <span data-ttu-id="f41e9-516">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-516">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-517">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-517">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="f41e9-518">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-518">*hexadecimal value*</span></span> | <span data-ttu-id="f41e9-519">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-519">.NET Core 1.0</span></span> |
| <span data-ttu-id="f41e9-520">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f41e9-520">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f41e9-521">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="f41e9-521">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="f41e9-522">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="f41e9-522">*decimal value*</span></span> | <span data-ttu-id="f41e9-523">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="f41e9-523">.NET Framework 4.8</span></span> |

<span data-ttu-id="f41e9-524">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f41e9-524">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="f41e9-525">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-525">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f41e9-526">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="f41e9-526">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f41e9-527">Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f41e9-527">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="f41e9-528">GC autonome</span><span class="sxs-lookup"><span data-stu-id="f41e9-528">Standalone GC</span></span>

- <span data-ttu-id="f41e9-529">Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.</span><span class="sxs-lookup"><span data-stu-id="f41e9-529">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="f41e9-530">Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="f41e9-530">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="f41e9-531">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="f41e9-531">Setting name</span></span> | <span data-ttu-id="f41e9-532">Valeurs</span><span class="sxs-lookup"><span data-stu-id="f41e9-532">Values</span></span> | <span data-ttu-id="f41e9-533">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f41e9-533">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f41e9-534">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="f41e9-534">**runtimeconfig.json**</span></span> | <span data-ttu-id="f41e9-535">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-535">N/A</span></span> | <span data-ttu-id="f41e9-536">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-536">N/A</span></span> | <span data-ttu-id="f41e9-537">N/A</span><span class="sxs-lookup"><span data-stu-id="f41e9-537">N/A</span></span> |
| <span data-ttu-id="f41e9-538">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="f41e9-538">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="f41e9-539">*string_path*</span><span class="sxs-lookup"><span data-stu-id="f41e9-539">*string_path*</span></span> | <span data-ttu-id="f41e9-540">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f41e9-540">.NET Core 2.0</span></span> |
