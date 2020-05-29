---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 0ce2f70204463c1525ef7d29de21ddf5384d0238
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202097"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="25545-103">Options de configuration au moment de l’exécution pour garbage collection</span><span class="sxs-lookup"><span data-stu-id="25545-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="25545-104">Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="25545-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="25545-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="25545-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="25545-106">Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="25545-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="25545-107">Les paramètres sont organisés en groupes dans cette page.</span><span class="sxs-lookup"><span data-stu-id="25545-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="25545-108">Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="25545-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="25545-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.</span><span class="sxs-lookup"><span data-stu-id="25545-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="25545-110">Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="25545-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="25545-111">Ces paramètres sont omis dans cette page.</span><span class="sxs-lookup"><span data-stu-id="25545-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="25545-112">Pour les valeurs numériques, utilisez la notation décimale pour les paramètres dans le fichier *runtimeconfig. JSON* et la notation hexadécimale pour les paramètres de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="25545-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="25545-113">Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».</span><span class="sxs-lookup"><span data-stu-id="25545-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="25545-114">Versions de garbage collection</span><span class="sxs-lookup"><span data-stu-id="25545-114">Flavors of garbage collection</span></span>

<span data-ttu-id="25545-115">Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="25545-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="25545-116">Pour plus d’informations sur les différences entre les deux, consultez [station de travail et serveur garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="25545-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="25545-117">Les sous-versions de garbage collection sont en arrière-plan et non simultanées.</span><span class="sxs-lookup"><span data-stu-id="25545-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="25545-118">Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :</span><span class="sxs-lookup"><span data-stu-id="25545-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="25545-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="25545-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="25545-120">Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="25545-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="25545-121">Par défaut : station de travail garbage collection.</span><span class="sxs-lookup"><span data-stu-id="25545-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="25545-122">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="25545-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="25545-123">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-123">Setting name</span></span> | <span data-ttu-id="25545-124">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-124">Values</span></span> | <span data-ttu-id="25545-125">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="25545-127">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="25545-127">`false` - workstation</span></span><br/><span data-ttu-id="25545-128">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="25545-128">`true` - server</span></span> | <span data-ttu-id="25545-129">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-130">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="25545-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="25545-131">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="25545-131">`false` - workstation</span></span><br/><span data-ttu-id="25545-132">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="25545-132">`true` - server</span></span> | <span data-ttu-id="25545-133">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-134">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="25545-135">`0`-station de travail</span><span class="sxs-lookup"><span data-stu-id="25545-135">`0` - workstation</span></span><br/><span data-ttu-id="25545-136">`1`-serveur</span><span class="sxs-lookup"><span data-stu-id="25545-136">`1` - server</span></span> | <span data-ttu-id="25545-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-138">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="25545-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="25545-140">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="25545-140">`false` - workstation</span></span><br/><span data-ttu-id="25545-141">`true`-serveur</span><span class="sxs-lookup"><span data-stu-id="25545-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="25545-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="25545-142">Examples</span></span>

<span data-ttu-id="25545-143">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="25545-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="25545-144">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="25545-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="25545-145">System. GC. concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="25545-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="25545-146">Configure si l’garbage collection d’arrière-plan (simultanée) est activée.</span><span class="sxs-lookup"><span data-stu-id="25545-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="25545-147">Valeur par défaut : utilisez GC d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="25545-147">Default: Use background GC.</span></span> <span data-ttu-id="25545-148">Cela équivaut à définir la valeur sur `true` .</span><span class="sxs-lookup"><span data-stu-id="25545-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="25545-149">Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="25545-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="25545-150">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-150">Setting name</span></span> | <span data-ttu-id="25545-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-151">Values</span></span> | <span data-ttu-id="25545-152">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="25545-154">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="25545-154">`true` - background GC</span></span><br/><span data-ttu-id="25545-155">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="25545-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="25545-156">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-157">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="25545-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="25545-158">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="25545-158">`true` - background GC</span></span><br/><span data-ttu-id="25545-159">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="25545-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="25545-160">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-161">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="25545-162">`1`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="25545-162">`1` - background GC</span></span><br/><span data-ttu-id="25545-163">`0`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="25545-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="25545-164">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-165">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="25545-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="25545-167">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="25545-167">`true` - background GC</span></span><br/><span data-ttu-id="25545-168">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="25545-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="25545-169">Exemples</span><span class="sxs-lookup"><span data-stu-id="25545-169">Examples</span></span>

