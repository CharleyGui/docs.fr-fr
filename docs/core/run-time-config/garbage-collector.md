---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: d7e3d040cd634eeb020beff806c60f834cc02585
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761978"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="c2991-103">Options de configuration au moment de l’exécution pour garbage collection</span><span class="sxs-lookup"><span data-stu-id="c2991-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="c2991-104">Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c2991-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="c2991-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="c2991-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="c2991-106">Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="c2991-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="c2991-107">Les paramètres sont organisés en groupes dans cette page.</span><span class="sxs-lookup"><span data-stu-id="c2991-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="c2991-108">Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="c2991-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="c2991-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.</span><span class="sxs-lookup"><span data-stu-id="c2991-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="c2991-110">Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="c2991-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="c2991-111">Ces paramètres sont omis dans cette page.</span><span class="sxs-lookup"><span data-stu-id="c2991-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="c2991-112">Pour les valeurs numériques, utilisez la notation décimale pour les paramètres dans le fichier *runtimeconfig. JSON* et la notation hexadécimale pour les paramètres de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c2991-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="c2991-113">Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».</span><span class="sxs-lookup"><span data-stu-id="c2991-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="c2991-114">Versions de garbage collection</span><span class="sxs-lookup"><span data-stu-id="c2991-114">Flavors of garbage collection</span></span>

<span data-ttu-id="c2991-115">Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="c2991-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="c2991-116">Pour plus d’informations sur les différences entre les deux, consultez [station de travail et serveur garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="c2991-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="c2991-117">Les sous-versions de garbage collection sont en arrière-plan et non simultanées.</span><span class="sxs-lookup"><span data-stu-id="c2991-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="c2991-118">Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :</span><span class="sxs-lookup"><span data-stu-id="c2991-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="c2991-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="c2991-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="c2991-120">Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="c2991-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="c2991-121">Par défaut : station de travail garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c2991-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="c2991-122">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="c2991-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="c2991-123">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-123">Setting name</span></span> | <span data-ttu-id="c2991-124">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-124">Values</span></span> | <span data-ttu-id="c2991-125">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="c2991-127">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="c2991-127">`false` - workstation</span></span><br/><span data-ttu-id="c2991-128">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="c2991-128">`true` - server</span></span> | <span data-ttu-id="c2991-129">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-130">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="c2991-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="c2991-131">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="c2991-131">`false` - workstation</span></span><br/><span data-ttu-id="c2991-132">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="c2991-132">`true` - server</span></span> | <span data-ttu-id="c2991-133">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-134">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="c2991-135">`0`-station de travail</span><span class="sxs-lookup"><span data-stu-id="c2991-135">`0` - workstation</span></span><br/><span data-ttu-id="c2991-136">`1`-serveur</span><span class="sxs-lookup"><span data-stu-id="c2991-136">`1` - server</span></span> | <span data-ttu-id="c2991-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-138">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="c2991-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="c2991-140">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="c2991-140">`false` - workstation</span></span><br/><span data-ttu-id="c2991-141">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="c2991-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="c2991-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="c2991-142">Examples</span></span>

<span data-ttu-id="c2991-143">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="c2991-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="c2991-144">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c2991-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="c2991-145">System. GC. concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="c2991-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="c2991-146">Configure si l’garbage collection d’arrière-plan (simultanée) est activée.</span><span class="sxs-lookup"><span data-stu-id="c2991-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="c2991-147">Valeur par défaut : utilisez GC d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c2991-147">Default: Use background GC.</span></span> <span data-ttu-id="c2991-148">Cela équivaut à définir la valeur sur `true` .</span><span class="sxs-lookup"><span data-stu-id="c2991-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="c2991-149">Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="c2991-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="c2991-150">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-150">Setting name</span></span> | <span data-ttu-id="c2991-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-151">Values</span></span> | <span data-ttu-id="c2991-152">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="c2991-154">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="c2991-154">`true` - background GC</span></span><br/><span data-ttu-id="c2991-155">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="c2991-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="c2991-156">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-157">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="c2991-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="c2991-158">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="c2991-158">`true` - background GC</span></span><br/><span data-ttu-id="c2991-159">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="c2991-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="c2991-160">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-161">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="c2991-162">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="c2991-162">`true` - background GC</span></span><br/><span data-ttu-id="c2991-163">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="c2991-163">`false` - non-concurrent GC</span></span> | <span data-ttu-id="c2991-164">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-165">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="c2991-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="c2991-167">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="c2991-167">`true` - background GC</span></span><br/><span data-ttu-id="c2991-168">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="c2991-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="c2991-169">Exemples</span><span class="sxs-lookup"><span data-stu-id="c2991-169">Examples</span></span>

