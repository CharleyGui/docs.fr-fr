---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733519"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="87afe-103">Options de configuration au moment de l’exécution pour garbage collection</span><span class="sxs-lookup"><span data-stu-id="87afe-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="87afe-104">Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="87afe-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="87afe-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="87afe-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="87afe-106">Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="87afe-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="87afe-107">Les paramètres sont organisés en groupes dans cette page.</span><span class="sxs-lookup"><span data-stu-id="87afe-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="87afe-108">Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="87afe-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="87afe-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.</span><span class="sxs-lookup"><span data-stu-id="87afe-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="87afe-110">Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="87afe-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="87afe-111">Ces paramètres sont omis dans cette page.</span><span class="sxs-lookup"><span data-stu-id="87afe-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="87afe-112">Pour les valeurs numériques, utilisez la notation décimale pour les paramètres dans le fichier *runtimeconfig. JSON* et la notation hexadécimale pour les paramètres de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="87afe-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="87afe-113">Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».</span><span class="sxs-lookup"><span data-stu-id="87afe-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="87afe-114">Versions de garbage collection</span><span class="sxs-lookup"><span data-stu-id="87afe-114">Flavors of garbage collection</span></span>

<span data-ttu-id="87afe-115">Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="87afe-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="87afe-116">Pour plus d’informations sur les différences entre les deux, consultez [principes de base de garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="87afe-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="87afe-117">Les sous-versions de garbage collection sont en arrière-plan et non simultanées.</span><span class="sxs-lookup"><span data-stu-id="87afe-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="87afe-118">Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :</span><span class="sxs-lookup"><span data-stu-id="87afe-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="87afe-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="87afe-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="87afe-120">Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="87afe-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="87afe-121">Par défaut : station de travail garbage collection (`false`).</span><span class="sxs-lookup"><span data-stu-id="87afe-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="87afe-122">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-122">Setting name</span></span> | <span data-ttu-id="87afe-123">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-123">Values</span></span> | <span data-ttu-id="87afe-124">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="87afe-126">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="87afe-126">`false` - workstation</span></span><br/><span data-ttu-id="87afe-127">serveur de `true`</span><span class="sxs-lookup"><span data-stu-id="87afe-127">`true` - server</span></span> | <span data-ttu-id="87afe-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-129">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="87afe-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="87afe-130">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="87afe-130">`false` - workstation</span></span><br/><span data-ttu-id="87afe-131">serveur de `true`</span><span class="sxs-lookup"><span data-stu-id="87afe-131">`true` - server</span></span> | <span data-ttu-id="87afe-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-133">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="87afe-134">`0`-station de travail</span><span class="sxs-lookup"><span data-stu-id="87afe-134">`0` - workstation</span></span><br/><span data-ttu-id="87afe-135">serveur de `1`</span><span class="sxs-lookup"><span data-stu-id="87afe-135">`1` - server</span></span> | <span data-ttu-id="87afe-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-137">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="87afe-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="87afe-139">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="87afe-139">`false` - workstation</span></span><br/><span data-ttu-id="87afe-140">serveur de `true`</span><span class="sxs-lookup"><span data-stu-id="87afe-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="87afe-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="87afe-141">Examples</span></span>

<span data-ttu-id="87afe-142">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="87afe-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="87afe-143">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="87afe-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="87afe-144">System. GC. concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="87afe-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="87afe-145">Configure si l’garbage collection d’arrière-plan (simultanée) est activée.</span><span class="sxs-lookup"><span data-stu-id="87afe-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="87afe-146">Valeur par défaut : activé (`true`).</span><span class="sxs-lookup"><span data-stu-id="87afe-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="87afe-147">Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) et [garbage collection de serveur d’arrière-plan](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="87afe-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="87afe-148">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-148">Setting name</span></span> | <span data-ttu-id="87afe-149">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-149">Values</span></span> | <span data-ttu-id="87afe-150">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-151">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="87afe-152">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="87afe-152">`true` - background GC</span></span><br/><span data-ttu-id="87afe-153">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="87afe-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="87afe-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-155">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="87afe-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="87afe-156">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="87afe-156">`true` - background GC</span></span><br/><span data-ttu-id="87afe-157">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="87afe-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="87afe-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-159">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="87afe-160">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="87afe-160">`true` - background GC</span></span><br/><span data-ttu-id="87afe-161">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="87afe-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="87afe-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-163">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="87afe-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="87afe-165">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="87afe-165">`true` - background GC</span></span><br/><span data-ttu-id="87afe-166">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="87afe-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="87afe-167">Exemples</span><span class="sxs-lookup"><span data-stu-id="87afe-167">Examples</span></span>