<span data-ttu-id="25545-170">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="25545-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="25545-171">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="25545-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="25545-172">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="25545-172">Manage resource usage</span></span>

<span data-ttu-id="25545-173">Utilisez les paramètres décrits dans cette section pour gérer la mémoire et l’utilisation du processeur du garbage collector.</span><span class="sxs-lookup"><span data-stu-id="25545-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="25545-174">Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="25545-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="25545-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="25545-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="25545-176">Limite le nombre de segments de mémoire créés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="25545-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="25545-177">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="25545-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="25545-178">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers `n` processeurs.</span><span class="sxs-lookup"><span data-stu-id="25545-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="25545-179">(Utilisez les paramètres [affinité Mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [affinité Ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) pour spécifier exactement les processeurs à affinité.)</span><span class="sxs-lookup"><span data-stu-id="25545-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="25545-180">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre limite le nombre de tas gc.</span><span class="sxs-lookup"><span data-stu-id="25545-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="25545-181">Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="25545-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="25545-182">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-182">Setting name</span></span> | <span data-ttu-id="25545-183">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-183">Values</span></span> | <span data-ttu-id="25545-184">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-185">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="25545-186">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-186">*decimal value*</span></span> | <span data-ttu-id="25545-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-188">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="25545-189">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="25545-189">*hexadecimal value*</span></span> | <span data-ttu-id="25545-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-191">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="25545-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="25545-193">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-193">*decimal value*</span></span> | <span data-ttu-id="25545-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="25545-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="25545-195">Exemple :</span><span class="sxs-lookup"><span data-stu-id="25545-195">Example:</span></span>

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
> <span data-ttu-id="25545-196">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="25545-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="25545-197">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="25545-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="25545-198">Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="25545-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="25545-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="25545-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="25545-200">Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.</span><span class="sxs-lookup"><span data-stu-id="25545-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="25545-201">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="25545-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="25545-202">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="25545-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="25545-203">La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="25545-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="25545-204">Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="25545-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="25545-205">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="25545-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="25545-206">Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="25545-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="25545-207">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-207">Setting name</span></span> | <span data-ttu-id="25545-208">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-208">Values</span></span> | <span data-ttu-id="25545-209">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-210">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="25545-211">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-211">*decimal value*</span></span> | <span data-ttu-id="25545-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-213">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="25545-214">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="25545-214">*hexadecimal value*</span></span> | <span data-ttu-id="25545-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-216">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="25545-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="25545-218">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-218">*decimal value*</span></span> | <span data-ttu-id="25545-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="25545-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="25545-220">Exemple :</span><span class="sxs-lookup"><span data-stu-id="25545-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="25545-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="25545-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="25545-222">Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.</span><span class="sxs-lookup"><span data-stu-id="25545-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="25545-223">Ce paramètre est similaire à [System. gc. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="25545-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="25545-224">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».</span><span class="sxs-lookup"><span data-stu-id="25545-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="25545-225">Si l' [affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="25545-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="25545-226">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="25545-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="25545-227">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="25545-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="25545-228">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-228">Setting name</span></span> | <span data-ttu-id="25545-229">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-229">Values</span></span> | <span data-ttu-id="25545-230">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-231">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="25545-232">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="25545-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="25545-233">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="25545-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="25545-234">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="25545-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="25545-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-236">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="25545-237">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="25545-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="25545-238">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="25545-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="25545-239">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="25545-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="25545-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-240">.NET Core 3.0</span></span> |

<span data-ttu-id="25545-241">Exemple :</span><span class="sxs-lookup"><span data-stu-id="25545-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="25545-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="25545-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="25545-243">Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .</span><span class="sxs-lookup"><span data-stu-id="25545-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="25545-244">Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="25545-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="25545-245">Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="25545-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="25545-246">S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.</span><span class="sxs-lookup"><span data-stu-id="25545-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="25545-247">Valeur par défaut : GC ne s’étend pas au-delà des groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="25545-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="25545-248">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="25545-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="25545-249">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="25545-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="25545-250">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-250">Setting name</span></span> | <span data-ttu-id="25545-251">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-251">Values</span></span> | <span data-ttu-id="25545-252">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-253">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="25545-254">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-254">N/A</span></span> | <span data-ttu-id="25545-255">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-255">N/A</span></span> | <span data-ttu-id="25545-256">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-256">N/A</span></span> |
| <span data-ttu-id="25545-257">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="25545-258">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="25545-258">`0` - disabled</span></span><br/><span data-ttu-id="25545-259">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="25545-259">`1` - enabled</span></span> | <span data-ttu-id="25545-260">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-261">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="25545-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="25545-263">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="25545-263">`false` - disabled</span></span><br/><span data-ttu-id="25545-264">`true`-activé</span><span class="sxs-lookup"><span data-stu-id="25545-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="25545-265">Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="25545-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="25545-266">Pour les applications .NET Core, vous pouvez activer cette option en affectant à la `COMPlus_Thread_UseAllCpuGroups` variable d’environnement la valeur `1` .</span><span class="sxs-lookup"><span data-stu-id="25545-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="25545-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="25545-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="25545-268">Spécifie s’il faut *affinité* garbage collection threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="25545-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="25545-269">La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique.</span><span class="sxs-lookup"><span data-stu-id="25545-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="25545-270">Un segment de mémoire est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="25545-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="25545-271">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="25545-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="25545-272">Par défaut : affinité garbage collection les threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="25545-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="25545-273">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="25545-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="25545-274">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-274">Setting name</span></span> | <span data-ttu-id="25545-275">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-275">Values</span></span> | <span data-ttu-id="25545-276">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-277">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="25545-278">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="25545-278">`false` - affinitize</span></span><br/><span data-ttu-id="25545-279">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="25545-279">`true` - don't affinitize</span></span> | <span data-ttu-id="25545-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-281">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="25545-282">`0`-affinité</span><span class="sxs-lookup"><span data-stu-id="25545-282">`0` - affinitize</span></span><br/><span data-ttu-id="25545-283">`1`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="25545-283">`1` - don't affinitize</span></span> | <span data-ttu-id="25545-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-285">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="25545-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="25545-287">`false`-affinité</span><span class="sxs-lookup"><span data-stu-id="25545-287">`false` - affinitize</span></span><br/><span data-ttu-id="25545-288">`true`-ne affinité</span><span class="sxs-lookup"><span data-stu-id="25545-288">`true` - don't affinitize</span></span> | <span data-ttu-id="25545-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="25545-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="25545-290">Exemple :</span><span class="sxs-lookup"><span data-stu-id="25545-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="25545-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="25545-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="25545-292">Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.</span><span class="sxs-lookup"><span data-stu-id="25545-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="25545-293">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="25545-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="25545-294">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus grande de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="25545-294">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="25545-295">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="25545-295">The default value applies if:</span></span>

  - <span data-ttu-id="25545-296">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="25545-296">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="25545-297">[System. gc. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="25545-297">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="25545-298">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-298">Setting name</span></span> | <span data-ttu-id="25545-299">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-299">Values</span></span> | <span data-ttu-id="25545-300">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-300">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-301">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-301">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="25545-302">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-302">*decimal value*</span></span> | <span data-ttu-id="25545-303">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-303">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-304">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-304">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="25545-305">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="25545-305">*hexadecimal value*</span></span> | <span data-ttu-id="25545-306">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-306">.NET Core 3.0</span></span> |

<span data-ttu-id="25545-307">Exemple :</span><span class="sxs-lookup"><span data-stu-id="25545-307">Example:</span></span>

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
> <span data-ttu-id="25545-308">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="25545-308">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="25545-309">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="25545-309">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="25545-310">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="25545-310">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="25545-311">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="25545-311">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="25545-312">Spécifie l’utilisation autorisée du tas GC comme pourcentage de la mémoire physique totale.</span><span class="sxs-lookup"><span data-stu-id="25545-312">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="25545-313">Si [System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) est également défini, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="25545-313">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="25545-314">Ce paramètre s’applique uniquement aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="25545-314">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="25545-315">Si le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé sous la forme d’un pourcentage de cette limite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="25545-315">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="25545-316">La valeur par défaut, qui s’applique uniquement dans certains cas, est la plus petite de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="25545-316">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="25545-317">La valeur par défaut s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="25545-317">The default value applies if:</span></span>

  - <span data-ttu-id="25545-318">Le processus s’exécute dans un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="25545-318">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="25545-319">[System. gc. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="25545-319">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="25545-320">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-320">Setting name</span></span> | <span data-ttu-id="25545-321">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-321">Values</span></span> | <span data-ttu-id="25545-322">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-323">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="25545-324">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-324">*decimal value*</span></span> | <span data-ttu-id="25545-325">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-325">.NET Core 3.0</span></span> |
| <span data-ttu-id="25545-326">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-326">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="25545-327">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="25545-327">*hexadecimal value*</span></span> | <span data-ttu-id="25545-328">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-328">.NET Core 3.0</span></span> |

<span data-ttu-id="25545-329">Exemple :</span><span class="sxs-lookup"><span data-stu-id="25545-329">Example:</span></span>

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
> <span data-ttu-id="25545-330">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="25545-330">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="25545-331">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="25545-331">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="25545-332">Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="25545-332">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="25545-333">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="25545-333">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="25545-334">Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="25545-334">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="25545-335">Valeur par défaut : relâcher les segments sur le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="25545-335">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="25545-336">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="25545-336">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="25545-337">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-337">Setting name</span></span> | <span data-ttu-id="25545-338">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-338">Values</span></span> | <span data-ttu-id="25545-339">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-339">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-340">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-340">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="25545-341">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="25545-341">`false` - release to OS</span></span><br/><span data-ttu-id="25545-342">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="25545-342">`true` - put on standby</span></span> | <span data-ttu-id="25545-343">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-343">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-344">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="25545-344">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="25545-345">`false`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="25545-345">`false` - release to OS</span></span><br/><span data-ttu-id="25545-346">`true`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="25545-346">`true` - put on standby</span></span> | <span data-ttu-id="25545-347">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-347">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-348">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-348">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="25545-349">`0`-version finale du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="25545-349">`0` - release to OS</span></span><br/><span data-ttu-id="25545-350">`1`-mise en veille</span><span class="sxs-lookup"><span data-stu-id="25545-350">`1` - put on standby</span></span> | <span data-ttu-id="25545-351">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-351">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="25545-352">Exemples</span><span class="sxs-lookup"><span data-stu-id="25545-352">Examples</span></span>

<span data-ttu-id="25545-353">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="25545-353">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="25545-354">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="25545-354">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="25545-355">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="25545-355">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="25545-356">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="25545-356">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="25545-357">Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="25545-357">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="25545-358">Valeur par défaut : n’utilisez pas de grandes pages lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="25545-358">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="25545-359">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="25545-359">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="25545-360">Il s’agit d’un paramètre expérimental.</span><span class="sxs-lookup"><span data-stu-id="25545-360">This is an experimental setting.</span></span>

| | <span data-ttu-id="25545-361">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-361">Setting name</span></span> | <span data-ttu-id="25545-362">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-362">Values</span></span> | <span data-ttu-id="25545-363">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-363">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-364">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-364">**runtimeconfig.json**</span></span> | <span data-ttu-id="25545-365">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-365">N/A</span></span> | <span data-ttu-id="25545-366">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-366">N/A</span></span> | <span data-ttu-id="25545-367">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-367">N/A</span></span> |
| <span data-ttu-id="25545-368">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-368">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="25545-369">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="25545-369">`0` - disabled</span></span><br/><span data-ttu-id="25545-370">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="25545-370">`1` - enabled</span></span> | <span data-ttu-id="25545-371">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="25545-371">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="25545-372">Objets volumineux</span><span class="sxs-lookup"><span data-stu-id="25545-372">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="25545-373">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="25545-373">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="25545-374">Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="25545-374">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="25545-375">Valeur par défaut : GC prend en charge les tableaux supérieurs à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="25545-375">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="25545-376">Cela équivaut à définir la valeur sur `1` .</span><span class="sxs-lookup"><span data-stu-id="25545-376">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="25545-377">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="25545-377">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="25545-378">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-378">Setting name</span></span> | <span data-ttu-id="25545-379">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-379">Values</span></span> | <span data-ttu-id="25545-380">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-380">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-381">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-381">**runtimeconfig.json**</span></span> | <span data-ttu-id="25545-382">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-382">N/A</span></span> | <span data-ttu-id="25545-383">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-383">N/A</span></span> | <span data-ttu-id="25545-384">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-384">N/A</span></span> |
| <span data-ttu-id="25545-385">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-385">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="25545-386">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="25545-386">`1` - enabled</span></span><br/> <span data-ttu-id="25545-387">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="25545-387">`0` - disabled</span></span> | <span data-ttu-id="25545-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-389">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-390">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="25545-390">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="25545-391">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="25545-391">`1` - enabled</span></span><br/> <span data-ttu-id="25545-392">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="25545-392">`0` - disabled</span></span> | <span data-ttu-id="25545-393">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="25545-393">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="25545-394">Seuil du tas des objets volumineux</span><span class="sxs-lookup"><span data-stu-id="25545-394">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="25545-395">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="25545-395">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="25545-396">Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="25545-396">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="25545-397">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="25545-397">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="25545-398">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="25545-398">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="25545-399">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-399">Setting name</span></span> | <span data-ttu-id="25545-400">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-400">Values</span></span> | <span data-ttu-id="25545-401">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-401">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-402">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-402">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="25545-403">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-403">*decimal value*</span></span> | <span data-ttu-id="25545-404">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-404">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-405">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-405">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="25545-406">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="25545-406">*hexadecimal value*</span></span> | <span data-ttu-id="25545-407">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="25545-407">.NET Core 1.0</span></span> |
| <span data-ttu-id="25545-408">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="25545-408">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="25545-409">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="25545-409">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="25545-410">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="25545-410">*decimal value*</span></span> | <span data-ttu-id="25545-411">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="25545-411">.NET Framework 4.8</span></span> |

<span data-ttu-id="25545-412">Exemple :</span><span class="sxs-lookup"><span data-stu-id="25545-412">Example:</span></span>

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
> <span data-ttu-id="25545-413">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="25545-413">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="25545-414">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="25545-414">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="25545-415">Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="25545-415">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="25545-416">GC autonome</span><span class="sxs-lookup"><span data-stu-id="25545-416">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="25545-417">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="25545-417">COMPlus_GCName</span></span>

- <span data-ttu-id="25545-418">Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.</span><span class="sxs-lookup"><span data-stu-id="25545-418">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="25545-419">Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="25545-419">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="25545-420">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="25545-420">Setting name</span></span> | <span data-ttu-id="25545-421">Valeurs</span><span class="sxs-lookup"><span data-stu-id="25545-421">Values</span></span> | <span data-ttu-id="25545-422">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25545-422">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="25545-423">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="25545-423">**runtimeconfig.json**</span></span> | <span data-ttu-id="25545-424">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-424">N/A</span></span> | <span data-ttu-id="25545-425">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-425">N/A</span></span> | <span data-ttu-id="25545-426">N/A</span><span class="sxs-lookup"><span data-stu-id="25545-426">N/A</span></span> |
| <span data-ttu-id="25545-427">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="25545-427">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="25545-428">*string_path*</span><span class="sxs-lookup"><span data-stu-id="25545-428">*string_path*</span></span> | <span data-ttu-id="25545-429">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="25545-429">.NET Core 2.0</span></span> |
