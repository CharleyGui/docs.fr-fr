---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 6ae5b7447fb0df4978ea9dcaa5e76fcc7a6cc4ca
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441403"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="783d6-103">Options de configuration au moment de l’exécution pour garbage collection</span><span class="sxs-lookup"><span data-stu-id="783d6-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="783d6-104">Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="783d6-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="783d6-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="783d6-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="783d6-106">Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="783d6-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="783d6-107">Les paramètres sont organisés en groupes dans cette page.</span><span class="sxs-lookup"><span data-stu-id="783d6-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="783d6-108">Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="783d6-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="783d6-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.</span><span class="sxs-lookup"><span data-stu-id="783d6-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="783d6-110">Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="783d6-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="783d6-111">Ces paramètres sont omis dans cette page.</span><span class="sxs-lookup"><span data-stu-id="783d6-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="783d6-112">Pour les valeurs numériques, utilisez la notation décimale pour les paramètres de la *runtimeconfig.jssur* fichier et notation hexadécimale pour les paramètres de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="783d6-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="783d6-113">Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».</span><span class="sxs-lookup"><span data-stu-id="783d6-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="783d6-114">Versions de garbage collection</span><span class="sxs-lookup"><span data-stu-id="783d6-114">Flavors of garbage collection</span></span>

<span data-ttu-id="783d6-115">Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="783d6-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="783d6-116">Pour plus d’informations sur les différences entre les deux, consultez [station de travail et serveur garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="783d6-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="783d6-117">Les sous-versions de garbage collection sont en arrière-plan et non simultanées.</span><span class="sxs-lookup"><span data-stu-id="783d6-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="783d6-118">Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :</span><span class="sxs-lookup"><span data-stu-id="783d6-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="783d6-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="783d6-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="783d6-120">Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="783d6-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="783d6-121">Par défaut : station de travail garbage collection.</span><span class="sxs-lookup"><span data-stu-id="783d6-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="783d6-122">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="783d6-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="783d6-123">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-123">Setting name</span></span> | <span data-ttu-id="783d6-124">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-124">Values</span></span> | <span data-ttu-id="783d6-125">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-126">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="783d6-127">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="783d6-127">`false` - workstation</span></span><br/><span data-ttu-id="783d6-128">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="783d6-128">`true` - server</span></span> | <span data-ttu-id="783d6-129">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-130">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="783d6-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="783d6-131">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="783d6-131">`false` - workstation</span></span><br/><span data-ttu-id="783d6-132">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="783d6-132">`true` - server</span></span> | <span data-ttu-id="783d6-133">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-134">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="783d6-135">`0`-station de travail</span><span class="sxs-lookup"><span data-stu-id="783d6-135">`0` - workstation</span></span><br/><span data-ttu-id="783d6-136">`1`-serveur</span><span class="sxs-lookup"><span data-stu-id="783d6-136">`1` - server</span></span> | <span data-ttu-id="783d6-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-138">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="783d6-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="783d6-140">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="783d6-140">`false` - workstation</span></span><br/><span data-ttu-id="783d6-141">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="783d6-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="783d6-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="783d6-142">Examples</span></span>

<span data-ttu-id="783d6-143">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="783d6-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="783d6-144">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="783d6-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="783d6-145">System. GC. concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="783d6-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="783d6-146">Configure si l’garbage collection d’arrière-plan (simultanée) est activée.</span><span class="sxs-lookup"><span data-stu-id="783d6-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="783d6-147">Valeur par défaut : utilisez GC d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="783d6-147">Default: Use background GC.</span></span> <span data-ttu-id="783d6-148">Cela équivaut à définir la valeur sur `true` .</span><span class="sxs-lookup"><span data-stu-id="783d6-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="783d6-149">Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="783d6-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="783d6-150">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-150">Setting name</span></span> | <span data-ttu-id="783d6-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-151">Values</span></span> | <span data-ttu-id="783d6-152">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-153">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="783d6-154">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="783d6-154">`true` - background GC</span></span><br/><span data-ttu-id="783d6-155">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="783d6-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="783d6-156">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-157">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="783d6-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="783d6-158">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="783d6-158">`true` - background GC</span></span><br/><span data-ttu-id="783d6-159">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="783d6-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="783d6-160">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-161">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="783d6-162">`1`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="783d6-162">`1` - background GC</span></span><br/><span data-ttu-id="783d6-163">`0`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="783d6-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="783d6-164">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-165">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="783d6-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="783d6-167">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="783d6-167">`true` - background GC</span></span><br/><span data-ttu-id="783d6-168">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="783d6-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="783d6-169">Exemples</span><span class="sxs-lookup"><span data-stu-id="783d6-169">Examples</span></span>

