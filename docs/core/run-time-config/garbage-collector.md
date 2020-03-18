---
title: Arrangements de config de collecteur d’ordures
description: Découvrez les paramètres de course pour configurer comment le collecteur d’ordures gère la mémoire des applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733519"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="ba208-103">Options de configuration en temps d’exécution pour la collecte des ordures</span><span class="sxs-lookup"><span data-stu-id="ba208-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="ba208-104">Cette page contient des informations sur les paramètres de collecteur d’ordures (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ba208-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="ba208-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="ba208-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="ba208-106">Cependant, les défauts offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="ba208-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="ba208-107">Les paramètres sont disposés en groupes sur cette page.</span><span class="sxs-lookup"><span data-stu-id="ba208-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="ba208-108">Les paramètres de chaque groupe sont couramment utilisés en conjonction les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="ba208-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="ba208-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application au fur et à mesure qu’elle est en cours d’exécution, de sorte que tous les paramètres de temps d’exécution que vous définissez peuvent être annulés.</span><span class="sxs-lookup"><span data-stu-id="ba208-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="ba208-110">Certains paramètres, tels que [le niveau de latence,](../../standard/garbage-collection/latency.md)ne sont généralement définis que par l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="ba208-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="ba208-111">Ces paramètres sont omis à partir de cette page.</span><span class="sxs-lookup"><span data-stu-id="ba208-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="ba208-112">Pour les valeurs de nombre, utilisez la notation décimale pour les paramètres du fichier *runtimeconfig.json* et la notation hexadecimal pour les paramètres variables de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="ba208-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="ba208-113">Pour les valeurs hexadecimales, vous pouvez les spécifier avec ou sans le préfixe "0x".</span><span class="sxs-lookup"><span data-stu-id="ba208-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="ba208-114">Saveurs de collecte des ordures</span><span class="sxs-lookup"><span data-stu-id="ba208-114">Flavors of garbage collection</span></span>

<span data-ttu-id="ba208-115">Les deux principales saveurs de la collecte des ordures sont le poste de travail GC et le serveur GC.</span><span class="sxs-lookup"><span data-stu-id="ba208-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="ba208-116">Pour plus d’informations sur les différences entre les deux, voir [Fondamentaux de la collecte des ordures](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="ba208-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="ba208-117">Les sous-composants de la collecte des ordures sont de fond et non simultanés.</span><span class="sxs-lookup"><span data-stu-id="ba208-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="ba208-118">Utilisez les paramètres suivants pour sélectionner les saveurs de la collecte des ordures :</span><span class="sxs-lookup"><span data-stu-id="ba208-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="ba208-119">System.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="ba208-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="ba208-120">Configure si l’application utilise la collecte des ordures de poste de travail ou la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="ba208-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="ba208-121">Défaut : Collecte des`false`ordures de poste de travail ().</span><span class="sxs-lookup"><span data-stu-id="ba208-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="ba208-122">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-122">Setting name</span></span> | <span data-ttu-id="ba208-123">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-123">Values</span></span> | <span data-ttu-id="ba208-124">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="ba208-126">`false`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="ba208-126">`false` - workstation</span></span><br/><span data-ttu-id="ba208-127">`true`- serveur</span><span class="sxs-lookup"><span data-stu-id="ba208-127">`true` - server</span></span> | <span data-ttu-id="ba208-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-129">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="ba208-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="ba208-130">`false`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="ba208-130">`false` - workstation</span></span><br/><span data-ttu-id="ba208-131">`true`- serveur</span><span class="sxs-lookup"><span data-stu-id="ba208-131">`true` - server</span></span> | <span data-ttu-id="ba208-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-133">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="ba208-134">`0`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="ba208-134">`0` - workstation</span></span><br/><span data-ttu-id="ba208-135">`1`- serveur</span><span class="sxs-lookup"><span data-stu-id="ba208-135">`1` - server</span></span> | <span data-ttu-id="ba208-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-137">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-138">GCServer (en)</span><span class="sxs-lookup"><span data-stu-id="ba208-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="ba208-139">`false`- poste de travail</span><span class="sxs-lookup"><span data-stu-id="ba208-139">`false` - workstation</span></span><br/><span data-ttu-id="ba208-140">`true`- serveur</span><span class="sxs-lookup"><span data-stu-id="ba208-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="ba208-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="ba208-141">Examples</span></span>

<span data-ttu-id="ba208-142">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="ba208-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="ba208-143">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="ba208-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="ba208-144">System.GC.Concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="ba208-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="ba208-145">Configure si la collecte des ordures de fond (concurrente) est activée.</span><span class="sxs-lookup"><span data-stu-id="ba208-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="ba208-146">Défaut: Activé`true`( ).</span><span class="sxs-lookup"><span data-stu-id="ba208-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="ba208-147">Pour plus d’informations, voir [Collection d’ordures Background](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) et [collecte des ordures serveur De fond](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="ba208-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="ba208-148">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-148">Setting name</span></span> | <span data-ttu-id="ba208-149">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-149">Values</span></span> | <span data-ttu-id="ba208-150">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="ba208-152">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="ba208-152">`true` - background GC</span></span><br/><span data-ttu-id="ba208-153">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="ba208-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="ba208-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-155">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="ba208-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="ba208-156">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="ba208-156">`true` - background GC</span></span><br/><span data-ttu-id="ba208-157">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="ba208-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="ba208-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-159">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="ba208-160">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="ba208-160">`true` - background GC</span></span><br/><span data-ttu-id="ba208-161">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="ba208-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="ba208-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-163">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="ba208-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="ba208-165">`true`- fond GC</span><span class="sxs-lookup"><span data-stu-id="ba208-165">`true` - background GC</span></span><br/><span data-ttu-id="ba208-166">`false`- GC non concomitant</span><span class="sxs-lookup"><span data-stu-id="ba208-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="ba208-167">Exemples</span><span class="sxs-lookup"><span data-stu-id="ba208-167">Examples</span></span>

<span data-ttu-id="ba208-168">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="ba208-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="ba208-169">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="ba208-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="ba208-170">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="ba208-170">Manage resource usage</span></span>

<span data-ttu-id="ba208-171">Utilisez les paramètres décrits dans cette section pour gérer la mémoire du collecteur d’ordures et l’utilisation du processeur.</span><span class="sxs-lookup"><span data-stu-id="ba208-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="ba208-172">Pour plus d’informations sur certains de ces paramètres, voir le [terrain intermédiaire entre la poste de travail et l’entrée de blog serveur GC.](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)</span><span class="sxs-lookup"><span data-stu-id="ba208-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="ba208-173">System.GC.HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="ba208-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="ba208-174">Limite le nombre de tas créés par le collecteur d’ordures.</span><span class="sxs-lookup"><span data-stu-id="ba208-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="ba208-175">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="ba208-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="ba208-176">Si l’affinité du processeur GC est activée, ce qui `n` est la valeur par défaut, `n` le réglage du nombre de tas affinitise les tas/threads GC aux premiers processeurs.</span><span class="sxs-lookup"><span data-stu-id="ba208-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="ba208-177">(Utilisez le masque affinitize ou affinitisez les paramètres des plages pour spécifier exactement les processeurs à affinitiser.)</span><span class="sxs-lookup"><span data-stu-id="ba208-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="ba208-178">Si l’affinité du processeur GC est désactivée, ce paramètre limite le nombre de tas de GC.</span><span class="sxs-lookup"><span data-stu-id="ba208-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="ba208-179">Pour plus d’informations, voir les [remarques GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="ba208-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="ba208-180">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-180">Setting name</span></span> | <span data-ttu-id="ba208-181">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-181">Values</span></span> | <span data-ttu-id="ba208-182">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="ba208-184">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-184">*decimal value*</span></span> | <span data-ttu-id="ba208-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-186">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="ba208-187">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="ba208-187">*hexadecimal value*</span></span> | <span data-ttu-id="ba208-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-189">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-190">GCHeapCount (en)</span><span class="sxs-lookup"><span data-stu-id="ba208-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="ba208-191">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-191">*decimal value*</span></span> | <span data-ttu-id="ba208-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ba208-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="ba208-193">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba208-193">Example:</span></span>

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
> <span data-ttu-id="ba208-194">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="ba208-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="ba208-195">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ba208-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="ba208-196">Par exemple, pour limiter le nombre de tas à 16, les valeurs seraient de 16 pour le fichier JSON et de 0x10 ou 10 pour la variable environnement.</span><span class="sxs-lookup"><span data-stu-id="ba208-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="ba208-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="ba208-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="ba208-198">Spécifie les processeurs exacts que les fils de collecteur d’ordures devraient utiliser.</span><span class="sxs-lookup"><span data-stu-id="ba208-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="ba208-199">Si l’affinité du `System.GC.NoAffinitize` `true`processeur est désactivée par réglage à , ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="ba208-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="ba208-200">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="ba208-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="ba208-201">La valeur est un masque peu qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="ba208-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="ba208-202">Par exemple, une valeur décimale de 1023 (ou une valeur hexadecimale de 0x3FF ou 3FF si vous utilisez la variable de l’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="ba208-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="ba208-203">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="ba208-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="ba208-204">Pour spécifier les 10 processeurs suivants, c’est-à-dire les processeurs 10-19, spécifient une valeur décimale de 1047552 (ou une valeur hexadecimale de 0xFFC00 ou FFC00), ce qui équivaut à une valeur binaire de 1111 1111 1100 000 0000.</span><span class="sxs-lookup"><span data-stu-id="ba208-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="ba208-205">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-205">Setting name</span></span> | <span data-ttu-id="ba208-206">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-206">Values</span></span> | <span data-ttu-id="ba208-207">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="ba208-209">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-209">*decimal value*</span></span> | <span data-ttu-id="ba208-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-211">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="ba208-212">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="ba208-212">*hexadecimal value*</span></span> | <span data-ttu-id="ba208-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-214">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="ba208-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="ba208-216">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-216">*decimal value*</span></span> | <span data-ttu-id="ba208-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ba208-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="ba208-218">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba208-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="ba208-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="ba208-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="ba208-220">Spécifie la liste des processeurs à utiliser pour les fils de collecteur d’ordures.</span><span class="sxs-lookup"><span data-stu-id="ba208-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="ba208-221">Ce paramètre `System.GC.HeapAffinitizeMask`est similaire à , sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="ba208-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="ba208-222">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe CPU](/windows/win32/procthread/processor-groups)correspondant, par exemple, "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="ba208-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="ba208-223">Si l’affinité du `System.GC.NoAffinitize` `true`processeur est désactivée par réglage à , ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="ba208-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="ba208-224">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="ba208-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="ba208-225">Pour plus d’informations, voir [Faire la configuration CPU mieux pour GC sur les machines avec > 64 processeurs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="ba208-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="ba208-226">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-226">Setting name</span></span> | <span data-ttu-id="ba208-227">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-227">Values</span></span> | <span data-ttu-id="ba208-228">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="ba208-230">Liste séparée par comma des numéros de processeur ou des gammes de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="ba208-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="ba208-231">Exemple d’Unix : « 1-10,12,50-52,70 »</span><span class="sxs-lookup"><span data-stu-id="ba208-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="ba208-232">Exemple windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="ba208-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="ba208-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-234">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="ba208-235">Liste séparée par comma des numéros de processeur ou des gammes de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="ba208-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="ba208-236">Exemple d’Unix : « 1-10,12,50-52,70 »</span><span class="sxs-lookup"><span data-stu-id="ba208-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="ba208-237">Exemple windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="ba208-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="ba208-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-238">.NET Core 3.0</span></span> |

<span data-ttu-id="ba208-239">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba208-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="ba208-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="ba208-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="ba208-241">Configure si le collecteur d’ordures utilise ou non [des groupes de processeurs.](/windows/win32/procthread/processor-groups)</span><span class="sxs-lookup"><span data-stu-id="ba208-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="ba208-242">Lorsqu’un ordinateur Windows 64 bits a plusieurs groupes de processeurs, c’est-à-dire qu’il y a plus de 64 processeurs, ce qui permet à cet élément d’étendre la collecte des ordures dans tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="ba208-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="ba208-243">Le collecteur d’ordures utilise tous les noyaux pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="ba208-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="ba208-244">S’applique uniquement à la collecte des ordures du serveur sur les systèmes d’exploitation Windows 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ba208-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="ba208-245">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="ba208-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="ba208-246">Pour plus d’informations, voir [Faire la configuration CPU mieux pour GC sur les machines avec > 64 processeurs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="ba208-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="ba208-247">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-247">Setting name</span></span> | <span data-ttu-id="ba208-248">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-248">Values</span></span> | <span data-ttu-id="ba208-249">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba208-251">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-251">N/A</span></span> | <span data-ttu-id="ba208-252">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-252">N/A</span></span> | <span data-ttu-id="ba208-253">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-253">N/A</span></span> |
| <span data-ttu-id="ba208-254">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="ba208-255">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="ba208-255">`0` - disabled</span></span><br/><span data-ttu-id="ba208-256">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="ba208-256">`1` - enabled</span></span> | <span data-ttu-id="ba208-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-258">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="ba208-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="ba208-260">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="ba208-260">`false` - disabled</span></span><br/><span data-ttu-id="ba208-261">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="ba208-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="ba208-262">Pour configurer l’heure de l’exécution de la langue commune (CLR) pour également distribuer les fils du pool de threads dans tous les groupes de processeur, activez [l’option Thread_UseAllCpuGroups élément.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="ba208-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="ba208-263">Pour les applications .NET Core, vous pouvez activer cette option en définissant la valeur de la variable de l’environnement `COMPlus_Thread_UseAllCpuGroups` à `1`.</span><span class="sxs-lookup"><span data-stu-id="ba208-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="ba208-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="ba208-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="ba208-265">Précise s’il faut *affinitiser les* fils de collecte des ordures avec les transformateurs.</span><span class="sxs-lookup"><span data-stu-id="ba208-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="ba208-266">Pour affinitiser un thread GC signifie qu’il ne peut fonctionner que sur son processeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="ba208-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="ba208-267">Un tas est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="ba208-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="ba208-268">S’applique uniquement à la collecte des ordures du serveur.</span><span class="sxs-lookup"><span data-stu-id="ba208-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="ba208-269">Défaut : Affinitiser les fils de`false`collecte des ordures avec les transformateurs ( ).</span><span class="sxs-lookup"><span data-stu-id="ba208-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="ba208-270">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-270">Setting name</span></span> | <span data-ttu-id="ba208-271">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-271">Values</span></span> | <span data-ttu-id="ba208-272">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="ba208-274">`false`- affinitiser</span><span class="sxs-lookup"><span data-stu-id="ba208-274">`false` - affinitize</span></span><br/><span data-ttu-id="ba208-275">`true`- n’affinitez pas</span><span class="sxs-lookup"><span data-stu-id="ba208-275">`true` - don't affinitize</span></span> | <span data-ttu-id="ba208-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-277">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="ba208-278">`0`- affinitiser</span><span class="sxs-lookup"><span data-stu-id="ba208-278">`0` - affinitize</span></span><br/><span data-ttu-id="ba208-279">`1`- n’affinitez pas</span><span class="sxs-lookup"><span data-stu-id="ba208-279">`1` - don't affinitize</span></span> | <span data-ttu-id="ba208-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-281">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="ba208-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="ba208-283">`false`- affinitiser</span><span class="sxs-lookup"><span data-stu-id="ba208-283">`false` - affinitize</span></span><br/><span data-ttu-id="ba208-284">`true`- n’affinitez pas</span><span class="sxs-lookup"><span data-stu-id="ba208-284">`true` - don't affinitize</span></span> | <span data-ttu-id="ba208-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ba208-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="ba208-286">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba208-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="ba208-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="ba208-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="ba208-288">Spécifie la taille maximale de commit, dans les octets, pour le tas GC et la comptabilité GC.</span><span class="sxs-lookup"><span data-stu-id="ba208-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="ba208-289">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-289">Setting name</span></span> | <span data-ttu-id="ba208-290">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-290">Values</span></span> | <span data-ttu-id="ba208-291">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-292">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="ba208-293">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-293">*decimal value*</span></span> | <span data-ttu-id="ba208-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-295">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="ba208-296">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="ba208-296">*hexadecimal value*</span></span> | <span data-ttu-id="ba208-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-297">.NET Core 3.0</span></span> |

<span data-ttu-id="ba208-298">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba208-298">Example:</span></span>

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
> <span data-ttu-id="ba208-299">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="ba208-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="ba208-300">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ba208-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="ba208-301">Par exemple, pour spécifier une limite de 200 mebioctets (MiB), les valeurs seraient 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable environnement.</span><span class="sxs-lookup"><span data-stu-id="ba208-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="ba208-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="ba208-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="ba208-303">Spécifie l’utilisation du tas GC en pourcentage de la mémoire totale.</span><span class="sxs-lookup"><span data-stu-id="ba208-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="ba208-304">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-304">Setting name</span></span> | <span data-ttu-id="ba208-305">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-305">Values</span></span> | <span data-ttu-id="ba208-306">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-307">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="ba208-308">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-308">*decimal value*</span></span> | <span data-ttu-id="ba208-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="ba208-310">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="ba208-311">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="ba208-311">*hexadecimal value*</span></span> | <span data-ttu-id="ba208-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-312">.NET Core 3.0</span></span> |

<span data-ttu-id="ba208-313">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba208-313">Example:</span></span>

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
> <span data-ttu-id="ba208-314">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="ba208-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="ba208-315">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ba208-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="ba208-316">Par exemple, pour limiter l’utilisation du tas à 30 %, les valeurs seraient de 30 pour le fichier JSON et de 0x1E ou 1E pour la variable de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="ba208-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="ba208-317">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="ba208-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="ba208-318">Configure si les segments qui doivent être supprimés sont mis sur une liste de veille pour une utilisation future ou sont libérés vers le système d’exploitation (OS).</span><span class="sxs-lookup"><span data-stu-id="ba208-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="ba208-319">Défaut : Les segments de`false`sortie retournent au système d’exploitation ().</span><span class="sxs-lookup"><span data-stu-id="ba208-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="ba208-320">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-320">Setting name</span></span> | <span data-ttu-id="ba208-321">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-321">Values</span></span> | <span data-ttu-id="ba208-322">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-323">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="ba208-324">`false`- sortie à OS</span><span class="sxs-lookup"><span data-stu-id="ba208-324">`false` - release to OS</span></span><br/><span data-ttu-id="ba208-325">`true`- mis en veille</span><span class="sxs-lookup"><span data-stu-id="ba208-325">`true` - put on standby</span></span> | <span data-ttu-id="ba208-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-327">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="ba208-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="ba208-328">`false`- sortie à OS</span><span class="sxs-lookup"><span data-stu-id="ba208-328">`false` - release to OS</span></span><br/><span data-ttu-id="ba208-329">`true`- mis en veille</span><span class="sxs-lookup"><span data-stu-id="ba208-329">`true` - put on standby</span></span> | <span data-ttu-id="ba208-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-331">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="ba208-332">`0`- sortie à OS</span><span class="sxs-lookup"><span data-stu-id="ba208-332">`0` - release to OS</span></span><br/><span data-ttu-id="ba208-333">`1`- mis en veille</span><span class="sxs-lookup"><span data-stu-id="ba208-333">`1` - put on standby</span></span> | <span data-ttu-id="ba208-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="ba208-335">Exemples</span><span class="sxs-lookup"><span data-stu-id="ba208-335">Examples</span></span>

<span data-ttu-id="ba208-336">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="ba208-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="ba208-337">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="ba208-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="ba208-338">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="ba208-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="ba208-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="ba208-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="ba208-340">Précise si de grandes pages doivent être utilisées lorsqu’une limite de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="ba208-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="ba208-341">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="ba208-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="ba208-342">C’est un cadre expérimental.</span><span class="sxs-lookup"><span data-stu-id="ba208-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="ba208-343">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-343">Setting name</span></span> | <span data-ttu-id="ba208-344">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-344">Values</span></span> | <span data-ttu-id="ba208-345">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-346">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba208-347">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-347">N/A</span></span> | <span data-ttu-id="ba208-348">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-348">N/A</span></span> | <span data-ttu-id="ba208-349">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-349">N/A</span></span> |
| <span data-ttu-id="ba208-350">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="ba208-351">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="ba208-351">`0` - disabled</span></span><br/><span data-ttu-id="ba208-352">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="ba208-352">`1` - enabled</span></span> | <span data-ttu-id="ba208-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ba208-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="ba208-354">Grands objets</span><span class="sxs-lookup"><span data-stu-id="ba208-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="ba208-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="ba208-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="ba208-356">Configure le support des collecteurs d’ordures sur les plates-formes 64 bits pour les tableaux de plus de 2 gigaoctets (GB) en taille totale.</span><span class="sxs-lookup"><span data-stu-id="ba208-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="ba208-357">Défaut: Activé`1`( ).</span><span class="sxs-lookup"><span data-stu-id="ba208-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="ba208-358">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="ba208-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="ba208-359">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-359">Setting name</span></span> | <span data-ttu-id="ba208-360">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-360">Values</span></span> | <span data-ttu-id="ba208-361">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-362">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba208-363">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-363">N/A</span></span> | <span data-ttu-id="ba208-364">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-364">N/A</span></span> | <span data-ttu-id="ba208-365">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-365">N/A</span></span> |
| <span data-ttu-id="ba208-366">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="ba208-367">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="ba208-367">`1` - enabled</span></span><br/> <span data-ttu-id="ba208-368">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="ba208-368">`0` - disabled</span></span> | <span data-ttu-id="ba208-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-370">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="ba208-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="ba208-372">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="ba208-372">`1` - enabled</span></span><br/> <span data-ttu-id="ba208-373">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="ba208-373">`0` - disabled</span></span> | <span data-ttu-id="ba208-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ba208-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="ba208-375">Grand seuil de tas d’objets</span><span class="sxs-lookup"><span data-stu-id="ba208-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="ba208-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="ba208-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="ba208-377">Spécifie la taille du seuil, dans les octets, qui provoque des objets à aller sur le tas de gros objets (LOH).</span><span class="sxs-lookup"><span data-stu-id="ba208-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="ba208-378">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="ba208-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="ba208-379">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="ba208-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="ba208-380">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-380">Setting name</span></span> | <span data-ttu-id="ba208-381">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-381">Values</span></span> | <span data-ttu-id="ba208-382">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-383">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="ba208-384">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-384">*decimal value*</span></span> | <span data-ttu-id="ba208-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-386">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="ba208-387">*valeur hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="ba208-387">*hexadecimal value*</span></span> | <span data-ttu-id="ba208-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ba208-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="ba208-389">**app.config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="ba208-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="ba208-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="ba208-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="ba208-391">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="ba208-391">*decimal value*</span></span> | <span data-ttu-id="ba208-392">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="ba208-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="ba208-393">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ba208-393">Example:</span></span>

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
> <span data-ttu-id="ba208-394">Si vous définissez l’option en *runtimeconfig.json*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="ba208-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="ba208-395">Si vous définissez l’option comme variable d’environnement, spécifiez une valeur hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ba208-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="ba208-396">Par exemple, pour fixer un seuil de 120 000 octets, les valeurs seraient de 120000 pour le fichier JSON et de 0x1D4C0 ou 1D4C0 pour la variable environnement.</span><span class="sxs-lookup"><span data-stu-id="ba208-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="ba208-397">GC autonome</span><span class="sxs-lookup"><span data-stu-id="ba208-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="ba208-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="ba208-398">COMPlus_GCName</span></span>

- <span data-ttu-id="ba208-399">Spécifie un chemin vers la bibliothèque contenant le éboueur que le temps d’exécution a l’intention de charger.</span><span class="sxs-lookup"><span data-stu-id="ba208-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="ba208-400">Pour plus d’informations, voir [La conception de chargeur Standalone GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="ba208-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="ba208-401">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ba208-401">Setting name</span></span> | <span data-ttu-id="ba208-402">Valeurs</span><span class="sxs-lookup"><span data-stu-id="ba208-402">Values</span></span> | <span data-ttu-id="ba208-403">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba208-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="ba208-404">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba208-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba208-405">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-405">N/A</span></span> | <span data-ttu-id="ba208-406">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-406">N/A</span></span> | <span data-ttu-id="ba208-407">N/A</span><span class="sxs-lookup"><span data-stu-id="ba208-407">N/A</span></span> |
| <span data-ttu-id="ba208-408">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="ba208-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="ba208-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="ba208-409">*string_path*</span></span> | <span data-ttu-id="ba208-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ba208-410">.NET Core 2.0</span></span> |
