---
title: Surveiller les événements d’exécution de contention de verrouillage
description: Consultez événements ETW qui collectent des informations spécifiques aux conflits de verrouillage de l’analyse.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588606"
---
# <a name="net-runtime-contention-events"></a><span data-ttu-id="4490a-103">Événements de conflit du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="4490a-103">.NET runtime contention events</span></span>

<span data-ttu-id="4490a-104">Ces événements de Runtime capturent des informations sur les conflits de verrous du moniteur tels que avec `Monitor.Enter` ou le mot clé C# lock.</span><span class="sxs-lookup"><span data-stu-id="4490a-104">These runtime events capture information about monitor lock contentions such as with `Monitor.Enter` or the C# lock keyword.</span></span> <span data-ttu-id="4490a-105">Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="4490a-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="contentionstart_v1-event"></a><span data-ttu-id="4490a-106">Événement ContentionStart_V1</span><span class="sxs-lookup"><span data-stu-id="4490a-106">ContentionStart_V1 event</span></span>

<span data-ttu-id="4490a-107">Cet événement est émis au démarrage d’une contention de verrouillage du moniteur.</span><span class="sxs-lookup"><span data-stu-id="4490a-107">This event is emitted at the start of a monitor lock contention.</span></span>

|<span data-ttu-id="4490a-108">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4490a-108">Keyword for raising the event</span></span>|<span data-ttu-id="4490a-109">Level</span><span class="sxs-lookup"><span data-stu-id="4490a-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4490a-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="4490a-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="4490a-111">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4490a-111">Informational (4)</span></span>|

 <span data-ttu-id="4490a-112">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4490a-112">The following table shows event information.</span></span>

|<span data-ttu-id="4490a-113">Événement</span><span class="sxs-lookup"><span data-stu-id="4490a-113">Event</span></span>|<span data-ttu-id="4490a-114">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4490a-114">Event ID</span></span>|<span data-ttu-id="4490a-115">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4490a-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="4490a-116">81</span><span class="sxs-lookup"><span data-stu-id="4490a-116">81</span></span>|<span data-ttu-id="4490a-117">Un conflit de verrouillage du moniteur démarre.</span><span class="sxs-lookup"><span data-stu-id="4490a-117">A monitor lock contention starts.</span></span>|

|<span data-ttu-id="4490a-118">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4490a-118">Field name</span></span>|<span data-ttu-id="4490a-119">Type de données</span><span class="sxs-lookup"><span data-stu-id="4490a-119">Data type</span></span>|<span data-ttu-id="4490a-120">Description</span><span class="sxs-lookup"><span data-stu-id="4490a-120">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="4490a-121">`0` pour managé ; `1` pour le mode natif.</span><span class="sxs-lookup"><span data-stu-id="4490a-121">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4490a-122">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4490a-122">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="contentionstop_v1-event"></a><span data-ttu-id="4490a-123">Événement ContentionStop_V1</span><span class="sxs-lookup"><span data-stu-id="4490a-123">ContentionStop_V1 event</span></span>

<span data-ttu-id="4490a-124">Cet événement est émis à la fin d’une contention de verrouillage du moniteur.</span><span class="sxs-lookup"><span data-stu-id="4490a-124">This event is emitted at the end of a monitor lock contention.</span></span>

|<span data-ttu-id="4490a-125">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4490a-125">Keyword for raising the event</span></span>|<span data-ttu-id="4490a-126">Level</span><span class="sxs-lookup"><span data-stu-id="4490a-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4490a-127">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="4490a-127">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="4490a-128">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4490a-128">Informational (4)</span></span>|

 <span data-ttu-id="4490a-129">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4490a-129">The following table shows event information.</span></span>

|<span data-ttu-id="4490a-130">Événement</span><span class="sxs-lookup"><span data-stu-id="4490a-130">Event</span></span>|<span data-ttu-id="4490a-131">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4490a-131">Event ID</span></span>|<span data-ttu-id="4490a-132">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4490a-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|<span data-ttu-id="4490a-133">91</span><span class="sxs-lookup"><span data-stu-id="4490a-133">91</span></span>|<span data-ttu-id="4490a-134">Une contention de verrouillage du moniteur se termine.</span><span class="sxs-lookup"><span data-stu-id="4490a-134">A monitor lock contention ends.</span></span>|

|<span data-ttu-id="4490a-135">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4490a-135">Field name</span></span>|<span data-ttu-id="4490a-136">Type de données</span><span class="sxs-lookup"><span data-stu-id="4490a-136">Data type</span></span>|<span data-ttu-id="4490a-137">Description</span><span class="sxs-lookup"><span data-stu-id="4490a-137">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="4490a-138">`0` pour managé ; `1` pour le mode natif.</span><span class="sxs-lookup"><span data-stu-id="4490a-138">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4490a-139">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4490a-139">Unique ID for the instance of CoreCLR.</span></span>|
|`DurationNs`|`win:Double`|<span data-ttu-id="4490a-140">Durée de la contention en nanosecondes.</span><span class="sxs-lookup"><span data-stu-id="4490a-140">Duration of the contention in nanoseconds.</span></span>|