<span data-ttu-id="c2991-170">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="c2991-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="c2991-171">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c2991-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="c2991-172">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="c2991-172">Manage resource usage</span></span>

<span data-ttu-id="c2991-173">Utilisez les paramètres décrits dans cette section pour gérer la mémoire et l’utilisation du processeur du garbage collector.</span><span class="sxs-lookup"><span data-stu-id="c2991-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="c2991-174">Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="c2991-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="c2991-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="c2991-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="c2991-176">Limite le nombre de segments de mémoire créés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="c2991-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="c2991-177">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="c2991-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c2991-178">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers `n` processeurs.</span><span class="sxs-lookup"><span data-stu-id="c2991-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="c2991-179">(Utilisez les paramètres [affinité Mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [affinité Ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) pour spécifier exactement les processeurs à affinité.)</span><span class="sxs-lookup"><span data-stu-id="c2991-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="c2991-180">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre limite le nombre de tas gc.</span><span class="sxs-lookup"><span data-stu-id="c2991-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="c2991-181">Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="c2991-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="c2991-182">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-182">Setting name</span></span> | <span data-ttu-id="c2991-183">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-183">Values</span></span> | <span data-ttu-id="c2991-184">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-185">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="c2991-186">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-186">*decimal value*</span></span> | <span data-ttu-id="c2991-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-188">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="c2991-189">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-189">*hexadecimal value*</span></span> | <span data-ttu-id="c2991-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-191">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="c2991-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="c2991-193">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-193">*decimal value*</span></span> | <span data-ttu-id="c2991-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c2991-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="c2991-195">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c2991-195">Example:</span></span>

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
> <span data-ttu-id="c2991-196">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c2991-197">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c2991-198">Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c2991-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="c2991-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="c2991-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="c2991-200">Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.</span><span class="sxs-lookup"><span data-stu-id="c2991-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="c2991-201">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="c2991-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="c2991-202">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="c2991-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c2991-203">La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="c2991-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="c2991-204">Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="c2991-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="c2991-205">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="c2991-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="c2991-206">Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="c2991-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="c2991-207">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-207">Setting name</span></span> | <span data-ttu-id="c2991-208">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-208">Values</span></span> | <span data-ttu-id="c2991-209">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-210">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="c2991-211">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-211">*decimal value*</span></span> | <span data-ttu-id="c2991-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-213">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="c2991-214">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-214">*hexadecimal value*</span></span> | <span data-ttu-id="c2991-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-216">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="c2991-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="c2991-218">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-218">*decimal value*</span></span> | <span data-ttu-id="c2991-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c2991-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="c2991-220">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c2991-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="c2991-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="c2991-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="c2991-222">Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.</span><span class="sxs-lookup"><span data-stu-id="c2991-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="c2991-223">Ce paramètre est similaire à [System. gc. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="c2991-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="c2991-224">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».</span><span class="sxs-lookup"><span data-stu-id="c2991-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="c2991-225">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="c2991-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="c2991-226">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="c2991-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c2991-227">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="c2991-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="c2991-228">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-228">Setting name</span></span> | <span data-ttu-id="c2991-229">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-229">Values</span></span> | <span data-ttu-id="c2991-230">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-231">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="c2991-232">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="c2991-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="c2991-233">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="c2991-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="c2991-234">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="c2991-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="c2991-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-236">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="c2991-237">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="c2991-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="c2991-238">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="c2991-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="c2991-239">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="c2991-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="c2991-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-240">.NET Core 3.0</span></span> |

<span data-ttu-id="c2991-241">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c2991-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="c2991-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="c2991-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="c2991-243">Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .</span><span class="sxs-lookup"><span data-stu-id="c2991-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="c2991-244">Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="c2991-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="c2991-245">Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="c2991-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="c2991-246">S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.</span><span class="sxs-lookup"><span data-stu-id="c2991-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="c2991-247">Valeur par défaut : GC ne s’étend pas au-delà des groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="c2991-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="c2991-248">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="c2991-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="c2991-249">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="c2991-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="c2991-250">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-250">Setting name</span></span> | <span data-ttu-id="c2991-251">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-251">Values</span></span> | <span data-ttu-id="c2991-252">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-253">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="c2991-254">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-254">N/A</span></span> | <span data-ttu-id="c2991-255">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-255">N/A</span></span> | <span data-ttu-id="c2991-256">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-256">N/A</span></span> |
| <span data-ttu-id="c2991-257">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="c2991-258">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="c2991-258">`0` - disabled</span></span><br/><span data-ttu-id="c2991-259">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="c2991-259">`1` - enabled</span></span> | <span data-ttu-id="c2991-260">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-261">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="c2991-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="c2991-263">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="c2991-263">`false` - disabled</span></span><br/><span data-ttu-id="c2991-264">`true`-activé</span><span class="sxs-lookup"><span data-stu-id="c2991-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="c2991-265">Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c2991-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="c2991-266">Pour les applications .NET Core, vous pouvez activer cette option en affectant à la `COMPlus_Thread_UseAllCpuGroups` variable d’environnement la valeur `1` .</span><span class="sxs-lookup"><span data-stu-id="c2991-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="c2991-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="c2991-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="c2991-268">Spécifie s’il faut *affinité* garbage collection threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="c2991-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="c2991-269">La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique.</span><span class="sxs-lookup"><span data-stu-id="c2991-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="c2991-270">Un segment de mémoire est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="c2991-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="c2991-271">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="c2991-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c2991-272">Par défaut : affinité garbage collection les threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="c2991-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="c2991-273">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="c2991-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="c2991-274">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-274">Setting name</span></span> | <span data-ttu-id="c2991-275">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-275">Values</span></span> | <span data-ttu-id="c2991-276">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-277">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="c2991-278">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="c2991-278">`false` - affinitize</span></span><br/><span data-ttu-id="c2991-279">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="c2991-279">`true` - don't affinitize</span></span> | <span data-ttu-id="c2991-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-281">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="c2991-282">`0`-affinité</span><span class="sxs-lookup"><span data-stu-id="c2991-282">`0` - affinitize</span></span><br/><span data-ttu-id="c2991-283">`1`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="c2991-283">`1` - don't affinitize</span></span> | <span data-ttu-id="c2991-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-285">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="c2991-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="c2991-287">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="c2991-287">`false` - affinitize</span></span><br/><span data-ttu-id="c2991-288">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="c2991-288">`true` - don't affinitize</span></span> | <span data-ttu-id="c2991-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c2991-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="c2991-290">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c2991-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="c2991-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="c2991-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="c2991-292">Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.</span><span class="sxs-lookup"><span data-stu-id="c2991-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="c2991-293">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c2991-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="c2991-294">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus grande de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="c2991-294">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="c2991-295">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="c2991-295">The default value applies if:</span></span>

  - <span data-ttu-id="c2991-296">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c2991-296">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="c2991-297">[System. gc. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="c2991-297">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="c2991-298">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-298">Setting name</span></span> | <span data-ttu-id="c2991-299">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-299">Values</span></span> | <span data-ttu-id="c2991-300">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-300">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-301">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-301">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="c2991-302">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-302">*decimal value*</span></span> | <span data-ttu-id="c2991-303">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-303">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-304">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-304">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="c2991-305">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-305">*hexadecimal value*</span></span> | <span data-ttu-id="c2991-306">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-306">.NET Core 3.0</span></span> |

<span data-ttu-id="c2991-307">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c2991-307">Example:</span></span>

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
> <span data-ttu-id="c2991-308">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-308">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c2991-309">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-309">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c2991-310">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c2991-310">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="c2991-311">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="c2991-311">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="c2991-312">Spécifie l’utilisation autorisée du tas GC comme pourcentage de la mémoire physique totale.</span><span class="sxs-lookup"><span data-stu-id="c2991-312">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="c2991-313">Si [System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) est également défini, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="c2991-313">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="c2991-314">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c2991-314">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="c2991-315">Si le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé sous la forme d’un pourcentage de cette limite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="c2991-315">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="c2991-316">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus petite de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="c2991-316">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="c2991-317">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="c2991-317">The default value applies if:</span></span>

  - <span data-ttu-id="c2991-318">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c2991-318">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="c2991-319">[System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="c2991-319">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="c2991-320">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-320">Setting name</span></span> | <span data-ttu-id="c2991-321">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-321">Values</span></span> | <span data-ttu-id="c2991-322">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-323">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="c2991-324">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-324">*decimal value*</span></span> | <span data-ttu-id="c2991-325">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-325">.NET Core 3.0</span></span> |
| <span data-ttu-id="c2991-326">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-326">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="c2991-327">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-327">*hexadecimal value*</span></span> | <span data-ttu-id="c2991-328">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-328">.NET Core 3.0</span></span> |

<span data-ttu-id="c2991-329">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c2991-329">Example:</span></span>

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
> <span data-ttu-id="c2991-330">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-330">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c2991-331">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-331">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c2991-332">Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c2991-332">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="c2991-333">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="c2991-333">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="c2991-334">Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c2991-334">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="c2991-335">Valeur par défaut : relâcher les segments sur le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c2991-335">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="c2991-336">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="c2991-336">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="c2991-337">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-337">Setting name</span></span> | <span data-ttu-id="c2991-338">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-338">Values</span></span> | <span data-ttu-id="c2991-339">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-339">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-340">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-340">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="c2991-341">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c2991-341">`false` - release to OS</span></span><br/><span data-ttu-id="c2991-342">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="c2991-342">`true` - put on standby</span></span> | <span data-ttu-id="c2991-343">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-343">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-344">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="c2991-344">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="c2991-345">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c2991-345">`false` - release to OS</span></span><br/><span data-ttu-id="c2991-346">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="c2991-346">`true` - put on standby</span></span> | <span data-ttu-id="c2991-347">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-347">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-348">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-348">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="c2991-349">`0`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c2991-349">`0` - release to OS</span></span><br/><span data-ttu-id="c2991-350">`1`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="c2991-350">`1` - put on standby</span></span> | <span data-ttu-id="c2991-351">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-351">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="c2991-352">Exemples</span><span class="sxs-lookup"><span data-stu-id="c2991-352">Examples</span></span>

<span data-ttu-id="c2991-353">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="c2991-353">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="c2991-354">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c2991-354">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="c2991-355">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="c2991-355">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="c2991-356">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="c2991-356">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="c2991-357">Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="c2991-357">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="c2991-358">Valeur par défaut : n’utilisez pas de grandes pages lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="c2991-358">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="c2991-359">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="c2991-359">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="c2991-360">Il s’agit d’un paramètre expérimental.</span><span class="sxs-lookup"><span data-stu-id="c2991-360">This is an experimental setting.</span></span>

| | <span data-ttu-id="c2991-361">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-361">Setting name</span></span> | <span data-ttu-id="c2991-362">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-362">Values</span></span> | <span data-ttu-id="c2991-363">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-363">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-364">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-364">**runtimeconfig.json**</span></span> | <span data-ttu-id="c2991-365">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-365">N/A</span></span> | <span data-ttu-id="c2991-366">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-366">N/A</span></span> | <span data-ttu-id="c2991-367">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-367">N/A</span></span> |
| <span data-ttu-id="c2991-368">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-368">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="c2991-369">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="c2991-369">`0` - disabled</span></span><br/><span data-ttu-id="c2991-370">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="c2991-370">`1` - enabled</span></span> | <span data-ttu-id="c2991-371">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2991-371">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="c2991-372">Objets volumineux</span><span class="sxs-lookup"><span data-stu-id="c2991-372">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="c2991-373">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="c2991-373">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="c2991-374">Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="c2991-374">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="c2991-375">Valeur par défaut : GC prend en charge les tableaux supérieurs à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="c2991-375">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="c2991-376">Cela équivaut à définir la valeur sur `1` .</span><span class="sxs-lookup"><span data-stu-id="c2991-376">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="c2991-377">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="c2991-377">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="c2991-378">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-378">Setting name</span></span> | <span data-ttu-id="c2991-379">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-379">Values</span></span> | <span data-ttu-id="c2991-380">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-380">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-381">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-381">**runtimeconfig.json**</span></span> | <span data-ttu-id="c2991-382">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-382">N/A</span></span> | <span data-ttu-id="c2991-383">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-383">N/A</span></span> | <span data-ttu-id="c2991-384">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-384">N/A</span></span> |
| <span data-ttu-id="c2991-385">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-385">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="c2991-386">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="c2991-386">`1` - enabled</span></span><br/> <span data-ttu-id="c2991-387">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="c2991-387">`0` - disabled</span></span> | <span data-ttu-id="c2991-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-389">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-390">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="c2991-390">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="c2991-391">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="c2991-391">`1` - enabled</span></span><br/> <span data-ttu-id="c2991-392">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="c2991-392">`0` - disabled</span></span> | <span data-ttu-id="c2991-393">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c2991-393">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="c2991-394">Seuil du tas des objets volumineux</span><span class="sxs-lookup"><span data-stu-id="c2991-394">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="c2991-395">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="c2991-395">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="c2991-396">Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="c2991-396">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="c2991-397">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="c2991-397">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="c2991-398">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="c2991-398">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="c2991-399">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-399">Setting name</span></span> | <span data-ttu-id="c2991-400">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-400">Values</span></span> | <span data-ttu-id="c2991-401">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-401">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-402">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-402">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="c2991-403">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-403">*decimal value*</span></span> | <span data-ttu-id="c2991-404">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-404">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-405">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-405">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="c2991-406">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-406">*hexadecimal value*</span></span> | <span data-ttu-id="c2991-407">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2991-407">.NET Core 1.0</span></span> |
| <span data-ttu-id="c2991-408">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c2991-408">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c2991-409">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="c2991-409">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="c2991-410">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="c2991-410">*decimal value*</span></span> | <span data-ttu-id="c2991-411">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="c2991-411">.NET Framework 4.8</span></span> |

<span data-ttu-id="c2991-412">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c2991-412">Example:</span></span>

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
> <span data-ttu-id="c2991-413">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-413">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c2991-414">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="c2991-414">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c2991-415">Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c2991-415">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="c2991-416">GC autonome</span><span class="sxs-lookup"><span data-stu-id="c2991-416">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="c2991-417">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="c2991-417">COMPlus_GCName</span></span>

- <span data-ttu-id="c2991-418">Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.</span><span class="sxs-lookup"><span data-stu-id="c2991-418">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="c2991-419">Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="c2991-419">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="c2991-420">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c2991-420">Setting name</span></span> | <span data-ttu-id="c2991-421">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c2991-421">Values</span></span> | <span data-ttu-id="c2991-422">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2991-422">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c2991-423">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c2991-423">**runtimeconfig.json**</span></span> | <span data-ttu-id="c2991-424">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-424">N/A</span></span> | <span data-ttu-id="c2991-425">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-425">N/A</span></span> | <span data-ttu-id="c2991-426">N/A</span><span class="sxs-lookup"><span data-stu-id="c2991-426">N/A</span></span> |
| <span data-ttu-id="c2991-427">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="c2991-427">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="c2991-428">*string_path*</span><span class="sxs-lookup"><span data-stu-id="c2991-428">*string_path*</span></span> | <span data-ttu-id="c2991-429">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c2991-429">.NET Core 2.0</span></span> |
