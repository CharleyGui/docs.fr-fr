---
title: Débogage des paramètres de configuration du profilage
description: En savoir plus sur les paramètres d’exécution qui configurent le débogage et le profilage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761991"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="4c82e-103">Options de configuration au moment de l’exécution pour le débogage et le profilage</span><span class="sxs-lookup"><span data-stu-id="4c82e-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="4c82e-104">Activation des diagnostics</span><span class="sxs-lookup"><span data-stu-id="4c82e-104">Enable diagnostics</span></span>

- <span data-ttu-id="4c82e-105">Configure si le débogueur, le profileur et les diagnostics EventPipe sont activés ou désactivés.</span><span class="sxs-lookup"><span data-stu-id="4c82e-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="4c82e-106">Si vous omettez ce paramètre, les diagnostics sont activés.</span><span class="sxs-lookup"><span data-stu-id="4c82e-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="4c82e-107">Cela équivaut à définir la valeur sur `1` .</span><span class="sxs-lookup"><span data-stu-id="4c82e-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="4c82e-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c82e-108">Setting name</span></span> | <span data-ttu-id="4c82e-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c82e-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4c82e-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c82e-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c82e-111">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-111">N/A</span></span> | <span data-ttu-id="4c82e-112">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-112">N/A</span></span> |
| <span data-ttu-id="4c82e-113">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="4c82e-114">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="4c82e-114">`1` - enabled</span></span><br/><span data-ttu-id="4c82e-115">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c82e-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="4c82e-116">Activer le profilage</span><span class="sxs-lookup"><span data-stu-id="4c82e-116">Enable profiling</span></span>

- <span data-ttu-id="4c82e-117">Configure si le profilage est activé pour le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c82e-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="4c82e-118">Si vous omettez ce paramètre, le profilage est désactivé.</span><span class="sxs-lookup"><span data-stu-id="4c82e-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="4c82e-119">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="4c82e-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="4c82e-120">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c82e-120">Setting name</span></span> | <span data-ttu-id="4c82e-121">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c82e-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4c82e-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c82e-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c82e-123">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-123">N/A</span></span> | <span data-ttu-id="4c82e-124">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-124">N/A</span></span> |
| <span data-ttu-id="4c82e-125">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="4c82e-126">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c82e-126">`0` - disabled</span></span><br/><span data-ttu-id="4c82e-127">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="4c82e-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="4c82e-128">GUID du profileur</span><span class="sxs-lookup"><span data-stu-id="4c82e-128">Profiler GUID</span></span>

- <span data-ttu-id="4c82e-129">Spécifie le GUID du profileur à charger dans le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c82e-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="4c82e-130">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c82e-130">Setting name</span></span> | <span data-ttu-id="4c82e-131">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c82e-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4c82e-132">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c82e-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c82e-133">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-133">N/A</span></span> | <span data-ttu-id="4c82e-134">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-134">N/A</span></span> |
| <span data-ttu-id="4c82e-135">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="4c82e-136">*GUID de chaîne*</span><span class="sxs-lookup"><span data-stu-id="4c82e-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="4c82e-137">Emplacement du profileur</span><span class="sxs-lookup"><span data-stu-id="4c82e-137">Profiler location</span></span>

- <span data-ttu-id="4c82e-138">Spécifie le chemin d’accès à la DLL du profileur à charger dans le processus en cours d’exécution (processus 32 bits ou 64 bits).</span><span class="sxs-lookup"><span data-stu-id="4c82e-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="4c82e-139">Si plusieurs variables sont définies, les variables spécifiques au nombre de bits sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="4c82e-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="4c82e-140">Ils spécifient le nombre de bits du profileur à charger.</span><span class="sxs-lookup"><span data-stu-id="4c82e-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="4c82e-141">Pour plus d’informations, consultez [recherche de la bibliothèque du profileur](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="4c82e-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="4c82e-142">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c82e-142">Setting name</span></span> | <span data-ttu-id="4c82e-143">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c82e-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4c82e-144">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="4c82e-145">*chaîne-chemin d’accès*</span><span class="sxs-lookup"><span data-stu-id="4c82e-145">*string-path*</span></span> |
| <span data-ttu-id="4c82e-146">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="4c82e-147">*chaîne-chemin d’accès*</span><span class="sxs-lookup"><span data-stu-id="4c82e-147">*string-path*</span></span> |
| <span data-ttu-id="4c82e-148">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="4c82e-149">*chaîne-chemin d’accès*</span><span class="sxs-lookup"><span data-stu-id="4c82e-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="4c82e-150">Écrire le mappage des performances</span><span class="sxs-lookup"><span data-stu-id="4c82e-150">Write perf map</span></span>

- <span data-ttu-id="4c82e-151">Active ou désactive l’écriture de */tmp/perf-$PID. map* sur les systèmes Linux.</span><span class="sxs-lookup"><span data-stu-id="4c82e-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="4c82e-152">Si vous omettez ce paramètre, l’écriture de la carte de performances est désactivée.</span><span class="sxs-lookup"><span data-stu-id="4c82e-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="4c82e-153">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="4c82e-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="4c82e-154">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c82e-154">Setting name</span></span> | <span data-ttu-id="4c82e-155">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c82e-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4c82e-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c82e-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c82e-157">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-157">N/A</span></span> | <span data-ttu-id="4c82e-158">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-158">N/A</span></span> |
| <span data-ttu-id="4c82e-159">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="4c82e-160">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c82e-160">`0` - disabled</span></span><br/><span data-ttu-id="4c82e-161">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="4c82e-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="4c82e-162">Marqueurs de journaux de performances</span><span class="sxs-lookup"><span data-stu-id="4c82e-162">Perf log markers</span></span>

- <span data-ttu-id="4c82e-163">Active ou désactive l’acceptation et l’ignorance du signal spécifié en tant que marqueur dans les journaux de performances.</span><span class="sxs-lookup"><span data-stu-id="4c82e-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="4c82e-164">Si vous omettez ce paramètre, le signal spécifié n’est pas ignoré.</span><span class="sxs-lookup"><span data-stu-id="4c82e-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="4c82e-165">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="4c82e-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="4c82e-166">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4c82e-166">Setting name</span></span> | <span data-ttu-id="4c82e-167">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4c82e-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4c82e-168">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4c82e-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="4c82e-169">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-169">N/A</span></span> | <span data-ttu-id="4c82e-170">N/A</span><span class="sxs-lookup"><span data-stu-id="4c82e-170">N/A</span></span> |
| <span data-ttu-id="4c82e-171">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4c82e-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="4c82e-172">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="4c82e-172">`0` - disabled</span></span><br/><span data-ttu-id="4c82e-173">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="4c82e-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="4c82e-174">Ce paramètre est ignoré si [COMPlus_PerfMapEnabled](#write-perf-map) est omis ou défini sur `0` (autrement dit, désactivé).</span><span class="sxs-lookup"><span data-stu-id="4c82e-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