<span data-ttu-id="87afe-168">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="87afe-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="87afe-169">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="87afe-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="87afe-170">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="87afe-170">Manage resource usage</span></span>

<span data-ttu-id="87afe-171">Utilisez les paramètres décrits dans cette section pour gérer la mémoire et l’utilisation du processeur du garbage collector.</span><span class="sxs-lookup"><span data-stu-id="87afe-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="87afe-172">Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="87afe-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="87afe-173">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="87afe-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="87afe-174">Limite le nombre de segments de mémoire créés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="87afe-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="87afe-175">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="87afe-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="87afe-176">Si l’affinité du processeur GC est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers processeurs `n`.</span><span class="sxs-lookup"><span data-stu-id="87afe-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="87afe-177">(Utilisez les paramètres affinité Mask ou affinité Ranges pour spécifier exactement les processeurs à affinité.)</span><span class="sxs-lookup"><span data-stu-id="87afe-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="87afe-178">Si l’affinité du processeur GC est désactivée, ce paramètre limite le nombre de tas GC.</span><span class="sxs-lookup"><span data-stu-id="87afe-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="87afe-179">Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="87afe-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="87afe-180">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-180">Setting name</span></span> | <span data-ttu-id="87afe-181">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-181">Values</span></span> | <span data-ttu-id="87afe-182">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-183">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="87afe-184">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-184">*decimal value*</span></span> | <span data-ttu-id="87afe-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-186">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="87afe-187">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-187">*hexadecimal value*</span></span> | <span data-ttu-id="87afe-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-189">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="87afe-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="87afe-191">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-191">*decimal value*</span></span> | <span data-ttu-id="87afe-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="87afe-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="87afe-193">Exemple :</span><span class="sxs-lookup"><span data-stu-id="87afe-193">Example:</span></span>

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
> <span data-ttu-id="87afe-194">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="87afe-195">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="87afe-196">Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="87afe-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="87afe-197">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="87afe-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="87afe-198">Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.</span><span class="sxs-lookup"><span data-stu-id="87afe-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="87afe-199">Si l’affinité du processeur est désactivée en définissant `System.GC.NoAffinitize` sur `true`, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="87afe-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="87afe-200">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="87afe-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="87afe-201">La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="87afe-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="87afe-202">Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="87afe-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="87afe-203">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="87afe-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="87afe-204">Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="87afe-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="87afe-205">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-205">Setting name</span></span> | <span data-ttu-id="87afe-206">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-206">Values</span></span> | <span data-ttu-id="87afe-207">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-208">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="87afe-209">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-209">*decimal value*</span></span> | <span data-ttu-id="87afe-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-211">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="87afe-212">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-212">*hexadecimal value*</span></span> | <span data-ttu-id="87afe-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-214">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="87afe-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="87afe-216">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-216">*decimal value*</span></span> | <span data-ttu-id="87afe-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="87afe-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="87afe-218">Exemple :</span><span class="sxs-lookup"><span data-stu-id="87afe-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="87afe-219">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="87afe-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="87afe-220">Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.</span><span class="sxs-lookup"><span data-stu-id="87afe-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="87afe-221">Ce paramètre est similaire à `System.GC.HeapAffinitizeMask`, sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="87afe-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="87afe-222">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».</span><span class="sxs-lookup"><span data-stu-id="87afe-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="87afe-223">Si l’affinité du processeur est désactivée en définissant `System.GC.NoAffinitize` sur `true`, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="87afe-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="87afe-224">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="87afe-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="87afe-225">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="87afe-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="87afe-226">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-226">Setting name</span></span> | <span data-ttu-id="87afe-227">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-227">Values</span></span> | <span data-ttu-id="87afe-228">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-229">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="87afe-230">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="87afe-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="87afe-231">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="87afe-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="87afe-232">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="87afe-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="87afe-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-234">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="87afe-235">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="87afe-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="87afe-236">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="87afe-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="87afe-237">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="87afe-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="87afe-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-238">.NET Core 3.0</span></span> |

