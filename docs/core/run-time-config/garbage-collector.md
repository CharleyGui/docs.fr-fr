---
title: Paramètres de configuration du garbage collector
description: En savoir plus sur les paramètres d’exécution pour la configuration de la façon dont le garbage collector gère la mémoire pour les applications .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900095"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="4c63c-103">Options de configuration au moment de l’exécution pour garbage collection</span><span class="sxs-lookup"><span data-stu-id="4c63c-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="4c63c-104">Cette page contient des informations sur les paramètres de garbage collector (GC) qui peuvent être modifiés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c63c-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="4c63c-105">Si vous essayez d’atteindre les performances maximales d’une application en cours d’exécution, envisagez d’utiliser ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="4c63c-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="4c63c-106">Toutefois, les valeurs par défaut offrent des performances optimales pour la plupart des applications dans des situations typiques.</span><span class="sxs-lookup"><span data-stu-id="4c63c-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="4c63c-107">Les paramètres sont organisés en groupes dans cette page.</span><span class="sxs-lookup"><span data-stu-id="4c63c-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="4c63c-108">Les paramètres de chaque groupe sont couramment utilisés conjointement les uns avec les autres pour obtenir un résultat spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c63c-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="4c63c-109">Ces paramètres peuvent également être modifiés dynamiquement par l’application en cours d’exécution, de sorte que tous les paramètres d’exécution que vous définissez peuvent être remplacés.</span><span class="sxs-lookup"><span data-stu-id="4c63c-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="4c63c-110">Certains paramètres, tels que le [niveau de latence](../../standard/garbage-collection/latency.md), sont généralement définis uniquement par le biais de l’API au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="4c63c-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="4c63c-111">Ces paramètres sont omis dans cette page.</span><span class="sxs-lookup"><span data-stu-id="4c63c-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="4c63c-112">Pour les valeurs numériques, utilisez la notation décimale pour les paramètres dans le fichier *runtimeconfig. JSON* et la notation hexadécimale pour les paramètres de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4c63c-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="4c63c-113">Pour les valeurs hexadécimales, vous pouvez les spécifier avec ou sans le préfixe « 0x ».</span><span class="sxs-lookup"><span data-stu-id="4c63c-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="4c63c-114">Versions de garbage collection</span><span class="sxs-lookup"><span data-stu-id="4c63c-114">Flavors of garbage collection</span></span>

