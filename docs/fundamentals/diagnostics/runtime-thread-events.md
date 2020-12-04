---
title: Événements d’exécution ThreadPool
description: Consultez événements du pool de threads du Runtime .NET qui recueillent des informations de diagnostic sur le pool de threads dans .NET Core. Les événements de pool de threads sont les événements de pool de threads de travail ou d’e/s.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96588677"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="4058d-104">Événements du pool de threads du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="4058d-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="4058d-105">Ces événements collectent des informations sur les threads de travail et d’e/s dans le ThreadPool.</span><span class="sxs-lookup"><span data-stu-id="4058d-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="4058d-106">Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="4058d-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="4058d-107">Événement IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="4058d-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="4058d-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-109">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-109">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-110">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-112">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-112">Informational (4)</span></span>|

 <span data-ttu-id="4058d-113">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-113">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-114">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-114">Event</span></span>|<span data-ttu-id="4058d-115">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-115">Event ID</span></span>|<span data-ttu-id="4058d-116">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4058d-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="4058d-117">44</span><span class="sxs-lookup"><span data-stu-id="4058d-117">44</span></span>|<span data-ttu-id="4058d-118">Un thread d'E/S est créé dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4058d-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="4058d-119">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-119">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-120">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-120">Field name</span></span>|<span data-ttu-id="4058d-121">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-121">Data type</span></span>|<span data-ttu-id="4058d-122">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4058d-123">Nombre de threads d'E/S, y compris le nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="4058d-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4058d-124">Nombre de threads de travail retirés</span><span class="sxs-lookup"><span data-stu-id="4058d-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-125">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="4058d-126">Événement IOThreadTerminate_V1</span><span class="sxs-lookup"><span data-stu-id="4058d-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="4058d-127">Le tableau suivant montre le mot clé et le niveau</span><span class="sxs-lookup"><span data-stu-id="4058d-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="4058d-128">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-128">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-129">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="4058d-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-131">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-131">Informational (4)</span></span>

 <span data-ttu-id="4058d-132">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-132">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-133">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-133">Event</span></span>|<span data-ttu-id="4058d-134">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-134">Event ID</span></span>|<span data-ttu-id="4058d-135">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4058d-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="4058d-136">45</span><span class="sxs-lookup"><span data-stu-id="4058d-136">45</span></span>|<span data-ttu-id="4058d-137">Un thread d’e/s se termine dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4058d-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="4058d-138">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-138">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-139">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-139">Field name</span></span>|<span data-ttu-id="4058d-140">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-140">Data type</span></span>|<span data-ttu-id="4058d-141">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4058d-142">Nombre de threads d'E/S restant dans le pool de threads</span><span class="sxs-lookup"><span data-stu-id="4058d-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4058d-143">Nombre de threads d'E/S retirés</span><span class="sxs-lookup"><span data-stu-id="4058d-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-144">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="4058d-145">Événement IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="4058d-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="4058d-146">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-147">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-147">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-148">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-150">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-150">Informational (4)</span></span>|

 <span data-ttu-id="4058d-151">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-151">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-152">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-152">Event</span></span>|<span data-ttu-id="4058d-153">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-153">Event ID</span></span>|<span data-ttu-id="4058d-154">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4058d-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="4058d-155">46</span><span class="sxs-lookup"><span data-stu-id="4058d-155">46</span></span>|<span data-ttu-id="4058d-156">Un thread d'E/S devient candidat au retrait.</span><span class="sxs-lookup"><span data-stu-id="4058d-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="4058d-157">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-157">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-158">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-158">Field name</span></span>|<span data-ttu-id="4058d-159">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-159">Data type</span></span>|<span data-ttu-id="4058d-160">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4058d-161">Nombre de threads d'E/S restant dans le pool de threads</span><span class="sxs-lookup"><span data-stu-id="4058d-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4058d-162">Nombre de threads d'E/S retirés</span><span class="sxs-lookup"><span data-stu-id="4058d-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-163">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="4058d-164">Événement IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="4058d-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="4058d-165">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-166">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-166">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-167">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-169">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-169">Informational (4)</span></span>|

 <span data-ttu-id="4058d-170">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-170">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-171">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-171">Event</span></span>|<span data-ttu-id="4058d-172">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-172">Event ID</span></span>|<span data-ttu-id="4058d-173">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4058d-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="4058d-174">47</span><span class="sxs-lookup"><span data-stu-id="4058d-174">47</span></span>|<span data-ttu-id="4058d-175">Le retrait d’un thread d'E/S est annulé en raison d'une E/S qui se produit au cours d’une période d'attente après que le thread est devenu un candidat au retrait.</span><span class="sxs-lookup"><span data-stu-id="4058d-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="4058d-176">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-176">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-177">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-177">Field name</span></span>|<span data-ttu-id="4058d-178">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-178">Data type</span></span>|<span data-ttu-id="4058d-179">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4058d-180">Nombre de threads d'E/S dans le pool de threads, y compris celui-ci</span><span class="sxs-lookup"><span data-stu-id="4058d-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4058d-181">Nombre de threads d'E/S retirés</span><span class="sxs-lookup"><span data-stu-id="4058d-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="4058d-182">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="4058d-183">Événement ThreadPoolWorkerThreadStart</span><span class="sxs-lookup"><span data-stu-id="4058d-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="4058d-184">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-184">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-185">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4058d-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-187">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-187">Informational (4)</span></span>|

