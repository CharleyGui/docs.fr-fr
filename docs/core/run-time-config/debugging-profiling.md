---
title: Débogage des paramètres de configuration du profilage
description: En savoir plus sur les paramètres d’exécution qui configurent le débogage et le profilage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802798"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="04878-103">Options de configuration au moment de l’exécution pour le débogage et le profilage</span><span class="sxs-lookup"><span data-stu-id="04878-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="04878-104">Activer le diagnostic</span><span class="sxs-lookup"><span data-stu-id="04878-104">Enable diagnostics</span></span>

- <span data-ttu-id="04878-105">Configure si le débogueur, le profileur et les diagnostics EventPipe sont activés ou désactivés.</span><span class="sxs-lookup"><span data-stu-id="04878-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="04878-106">Valeur par défaut : activé (`1`).</span><span class="sxs-lookup"><span data-stu-id="04878-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="04878-107">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="04878-107">Setting name</span></span> | <span data-ttu-id="04878-108">Valeurs</span><span class="sxs-lookup"><span data-stu-id="04878-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04878-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="04878-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="04878-110">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-110">N/A</span></span> | <span data-ttu-id="04878-111">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-111">N/A</span></span> |
| <span data-ttu-id="04878-112">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="04878-113">activé `1`</span><span class="sxs-lookup"><span data-stu-id="04878-113">`1` - enabled</span></span><br/><span data-ttu-id="04878-114">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="04878-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="04878-115">Activer le profilage</span><span class="sxs-lookup"><span data-stu-id="04878-115">Enable profiling</span></span>

- <span data-ttu-id="04878-116">Configure si le profilage est activé pour le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="04878-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="04878-117">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="04878-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="04878-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="04878-118">Setting name</span></span> | <span data-ttu-id="04878-119">Valeurs</span><span class="sxs-lookup"><span data-stu-id="04878-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04878-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="04878-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="04878-121">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-121">N/A</span></span> | <span data-ttu-id="04878-122">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-122">N/A</span></span> |
| <span data-ttu-id="04878-123">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="04878-124">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="04878-124">`0` - disabled</span></span><br/><span data-ttu-id="04878-125">activé `1`</span><span class="sxs-lookup"><span data-stu-id="04878-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="04878-126">GUID du profileur</span><span class="sxs-lookup"><span data-stu-id="04878-126">Profiler GUID</span></span>

- <span data-ttu-id="04878-127">Spécifie le GUID du profileur à charger dans le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="04878-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="04878-128">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="04878-128">Setting name</span></span> | <span data-ttu-id="04878-129">Valeurs</span><span class="sxs-lookup"><span data-stu-id="04878-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04878-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="04878-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="04878-131">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-131">N/A</span></span> | <span data-ttu-id="04878-132">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-132">N/A</span></span> |
| <span data-ttu-id="04878-133">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="04878-134">*GUID de chaîne*</span><span class="sxs-lookup"><span data-stu-id="04878-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="04878-135">Emplacement du profileur</span><span class="sxs-lookup"><span data-stu-id="04878-135">Profiler location</span></span>

- <span data-ttu-id="04878-136">Spécifie le chemin d’accès à la DLL du profileur à charger dans le processus en cours d’exécution (processus 32 bits ou 64 bits).</span><span class="sxs-lookup"><span data-stu-id="04878-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="04878-137">Si plusieurs variables sont définies, les variables spécifiques au nombre de bits sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="04878-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="04878-138">Ils spécifient le nombre de bits du profileur à charger.</span><span class="sxs-lookup"><span data-stu-id="04878-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="04878-139">Pour plus d’informations, consultez [recherche de la bibliothèque du profileur](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="04878-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="04878-140">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="04878-140">Setting name</span></span> | <span data-ttu-id="04878-141">Valeurs</span><span class="sxs-lookup"><span data-stu-id="04878-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04878-142">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="04878-143">*chaîne-chemin d’accès*</span><span class="sxs-lookup"><span data-stu-id="04878-143">*string-path*</span></span> |
| <span data-ttu-id="04878-144">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="04878-145">*chaîne-chemin d’accès*</span><span class="sxs-lookup"><span data-stu-id="04878-145">*string-path*</span></span> |
| <span data-ttu-id="04878-146">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="04878-147">*chaîne-chemin d’accès*</span><span class="sxs-lookup"><span data-stu-id="04878-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="04878-148">Écrire le mappage des performances</span><span class="sxs-lookup"><span data-stu-id="04878-148">Write perf map</span></span>

- <span data-ttu-id="04878-149">Active ou désactive l’écriture de */tmp/perf-$PID. map* sur les systèmes Linux.</span><span class="sxs-lookup"><span data-stu-id="04878-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="04878-150">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="04878-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="04878-151">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="04878-151">Setting name</span></span> | <span data-ttu-id="04878-152">Valeurs</span><span class="sxs-lookup"><span data-stu-id="04878-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04878-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="04878-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="04878-154">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-154">N/A</span></span> | <span data-ttu-id="04878-155">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-155">N/A</span></span> |
| <span data-ttu-id="04878-156">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="04878-157">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="04878-157">`0` - disabled</span></span><br/><span data-ttu-id="04878-158">activé `1`</span><span class="sxs-lookup"><span data-stu-id="04878-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="04878-159">Marqueurs de journaux de performances</span><span class="sxs-lookup"><span data-stu-id="04878-159">Perf log markers</span></span>

- <span data-ttu-id="04878-160">Lorsque `COMPlus_PerfMapEnabled` a la valeur `1`, active ou désactive l’acceptation et l’ignorance du signal spécifié en tant que marqueur dans les journaux de performances.</span><span class="sxs-lookup"><span data-stu-id="04878-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="04878-161">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="04878-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="04878-162">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="04878-162">Setting name</span></span> | <span data-ttu-id="04878-163">Valeurs</span><span class="sxs-lookup"><span data-stu-id="04878-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="04878-164">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="04878-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="04878-165">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-165">N/A</span></span> | <span data-ttu-id="04878-166">Non applicable</span><span class="sxs-lookup"><span data-stu-id="04878-166">N/A</span></span> |
| <span data-ttu-id="04878-167">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="04878-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="04878-168">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="04878-168">`0` - disabled</span></span><br/><span data-ttu-id="04878-169">activé `1`</span><span class="sxs-lookup"><span data-stu-id="04878-169">`1` - enabled</span></span> |
