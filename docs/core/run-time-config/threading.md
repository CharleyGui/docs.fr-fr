---
title: Paramètres de configuration de thread
description: En savoir plus sur les paramètres d’exécution qui configurent les threads pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761926"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="316bb-103">Options de configuration au moment de l’exécution pour le Threading</span><span class="sxs-lookup"><span data-stu-id="316bb-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="316bb-104">Groupes de PROCESSEURs</span><span class="sxs-lookup"><span data-stu-id="316bb-104">CPU groups</span></span>

- <span data-ttu-id="316bb-105">Configure si les threads sont automatiquement distribués entre les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="316bb-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="316bb-106">Si vous omettez ce paramètre, les threads ne sont pas distribués entre les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="316bb-106">If you omit this setting, threads are not distributed across CPU groups.</span></span> <span data-ttu-id="316bb-107">Cela équivaut à définir la valeur sur `0` .</span><span class="sxs-lookup"><span data-stu-id="316bb-107">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="316bb-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="316bb-108">Setting name</span></span> | <span data-ttu-id="316bb-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="316bb-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="316bb-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="316bb-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="316bb-111">N/A</span><span class="sxs-lookup"><span data-stu-id="316bb-111">N/A</span></span> | <span data-ttu-id="316bb-112">N/A</span><span class="sxs-lookup"><span data-stu-id="316bb-112">N/A</span></span> |
| <span data-ttu-id="316bb-113">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="316bb-113">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="316bb-114">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="316bb-114">`0` - disabled</span></span><br/><span data-ttu-id="316bb-115">`1`-activé</span><span class="sxs-lookup"><span data-stu-id="316bb-115">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="316bb-116">Nombre minimal de threads</span><span class="sxs-lookup"><span data-stu-id="316bb-116">Minimum threads</span></span>

- <span data-ttu-id="316bb-117">Spécifie le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="316bb-117">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="316bb-118">Correspond à la <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="316bb-118">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="316bb-119">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="316bb-119">Setting name</span></span> | <span data-ttu-id="316bb-120">Valeurs</span><span class="sxs-lookup"><span data-stu-id="316bb-120">Values</span></span> |
| - | - | - |
| <span data-ttu-id="316bb-121">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="316bb-121">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="316bb-122">Entier qui représente le nombre minimal de threads.</span><span class="sxs-lookup"><span data-stu-id="316bb-122">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="316bb-123">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="316bb-123">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="316bb-124">Entier qui représente le nombre minimal de threads.</span><span class="sxs-lookup"><span data-stu-id="316bb-124">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="316bb-125">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="316bb-125">**Environment variable**</span></span> | <span data-ttu-id="316bb-126">N/A</span><span class="sxs-lookup"><span data-stu-id="316bb-126">N/A</span></span> | <span data-ttu-id="316bb-127">N/A</span><span class="sxs-lookup"><span data-stu-id="316bb-127">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="316bb-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="316bb-128">Examples</span></span>

<span data-ttu-id="316bb-129">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="316bb-129">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="316bb-130">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="316bb-130">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="316bb-131">Nombre maximal de threads</span><span class="sxs-lookup"><span data-stu-id="316bb-131">Maximum threads</span></span>

- <span data-ttu-id="316bb-132">Spécifie le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="316bb-132">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="316bb-133">Correspond à la <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="316bb-133">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="316bb-134">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="316bb-134">Setting name</span></span> | <span data-ttu-id="316bb-135">Valeurs</span><span class="sxs-lookup"><span data-stu-id="316bb-135">Values</span></span> |
| - | - | - |
| <span data-ttu-id="316bb-136">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="316bb-136">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="316bb-137">Entier qui représente le nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="316bb-137">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="316bb-138">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="316bb-138">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="316bb-139">Entier qui représente le nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="316bb-139">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="316bb-140">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="316bb-140">**Environment variable**</span></span> | <span data-ttu-id="316bb-141">N/A</span><span class="sxs-lookup"><span data-stu-id="316bb-141">N/A</span></span> | <span data-ttu-id="316bb-142">N/A</span><span class="sxs-lookup"><span data-stu-id="316bb-142">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="316bb-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="316bb-143">Examples</span></span>

<span data-ttu-id="316bb-144">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="316bb-144">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="316bb-145">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="316bb-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