|<span data-ttu-id="4058d-188">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-188">Event</span></span>|<span data-ttu-id="4058d-189">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-189">Event ID</span></span>|<span data-ttu-id="4058d-190">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="4058d-191">50</span><span class="sxs-lookup"><span data-stu-id="4058d-191">50</span></span>|<span data-ttu-id="4058d-192">Un thread de travail est créé.</span><span class="sxs-lookup"><span data-stu-id="4058d-192">A worker thread is created.</span></span>|

|<span data-ttu-id="4058d-193">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-193">Field name</span></span>|<span data-ttu-id="4058d-194">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-194">Data type</span></span>|<span data-ttu-id="4058d-195">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-196">Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="4058d-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-197">Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4058d-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-198">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="4058d-199">Événement ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="4058d-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="4058d-200">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-200">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-201">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4058d-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-203">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-203">Informational (4)</span></span>|

|<span data-ttu-id="4058d-204">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-204">Event</span></span>|<span data-ttu-id="4058d-205">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-205">Event ID</span></span>|<span data-ttu-id="4058d-206">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="4058d-207">51</span><span class="sxs-lookup"><span data-stu-id="4058d-207">51</span></span>|<span data-ttu-id="4058d-208">Un thread de travail est arrêté.</span><span class="sxs-lookup"><span data-stu-id="4058d-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="4058d-209">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-209">Field name</span></span>|<span data-ttu-id="4058d-210">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-210">Data type</span></span>|<span data-ttu-id="4058d-211">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-212">Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="4058d-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-213">Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4058d-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-214">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="4058d-215">Événement ThreadPoolWorkerThreadWait</span><span class="sxs-lookup"><span data-stu-id="4058d-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="4058d-216">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-216">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-217">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4058d-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-219">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-219">Informational (4)</span></span>|

|<span data-ttu-id="4058d-220">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-220">Event</span></span>|<span data-ttu-id="4058d-221">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-221">Event ID</span></span>|<span data-ttu-id="4058d-222">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="4058d-223">57</span><span class="sxs-lookup"><span data-stu-id="4058d-223">57</span></span>|<span data-ttu-id="4058d-224">Un thread de travail commence à attendre du travail.</span><span class="sxs-lookup"><span data-stu-id="4058d-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="4058d-225">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-225">Field name</span></span>|<span data-ttu-id="4058d-226">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-226">Data type</span></span>|<span data-ttu-id="4058d-227">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-228">Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="4058d-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-229">Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4058d-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-230">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="4058d-231">Événement ThreadPoolWorkerThreadRetirementStart</span><span class="sxs-lookup"><span data-stu-id="4058d-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="4058d-232">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-232">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-233">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4058d-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-235">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-235">Informational (4)</span></span>|

