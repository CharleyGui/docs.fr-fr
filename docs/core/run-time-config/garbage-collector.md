---
title: Arrangements de config de collecteur d’ordures
description: Découvrez les paramètres de course pour configurer comment le collecteur d’ordures gère la mémoire des applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607808"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="defea-103">Options de configuration en temps d’exécution pour la collecte des ordures</span><span class="sxs-lookup"><span data-stu-id="defea-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="defea-104">Cette page contient des informations sur les paramètres de collecteur d’ordures (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="defea-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="defea-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="defea-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="defea-106">Cependant, les défauts offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="defea-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="defea-107">Les paramètres sont disposés en groupes sur cette page.</span><span class="sxs-lookup"><span data-stu-id="defea-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="defea-108">Les paramètres de chaque groupe sont couramment utilisés en conjonction les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="defea-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="defea-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application au fur et à mesure qu’elle est en cours d’exécution, de sorte que tous les paramètres de temps d’exécution que vous définissez peuvent être annulés.</span><span class="sxs-lookup"><span data-stu-id="defea-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="defea-110">Certains paramètres, tels que [le niveau de latence,](../../standard/garbage-collection/latency.md)ne sont généralement définis que par l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="defea-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="defea-111">Ces paramètres sont omis à partir de cette page.</span><span class="sxs-lookup"><span data-stu-id="defea-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="defea-112">Pour les valeurs de nombre, utilisez la notation décimale pour les paramètres du fichier *runtimeconfig.json* et la notation hexadecimal pour les paramètres variables de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="defea-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="defea-113">Pour les valeurs hexadecimales, vous pouvez les spécifier avec ou sans le préfixe "0x".</span><span class="sxs-lookup"><span data-stu-id="defea-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="defea-114">Saveurs de collecte des ordures</span><span class="sxs-lookup"><span data-stu-id="defea-114">Flavors of garbage collection</span></span>

<span data-ttu-id="defea-115">Les deux principales saveurs de la collecte des ordures sont le poste de travail GC et le serveur GC.</span><span class="sxs-lookup"><span data-stu-id="defea-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="defea-116">Pour plus d’informations sur les différences entre les deux, voir [Fondamentaux de la collecte des ordures](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="defea-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="defea-117">Les sous-composants de la collecte des ordures sont de fond et non simultanés.</span><span class="sxs-lookup"><span data-stu-id="defea-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="defea-118">Utilisez les paramètres suivants pour sélectionner les saveurs de la collecte des ordures :</span><span class="sxs-lookup"><span data-stu-id="defea-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="defea-119">System.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="defea-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="defea-120">Configure si l’application utilise la collecte des ordures de poste de travail ou la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="defea-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="defea-121">Défaut : Collecte des`false`ordures de poste de travail ().</span><span class="sxs-lookup"><span data-stu-id="defea-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="defea-122">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-122">Setting name</span></span> | <span data-ttu-id="defea-123">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-123">Values</span></span> | <span data-ttu-id="defea-124">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="defea-126">`false`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="defea-126">`false` - workstation</span></span><br/><span data-ttu-id="defea-127">`true`- serveur</span><span class="sxs-lookup"><span data-stu-id="defea-127">`true` - server</span></span> | <span data-ttu-id="defea-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-129">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="defea-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="defea-130">`false`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="defea-130">`false` - workstation</span></span><br/><span data-ttu-id="defea-131">`true`- serveur</span><span class="sxs-lookup"><span data-stu-id="defea-131">`true` - server</span></span> | <span data-ttu-id="defea-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-133">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="defea-134">`0`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="defea-134">`0` - workstation</span></span><br/><span data-ttu-id="defea-135">`1`- serveur</span><span class="sxs-lookup"><span data-stu-id="defea-135">`1` - server</span></span> | <span data-ttu-id="defea-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-137">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-138">GCServer (en)</span><span class="sxs-lookup"><span data-stu-id="defea-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="defea-139">`false`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="defea-139">`false` - workstation</span></span><br/><span data-ttu-id="defea-140">`true`- serveur</span><span class="sxs-lookup"><span data-stu-id="defea-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="defea-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="defea-141">Examples</span></span>

<span data-ttu-id="defea-142">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="defea-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="defea-143">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="defea-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="defea-144">System.GC.Concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="defea-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="defea-145">Configure si la collecte des ordures de fond (concurrente) est activée.</span><span class="sxs-lookup"><span data-stu-id="defea-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="defea-146">Défaut: Activé`true`( ).</span><span class="sxs-lookup"><span data-stu-id="defea-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="defea-147">Pour plus d’informations, voir [Collection d’ordures Background](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) et [collecte des ordures serveur De fond](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="defea-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="defea-148">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-148">Setting name</span></span> | <span data-ttu-id="defea-149">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-149">Values</span></span> | <span data-ttu-id="defea-150">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="defea-152">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="defea-152">`true` - background GC</span></span><br/><span data-ttu-id="defea-153">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="defea-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="defea-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-155">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="defea-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="defea-156">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="defea-156">`true` - background GC</span></span><br/><span data-ttu-id="defea-157">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="defea-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="defea-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-159">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="defea-160">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="defea-160">`true` - background GC</span></span><br/><span data-ttu-id="defea-161">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="defea-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="defea-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-163">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="defea-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="defea-165">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="defea-165">`true` - background GC</span></span><br/><span data-ttu-id="defea-166">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="defea-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="defea-167">Exemples</span><span class="sxs-lookup"><span data-stu-id="defea-167">Examples</span></span>

<span data-ttu-id="defea-168">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="defea-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="defea-169">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="defea-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="defea-170">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="defea-170">Manage resource usage</span></span>

<span data-ttu-id="defea-171">Utilisez les paramètres décrits dans cette section pour gérer la mémoire du collecteur d’ordures et l’utilisation du processeur.</span><span class="sxs-lookup"><span data-stu-id="defea-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="defea-172">Pour plus d’informations sur certains de ces paramètres, voir le [terrain intermédiaire entre la poste de travail et l’entrée de blog serveur GC.](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)</span><span class="sxs-lookup"><span data-stu-id="defea-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="defea-173">System.GC.HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="defea-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="defea-174">Limite le nombre de tas créés par le collecteur d’ordures.</span><span class="sxs-lookup"><span data-stu-id="defea-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="defea-175">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="defea-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="defea-176">Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est activée, ce qui `n` est la valeur par défaut, `n` le réglage du nombre de tas affinitise les tas/threads GC aux premiers processeurs.</span><span class="sxs-lookup"><span data-stu-id="defea-176">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="defea-177">(Utilisez le [masque affinitize](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [affinitisez](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) les paramètres des plages pour spécifier exactement les processeurs à affinitiser.)</span><span class="sxs-lookup"><span data-stu-id="defea-177">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="defea-178">Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre limite le nombre de tas de GC.</span><span class="sxs-lookup"><span data-stu-id="defea-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="defea-179">Pour plus d’informations, voir les [remarques GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="defea-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="defea-180">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-180">Setting name</span></span> | <span data-ttu-id="defea-181">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-181">Values</span></span> | <span data-ttu-id="defea-182">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="defea-184">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-184">*decimal value*</span></span> | <span data-ttu-id="defea-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-186">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="defea-187">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="defea-187">*hexadecimal value*</span></span> | <span data-ttu-id="defea-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-189">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-190">GCHeapCount (en)</span><span class="sxs-lookup"><span data-stu-id="defea-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="defea-191">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-191">*decimal value*</span></span> | <span data-ttu-id="defea-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="defea-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="defea-193">Exemple :</span><span class="sxs-lookup"><span data-stu-id="defea-193">Example:</span></span>

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
> <span data-ttu-id="defea-194">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="defea-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="defea-195">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="defea-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="defea-196">Par exemple, pour limiter le nombre de tas à 16, les valeurs seraient de 16 pour le fichier JSON et de 0x10 ou 10 pour la variable environnement.</span><span class="sxs-lookup"><span data-stu-id="defea-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="defea-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="defea-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="defea-198">Spécifie les processeurs exacts que les fils de collecteur d’ordures devraient utiliser.</span><span class="sxs-lookup"><span data-stu-id="defea-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="defea-199">Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="defea-199">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="defea-200">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="defea-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="defea-201">La valeur est un masque peu qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="defea-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="defea-202">Par exemple, une valeur décimale de 1023 (ou une valeur hexadecimale de 0x3FF ou 3FF si vous utilisez la variable de l’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="defea-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="defea-203">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="defea-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="defea-204">Pour spécifier les 10 processeurs suivants, c’est-à-dire les processeurs 10-19, spécifient une valeur décimale de 1047552 (ou une valeur hexadecimale de 0xFFC00 ou FFC00), ce qui équivaut à une valeur binaire de 1111 1111 1100 000 0000.</span><span class="sxs-lookup"><span data-stu-id="defea-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="defea-205">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-205">Setting name</span></span> | <span data-ttu-id="defea-206">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-206">Values</span></span> | <span data-ttu-id="defea-207">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="defea-209">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-209">*decimal value*</span></span> | <span data-ttu-id="defea-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-211">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="defea-212">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="defea-212">*hexadecimal value*</span></span> | <span data-ttu-id="defea-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-214">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="defea-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="defea-216">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-216">*decimal value*</span></span> | <span data-ttu-id="defea-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="defea-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="defea-218">Exemple :</span><span class="sxs-lookup"><span data-stu-id="defea-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="defea-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="defea-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="defea-220">Spécifie la liste des processeurs à utiliser pour les fils de collecteur d’ordures.</span><span class="sxs-lookup"><span data-stu-id="defea-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="defea-221">Ce paramètre est similaire à [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="defea-221">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="defea-222">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe CPU](/windows/win32/procthread/processor-groups)correspondant, par exemple, "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="defea-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="defea-223">Si [l’affinité du processeur GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) est désactivée, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="defea-223">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="defea-224">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="defea-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="defea-225">Pour plus d’informations, voir [Faire la configuration CPU mieux pour GC sur les machines avec > 64 processeurs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="defea-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="defea-226">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-226">Setting name</span></span> | <span data-ttu-id="defea-227">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-227">Values</span></span> | <span data-ttu-id="defea-228">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="defea-230">Liste séparée par comma des numéros de processeur ou des gammes de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="defea-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="defea-231">Exemple d’Unix : « 1-10,12,50-52,70 »</span><span class="sxs-lookup"><span data-stu-id="defea-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="defea-232">Exemple windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="defea-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="defea-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-234">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="defea-235">Liste séparée par comma des numéros de processeur ou des gammes de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="defea-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="defea-236">Exemple d’Unix : « 1-10,12,50-52,70 »</span><span class="sxs-lookup"><span data-stu-id="defea-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="defea-237">Exemple windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="defea-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="defea-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-238">.NET Core 3.0</span></span> |

<span data-ttu-id="defea-239">Exemple :</span><span class="sxs-lookup"><span data-stu-id="defea-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="defea-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="defea-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="defea-241">Configure si le collecteur d’ordures utilise ou non [des groupes de processeurs.](/windows/win32/procthread/processor-groups)</span><span class="sxs-lookup"><span data-stu-id="defea-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="defea-242">Lorsqu’un ordinateur Windows 64 bits a plusieurs groupes de processeurs, c’est-à-dire qu’il y a plus de 64 processeurs, ce qui permet à cet élément d’étendre la collecte des ordures dans tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="defea-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="defea-243">Le collecteur d’ordures utilise tous les noyaux pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="defea-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="defea-244">S’applique uniquement à la collecte des ordures du serveur sur les systèmes d’exploitation Windows 64 bits.</span><span class="sxs-lookup"><span data-stu-id="defea-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="defea-245">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="defea-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="defea-246">Pour plus d’informations, voir [Faire la configuration CPU mieux pour GC sur les machines avec > 64 processeurs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="defea-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="defea-247">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-247">Setting name</span></span> | <span data-ttu-id="defea-248">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-248">Values</span></span> | <span data-ttu-id="defea-249">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="defea-251">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-251">N/A</span></span> | <span data-ttu-id="defea-252">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-252">N/A</span></span> | <span data-ttu-id="defea-253">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-253">N/A</span></span> |
| <span data-ttu-id="defea-254">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="defea-255">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="defea-255">`0` - disabled</span></span><br/><span data-ttu-id="defea-256">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="defea-256">`1` - enabled</span></span> | <span data-ttu-id="defea-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-258">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="defea-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="defea-260">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="defea-260">`false` - disabled</span></span><br/><span data-ttu-id="defea-261">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="defea-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="defea-262">Pour configurer l’heure de l’exécution de la langue commune (CLR) pour également distribuer les fils du pool de threads dans tous les groupes de processeur, activez [l’option Thread_UseAllCpuGroups élément.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="defea-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="defea-263">Pour les applications .NET Core, vous pouvez activer cette option en définissant la valeur de la variable de l’environnement `COMPlus_Thread_UseAllCpuGroups` à `1`.</span><span class="sxs-lookup"><span data-stu-id="defea-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="defea-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="defea-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="defea-265">Précise s’il faut *affinitiser les* fils de collecte des ordures avec les transformateurs.</span><span class="sxs-lookup"><span data-stu-id="defea-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="defea-266">Pour affinitiser un thread GC signifie qu’il ne peut fonctionner que sur son processeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="defea-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="defea-267">Un tas est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="defea-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="defea-268">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="defea-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="defea-269">Défaut : Affinitiser les fils de`false`collecte des ordures avec les transformateurs ( ).</span><span class="sxs-lookup"><span data-stu-id="defea-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="defea-270">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-270">Setting name</span></span> | <span data-ttu-id="defea-271">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-271">Values</span></span> | <span data-ttu-id="defea-272">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="defea-274">`false`- affinitiser</span><span class="sxs-lookup"><span data-stu-id="defea-274">`false` - affinitize</span></span><br/><span data-ttu-id="defea-275">`true`- n’affinitez pas</span><span class="sxs-lookup"><span data-stu-id="defea-275">`true` - don't affinitize</span></span> | <span data-ttu-id="defea-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-277">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="defea-278">`0`- affinitiser</span><span class="sxs-lookup"><span data-stu-id="defea-278">`0` - affinitize</span></span><br/><span data-ttu-id="defea-279">`1`- n’affinitez pas</span><span class="sxs-lookup"><span data-stu-id="defea-279">`1` - don't affinitize</span></span> | <span data-ttu-id="defea-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-281">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="defea-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="defea-283">`false`- affinitiser</span><span class="sxs-lookup"><span data-stu-id="defea-283">`false` - affinitize</span></span><br/><span data-ttu-id="defea-284">`true`- n’affinitez pas</span><span class="sxs-lookup"><span data-stu-id="defea-284">`true` - don't affinitize</span></span> | <span data-ttu-id="defea-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="defea-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="defea-286">Exemple :</span><span class="sxs-lookup"><span data-stu-id="defea-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="defea-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="defea-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="defea-288">Spécifie la taille maximale de commit, dans les octets, pour le tas GC et la comptabilité GC.</span><span class="sxs-lookup"><span data-stu-id="defea-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="defea-289">Ce paramètre ne s’applique qu’aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="defea-289">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="defea-290">La valeur par défaut, qui ne s’applique que dans certains cas, est la moindre de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="defea-290">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="defea-291">La valeur par défaut s’applique si :</span><span class="sxs-lookup"><span data-stu-id="defea-291">The default value applies if:</span></span>

  - <span data-ttu-id="defea-292">Le processus est en cours d’exécution à l’intérieur d’un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="defea-292">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="defea-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="defea-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="defea-294">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-294">Setting name</span></span> | <span data-ttu-id="defea-295">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-295">Values</span></span> | <span data-ttu-id="defea-296">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-296">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-297">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-297">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="defea-298">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-298">*decimal value*</span></span> | <span data-ttu-id="defea-299">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-299">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-300">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-300">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="defea-301">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="defea-301">*hexadecimal value*</span></span> | <span data-ttu-id="defea-302">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-302">.NET Core 3.0</span></span> |

<span data-ttu-id="defea-303">Exemple :</span><span class="sxs-lookup"><span data-stu-id="defea-303">Example:</span></span>

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
> <span data-ttu-id="defea-304">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="defea-304">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="defea-305">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="defea-305">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="defea-306">Par exemple, pour spécifier une limite de 200 mebioctets (MiB), les valeurs seraient 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable environnement.</span><span class="sxs-lookup"><span data-stu-id="defea-306">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="defea-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="defea-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="defea-308">Spécifie l’utilisation autorisée de tas de GC en pourcentage de la mémoire physique totale.</span><span class="sxs-lookup"><span data-stu-id="defea-308">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="defea-309">Si [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) est également défini, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="defea-309">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="defea-310">Ce paramètre ne s’applique qu’aux ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="defea-310">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="defea-311">Si le processus est en cours d’exécution à l’intérieur d’un conteneur qui a une limite de mémoire spécifiée, le pourcentage est calculé comme un pourcentage de cette limite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="defea-311">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="defea-312">La valeur par défaut, qui ne s’applique que dans certains cas, est la moindre de 20 Mo ou 75% de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="defea-312">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="defea-313">La valeur par défaut s’applique si :</span><span class="sxs-lookup"><span data-stu-id="defea-313">The default value applies if:</span></span>

  - <span data-ttu-id="defea-314">Le processus est en cours d’exécution à l’intérieur d’un conteneur qui a une limite de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="defea-314">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="defea-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="defea-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="defea-316">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-316">Setting name</span></span> | <span data-ttu-id="defea-317">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-317">Values</span></span> | <span data-ttu-id="defea-318">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-318">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-319">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-319">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="defea-320">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-320">*decimal value*</span></span> | <span data-ttu-id="defea-321">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-321">.NET Core 3.0</span></span> |
| <span data-ttu-id="defea-322">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-322">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="defea-323">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="defea-323">*hexadecimal value*</span></span> | <span data-ttu-id="defea-324">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-324">.NET Core 3.0</span></span> |

<span data-ttu-id="defea-325">Exemple :</span><span class="sxs-lookup"><span data-stu-id="defea-325">Example:</span></span>

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
> <span data-ttu-id="defea-326">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="defea-326">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="defea-327">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="defea-327">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="defea-328">Par exemple, pour limiter l’utilisation du tas à 30 %, les valeurs seraient de 30 pour le fichier JSON et de 0x1E ou 1E pour la variable de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="defea-328">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="defea-329">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="defea-329">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="defea-330">Configure si les segments qui doivent être supprimés sont mis sur une liste de veille pour une utilisation future ou sont libérés vers le système d’exploitation (OS).</span><span class="sxs-lookup"><span data-stu-id="defea-330">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="defea-331">Défaut : Les segments de`false`sortie retournent au système d’exploitation ().</span><span class="sxs-lookup"><span data-stu-id="defea-331">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="defea-332">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-332">Setting name</span></span> | <span data-ttu-id="defea-333">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-333">Values</span></span> | <span data-ttu-id="defea-334">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-334">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-335">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-335">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="defea-336">`false`- sortie à OS</span><span class="sxs-lookup"><span data-stu-id="defea-336">`false` - release to OS</span></span><br/><span data-ttu-id="defea-337">`true`- mis en veille</span><span class="sxs-lookup"><span data-stu-id="defea-337">`true` - put on standby</span></span> | <span data-ttu-id="defea-338">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-338">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-339">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="defea-339">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="defea-340">`false`- sortie à OS</span><span class="sxs-lookup"><span data-stu-id="defea-340">`false` - release to OS</span></span><br/><span data-ttu-id="defea-341">`true`- mis en veille</span><span class="sxs-lookup"><span data-stu-id="defea-341">`true` - put on standby</span></span> | <span data-ttu-id="defea-342">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-342">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-343">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-343">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="defea-344">`0`- sortie à OS</span><span class="sxs-lookup"><span data-stu-id="defea-344">`0` - release to OS</span></span><br/><span data-ttu-id="defea-345">`1`- mis en veille</span><span class="sxs-lookup"><span data-stu-id="defea-345">`1` - put on standby</span></span> | <span data-ttu-id="defea-346">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-346">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="defea-347">Exemples</span><span class="sxs-lookup"><span data-stu-id="defea-347">Examples</span></span>

<span data-ttu-id="defea-348">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="defea-348">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="defea-349">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="defea-349">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="defea-350">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="defea-350">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="defea-351">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="defea-351">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="defea-352">Précise si de grandes pages doivent être utilisées lorsqu’une limite de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="defea-352">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="defea-353">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="defea-353">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="defea-354">C’est un cadre expérimental.</span><span class="sxs-lookup"><span data-stu-id="defea-354">This is an experimental setting.</span></span>

| | <span data-ttu-id="defea-355">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-355">Setting name</span></span> | <span data-ttu-id="defea-356">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-356">Values</span></span> | <span data-ttu-id="defea-357">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-358">**runtimeconfig.json**</span></span> | <span data-ttu-id="defea-359">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-359">N/A</span></span> | <span data-ttu-id="defea-360">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-360">N/A</span></span> | <span data-ttu-id="defea-361">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-361">N/A</span></span> |
| <span data-ttu-id="defea-362">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-362">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="defea-363">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="defea-363">`0` - disabled</span></span><br/><span data-ttu-id="defea-364">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="defea-364">`1` - enabled</span></span> | <span data-ttu-id="defea-365">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="defea-365">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="defea-366">Grands objets</span><span class="sxs-lookup"><span data-stu-id="defea-366">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="defea-367">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="defea-367">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="defea-368">Configure le support des collecteurs d’ordures sur les plates-formes 64 bits pour les tableaux de plus de 2 gigaoctets (GB) en taille totale.</span><span class="sxs-lookup"><span data-stu-id="defea-368">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="defea-369">Défaut: Activé`1`( ).</span><span class="sxs-lookup"><span data-stu-id="defea-369">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="defea-370">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="defea-370">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="defea-371">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-371">Setting name</span></span> | <span data-ttu-id="defea-372">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-372">Values</span></span> | <span data-ttu-id="defea-373">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-373">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-374">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-374">**runtimeconfig.json**</span></span> | <span data-ttu-id="defea-375">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-375">N/A</span></span> | <span data-ttu-id="defea-376">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-376">N/A</span></span> | <span data-ttu-id="defea-377">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-377">N/A</span></span> |
| <span data-ttu-id="defea-378">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-378">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="defea-379">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="defea-379">`1` - enabled</span></span><br/> <span data-ttu-id="defea-380">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="defea-380">`0` - disabled</span></span> | <span data-ttu-id="defea-381">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-381">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-382">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-382">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-383">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="defea-383">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="defea-384">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="defea-384">`1` - enabled</span></span><br/> <span data-ttu-id="defea-385">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="defea-385">`0` - disabled</span></span> | <span data-ttu-id="defea-386">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="defea-386">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="defea-387">Grand seuil de tas d’objets</span><span class="sxs-lookup"><span data-stu-id="defea-387">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="defea-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="defea-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="defea-389">Spécifie la taille du seuil, dans les octets, qui provoque des objets à aller sur le tas de gros objets (LOH).</span><span class="sxs-lookup"><span data-stu-id="defea-389">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="defea-390">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="defea-390">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="defea-391">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="defea-391">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="defea-392">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-392">Setting name</span></span> | <span data-ttu-id="defea-393">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-393">Values</span></span> | <span data-ttu-id="defea-394">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-394">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-395">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-395">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="defea-396">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-396">*decimal value*</span></span> | <span data-ttu-id="defea-397">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-397">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-398">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-398">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="defea-399">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="defea-399">*hexadecimal value*</span></span> | <span data-ttu-id="defea-400">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="defea-400">.NET Core 1.0</span></span> |
| <span data-ttu-id="defea-401">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="defea-401">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="defea-402">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="defea-402">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="defea-403">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="defea-403">*decimal value*</span></span> | <span data-ttu-id="defea-404">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="defea-404">.NET Framework 4.8</span></span> |

<span data-ttu-id="defea-405">Exemple :</span><span class="sxs-lookup"><span data-stu-id="defea-405">Example:</span></span>

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
> <span data-ttu-id="defea-406">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="defea-406">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="defea-407">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="defea-407">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="defea-408">Par exemple, pour fixer un seuil de 120 000 octets, les valeurs seraient de 120000 pour le fichier JSON et de 0x1D4C0 ou 1D4C0 pour la variable environnement.</span><span class="sxs-lookup"><span data-stu-id="defea-408">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="defea-409">GC autonome</span><span class="sxs-lookup"><span data-stu-id="defea-409">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="defea-410">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="defea-410">COMPlus_GCName</span></span>

- <span data-ttu-id="defea-411">Spécifie un chemin vers la bibliothèque contenant le éboueur que le temps d’exécution a l’intention de charger.</span><span class="sxs-lookup"><span data-stu-id="defea-411">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="defea-412">Pour plus d’informations, voir [La conception de chargeur Standalone GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="defea-412">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="defea-413">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="defea-413">Setting name</span></span> | <span data-ttu-id="defea-414">Valeurs</span><span class="sxs-lookup"><span data-stu-id="defea-414">Values</span></span> | <span data-ttu-id="defea-415">Version introduite</span><span class="sxs-lookup"><span data-stu-id="defea-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="defea-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="defea-416">**runtimeconfig.json**</span></span> | <span data-ttu-id="defea-417">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-417">N/A</span></span> | <span data-ttu-id="defea-418">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-418">N/A</span></span> | <span data-ttu-id="defea-419">N/A</span><span class="sxs-lookup"><span data-stu-id="defea-419">N/A</span></span> |
| <span data-ttu-id="defea-420">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="defea-420">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="defea-421">*string_path*</span><span class="sxs-lookup"><span data-stu-id="defea-421">*string_path*</span></span> | <span data-ttu-id="defea-422">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="defea-422">.NET Core 2.0</span></span> |
