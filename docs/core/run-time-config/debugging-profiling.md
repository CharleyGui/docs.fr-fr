---
title: Réglages de profilage de débogage
description: Renseignez-vous sur les paramètres de course qui configurent le débogage et le profilage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802798"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="7b6e1-103">Options de configuration en temps d’exécution pour le débogage et le profilage</span><span class="sxs-lookup"><span data-stu-id="7b6e1-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="7b6e1-104">Activation des diagnostics</span><span class="sxs-lookup"><span data-stu-id="7b6e1-104">Enable diagnostics</span></span>

- <span data-ttu-id="7b6e1-105">Configure si le débbuggeur, le profileur et les diagnostics EventPipe sont activés ou désactivés.</span><span class="sxs-lookup"><span data-stu-id="7b6e1-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="7b6e1-106">Défaut: Activé`1`( ).</span><span class="sxs-lookup"><span data-stu-id="7b6e1-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="7b6e1-107">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="7b6e1-107">Setting name</span></span> | <span data-ttu-id="7b6e1-108">Valeurs</span><span class="sxs-lookup"><span data-stu-id="7b6e1-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b6e1-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="7b6e1-110">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-110">N/A</span></span> | <span data-ttu-id="7b6e1-111">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-111">N/A</span></span> |
| <span data-ttu-id="7b6e1-112">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="7b6e1-113">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-113">`1` - enabled</span></span><br/><span data-ttu-id="7b6e1-114">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="7b6e1-115">Activer le profilage</span><span class="sxs-lookup"><span data-stu-id="7b6e1-115">Enable profiling</span></span>

- <span data-ttu-id="7b6e1-116">Configure si le profilage est activé pour le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7b6e1-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="7b6e1-117">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="7b6e1-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7b6e1-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="7b6e1-118">Setting name</span></span> | <span data-ttu-id="7b6e1-119">Valeurs</span><span class="sxs-lookup"><span data-stu-id="7b6e1-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b6e1-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="7b6e1-121">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-121">N/A</span></span> | <span data-ttu-id="7b6e1-122">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-122">N/A</span></span> |
| <span data-ttu-id="7b6e1-123">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="7b6e1-124">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-124">`0` - disabled</span></span><br/><span data-ttu-id="7b6e1-125">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="7b6e1-126">Profiler GUID</span><span class="sxs-lookup"><span data-stu-id="7b6e1-126">Profiler GUID</span></span>

- <span data-ttu-id="7b6e1-127">Spécifie le GUID du profileur à charger dans le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7b6e1-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="7b6e1-128">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="7b6e1-128">Setting name</span></span> | <span data-ttu-id="7b6e1-129">Valeurs</span><span class="sxs-lookup"><span data-stu-id="7b6e1-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b6e1-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="7b6e1-131">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-131">N/A</span></span> | <span data-ttu-id="7b6e1-132">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-132">N/A</span></span> |
| <span data-ttu-id="7b6e1-133">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="7b6e1-134">*chaîne-guid*</span><span class="sxs-lookup"><span data-stu-id="7b6e1-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="7b6e1-135">Emplacement profileur</span><span class="sxs-lookup"><span data-stu-id="7b6e1-135">Profiler location</span></span>

- <span data-ttu-id="7b6e1-136">Spécifie le chemin vers le profileur DLL pour charger dans le processus en cours d’exécution (ou 32 bits ou 64 bits processus).</span><span class="sxs-lookup"><span data-stu-id="7b6e1-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="7b6e1-137">Si plus d’une variable est réglée, les variables spécifiques à la bits ont préséance.</span><span class="sxs-lookup"><span data-stu-id="7b6e1-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="7b6e1-138">Ils spécifient quelle bitté de profiler à charger.</span><span class="sxs-lookup"><span data-stu-id="7b6e1-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="7b6e1-139">Pour plus d’informations, voir [Trouver la bibliothèque de profileur](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="7b6e1-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="7b6e1-140">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="7b6e1-140">Setting name</span></span> | <span data-ttu-id="7b6e1-141">Valeurs</span><span class="sxs-lookup"><span data-stu-id="7b6e1-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b6e1-142">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="7b6e1-143">*corde-chemin*</span><span class="sxs-lookup"><span data-stu-id="7b6e1-143">*string-path*</span></span> |
| <span data-ttu-id="7b6e1-144">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="7b6e1-145">*corde-chemin*</span><span class="sxs-lookup"><span data-stu-id="7b6e1-145">*string-path*</span></span> |
| <span data-ttu-id="7b6e1-146">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="7b6e1-147">*corde-chemin*</span><span class="sxs-lookup"><span data-stu-id="7b6e1-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="7b6e1-148">Écrire la carte de perf</span><span class="sxs-lookup"><span data-stu-id="7b6e1-148">Write perf map</span></span>

- <span data-ttu-id="7b6e1-149">Permet ou désactive l’écriture */tmp/perf-$pid.map* sur les systèmes Linux.</span><span class="sxs-lookup"><span data-stu-id="7b6e1-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="7b6e1-150">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="7b6e1-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7b6e1-151">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="7b6e1-151">Setting name</span></span> | <span data-ttu-id="7b6e1-152">Valeurs</span><span class="sxs-lookup"><span data-stu-id="7b6e1-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b6e1-153">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="7b6e1-154">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-154">N/A</span></span> | <span data-ttu-id="7b6e1-155">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-155">N/A</span></span> |
| <span data-ttu-id="7b6e1-156">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="7b6e1-157">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-157">`0` - disabled</span></span><br/><span data-ttu-id="7b6e1-158">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="7b6e1-159">Marqueurs de journal Perf</span><span class="sxs-lookup"><span data-stu-id="7b6e1-159">Perf log markers</span></span>

- <span data-ttu-id="7b6e1-160">Quand `COMPlus_PerfMapEnabled` est `1`réglé à , permet ou désactive le signal spécifié d’être accepté et ignoré comme un marqueur dans les journaux perf.</span><span class="sxs-lookup"><span data-stu-id="7b6e1-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="7b6e1-161">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="7b6e1-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7b6e1-162">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="7b6e1-162">Setting name</span></span> | <span data-ttu-id="7b6e1-163">Valeurs</span><span class="sxs-lookup"><span data-stu-id="7b6e1-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b6e1-164">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="7b6e1-165">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-165">N/A</span></span> | <span data-ttu-id="7b6e1-166">N/A</span><span class="sxs-lookup"><span data-stu-id="7b6e1-166">N/A</span></span> |
| <span data-ttu-id="7b6e1-167">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="7b6e1-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="7b6e1-168">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-168">`0` - disabled</span></span><br/><span data-ttu-id="7b6e1-169">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="7b6e1-169">`1` - enabled</span></span> |