|<span data-ttu-id="4058d-236">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-236">Event</span></span>|<span data-ttu-id="4058d-237">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-237">Event ID</span></span>|<span data-ttu-id="4058d-238">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="4058d-239">52</span><span class="sxs-lookup"><span data-stu-id="4058d-239">52</span></span>|<span data-ttu-id="4058d-240">Un thread de travail est retiré.</span><span class="sxs-lookup"><span data-stu-id="4058d-240">A worker thread retires.</span></span>|

|<span data-ttu-id="4058d-241">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-241">Field name</span></span>|<span data-ttu-id="4058d-242">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-242">Data type</span></span>|<span data-ttu-id="4058d-243">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-244">Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="4058d-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-245">Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4058d-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-246">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="4058d-247">Événement ThreadPoolWorkerThreadRetirementStop</span><span class="sxs-lookup"><span data-stu-id="4058d-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="4058d-248">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-248">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-249">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4058d-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-251">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-251">Informational (4)</span></span>|

|<span data-ttu-id="4058d-252">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-252">Event</span></span>|<span data-ttu-id="4058d-253">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-253">Event ID</span></span>|<span data-ttu-id="4058d-254">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="4058d-255">53</span><span class="sxs-lookup"><span data-stu-id="4058d-255">53</span></span>|<span data-ttu-id="4058d-256">Un thread de travail retiré redevient actif.</span><span class="sxs-lookup"><span data-stu-id="4058d-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="4058d-257">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-257">Field name</span></span>|<span data-ttu-id="4058d-258">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-258">Data type</span></span>|<span data-ttu-id="4058d-259">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-260">Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="4058d-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-261">Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4058d-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-262">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="4058d-263">Événement ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="4058d-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="4058d-264">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-265">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-265">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-266">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-268">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-268">Informational (4)</span></span>|

 <span data-ttu-id="4058d-269">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-269">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-270">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-270">Event</span></span>|<span data-ttu-id="4058d-271">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-271">Event ID</span></span>|<span data-ttu-id="4058d-272">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="4058d-273">54</span><span class="sxs-lookup"><span data-stu-id="4058d-273">54</span></span>|<span data-ttu-id="4058d-274">Fait référence à la collecte d'informations pour un exemple. Autrement dit, une mesure de débit avec un certain niveau d’accès concurrentiel à un instant donné.</span><span class="sxs-lookup"><span data-stu-id="4058d-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="4058d-275">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-275">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-276">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-276">Field name</span></span>|<span data-ttu-id="4058d-277">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-277">Data type</span></span>|<span data-ttu-id="4058d-278">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="4058d-279">Nombre d'achèvements par unité de temps</span><span class="sxs-lookup"><span data-stu-id="4058d-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-280">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="4058d-281">Événement ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="4058d-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="4058d-282">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-283">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-283">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-284">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-286">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-286">Informational (4)</span></span>|

 <span data-ttu-id="4058d-287">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-287">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-288">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-288">Event</span></span>|<span data-ttu-id="4058d-289">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-289">Event ID</span></span>|<span data-ttu-id="4058d-290">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="4058d-291">55</span><span class="sxs-lookup"><span data-stu-id="4058d-291">55</span></span>|<span data-ttu-id="4058d-292">Enregistre une modification dans le contrôle, quand l'algorithme d'injection de thread (hill-climbing) détermine qu'une modification du niveau d'accès concurrentiel a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="4058d-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="4058d-293">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-293">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-294">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-294">Field name</span></span>|<span data-ttu-id="4058d-295">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-295">Data type</span></span>|<span data-ttu-id="4058d-296">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="4058d-297">Débit moyen d'un échantillon de mesures</span><span class="sxs-lookup"><span data-stu-id="4058d-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4058d-298">Nouveau nombre de threads de travail actifs</span><span class="sxs-lookup"><span data-stu-id="4058d-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="4058d-299">Raison de l'ajustement</span><span class="sxs-lookup"><span data-stu-id="4058d-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="4058d-300">`0x0` Chauffage.</span><span class="sxs-lookup"><span data-stu-id="4058d-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="4058d-301">`0x1` Initialisation.</span><span class="sxs-lookup"><span data-stu-id="4058d-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="4058d-302">`0x2` -Déplacement aléatoire.</span><span class="sxs-lookup"><span data-stu-id="4058d-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="4058d-303">`0x3` -Escalade Move.</span><span class="sxs-lookup"><span data-stu-id="4058d-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="4058d-304">`0x4` -Changer de point.</span><span class="sxs-lookup"><span data-stu-id="4058d-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="4058d-305">`0x5` Stabilisation.</span><span class="sxs-lookup"><span data-stu-id="4058d-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="4058d-306">`0x6` Faim.</span><span class="sxs-lookup"><span data-stu-id="4058d-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="4058d-307">`0x7` -Expiration du délai d’attente du thread.</span><span class="sxs-lookup"><span data-stu-id="4058d-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-308">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="4058d-309">Événement ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="4058d-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="4058d-310">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-311">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-311">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-312">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-314">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="4058d-314">Verbose (5)</span></span>

 <span data-ttu-id="4058d-315">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-315">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-316">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-316">Event</span></span>|<span data-ttu-id="4058d-317">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-317">Event ID</span></span>|<span data-ttu-id="4058d-318">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="4058d-319">56</span><span class="sxs-lookup"><span data-stu-id="4058d-319">56</span></span>|<span data-ttu-id="4058d-320">Rassemble des données sur le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4058d-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="4058d-321">Le tableau suivant présente les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="4058d-321">The following table shows the event data</span></span>