<span data-ttu-id="87afe-239">Exemple :</span><span class="sxs-lookup"><span data-stu-id="87afe-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="87afe-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="87afe-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="87afe-241">Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .</span><span class="sxs-lookup"><span data-stu-id="87afe-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="87afe-242">Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="87afe-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="87afe-243">Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="87afe-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="87afe-244">S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.</span><span class="sxs-lookup"><span data-stu-id="87afe-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="87afe-245">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="87afe-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="87afe-246">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="87afe-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="87afe-247">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-247">Setting name</span></span> | <span data-ttu-id="87afe-248">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-248">Values</span></span> | <span data-ttu-id="87afe-249">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-250">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="87afe-251">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-251">N/A</span></span> | <span data-ttu-id="87afe-252">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-252">N/A</span></span> | <span data-ttu-id="87afe-253">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-253">N/A</span></span> |
| <span data-ttu-id="87afe-254">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="87afe-255">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="87afe-255">`0` - disabled</span></span><br/><span data-ttu-id="87afe-256">activé `1`</span><span class="sxs-lookup"><span data-stu-id="87afe-256">`1` - enabled</span></span> | <span data-ttu-id="87afe-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-258">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="87afe-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="87afe-260">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="87afe-260">`false` - disabled</span></span><br/><span data-ttu-id="87afe-261">activé `true`</span><span class="sxs-lookup"><span data-stu-id="87afe-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="87afe-262">Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="87afe-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="87afe-263">Pour les applications .NET Core, vous pouvez activer cette option en définissant la valeur de la variable d’environnement `COMPlus_Thread_UseAllCpuGroups` sur `1`.</span><span class="sxs-lookup"><span data-stu-id="87afe-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="87afe-264">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="87afe-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="87afe-265">Spécifie s’il faut *affinité* garbage collection threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="87afe-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="87afe-266">La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique.</span><span class="sxs-lookup"><span data-stu-id="87afe-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="87afe-267">Un segment de mémoire est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="87afe-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="87afe-268">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="87afe-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="87afe-269">Par défaut : affinité garbage collection threads avec processeurs (`false`).</span><span class="sxs-lookup"><span data-stu-id="87afe-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="87afe-270">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-270">Setting name</span></span> | <span data-ttu-id="87afe-271">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-271">Values</span></span> | <span data-ttu-id="87afe-272">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-273">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="87afe-274">`false` affinité</span><span class="sxs-lookup"><span data-stu-id="87afe-274">`false` - affinitize</span></span><br/><span data-ttu-id="87afe-275">`true`-ne pas affinité</span><span class="sxs-lookup"><span data-stu-id="87afe-275">`true` - don't affinitize</span></span> | <span data-ttu-id="87afe-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-277">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="87afe-278">`0` affinité</span><span class="sxs-lookup"><span data-stu-id="87afe-278">`0` - affinitize</span></span><br/><span data-ttu-id="87afe-279">`1`-ne pas affinité</span><span class="sxs-lookup"><span data-stu-id="87afe-279">`1` - don't affinitize</span></span> | <span data-ttu-id="87afe-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-281">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="87afe-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="87afe-283">`false` affinité</span><span class="sxs-lookup"><span data-stu-id="87afe-283">`false` - affinitize</span></span><br/><span data-ttu-id="87afe-284">`true`-ne pas affinité</span><span class="sxs-lookup"><span data-stu-id="87afe-284">`true` - don't affinitize</span></span> | <span data-ttu-id="87afe-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="87afe-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="87afe-286">Exemple :</span><span class="sxs-lookup"><span data-stu-id="87afe-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="87afe-287">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="87afe-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="87afe-288">Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.</span><span class="sxs-lookup"><span data-stu-id="87afe-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="87afe-289">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-289">Setting name</span></span> | <span data-ttu-id="87afe-290">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-290">Values</span></span> | <span data-ttu-id="87afe-291">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-292">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="87afe-293">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-293">*decimal value*</span></span> | <span data-ttu-id="87afe-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-295">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="87afe-296">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-296">*hexadecimal value*</span></span> | <span data-ttu-id="87afe-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-297">.NET Core 3.0</span></span> |

