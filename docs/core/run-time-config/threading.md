---
title: Paramètres de configuration de thread
description: En savoir plus sur les paramètres d’exécution qui configurent les threads pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802763"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="113b2-103">Options de configuration au moment de l’exécution pour le Threading</span><span class="sxs-lookup"><span data-stu-id="113b2-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="113b2-104">Groupes de PROCESSEURs</span><span class="sxs-lookup"><span data-stu-id="113b2-104">CPU groups</span></span>

- <span data-ttu-id="113b2-105">Configure si les threads sont automatiquement distribués entre les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="113b2-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="113b2-106">Valeur par défaut : désactivé (`0`).</span><span class="sxs-lookup"><span data-stu-id="113b2-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="113b2-107">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="113b2-107">Setting name</span></span> | <span data-ttu-id="113b2-108">Valeurs</span><span class="sxs-lookup"><span data-stu-id="113b2-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="113b2-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="113b2-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="113b2-110">Non applicable</span><span class="sxs-lookup"><span data-stu-id="113b2-110">N/A</span></span> | <span data-ttu-id="113b2-111">Non applicable</span><span class="sxs-lookup"><span data-stu-id="113b2-111">N/A</span></span> |
| <span data-ttu-id="113b2-112">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="113b2-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="113b2-113">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="113b2-113">`0` - disabled</span></span><br/><span data-ttu-id="113b2-114">activé `1`</span><span class="sxs-lookup"><span data-stu-id="113b2-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="113b2-115">Nombre minimal de threads</span><span class="sxs-lookup"><span data-stu-id="113b2-115">Minimum threads</span></span>

- <span data-ttu-id="113b2-116">Spécifie le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="113b2-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="113b2-117">Correspond à la méthode <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="113b2-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="113b2-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="113b2-118">Setting name</span></span> | <span data-ttu-id="113b2-119">Valeurs</span><span class="sxs-lookup"><span data-stu-id="113b2-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="113b2-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="113b2-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="113b2-121">Entier qui représente le nombre minimal de threads.</span><span class="sxs-lookup"><span data-stu-id="113b2-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="113b2-122">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="113b2-122">**Environment variable**</span></span> | <span data-ttu-id="113b2-123">Non applicable</span><span class="sxs-lookup"><span data-stu-id="113b2-123">N/A</span></span> | <span data-ttu-id="113b2-124">Non applicable</span><span class="sxs-lookup"><span data-stu-id="113b2-124">N/A</span></span> |

## <a name="maximum-threads"></a><span data-ttu-id="113b2-125">Nombre maximal de threads</span><span class="sxs-lookup"><span data-stu-id="113b2-125">Maximum threads</span></span>

- <span data-ttu-id="113b2-126">Spécifie le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="113b2-126">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="113b2-127">Correspond à la méthode <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="113b2-127">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="113b2-128">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="113b2-128">Setting name</span></span> | <span data-ttu-id="113b2-129">Valeurs</span><span class="sxs-lookup"><span data-stu-id="113b2-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="113b2-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="113b2-130">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="113b2-131">Entier qui représente le nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="113b2-131">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="113b2-132">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="113b2-132">**Environment variable**</span></span> | <span data-ttu-id="113b2-133">Non applicable</span><span class="sxs-lookup"><span data-stu-id="113b2-133">N/A</span></span> | <span data-ttu-id="113b2-134">Non applicable</span><span class="sxs-lookup"><span data-stu-id="113b2-134">N/A</span></span> |