|<span data-ttu-id="4058d-322">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-322">Field name</span></span>|<span data-ttu-id="4058d-323">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-323">Data type</span></span>|<span data-ttu-id="4058d-324">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="4058d-325">Durée, en secondes, pendant laquelle ces statistiques ont été collectées.</span><span class="sxs-lookup"><span data-stu-id="4058d-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="4058d-326">Nombre moyen d'achèvements par seconde au cours de cet intervalle.</span><span class="sxs-lookup"><span data-stu-id="4058d-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="4058d-327">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="4058d-328">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="4058d-329">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="4058d-330">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="4058d-331">Amélioration relative du débit provoquée par les variations du nombre de threads de travail actifs au cours de cet intervalle.</span><span class="sxs-lookup"><span data-stu-id="4058d-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="4058d-332">Mesure de la validité du champ ThroughputRatio.</span><span class="sxs-lookup"><span data-stu-id="4058d-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="4058d-333">Nombre de threads de travail actifs qui servira de référence pour les futures variations du nombre de threads actifs.</span><span class="sxs-lookup"><span data-stu-id="4058d-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="4058d-334">Importance des futures variations du nombre de threads actifs.</span><span class="sxs-lookup"><span data-stu-id="4058d-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-335">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="4058d-336">Événement ThreadPoolEnqueue</span><span class="sxs-lookup"><span data-stu-id="4058d-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="4058d-337">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-338">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-338">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-339">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-341">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="4058d-341">Verbose (5)</span></span>

 <span data-ttu-id="4058d-342">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-342">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-343">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-343">Event</span></span>|<span data-ttu-id="4058d-344">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-344">Event ID</span></span>|<span data-ttu-id="4058d-345">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="4058d-346">61</span><span class="sxs-lookup"><span data-stu-id="4058d-346">61</span></span>|<span data-ttu-id="4058d-347">Un élément de travail a été mis en file d’attente dans la file d’attente du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4058d-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="4058d-348">Le tableau suivant présente les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="4058d-348">The following table shows the event data</span></span>