<span data-ttu-id="87afe-298">Exemple :</span><span class="sxs-lookup"><span data-stu-id="87afe-298">Example:</span></span>

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
> <span data-ttu-id="87afe-299">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="87afe-300">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="87afe-301">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="87afe-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="87afe-302">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="87afe-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="87afe-303">Spécifie l’utilisation du tas GC comme pourcentage de la mémoire totale.</span><span class="sxs-lookup"><span data-stu-id="87afe-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="87afe-304">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-304">Setting name</span></span> | <span data-ttu-id="87afe-305">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-305">Values</span></span> | <span data-ttu-id="87afe-306">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-307">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="87afe-308">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-308">*decimal value*</span></span> | <span data-ttu-id="87afe-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="87afe-310">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="87afe-311">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-311">*hexadecimal value*</span></span> | <span data-ttu-id="87afe-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-312">.NET Core 3.0</span></span> |

<span data-ttu-id="87afe-313">Exemple :</span><span class="sxs-lookup"><span data-stu-id="87afe-313">Example:</span></span>

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
> <span data-ttu-id="87afe-314">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="87afe-315">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="87afe-316">Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="87afe-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="87afe-317">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="87afe-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="87afe-318">Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="87afe-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="87afe-319">Valeur par défaut : relâcher les segments sur le système d’exploitation (`false`).</span><span class="sxs-lookup"><span data-stu-id="87afe-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="87afe-320">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-320">Setting name</span></span> | <span data-ttu-id="87afe-321">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-321">Values</span></span> | <span data-ttu-id="87afe-322">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="87afe-324">`false`-version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="87afe-324">`false` - release to OS</span></span><br/><span data-ttu-id="87afe-325">`true`-mettre en veille</span><span class="sxs-lookup"><span data-stu-id="87afe-325">`true` - put on standby</span></span> | <span data-ttu-id="87afe-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-327">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="87afe-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="87afe-328">`false`-version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="87afe-328">`false` - release to OS</span></span><br/><span data-ttu-id="87afe-329">`true`-mettre en veille</span><span class="sxs-lookup"><span data-stu-id="87afe-329">`true` - put on standby</span></span> | <span data-ttu-id="87afe-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-331">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="87afe-332">`0`-version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="87afe-332">`0` - release to OS</span></span><br/><span data-ttu-id="87afe-333">`1`-mettre en veille</span><span class="sxs-lookup"><span data-stu-id="87afe-333">`1` - put on standby</span></span> | <span data-ttu-id="87afe-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="87afe-335">Exemples</span><span class="sxs-lookup"><span data-stu-id="87afe-335">Examples</span></span>