<span data-ttu-id="4c63c-115">Les deux principales versions de garbage collection sont GC de station de travail et garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="4c63c-116">Pour plus d’informations sur les différences entre les deux, consultez [principes de base de garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="4c63c-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="4c63c-117">Les sous-versions de garbage collection sont en arrière-plan et non simultanées.</span><span class="sxs-lookup"><span data-stu-id="4c63c-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="4c63c-118">Utilisez les paramètres suivants pour sélectionner les versions de garbage collection :</span><span class="sxs-lookup"><span data-stu-id="4c63c-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="4c63c-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="4c63c-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="4c63c-120">Configure si l’application utilise des garbage collection de station de travail ou des garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="4c63c-121">Par défaut : station de travail garbage collection (`false`).</span><span class="sxs-lookup"><span data-stu-id="4c63c-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="4c63c-122">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-122">Setting name</span></span> | <span data-ttu-id="4c63c-123">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-123">Values</span></span> | <span data-ttu-id="4c63c-124">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="4c63c-126">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="4c63c-126">`false` - workstation</span></span><br/><span data-ttu-id="4c63c-127">serveur de `true`</span><span class="sxs-lookup"><span data-stu-id="4c63c-127">`true` - server</span></span> | <span data-ttu-id="4c63c-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-129">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-129">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="4c63c-130">`0`-station de travail</span><span class="sxs-lookup"><span data-stu-id="4c63c-130">`0` - workstation</span></span><br/><span data-ttu-id="4c63c-131">serveur de `1`</span><span class="sxs-lookup"><span data-stu-id="4c63c-131">`1` - server</span></span> | <span data-ttu-id="4c63c-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-133">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-133">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-134">GCServer</span><span class="sxs-lookup"><span data-stu-id="4c63c-134">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="4c63c-135">`false`-station de travail</span><span class="sxs-lookup"><span data-stu-id="4c63c-135">`false` - workstation</span></span><br/><span data-ttu-id="4c63c-136">serveur de `true`</span><span class="sxs-lookup"><span data-stu-id="4c63c-136">`true` - server</span></span> |  |

<span data-ttu-id="4c63c-137">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-137">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="4c63c-138">System. GC. concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="4c63c-138">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="4c63c-139">Configure si l’garbage collection d’arrière-plan (simultanée) est activée.</span><span class="sxs-lookup"><span data-stu-id="4c63c-139">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="4c63c-140">Valeur par défaut : activé (`true`).</span><span class="sxs-lookup"><span data-stu-id="4c63c-140">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="4c63c-141">Pour plus d’informations, consultez [garbage collection d’arrière-plan](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) et [garbage collection de serveur d’arrière-plan](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="4c63c-141">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="4c63c-142">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-142">Setting name</span></span> | <span data-ttu-id="4c63c-143">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-143">Values</span></span> | <span data-ttu-id="4c63c-144">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-144">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-145">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-145">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="4c63c-146">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="4c63c-146">`true` - background GC</span></span><br/><span data-ttu-id="4c63c-147">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="4c63c-147">`false` - non-concurrent GC</span></span> | <span data-ttu-id="4c63c-148">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-148">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-149">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-149">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="4c63c-150">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="4c63c-150">`true` - background GC</span></span><br/><span data-ttu-id="4c63c-151">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="4c63c-151">`false` - non-concurrent GC</span></span> | <span data-ttu-id="4c63c-152">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-152">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-153">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-153">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-154">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="4c63c-154">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="4c63c-155">`true`-arrière-plan GC</span><span class="sxs-lookup"><span data-stu-id="4c63c-155">`true` - background GC</span></span><br/><span data-ttu-id="4c63c-156">`false`-GC non simultané</span><span class="sxs-lookup"><span data-stu-id="4c63c-156">`false` - non-concurrent GC</span></span> |  |

<span data-ttu-id="4c63c-157">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-157">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a><span data-ttu-id="4c63c-158">Gérer l’utilisation des ressources</span><span class="sxs-lookup"><span data-stu-id="4c63c-158">Manage resource usage</span></span>

<span data-ttu-id="4c63c-159">Utilisez les paramètres décrits dans cette section pour gérer la mémoire et l’utilisation du processeur du garbage collector.</span><span class="sxs-lookup"><span data-stu-id="4c63c-159">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="4c63c-160">Pour plus d’informations sur certains de ces paramètres, consultez l’entrée de blog [Middle sol between station de travail et serveur gc](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="4c63c-160">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="4c63c-161">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="4c63c-161">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="4c63c-162">Limite le nombre de segments de mémoire créés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="4c63c-162">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="4c63c-163">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-163">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="4c63c-164">Si l’affinité du processeur GC est activée, ce qui correspond à la valeur par défaut, le nombre de segments de mémoire définissant affinité entre `n` les tas/threads GC sur les premiers processeurs `n`.</span><span class="sxs-lookup"><span data-stu-id="4c63c-164">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="4c63c-165">(Utilisez les paramètres affinité Mask ou affinité Ranges pour spécifier exactement les processeurs à affinité.)</span><span class="sxs-lookup"><span data-stu-id="4c63c-165">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="4c63c-166">Si l’affinité du processeur GC est désactivée, ce paramètre limite le nombre de tas GC.</span><span class="sxs-lookup"><span data-stu-id="4c63c-166">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="4c63c-167">Pour plus d’informations, consultez les [Notes GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="4c63c-167">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="4c63c-168">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-168">Setting name</span></span> | <span data-ttu-id="4c63c-169">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-169">Values</span></span> | <span data-ttu-id="4c63c-170">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-170">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-171">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="4c63c-172">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-172">*decimal value*</span></span> | <span data-ttu-id="4c63c-173">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-173">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-174">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-174">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="4c63c-175">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-175">*hexadecimal value*</span></span> | <span data-ttu-id="4c63c-176">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-176">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-177">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-177">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-178">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="4c63c-178">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="4c63c-179">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-179">*decimal value*</span></span> | <span data-ttu-id="4c63c-180">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="4c63c-180">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="4c63c-181">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-181">Example:</span></span>

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
> <span data-ttu-id="4c63c-182">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-182">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="4c63c-183">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-183">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="4c63c-184">Par exemple, pour limiter le nombre de segments à 16, les valeurs sont 16 pour le fichier JSON et 0x10 ou 10 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4c63c-184">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="4c63c-185">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="4c63c-185">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="4c63c-186">Spécifie les processeurs exacts que les threads de garbage collector doivent utiliser.</span><span class="sxs-lookup"><span data-stu-id="4c63c-186">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="4c63c-187">Si l’affinité du processeur est désactivée en définissant `System.GC.NoAffinitize` sur `true`, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4c63c-187">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="4c63c-188">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-188">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="4c63c-189">La valeur est un masque de bits qui définit les processeurs qui sont disponibles pour le processus.</span><span class="sxs-lookup"><span data-stu-id="4c63c-189">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="4c63c-190">Par exemple, une valeur décimale de 1023 (ou une valeur hexadécimale de 0x3FF ou 3FF si vous utilisez la variable d’environnement) est 0011 1111 1111 en notation binaire.</span><span class="sxs-lookup"><span data-stu-id="4c63c-190">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="4c63c-191">Cela spécifie que les 10 premiers processeurs doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="4c63c-191">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="4c63c-192">Pour spécifier les 10 processeurs suivants, autrement dit, les processeurs 10-19, spécifiez une valeur décimale de 1047552 (ou une valeur hexadécimale de 0xFFC00 ou FFC00), qui est équivalente à une valeur binaire de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="4c63c-192">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="4c63c-193">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-193">Setting name</span></span> | <span data-ttu-id="4c63c-194">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-194">Values</span></span> | <span data-ttu-id="4c63c-195">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-195">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-196">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-196">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="4c63c-197">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-197">*decimal value*</span></span> | <span data-ttu-id="4c63c-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-198">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-199">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-199">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="4c63c-200">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-200">*hexadecimal value*</span></span> | <span data-ttu-id="4c63c-201">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-201">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-202">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-202">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-203">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="4c63c-203">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="4c63c-204">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-204">*decimal value*</span></span> | <span data-ttu-id="4c63c-205">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="4c63c-205">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="4c63c-206">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-206">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="4c63c-207">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="4c63c-207">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="4c63c-208">Spécifie la liste des processeurs à utiliser pour les threads de garbage collector.</span><span class="sxs-lookup"><span data-stu-id="4c63c-208">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="4c63c-209">Ce paramètre est similaire à `System.GC.HeapAffinitizeMask`, sauf qu’il vous permet de spécifier plus de 64 processeurs.</span><span class="sxs-lookup"><span data-stu-id="4c63c-209">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="4c63c-210">Pour les systèmes d’exploitation Windows, préfixez le numéro de processeur ou la plage avec le [groupe de processeurs](/windows/win32/procthread/processor-groups)correspondant, par exemple, « 0:1-10, 0:12, 1:50-52, 1:70 ».</span><span class="sxs-lookup"><span data-stu-id="4c63c-210">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="4c63c-211">Si l’affinité du processeur est désactivée en définissant `System.GC.NoAffinitize` sur `true`, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4c63c-211">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="4c63c-212">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-212">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="4c63c-213">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="4c63c-213">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="4c63c-214">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-214">Setting name</span></span> | <span data-ttu-id="4c63c-215">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-215">Values</span></span> | <span data-ttu-id="4c63c-216">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-216">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-217">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-217">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="4c63c-218">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-218">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="4c63c-219">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="4c63c-219">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="4c63c-220">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="4c63c-220">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="4c63c-221">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-221">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-222">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-222">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="4c63c-223">Liste séparée par des virgules des numéros de processeur ou des plages de numéros de processeur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-223">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="4c63c-224">Exemple UNIX : "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="4c63c-224">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="4c63c-225">Exemple Windows : « 0:1-10, 0:12, 1:50-52, 1:70 »</span><span class="sxs-lookup"><span data-stu-id="4c63c-225">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="4c63c-226">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-226">.NET Core 3.0</span></span> |

<span data-ttu-id="4c63c-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-227">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="4c63c-228">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="4c63c-228">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="4c63c-229">Configure si le garbage collector utilise ou non des [groupes de processeurs](/windows/win32/procthread/processor-groups) .</span><span class="sxs-lookup"><span data-stu-id="4c63c-229">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="4c63c-230">Quand un ordinateur Windows 64 bits a plusieurs groupes de PROCESSEURs, autrement dit, il y a plus de 64 processeurs, l’activation de cet élément étend garbage collection sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="4c63c-230">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="4c63c-231">Le garbage collector utilise tous les cœurs pour créer et équilibrer les tas.</span><span class="sxs-lookup"><span data-stu-id="4c63c-231">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="4c63c-232">S’applique aux garbage collection serveur sur les systèmes d’exploitation Windows 64 bits uniquement.</span><span class="sxs-lookup"><span data-stu-id="4c63c-232">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="4c63c-233">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="4c63c-233">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="4c63c-234">Pour plus d’informations, consultez [amélioration de la configuration de l’UC pour GC sur les ordinateurs avec > uc 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) sur le blog de maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="4c63c-234">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="4c63c-235">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-235">Setting name</span></span> | <span data-ttu-id="4c63c-236">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-236">Values</span></span> | <span data-ttu-id="4c63c-237">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-237">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-238">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-238">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c63c-239">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-239">N/A</span></span> | <span data-ttu-id="4c63c-240">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-240">N/A</span></span> | <span data-ttu-id="4c63c-241">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-241">N/A</span></span> |
| <span data-ttu-id="4c63c-242">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-242">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="4c63c-243">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c63c-243">`0` - disabled</span></span><br/><span data-ttu-id="4c63c-244">activé `1`</span><span class="sxs-lookup"><span data-stu-id="4c63c-244">`1` - enabled</span></span> | <span data-ttu-id="4c63c-245">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-245">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-246">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-246">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-247">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="4c63c-247">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="4c63c-248">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c63c-248">`false` - disabled</span></span><br/><span data-ttu-id="4c63c-249">activé `true`</span><span class="sxs-lookup"><span data-stu-id="4c63c-249">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="4c63c-250">Pour configurer le common language runtime (CLR) pour distribuer également des threads à partir du pool de threads sur tous les groupes de PROCESSEURs, activez l’option d' [élément Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="4c63c-250">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="4c63c-251">Pour les applications .NET Core, vous pouvez activer cette option en définissant la valeur de la variable d’environnement `COMPlus_Thread_UseAllCpuGroups` sur `1`.</span><span class="sxs-lookup"><span data-stu-id="4c63c-251">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="4c63c-252">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="4c63c-252">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="4c63c-253">Spécifie s’il faut *affinité* garbage collection threads avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="4c63c-253">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="4c63c-254">La affinité d’un thread GC signifie qu’il ne peut s’exécuter que sur son UC spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c63c-254">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="4c63c-255">Un segment de mémoire est créé pour chaque thread GC.</span><span class="sxs-lookup"><span data-stu-id="4c63c-255">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="4c63c-256">S’applique uniquement aux garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="4c63c-256">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="4c63c-257">Par défaut : affinité garbage collection threads avec processeurs (`false`).</span><span class="sxs-lookup"><span data-stu-id="4c63c-257">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="4c63c-258">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-258">Setting name</span></span> | <span data-ttu-id="4c63c-259">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-259">Values</span></span> | <span data-ttu-id="4c63c-260">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-260">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-261">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-261">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="4c63c-262">`false` affinité</span><span class="sxs-lookup"><span data-stu-id="4c63c-262">`false` - affinitize</span></span><br/><span data-ttu-id="4c63c-263">`true`-ne pas affinité</span><span class="sxs-lookup"><span data-stu-id="4c63c-263">`true` - don't affinitize</span></span> | <span data-ttu-id="4c63c-264">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-264">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-265">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-265">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="4c63c-266">`0` affinité</span><span class="sxs-lookup"><span data-stu-id="4c63c-266">`0` - affinitize</span></span><br/><span data-ttu-id="4c63c-267">`1`-ne pas affinité</span><span class="sxs-lookup"><span data-stu-id="4c63c-267">`1` - don't affinitize</span></span> | <span data-ttu-id="4c63c-268">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-268">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-269">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-269">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-270">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="4c63c-270">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="4c63c-271">`false` affinité</span><span class="sxs-lookup"><span data-stu-id="4c63c-271">`false` - affinitize</span></span><br/><span data-ttu-id="4c63c-272">`true`-ne pas affinité</span><span class="sxs-lookup"><span data-stu-id="4c63c-272">`true` - don't affinitize</span></span> | <span data-ttu-id="4c63c-273">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="4c63c-273">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="4c63c-274">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-274">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="4c63c-275">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="4c63c-275">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="4c63c-276">Spécifie la taille maximale de validation, en octets, pour le tas GC et la comptabilité du catalogue global.</span><span class="sxs-lookup"><span data-stu-id="4c63c-276">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="4c63c-277">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-277">Setting name</span></span> | <span data-ttu-id="4c63c-278">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-278">Values</span></span> | <span data-ttu-id="4c63c-279">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-279">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-280">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-280">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="4c63c-281">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-281">*decimal value*</span></span> | <span data-ttu-id="4c63c-282">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-282">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-283">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-283">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="4c63c-284">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-284">*hexadecimal value*</span></span> | <span data-ttu-id="4c63c-285">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-285">.NET Core 3.0</span></span> |

<span data-ttu-id="4c63c-286">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-286">Example:</span></span>

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
> <span data-ttu-id="4c63c-287">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-287">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="4c63c-288">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-288">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="4c63c-289">Par exemple, pour spécifier une limite inconditionnelle de segment de mémoire de 200 mebibytes (MiB), les valeurs sont 209715200 pour le fichier JSON et 0xC800000 ou C800000 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4c63c-289">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="4c63c-290">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="4c63c-290">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="4c63c-291">Spécifie l’utilisation du tas GC comme pourcentage de la mémoire totale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-291">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="4c63c-292">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-292">Setting name</span></span> | <span data-ttu-id="4c63c-293">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-293">Values</span></span> | <span data-ttu-id="4c63c-294">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-294">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-295">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-295">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="4c63c-296">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-296">*decimal value*</span></span> | <span data-ttu-id="4c63c-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="4c63c-298">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-298">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="4c63c-299">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-299">*hexadecimal value*</span></span> | <span data-ttu-id="4c63c-300">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-300">.NET Core 3.0</span></span> |

<span data-ttu-id="4c63c-301">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-301">Example:</span></span>

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
> <span data-ttu-id="4c63c-302">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-302">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="4c63c-303">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-303">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="4c63c-304">Par exemple, pour limiter l’utilisation du tas à 30%, les valeurs sont 30 pour le fichier JSON et 0x1E ou 1E pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4c63c-304">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="4c63c-305">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="4c63c-305">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="4c63c-306">Configure si les segments qui doivent être supprimés sont placés dans une liste d’attente pour une utilisation ultérieure ou sont remis dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4c63c-306">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="4c63c-307">Valeur par défaut : relâcher les segments sur le système d’exploitation (`false`).</span><span class="sxs-lookup"><span data-stu-id="4c63c-307">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="4c63c-308">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-308">Setting name</span></span> | <span data-ttu-id="4c63c-309">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-309">Values</span></span> | <span data-ttu-id="4c63c-310">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-310">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-311">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-311">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="4c63c-312">`false`-version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="4c63c-312">`false` - release to OS</span></span><br/><span data-ttu-id="4c63c-313">`true`-mettre en veille</span><span class="sxs-lookup"><span data-stu-id="4c63c-313">`true` - put on standby</span></span>| <span data-ttu-id="4c63c-314">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-314">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-315">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-315">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="4c63c-316">`0`-version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="4c63c-316">`0` - release to OS</span></span><br/><span data-ttu-id="4c63c-317">`1`-mettre en veille</span><span class="sxs-lookup"><span data-stu-id="4c63c-317">`1` - put on standby</span></span> | <span data-ttu-id="4c63c-318">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-318">.NET Core 1.0</span></span> |

<span data-ttu-id="4c63c-319">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-319">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a><span data-ttu-id="4c63c-320">Grandes pages</span><span class="sxs-lookup"><span data-stu-id="4c63c-320">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="4c63c-321">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="4c63c-321">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="4c63c-322">Spécifie si les pages de grande taille doivent être utilisées lorsqu’une limite matérielle de tas est définie.</span><span class="sxs-lookup"><span data-stu-id="4c63c-322">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="4c63c-323">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="4c63c-323">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="4c63c-324">Il s’agit d’un paramètre expérimental.</span><span class="sxs-lookup"><span data-stu-id="4c63c-324">This is an experimental setting.</span></span>

| | <span data-ttu-id="4c63c-325">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-325">Setting name</span></span> | <span data-ttu-id="4c63c-326">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-326">Values</span></span> | <span data-ttu-id="4c63c-327">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-327">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-328">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-328">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c63c-329">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-329">N/A</span></span> | <span data-ttu-id="4c63c-330">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-330">N/A</span></span> | <span data-ttu-id="4c63c-331">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-331">N/A</span></span> |
| <span data-ttu-id="4c63c-332">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-332">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="4c63c-333">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c63c-333">`0` - disabled</span></span><br/><span data-ttu-id="4c63c-334">activé `1`</span><span class="sxs-lookup"><span data-stu-id="4c63c-334">`1` - enabled</span></span> | <span data-ttu-id="4c63c-335">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-335">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="4c63c-336">Objets volumineux</span><span class="sxs-lookup"><span data-stu-id="4c63c-336">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="4c63c-337">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="4c63c-337">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="4c63c-338">Configure la prise en charge du garbage collector sur les plateformes 64 bits pour les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="4c63c-338">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="4c63c-339">Valeur par défaut : activé (`1`).</span><span class="sxs-lookup"><span data-stu-id="4c63c-339">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="4c63c-340">Cette option peut devenir obsolète dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="4c63c-340">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="4c63c-341">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-341">Setting name</span></span> | <span data-ttu-id="4c63c-342">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-342">Values</span></span> | <span data-ttu-id="4c63c-343">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-343">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-344">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-344">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c63c-345">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-345">N/A</span></span> | <span data-ttu-id="4c63c-346">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-346">N/A</span></span> | <span data-ttu-id="4c63c-347">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-347">N/A</span></span> |
| <span data-ttu-id="4c63c-348">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-348">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="4c63c-349">activé `1`</span><span class="sxs-lookup"><span data-stu-id="4c63c-349">`1` - enabled</span></span><br/> <span data-ttu-id="4c63c-350">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c63c-350">`0` - disabled</span></span> | <span data-ttu-id="4c63c-351">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-351">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-352">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-352">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-353">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="4c63c-353">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="4c63c-354">activé `1`</span><span class="sxs-lookup"><span data-stu-id="4c63c-354">`1` - enabled</span></span><br/> <span data-ttu-id="4c63c-355">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c63c-355">`0` - disabled</span></span> | <span data-ttu-id="4c63c-356">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="4c63c-356">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="4c63c-357">Seuil du tas des objets volumineux</span><span class="sxs-lookup"><span data-stu-id="4c63c-357">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="4c63c-358">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="4c63c-358">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="4c63c-359">Spécifie la taille du seuil, en octets, qui fait que les objets sont placés sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="4c63c-359">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="4c63c-360">Le seuil par défaut est de 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="4c63c-360">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="4c63c-361">La valeur que vous spécifiez doit être supérieure au seuil par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c63c-361">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="4c63c-362">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-362">Setting name</span></span> | <span data-ttu-id="4c63c-363">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-363">Values</span></span> | <span data-ttu-id="4c63c-364">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-364">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-365">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-365">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="4c63c-366">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-366">*decimal value*</span></span> | <span data-ttu-id="4c63c-367">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-367">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-368">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-368">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="4c63c-369">*valeur hexadécimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-369">*hexadecimal value*</span></span> | <span data-ttu-id="4c63c-370">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-370">.NET Core 1.0</span></span> |
| <span data-ttu-id="4c63c-371">**App. config pour .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="4c63c-371">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="4c63c-372">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="4c63c-372">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="4c63c-373">*valeur décimale*</span><span class="sxs-lookup"><span data-stu-id="4c63c-373">*decimal value*</span></span> | <span data-ttu-id="4c63c-374">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="4c63c-374">.NET Framework 4.8</span></span> |

<span data-ttu-id="4c63c-375">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4c63c-375">Example:</span></span>

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
> <span data-ttu-id="4c63c-376">Si vous définissez l’option dans *runtimeconfig. JSON*, spécifiez une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-376">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="4c63c-377">Si vous définissez l’option en tant que variable d’environnement, spécifiez une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="4c63c-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="4c63c-378">Par exemple, pour définir une taille de seuil de 120 000 octets, les valeurs sont 120000 pour le fichier JSON et 0x1D4C0 ou 1D4C0 pour la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="4c63c-378">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="4c63c-379">GC autonome</span><span class="sxs-lookup"><span data-stu-id="4c63c-379">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="4c63c-380">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="4c63c-380">COMPlus_GCName</span></span>

- <span data-ttu-id="4c63c-381">Spécifie un chemin d’accès à la bibliothèque contenant le garbage collector que le runtime envisage de charger.</span><span class="sxs-lookup"><span data-stu-id="4c63c-381">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="4c63c-382">Pour plus d’informations, consultez [conception de chargeur gc autonome](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="4c63c-382">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="4c63c-383">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c63c-383">Setting name</span></span> | <span data-ttu-id="4c63c-384">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c63c-384">Values</span></span> | <span data-ttu-id="4c63c-385">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4c63c-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4c63c-386">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c63c-386">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c63c-387">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-387">N/A</span></span> | <span data-ttu-id="4c63c-388">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-388">N/A</span></span> | <span data-ttu-id="4c63c-389">Non applicable</span><span class="sxs-lookup"><span data-stu-id="4c63c-389">N/A</span></span> |
| <span data-ttu-id="4c63c-390">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="4c63c-390">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="4c63c-391">*string_path*</span><span class="sxs-lookup"><span data-stu-id="4c63c-391">*string_path*</span></span> | <span data-ttu-id="4c63c-392">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4c63c-392">.NET Core 2.0</span></span> |