|<span data-ttu-id="4058d-349">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-349">Field name</span></span>|<span data-ttu-id="4058d-350">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-350">Data type</span></span>|<span data-ttu-id="4058d-351">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="4058d-352">Pointeur vers la demande de travail.</span><span class="sxs-lookup"><span data-stu-id="4058d-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-353">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="4058d-354">Événement ThreadPoolDequeue</span><span class="sxs-lookup"><span data-stu-id="4058d-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="4058d-355">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-356">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-356">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-357">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-359">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="4058d-359">Verbose (5)</span></span>

 <span data-ttu-id="4058d-360">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-360">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-361">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-361">Event</span></span>|<span data-ttu-id="4058d-362">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-362">Event ID</span></span>|<span data-ttu-id="4058d-363">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="4058d-364">62</span><span class="sxs-lookup"><span data-stu-id="4058d-364">62</span></span>|<span data-ttu-id="4058d-365">Un élément de travail a été retiré de la file d’attente du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4058d-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="4058d-366">Le tableau suivant présente les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="4058d-366">The following table shows the event data</span></span>

|<span data-ttu-id="4058d-367">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-367">Field name</span></span>|<span data-ttu-id="4058d-368">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-368">Data type</span></span>|<span data-ttu-id="4058d-369">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="4058d-370">Pointeur vers la demande de travail.</span><span class="sxs-lookup"><span data-stu-id="4058d-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-371">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="4058d-372">Événement ThreadPoolIOEnqueue</span><span class="sxs-lookup"><span data-stu-id="4058d-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="4058d-373">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-374">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-374">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-375">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-377">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="4058d-377">Verbose (5)</span></span>

 <span data-ttu-id="4058d-378">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-378">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-379">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-379">Event</span></span>|<span data-ttu-id="4058d-380">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-380">Event ID</span></span>|<span data-ttu-id="4058d-381">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="4058d-382">63</span><span class="sxs-lookup"><span data-stu-id="4058d-382">63</span></span>|<span data-ttu-id="4058d-383">Un thread met en file d’attente une notification de fin d’e/s après une fin d’e/s asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4058d-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="4058d-384">Le tableau suivant présente les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="4058d-384">The following table shows the event data</span></span>

|<span data-ttu-id="4058d-385">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-385">Field name</span></span>|<span data-ttu-id="4058d-386">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-386">Data type</span></span>|<span data-ttu-id="4058d-387">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="4058d-388">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="4058d-389">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="4058d-390">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-391">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="4058d-392">Événement ThreadPoolIODequeue</span><span class="sxs-lookup"><span data-stu-id="4058d-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="4058d-393">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-394">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-394">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-395">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-397">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="4058d-397">Verbose (5)</span></span>

 <span data-ttu-id="4058d-398">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-398">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-399">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-399">Event</span></span>|<span data-ttu-id="4058d-400">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-400">Event ID</span></span>|<span data-ttu-id="4058d-401">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="4058d-402">64</span><span class="sxs-lookup"><span data-stu-id="4058d-402">64</span></span>|<span data-ttu-id="4058d-403">Un thread met en file d’attente la notification d’achèvement d’e/s.</span><span class="sxs-lookup"><span data-stu-id="4058d-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="4058d-404">Le tableau suivant présente les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="4058d-404">The following table shows the event data</span></span>