<span data-ttu-id="87afe-336">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="87afe-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="87afe-337">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="87afe-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="87afe-338">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="87afe-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="87afe-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="87afe-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="87afe-340">Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="87afe-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="87afe-341">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="87afe-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="87afe-342">Il s’agit d’un paramètre expérimental.</span><span class="sxs-lookup"><span data-stu-id="87afe-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="87afe-343">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-343">Setting name</span></span> | <span data-ttu-id="87afe-344">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-344">Values</span></span> | <span data-ttu-id="87afe-345">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-346">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="87afe-347">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-347">N/A</span></span> | <span data-ttu-id="87afe-348">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-348">N/A</span></span> | <span data-ttu-id="87afe-349">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-349">N/A</span></span> |
| <span data-ttu-id="87afe-350">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="87afe-351">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="87afe-351">`0` - disabled</span></span><br/><span data-ttu-id="87afe-352">activé `1`</span><span class="sxs-lookup"><span data-stu-id="87afe-352">`1` - enabled</span></span> | <span data-ttu-id="87afe-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87afe-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="87afe-354">Objets volumineux</span><span class="sxs-lookup"><span data-stu-id="87afe-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="87afe-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="87afe-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="87afe-356">Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="87afe-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="87afe-357">Valeur par défaut : activé (`1`).</span><span class="sxs-lookup"><span data-stu-id="87afe-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="87afe-358">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="87afe-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="87afe-359">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-359">Setting name</span></span> | <span data-ttu-id="87afe-360">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-360">Values</span></span> | <span data-ttu-id="87afe-361">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-362">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="87afe-363">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-363">N/A</span></span> | <span data-ttu-id="87afe-364">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-364">N/A</span></span> | <span data-ttu-id="87afe-365">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-365">N/A</span></span> |
| <span data-ttu-id="87afe-366">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="87afe-367">activé `1`</span><span class="sxs-lookup"><span data-stu-id="87afe-367">`1` - enabled</span></span><br/> <span data-ttu-id="87afe-368">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="87afe-368">`0` - disabled</span></span> | <span data-ttu-id="87afe-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-370">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="87afe-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="87afe-372">activé `1`</span><span class="sxs-lookup"><span data-stu-id="87afe-372">`1` - enabled</span></span><br/> <span data-ttu-id="87afe-373">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="87afe-373">`0` - disabled</span></span> | <span data-ttu-id="87afe-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="87afe-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="87afe-375">Seuil du tas des objets volumineux</span><span class="sxs-lookup"><span data-stu-id="87afe-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="87afe-376">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="87afe-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="87afe-377">Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="87afe-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="87afe-378">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="87afe-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="87afe-379">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="87afe-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="87afe-380">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-380">Setting name</span></span> | <span data-ttu-id="87afe-381">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-381">Values</span></span> | <span data-ttu-id="87afe-382">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-383">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="87afe-384">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-384">*decimal value*</span></span> | <span data-ttu-id="87afe-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-386">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="87afe-387">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-387">*hexadecimal value*</span></span> | <span data-ttu-id="87afe-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="87afe-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="87afe-389">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="87afe-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="87afe-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="87afe-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="87afe-391">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="87afe-391">*decimal value*</span></span> | <span data-ttu-id="87afe-392">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="87afe-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="87afe-393">Exemple :</span><span class="sxs-lookup"><span data-stu-id="87afe-393">Example:</span></span>

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
> <span data-ttu-id="87afe-394">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="87afe-395">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="87afe-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="87afe-396">Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="87afe-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="87afe-397">GC autonome</span><span class="sxs-lookup"><span data-stu-id="87afe-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="87afe-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="87afe-398">COMPlus_GCName</span></span>

- <span data-ttu-id="87afe-399">Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.</span><span class="sxs-lookup"><span data-stu-id="87afe-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="87afe-400">Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="87afe-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="87afe-401">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="87afe-401">Setting name</span></span> | <span data-ttu-id="87afe-402">Valeurs</span><span class="sxs-lookup"><span data-stu-id="87afe-402">Values</span></span> | <span data-ttu-id="87afe-403">Version introduite</span><span class="sxs-lookup"><span data-stu-id="87afe-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="87afe-404">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="87afe-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="87afe-405">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-405">N/A</span></span> | <span data-ttu-id="87afe-406">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-406">N/A</span></span> | <span data-ttu-id="87afe-407">N/A</span><span class="sxs-lookup"><span data-stu-id="87afe-407">N/A</span></span> |
| <span data-ttu-id="87afe-408">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="87afe-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="87afe-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="87afe-409">*string_path*</span></span> | <span data-ttu-id="87afe-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="87afe-410">.NET Core 2.0</span></span> |
