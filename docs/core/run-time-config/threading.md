---
title: Paramètres de configuration de thread
description: En savoir plus sur les paramètres d’exécution qui configurent les threads pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733433"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="e4d3b-103">Options de configuration au moment de l’exécution pour le Threading</span><span class="sxs-lookup"><span data-stu-id="e4d3b-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="e4d3b-104">Groupes de PROCESSEURs</span><span class="sxs-lookup"><span data-stu-id="e4d3b-104">CPU groups</span></span>

- <span data-ttu-id="e4d3b-105">Configure si les threads sont automatiquement distribués entre les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="e4d3b-106">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="e4d3b-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="e4d3b-107">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="e4d3b-107">Setting name</span></span> | <span data-ttu-id="e4d3b-108">Valeurs</span><span class="sxs-lookup"><span data-stu-id="e4d3b-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e4d3b-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="e4d3b-110">Non applicable</span><span class="sxs-lookup"><span data-stu-id="e4d3b-110">N/A</span></span> | <span data-ttu-id="e4d3b-111">Non applicable</span><span class="sxs-lookup"><span data-stu-id="e4d3b-111">N/A</span></span> |
| <span data-ttu-id="e4d3b-112">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="e4d3b-113">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="e4d3b-113">`0` - disabled</span></span><br/><span data-ttu-id="e4d3b-114">activé `1`</span><span class="sxs-lookup"><span data-stu-id="e4d3b-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="e4d3b-115">Nombre minimal de threads</span><span class="sxs-lookup"><span data-stu-id="e4d3b-115">Minimum threads</span></span>

- <span data-ttu-id="e4d3b-116">Spécifie le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="e4d3b-117">Correspond à la méthode <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="e4d3b-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="e4d3b-118">Setting name</span></span> | <span data-ttu-id="e4d3b-119">Valeurs</span><span class="sxs-lookup"><span data-stu-id="e4d3b-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e4d3b-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="e4d3b-121">Entier qui représente le nombre minimal de threads.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="e4d3b-122">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="e4d3b-123">Entier qui représente le nombre minimal de threads.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="e4d3b-124">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-124">**Environment variable**</span></span> | <span data-ttu-id="e4d3b-125">Non applicable</span><span class="sxs-lookup"><span data-stu-id="e4d3b-125">N/A</span></span> | <span data-ttu-id="e4d3b-126">Non applicable</span><span class="sxs-lookup"><span data-stu-id="e4d3b-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="e4d3b-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="e4d3b-127">Examples</span></span>

<span data-ttu-id="e4d3b-128">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="e4d3b-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="e4d3b-129">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="e4d3b-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="e4d3b-130">Nombre maximal de threads</span><span class="sxs-lookup"><span data-stu-id="e4d3b-130">Maximum threads</span></span>

- <span data-ttu-id="e4d3b-131">Spécifie le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-131">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="e4d3b-132">Correspond à la méthode <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="e4d3b-133">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="e4d3b-133">Setting name</span></span> | <span data-ttu-id="e4d3b-134">Valeurs</span><span class="sxs-lookup"><span data-stu-id="e4d3b-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e4d3b-135">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="e4d3b-136">Entier qui représente le nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="e4d3b-137">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="e4d3b-138">Entier qui représente le nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="e4d3b-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="e4d3b-139">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="e4d3b-139">**Environment variable**</span></span> | <span data-ttu-id="e4d3b-140">Non applicable</span><span class="sxs-lookup"><span data-stu-id="e4d3b-140">N/A</span></span> | <span data-ttu-id="e4d3b-141">Non applicable</span><span class="sxs-lookup"><span data-stu-id="e4d3b-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="e4d3b-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="e4d3b-142">Examples</span></span>

<span data-ttu-id="e4d3b-143">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="e4d3b-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="e4d3b-144">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="e4d3b-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