|<span data-ttu-id="4058d-405">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-405">Field name</span></span>|<span data-ttu-id="4058d-406">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-406">Data type</span></span>|<span data-ttu-id="4058d-407">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="4058d-408">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="4058d-409">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="4058d-410">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-411">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="4058d-412">Événement ThreadPoolIOPack</span><span class="sxs-lookup"><span data-stu-id="4058d-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="4058d-413">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4058d-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4058d-414">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-414">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-415">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-417">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="4058d-417">Verbose (5)</span></span>|

 <span data-ttu-id="4058d-418">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-418">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-419">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-419">Event</span></span>|<span data-ttu-id="4058d-420">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-420">Event ID</span></span>|<span data-ttu-id="4058d-421">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="4058d-422">65</span><span class="sxs-lookup"><span data-stu-id="4058d-422">65</span></span>|<span data-ttu-id="4058d-423">Le pack d’e/s avec chevauchement de pool de threads est appelé.</span><span class="sxs-lookup"><span data-stu-id="4058d-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="4058d-424">Le tableau suivant présente les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="4058d-424">The following table shows the event data</span></span>

|<span data-ttu-id="4058d-425">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-425">Field name</span></span>|<span data-ttu-id="4058d-426">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-426">Data type</span></span>|<span data-ttu-id="4058d-427">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="4058d-428">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="4058d-429">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="4058d-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-430">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="4058d-431">Événement ThreadCreating</span><span class="sxs-lookup"><span data-stu-id="4058d-431">ThreadCreating event</span></span>

 <span data-ttu-id="4058d-432">Le tableau suivant présente les mots clés et le niveau.</span><span class="sxs-lookup"><span data-stu-id="4058d-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="4058d-433">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-433">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-434">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-436">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-436">Informational (4)</span></span>|

 <span data-ttu-id="4058d-437">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-437">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-438">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-438">Event</span></span>|<span data-ttu-id="4058d-439">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-439">Event ID</span></span>|<span data-ttu-id="4058d-440">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="4058d-441">70</span><span class="sxs-lookup"><span data-stu-id="4058d-441">70</span></span>|<span data-ttu-id="4058d-442">Le thread a été créé.</span><span class="sxs-lookup"><span data-stu-id="4058d-442">Thread has been created.</span></span>|

 <span data-ttu-id="4058d-443">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-443">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-444">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-444">Field name</span></span>|<span data-ttu-id="4058d-445">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-445">Data type</span></span>|<span data-ttu-id="4058d-446">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="4058d-447">ID du thread</span><span class="sxs-lookup"><span data-stu-id="4058d-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-448">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="4058d-449">Événement ThreadRunning</span><span class="sxs-lookup"><span data-stu-id="4058d-449">ThreadRunning event</span></span>

 <span data-ttu-id="4058d-450">Le tableau suivant présente les mots clés et le niveau.</span><span class="sxs-lookup"><span data-stu-id="4058d-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="4058d-451">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4058d-451">Keyword for raising the event</span></span>|<span data-ttu-id="4058d-452">Level</span><span class="sxs-lookup"><span data-stu-id="4058d-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4058d-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4058d-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4058d-454">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4058d-454">Informational (4)</span></span>|

 <span data-ttu-id="4058d-455">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-455">The following table shows the event information.</span></span>

|<span data-ttu-id="4058d-456">Événement</span><span class="sxs-lookup"><span data-stu-id="4058d-456">Event</span></span>|<span data-ttu-id="4058d-457">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4058d-457">Event ID</span></span>|<span data-ttu-id="4058d-458">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="4058d-459">71</span><span class="sxs-lookup"><span data-stu-id="4058d-459">71</span></span>|<span data-ttu-id="4058d-460">Le thread a commencé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="4058d-460">Thread has started running.</span></span>|

 <span data-ttu-id="4058d-461">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4058d-461">The following table shows the event data.</span></span>

|<span data-ttu-id="4058d-462">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4058d-462">Field name</span></span>|<span data-ttu-id="4058d-463">Type de données</span><span class="sxs-lookup"><span data-stu-id="4058d-463">Data type</span></span>|<span data-ttu-id="4058d-464">Description</span><span class="sxs-lookup"><span data-stu-id="4058d-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="4058d-465">ID du thread</span><span class="sxs-lookup"><span data-stu-id="4058d-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4058d-466">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4058d-466">Unique ID for the instance of CoreCLR.</span></span>|
