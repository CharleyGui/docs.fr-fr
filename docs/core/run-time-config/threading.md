---
title: Réglages de config de threading
description: Découvrez les paramètres en temps d’exécution qui configurent le threading pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789851"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="9e7b9-103">Options de configuration en temps d’exécution pour le threading</span><span class="sxs-lookup"><span data-stu-id="9e7b9-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="9e7b9-104">Groupes CPU</span><span class="sxs-lookup"><span data-stu-id="9e7b9-104">CPU groups</span></span>

- <span data-ttu-id="9e7b9-105">Configure si les threads sont automatiquement distribués entre les groupes CPU.</span><span class="sxs-lookup"><span data-stu-id="9e7b9-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="9e7b9-106">Défaut: Désactivé`0`( ).</span><span class="sxs-lookup"><span data-stu-id="9e7b9-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="9e7b9-107">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="9e7b9-107">Setting name</span></span> | <span data-ttu-id="9e7b9-108">Valeurs</span><span class="sxs-lookup"><span data-stu-id="9e7b9-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="9e7b9-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="9e7b9-110">N/A</span><span class="sxs-lookup"><span data-stu-id="9e7b9-110">N/A</span></span> | <span data-ttu-id="9e7b9-111">N/A</span><span class="sxs-lookup"><span data-stu-id="9e7b9-111">N/A</span></span> |
| <span data-ttu-id="9e7b9-112">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="9e7b9-113">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="9e7b9-113">`0` - disabled</span></span><br/><span data-ttu-id="9e7b9-114">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="9e7b9-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="9e7b9-115">Fils minimums</span><span class="sxs-lookup"><span data-stu-id="9e7b9-115">Minimum threads</span></span>

- <span data-ttu-id="9e7b9-116">Spécifie le nombre minimum de threads pour le pool de threads du travailleur.</span><span class="sxs-lookup"><span data-stu-id="9e7b9-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="9e7b9-117">Correspond à <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> la méthode.</span><span class="sxs-lookup"><span data-stu-id="9e7b9-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="9e7b9-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="9e7b9-118">Setting name</span></span> | <span data-ttu-id="9e7b9-119">Valeurs</span><span class="sxs-lookup"><span data-stu-id="9e7b9-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="9e7b9-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="9e7b9-121">Un intégrant qui représente le nombre minimum de fils</span><span class="sxs-lookup"><span data-stu-id="9e7b9-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="9e7b9-122">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="9e7b9-123">Un intégrant qui représente le nombre minimum de fils</span><span class="sxs-lookup"><span data-stu-id="9e7b9-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="9e7b9-124">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-124">**Environment variable**</span></span> | <span data-ttu-id="9e7b9-125">N/A</span><span class="sxs-lookup"><span data-stu-id="9e7b9-125">N/A</span></span> | <span data-ttu-id="9e7b9-126">N/A</span><span class="sxs-lookup"><span data-stu-id="9e7b9-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="9e7b9-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="9e7b9-127">Examples</span></span>

<span data-ttu-id="9e7b9-128">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="9e7b9-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="9e7b9-129">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="9e7b9-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="9e7b9-130">Fils maximums</span><span class="sxs-lookup"><span data-stu-id="9e7b9-130">Maximum threads</span></span>

- <span data-ttu-id="9e7b9-131">Spécifie le nombre maximum de threads pour le pool de thread du travailleur.</span><span class="sxs-lookup"><span data-stu-id="9e7b9-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="9e7b9-132">Correspond à <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> la méthode.</span><span class="sxs-lookup"><span data-stu-id="9e7b9-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="9e7b9-133">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="9e7b9-133">Setting name</span></span> | <span data-ttu-id="9e7b9-134">Valeurs</span><span class="sxs-lookup"><span data-stu-id="9e7b9-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="9e7b9-135">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="9e7b9-136">Un intégrant qui représente le nombre maximum de fils</span><span class="sxs-lookup"><span data-stu-id="9e7b9-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="9e7b9-137">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="9e7b9-138">Un intégrant qui représente le nombre maximum de fils</span><span class="sxs-lookup"><span data-stu-id="9e7b9-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="9e7b9-139">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="9e7b9-139">**Environment variable**</span></span> | <span data-ttu-id="9e7b9-140">N/A</span><span class="sxs-lookup"><span data-stu-id="9e7b9-140">N/A</span></span> | <span data-ttu-id="9e7b9-141">N/A</span><span class="sxs-lookup"><span data-stu-id="9e7b9-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="9e7b9-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="9e7b9-142">Examples</span></span>

<span data-ttu-id="9e7b9-143">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="9e7b9-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="9e7b9-144">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="9e7b9-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