<span data-ttu-id="783d6-170">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="783d6-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="783d6-171">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="783d6-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="783d6-172">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="783d6-172">Manage resource usage</span></span>

<span data-ttu-id="783d6-173">Utilisez les paramètres décrits dans cette section pour gérer la mémoire et l’utilisation du processeur du garbage collector.</span><span class="sxs-lookup"><span data-stu-id="783d6-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="783d6-174">Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="783d6-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="783d6-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="783d6-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="783d6-176">Limite le nombre de segments de mémoire créés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="783d6-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="783d6-177">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="783d6-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="783d6-178">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers `n` processeurs.</span><span class="sxs-lookup"><span data-stu-id="783d6-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="783d6-179">(Utilisez les paramètres [affinité Mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [affinité Ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) pour spécifier exactement les processeurs à affinité.)</span><span class="sxs-lookup"><span data-stu-id="783d6-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="783d6-180">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre limite le nombre de tas gc.</span><span class="sxs-lookup"><span data-stu-id="783d6-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="783d6-181">Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="783d6-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="783d6-182">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-182">Setting name</span></span> | <span data-ttu-id="783d6-183">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-183">Values</span></span> | <span data-ttu-id="783d6-184">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-185">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="783d6-186">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-186">*decimal value*</span></span> | <span data-ttu-id="783d6-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-188">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="783d6-189">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-189">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-191">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="783d6-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="783d6-193">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-193">*decimal value*</span></span> | <span data-ttu-id="783d6-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="783d6-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="783d6-195">Exemple :</span><span class="sxs-lookup"><span data-stu-id="783d6-195">Example:</span></span>

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
> <span data-ttu-id="783d6-196">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="783d6-197">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="783d6-198">Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="783d6-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="783d6-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="783d6-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="783d6-200">Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.</span><span class="sxs-lookup"><span data-stu-id="783d6-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="783d6-201">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="783d6-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="783d6-202">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="783d6-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="783d6-203">La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="783d6-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="783d6-204">Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="783d6-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="783d6-205">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="783d6-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="783d6-206">Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="783d6-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="783d6-207">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-207">Setting name</span></span> | <span data-ttu-id="783d6-208">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-208">Values</span></span> | <span data-ttu-id="783d6-209">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-210">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="783d6-211">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-211">*decimal value*</span></span> | <span data-ttu-id="783d6-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-213">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="783d6-214">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-214">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-216">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="783d6-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="783d6-218">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-218">*decimal value*</span></span> | <span data-ttu-id="783d6-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="783d6-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="783d6-220">Exemple :</span><span class="sxs-lookup"><span data-stu-id="783d6-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="783d6-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="783d6-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="783d6-222">Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.</span><span class="sxs-lookup"><span data-stu-id="783d6-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="783d6-223">Ce paramètre est similaire à [System. gc. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="783d6-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="783d6-224">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».</span><span class="sxs-lookup"><span data-stu-id="783d6-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="783d6-225">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="783d6-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="783d6-226">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="783d6-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="783d6-227">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="783d6-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="783d6-228">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-228">Setting name</span></span> | <span data-ttu-id="783d6-229">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-229">Values</span></span> | <span data-ttu-id="783d6-230">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-231">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="783d6-232">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="783d6-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="783d6-233">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="783d6-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="783d6-234">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="783d6-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="783d6-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-236">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="783d6-237">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="783d6-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="783d6-238">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="783d6-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="783d6-239">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="783d6-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="783d6-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-240">.NET Core 3.0</span></span> |

<span data-ttu-id="783d6-241">Exemple :</span><span class="sxs-lookup"><span data-stu-id="783d6-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="783d6-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="783d6-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="783d6-243">Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .</span><span class="sxs-lookup"><span data-stu-id="783d6-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="783d6-244">Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="783d6-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="783d6-245">Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="783d6-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="783d6-246">S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.</span><span class="sxs-lookup"><span data-stu-id="783d6-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="783d6-247">Valeur par défaut : GC ne s’étend pas au-delà des groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="783d6-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="783d6-248">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="783d6-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="783d6-249">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="783d6-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="783d6-250">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-250">Setting name</span></span> | <span data-ttu-id="783d6-251">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-251">Values</span></span> | <span data-ttu-id="783d6-252">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-253">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="783d6-254">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-254">N/A</span></span> | <span data-ttu-id="783d6-255">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-255">N/A</span></span> | <span data-ttu-id="783d6-256">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-256">N/A</span></span> |
| <span data-ttu-id="783d6-257">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="783d6-258">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="783d6-258">`0` - disabled</span></span><br/><span data-ttu-id="783d6-259">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="783d6-259">`1` - enabled</span></span> | <span data-ttu-id="783d6-260">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-261">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="783d6-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="783d6-263">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="783d6-263">`false` - disabled</span></span><br/><span data-ttu-id="783d6-264">`true`-activé</span><span class="sxs-lookup"><span data-stu-id="783d6-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="783d6-265">Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="783d6-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="783d6-266">Pour les applications .NET Core, vous pouvez activer cette option en affectant à la `COMPlus_Thread_UseAllCpuGroups` variable d’environnement la valeur `1` .</span><span class="sxs-lookup"><span data-stu-id="783d6-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="783d6-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="783d6-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="783d6-268">Spécifie s’il faut *affinité* garbage collection threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="783d6-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="783d6-269">La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique.</span><span class="sxs-lookup"><span data-stu-id="783d6-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="783d6-270">Un segment de mémoire est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="783d6-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="783d6-271">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="783d6-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="783d6-272">Par défaut : affinité garbage collection les threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="783d6-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="783d6-273">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="783d6-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="783d6-274">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-274">Setting name</span></span> | <span data-ttu-id="783d6-275">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-275">Values</span></span> | <span data-ttu-id="783d6-276">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-277">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="783d6-278">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="783d6-278">`false` - affinitize</span></span><br/><span data-ttu-id="783d6-279">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="783d6-279">`true` - don't affinitize</span></span> | <span data-ttu-id="783d6-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-281">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="783d6-282">`0`-affinité</span><span class="sxs-lookup"><span data-stu-id="783d6-282">`0` - affinitize</span></span><br/><span data-ttu-id="783d6-283">`1`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="783d6-283">`1` - don't affinitize</span></span> | <span data-ttu-id="783d6-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-285">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="783d6-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="783d6-287">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="783d6-287">`false` - affinitize</span></span><br/><span data-ttu-id="783d6-288">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="783d6-288">`true` - don't affinitize</span></span> | <span data-ttu-id="783d6-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="783d6-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="783d6-290">Exemple :</span><span class="sxs-lookup"><span data-stu-id="783d6-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="783d6-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="783d6-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="783d6-292">Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.</span><span class="sxs-lookup"><span data-stu-id="783d6-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="783d6-293">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="783d6-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="783d6-294">Ce paramètre est ignoré si les [limites par objet/tas](#per-object-heap-limits) sont configurées.</span><span class="sxs-lookup"><span data-stu-id="783d6-294">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="783d6-295">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus grande de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="783d6-295">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="783d6-296">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="783d6-296">The default value applies if:</span></span>

  - <span data-ttu-id="783d6-297">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="783d6-297">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="783d6-298">[System. gc. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="783d6-298">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="783d6-299">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-299">Setting name</span></span> | <span data-ttu-id="783d6-300">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-300">Values</span></span> | <span data-ttu-id="783d6-301">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-301">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-302">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-302">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="783d6-303">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-303">*decimal value*</span></span> | <span data-ttu-id="783d6-304">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-304">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-305">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-305">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="783d6-306">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-306">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-307">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-307">.NET Core 3.0</span></span> |

<span data-ttu-id="783d6-308">Exemple :</span><span class="sxs-lookup"><span data-stu-id="783d6-308">Example:</span></span>

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
> <span data-ttu-id="783d6-309">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-309">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="783d6-310">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-310">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="783d6-311">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="783d6-311">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="783d6-312">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="783d6-312">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="783d6-313">Spécifie l’utilisation autorisée du tas GC comme pourcentage de la mémoire physique totale.</span><span class="sxs-lookup"><span data-stu-id="783d6-313">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="783d6-314">Si [System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) est également défini, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="783d6-314">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="783d6-315">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="783d6-315">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="783d6-316">Si le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé sous la forme d’un pourcentage de cette limite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="783d6-316">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="783d6-317">Ce paramètre est ignoré si les [limites par objet/tas](#per-object-heap-limits) sont configurées.</span><span class="sxs-lookup"><span data-stu-id="783d6-317">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="783d6-318">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus petite de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="783d6-318">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="783d6-319">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="783d6-319">The default value applies if:</span></span>

  - <span data-ttu-id="783d6-320">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="783d6-320">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="783d6-321">[System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="783d6-321">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="783d6-322">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-322">Setting name</span></span> | <span data-ttu-id="783d6-323">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-323">Values</span></span> | <span data-ttu-id="783d6-324">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-324">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-325">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-325">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="783d6-326">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-326">*decimal value*</span></span> | <span data-ttu-id="783d6-327">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-327">.NET Core 3.0</span></span> |
| <span data-ttu-id="783d6-328">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-328">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="783d6-329">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-329">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-330">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-330">.NET Core 3.0</span></span> |

<span data-ttu-id="783d6-331">Exemple :</span><span class="sxs-lookup"><span data-stu-id="783d6-331">Example:</span></span>

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
> <span data-ttu-id="783d6-332">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-332">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="783d6-333">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-333">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="783d6-334">Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="783d6-334">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="783d6-335">Limites par objet-tas</span><span class="sxs-lookup"><span data-stu-id="783d6-335">Per-object-heap limits</span></span>

<span data-ttu-id="783d6-336">Vous pouvez spécifier l’utilisation autorisée du tas du GC pour chaque segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="783d6-336">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="783d6-337">Les différents tas sont le tas d’objets volumineux (LOH), le tas de petits objets (SOH) et le tas d’objets épinglés (POH).</span><span class="sxs-lookup"><span data-stu-id="783d6-337">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

#### <a name="complus_gcheaphardlimitsoh-complus_gcheaphardlimitloh-complus_gcheaphardlimitpoh"></a><span data-ttu-id="783d6-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH COMPLUS_GCHeapHardLimitPOH</span><span class="sxs-lookup"><span data-stu-id="783d6-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span></span>

- <span data-ttu-id="783d6-339">Si vous spécifiez une valeur pour l’un `COMPLUS_GCHeapHardLimitSOH` des `COMPLUS_GCHeapHardLimitLOH` paramètres, ou `COMPLUS_GCHeapHardLimitPOH` , vous devez également spécifier une valeur pour `COMPLUS_GCHeapHardLimitSOH` et `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="783d6-339">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="783d6-340">Si ce n’est pas le cas, l’initialisation du runtime échoue.</span><span class="sxs-lookup"><span data-stu-id="783d6-340">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="783d6-341">La valeur par défaut pour `COMPLUS_GCHeapHardLimitPOH` est 0.</span><span class="sxs-lookup"><span data-stu-id="783d6-341">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="783d6-342">`COMPLUS_GCHeapHardLimitSOH`et `COMPLUS_GCHeapHardLimitLOH` n’ont pas de valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="783d6-342">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="783d6-343">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-343">Setting name</span></span> | <span data-ttu-id="783d6-344">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-344">Values</span></span> | <span data-ttu-id="783d6-345">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-346">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-346">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="783d6-347">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-347">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-348">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="783d6-348">.NET 5.0</span></span> |
| <span data-ttu-id="783d6-349">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-349">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="783d6-350">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-350">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-351">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="783d6-351">.NET 5.0</span></span> |
| <span data-ttu-id="783d6-352">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-352">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="783d6-353">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-353">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-354">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="783d6-354">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="783d6-355">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-355">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="783d6-356">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), la valeur est 0xC800000 ou C800000.</span><span class="sxs-lookup"><span data-stu-id="783d6-356">For example, to specify a heap hard limit of 200 mebibytes (MiB), the value would be 0xC800000 or C800000.</span></span>

#### <a name="complus_gcheaphardlimitsohpercent-complus_gcheaphardlimitlohpercent-complus_gcheaphardlimitpohpercent"></a><span data-ttu-id="783d6-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent COMPLUS_GCHeapHardLimitPOHPercent</span><span class="sxs-lookup"><span data-stu-id="783d6-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span></span>

- <span data-ttu-id="783d6-358">Si vous spécifiez une valeur pour l’un `COMPLUS_GCHeapHardLimitSOHPercent` des `COMPLUS_GCHeapHardLimitLOHPercent` paramètres, ou `COMPLUS_GCHeapHardLimitPOHPercent` , vous devez également spécifier une valeur pour `COMPLUS_GCHeapHardLimitSOHPercent` et `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="783d6-358">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="783d6-359">Si ce n’est pas le cas, l’initialisation du runtime échoue.</span><span class="sxs-lookup"><span data-stu-id="783d6-359">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="783d6-360">Ces paramètres sont ignorés si `COMPLUS_GCHeapHardLimitSOH` , `COMPLUS_GCHeapHardLimitLOH` et `COMPLUS_GCHeapHardLimitPOH` sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="783d6-360">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="783d6-361">La valeur 1 signifie que GC utilise 1% de la mémoire physique totale pour ce tas d’objets.</span><span class="sxs-lookup"><span data-stu-id="783d6-361">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="783d6-362">Chaque valeur doit être supérieure à zéro et inférieure à 100.</span><span class="sxs-lookup"><span data-stu-id="783d6-362">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="783d6-363">En outre, la somme des trois valeurs de pourcentage doit être inférieure à 100.</span><span class="sxs-lookup"><span data-stu-id="783d6-363">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="783d6-364">Dans le cas contraire, le runtime ne pourra pas s’initialiser.</span><span class="sxs-lookup"><span data-stu-id="783d6-364">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="783d6-365">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-365">Setting name</span></span> | <span data-ttu-id="783d6-366">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-366">Values</span></span> | <span data-ttu-id="783d6-367">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-367">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-368">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-368">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="783d6-369">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-369">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-370">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="783d6-370">.NET 5.0</span></span> |
| <span data-ttu-id="783d6-371">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-371">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="783d6-372">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-372">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-373">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="783d6-373">.NET 5.0</span></span> |
| <span data-ttu-id="783d6-374">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-374">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="783d6-375">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-375">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-376">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="783d6-376">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="783d6-377">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="783d6-378">Par exemple, pour limiter l’utilisation du tas à 30%, la valeur est 0x1E ou 1E.</span><span class="sxs-lookup"><span data-stu-id="783d6-378">For example, to limit the heap usage to 30%, the value would be 0x1E or 1E.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="783d6-379">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="783d6-379">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="783d6-380">Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="783d6-380">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="783d6-381">Valeur par défaut : relâcher les segments sur le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="783d6-381">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="783d6-382">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="783d6-382">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="783d6-383">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-383">Setting name</span></span> | <span data-ttu-id="783d6-384">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-384">Values</span></span> | <span data-ttu-id="783d6-385">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-386">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-386">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="783d6-387">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="783d6-387">`false` - release to OS</span></span><br/><span data-ttu-id="783d6-388">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="783d6-388">`true` - put on standby</span></span> | <span data-ttu-id="783d6-389">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-389">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-390">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="783d6-390">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="783d6-391">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="783d6-391">`false` - release to OS</span></span><br/><span data-ttu-id="783d6-392">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="783d6-392">`true` - put on standby</span></span> | <span data-ttu-id="783d6-393">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-393">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-394">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-394">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="783d6-395">`0`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="783d6-395">`0` - release to OS</span></span><br/><span data-ttu-id="783d6-396">`1`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="783d6-396">`1` - put on standby</span></span> | <span data-ttu-id="783d6-397">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-397">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="783d6-398">Exemples</span><span class="sxs-lookup"><span data-stu-id="783d6-398">Examples</span></span>

<span data-ttu-id="783d6-399">*runtimeconfig.jssur le* fichier :</span><span class="sxs-lookup"><span data-stu-id="783d6-399">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="783d6-400">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="783d6-400">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="783d6-401">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="783d6-401">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="783d6-402">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="783d6-402">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="783d6-403">Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="783d6-403">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="783d6-404">Valeur par défaut : n’utilisez pas de grandes pages lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="783d6-404">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="783d6-405">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="783d6-405">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="783d6-406">Il s’agit d’un paramètre expérimental.</span><span class="sxs-lookup"><span data-stu-id="783d6-406">This is an experimental setting.</span></span>

| | <span data-ttu-id="783d6-407">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-407">Setting name</span></span> | <span data-ttu-id="783d6-408">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-408">Values</span></span> | <span data-ttu-id="783d6-409">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-409">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-410">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-410">**runtimeconfig.json**</span></span> | <span data-ttu-id="783d6-411">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-411">N/A</span></span> | <span data-ttu-id="783d6-412">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-412">N/A</span></span> | <span data-ttu-id="783d6-413">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-413">N/A</span></span> |
| <span data-ttu-id="783d6-414">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-414">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="783d6-415">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="783d6-415">`0` - disabled</span></span><br/><span data-ttu-id="783d6-416">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="783d6-416">`1` - enabled</span></span> | <span data-ttu-id="783d6-417">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="783d6-417">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="783d6-418">Objets volumineux</span><span class="sxs-lookup"><span data-stu-id="783d6-418">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="783d6-419">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="783d6-419">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="783d6-420">Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="783d6-420">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="783d6-421">Valeur par défaut : GC prend en charge les tableaux supérieurs à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="783d6-421">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="783d6-422">Cela équivaut à définir la valeur sur `1` .</span><span class="sxs-lookup"><span data-stu-id="783d6-422">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="783d6-423">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="783d6-423">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="783d6-424">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-424">Setting name</span></span> | <span data-ttu-id="783d6-425">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-425">Values</span></span> | <span data-ttu-id="783d6-426">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-426">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-427">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-427">**runtimeconfig.json**</span></span> | <span data-ttu-id="783d6-428">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-428">N/A</span></span> | <span data-ttu-id="783d6-429">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-429">N/A</span></span> | <span data-ttu-id="783d6-430">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-430">N/A</span></span> |
| <span data-ttu-id="783d6-431">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-431">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="783d6-432">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="783d6-432">`1` - enabled</span></span><br/> <span data-ttu-id="783d6-433">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="783d6-433">`0` - disabled</span></span> | <span data-ttu-id="783d6-434">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-434">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-435">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-435">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-436">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="783d6-436">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="783d6-437">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="783d6-437">`1` - enabled</span></span><br/> <span data-ttu-id="783d6-438">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="783d6-438">`0` - disabled</span></span> | <span data-ttu-id="783d6-439">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="783d6-439">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="783d6-440">Seuil du tas des objets volumineux</span><span class="sxs-lookup"><span data-stu-id="783d6-440">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="783d6-441">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="783d6-441">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="783d6-442">Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="783d6-442">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="783d6-443">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="783d6-443">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="783d6-444">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="783d6-444">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="783d6-445">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-445">Setting name</span></span> | <span data-ttu-id="783d6-446">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-446">Values</span></span> | <span data-ttu-id="783d6-447">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-447">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-448">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-448">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="783d6-449">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-449">*decimal value*</span></span> | <span data-ttu-id="783d6-450">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-450">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-451">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-451">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="783d6-452">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-452">*hexadecimal value*</span></span> | <span data-ttu-id="783d6-453">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="783d6-453">.NET Core 1.0</span></span> |
| <span data-ttu-id="783d6-454">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="783d6-454">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="783d6-455">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="783d6-455">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="783d6-456">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="783d6-456">*decimal value*</span></span> | <span data-ttu-id="783d6-457">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="783d6-457">.NET Framework 4.8</span></span> |

<span data-ttu-id="783d6-458">Exemple :</span><span class="sxs-lookup"><span data-stu-id="783d6-458">Example:</span></span>

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
> <span data-ttu-id="783d6-459">Si vous définissez l’option dans *runtimeconfig.js*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-459">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="783d6-460">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="783d6-460">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="783d6-461">Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="783d6-461">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="783d6-462">GC autonome</span><span class="sxs-lookup"><span data-stu-id="783d6-462">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="783d6-463">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="783d6-463">COMPlus_GCName</span></span>

- <span data-ttu-id="783d6-464">Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.</span><span class="sxs-lookup"><span data-stu-id="783d6-464">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="783d6-465">Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="783d6-465">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="783d6-466">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="783d6-466">Setting name</span></span> | <span data-ttu-id="783d6-467">Valeurs</span><span class="sxs-lookup"><span data-stu-id="783d6-467">Values</span></span> | <span data-ttu-id="783d6-468">Version introduite</span><span class="sxs-lookup"><span data-stu-id="783d6-468">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="783d6-469">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="783d6-469">**runtimeconfig.json**</span></span> | <span data-ttu-id="783d6-470">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-470">N/A</span></span> | <span data-ttu-id="783d6-471">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-471">N/A</span></span> | <span data-ttu-id="783d6-472">N/A</span><span class="sxs-lookup"><span data-stu-id="783d6-472">N/A</span></span> |
| <span data-ttu-id="783d6-473">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="783d6-473">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="783d6-474">*string_path*</span><span class="sxs-lookup"><span data-stu-id="783d6-474">*string_path*</span></span> | <span data-ttu-id="783d6-475">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="783d6-475">.NET Core 2.0</span></span> |
