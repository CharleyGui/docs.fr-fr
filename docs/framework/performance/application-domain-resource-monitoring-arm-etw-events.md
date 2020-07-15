---
title: Événements ETW d'analyse de ressource de domaine d'application
description: En savoir plus sur les événements ETW ARM (application domain Resource Monitoring) dans .NET, tels que ThreadCreated, AppDomainMemAllocated, AppDomainMemSurvived, etc.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309779"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="a6afb-103">Événements ETW d'analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="a6afb-103">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="a6afb-104">Ces événements fournissent des informations de diagnostic détaillées sur l'état d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="a6afb-104">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="a6afb-105">Vous pouvez utiliser ces événements ou la fonctionnalité ARM d'analyse de ressource de domaine d'application pour obtenir les mêmes informations.</span><span class="sxs-lookup"><span data-stu-id="a6afb-105">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="a6afb-106">Événement ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="a6afb-106">ThreadCreated Event</span></span>

<span data-ttu-id="a6afb-107">Cet événement est également déclenché sous le fournisseur d'arrêt en tant que `ThreadDC` (sous le mot clé `AppDomainResourceManagementRundownKeyword` ).</span><span class="sxs-lookup"><span data-stu-id="a6afb-107">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="a6afb-108">Il s’agit du seul événement déclenché sous le fournisseur d'arrêt dans cette catégorie.</span><span class="sxs-lookup"><span data-stu-id="a6afb-108">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="a6afb-109">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="a6afb-109">The following table shows the keyword and level.</span></span> <span data-ttu-id="a6afb-110">Pour plus d’informations, consultez [niveaux et Mots clés ETW du CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a6afb-110">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="a6afb-111">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-111">Keyword for raising the event</span></span>|<span data-ttu-id="a6afb-112">Level</span><span class="sxs-lookup"><span data-stu-id="a6afb-112">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a6afb-113">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a6afb-113">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a6afb-114">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-114">Informational(4)</span></span>|
|<span data-ttu-id="a6afb-115">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a6afb-115">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a6afb-116">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-116">Informational(4)</span></span>|

<span data-ttu-id="a6afb-117">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-117">The following table shows the event information:</span></span>

|<span data-ttu-id="a6afb-118">Événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-118">Event</span></span>|<span data-ttu-id="a6afb-119">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-119">Event ID</span></span>|<span data-ttu-id="a6afb-120">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="a6afb-120">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="a6afb-121">85 %</span><span class="sxs-lookup"><span data-stu-id="a6afb-121">85</span></span>|<span data-ttu-id="a6afb-122">Un thread a été créé pour le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="a6afb-122">A thread was created for the application domain.</span></span>|

<span data-ttu-id="a6afb-123">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-123">The following table shows the event data:</span></span>

|<span data-ttu-id="a6afb-124">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="a6afb-124">Field name</span></span>|<span data-ttu-id="a6afb-125">Type de données</span><span class="sxs-lookup"><span data-stu-id="a6afb-125">Data type</span></span>|<span data-ttu-id="a6afb-126">Description</span><span class="sxs-lookup"><span data-stu-id="a6afb-126">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a6afb-127">ThreadID</span><span class="sxs-lookup"><span data-stu-id="a6afb-127">ThreadID</span></span>|<span data-ttu-id="a6afb-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-128">win:UInt64</span></span>|<span data-ttu-id="a6afb-129">ID du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="a6afb-129">ID of the thread that was created.</span></span>|
|<span data-ttu-id="a6afb-130">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a6afb-130">AppDomainID</span></span>|<span data-ttu-id="a6afb-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-131">win:UInt64</span></span>|<span data-ttu-id="a6afb-132">Identificateur du domaine d'application pour lequel l'activité du thread est signalée.</span><span class="sxs-lookup"><span data-stu-id="a6afb-132">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="a6afb-133">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="a6afb-133">Flags</span></span>|<span data-ttu-id="a6afb-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a6afb-134">win:UInt32</span></span>|<span data-ttu-id="a6afb-135">Indicateurs de création de thread.</span><span class="sxs-lookup"><span data-stu-id="a6afb-135">Thread creation flags.</span></span>|
|<span data-ttu-id="a6afb-136">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="a6afb-136">ManagedThreadIndex</span></span>|<span data-ttu-id="a6afb-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a6afb-137">win:UInt32</span></span>|<span data-ttu-id="a6afb-138">Index managé du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="a6afb-138">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="a6afb-139">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="a6afb-139">OSThreadID</span></span>|<span data-ttu-id="a6afb-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a6afb-140">win:UInt32</span></span>|<span data-ttu-id="a6afb-141">ID de système d’exploitation du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="a6afb-141">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="a6afb-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6afb-142">ClrInstanceID</span></span>|<span data-ttu-id="a6afb-143">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6afb-143">win:UInt16</span></span>|<span data-ttu-id="a6afb-144">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a6afb-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="a6afb-145">Événement AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="a6afb-145">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="a6afb-146">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="a6afb-146">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a6afb-147">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-147">Keyword for raising the event</span></span>|<span data-ttu-id="a6afb-148">Level</span><span class="sxs-lookup"><span data-stu-id="a6afb-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a6afb-149">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a6afb-149">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a6afb-150">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-150">Informational(4)</span></span>|

<span data-ttu-id="a6afb-151">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-151">The following table shows the event information:</span></span>

|<span data-ttu-id="a6afb-152">Événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-152">Event</span></span>|<span data-ttu-id="a6afb-153">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-153">Event ID</span></span>|<span data-ttu-id="a6afb-154">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="a6afb-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="a6afb-155">83</span><span class="sxs-lookup"><span data-stu-id="a6afb-155">83</span></span>|<span data-ttu-id="a6afb-156">Chaque bloc de 4 Mo de mémoire (environ) est alloué dans le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="a6afb-156">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="a6afb-157">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-157">The following table shows the event data:</span></span>

|<span data-ttu-id="a6afb-158">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="a6afb-158">Field name</span></span>|<span data-ttu-id="a6afb-159">Type de données</span><span class="sxs-lookup"><span data-stu-id="a6afb-159">Data type</span></span>|<span data-ttu-id="a6afb-160">Description</span><span class="sxs-lookup"><span data-stu-id="a6afb-160">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a6afb-161">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a6afb-161">AppDomainID</span></span>|<span data-ttu-id="a6afb-162">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-162">win:UInt64</span></span>|<span data-ttu-id="a6afb-163">Identificateur du domaine d'application pour lequel l'utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="a6afb-163">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="a6afb-164">Allocated</span><span class="sxs-lookup"><span data-stu-id="a6afb-164">Allocated</span></span>|<span data-ttu-id="a6afb-165">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-165">win:UInt64</span></span>|<span data-ttu-id="a6afb-166">Nombre total d'octets alloués dans ce domaine d'application depuis sa création (la quantité de mémoire libérée n'est pas soustraite).</span><span class="sxs-lookup"><span data-stu-id="a6afb-166">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="a6afb-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6afb-167">ClrInstanceID</span></span>|<span data-ttu-id="a6afb-168">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6afb-168">win:UInt16</span></span>|<span data-ttu-id="a6afb-169">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a6afb-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="a6afb-170">Événement AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="a6afb-170">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="a6afb-171">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="a6afb-171">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a6afb-172">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-172">Keyword for raising the event</span></span>|<span data-ttu-id="a6afb-173">Level</span><span class="sxs-lookup"><span data-stu-id="a6afb-173">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a6afb-174">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a6afb-174">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a6afb-175">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-175">Informational(4)</span></span>|

<span data-ttu-id="a6afb-176">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-176">The following table shows the event information:</span></span>

|<span data-ttu-id="a6afb-177">Événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-177">Event</span></span>|<span data-ttu-id="a6afb-178">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-178">Event ID</span></span>|<span data-ttu-id="a6afb-179">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="a6afb-179">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="a6afb-180">84</span><span class="sxs-lookup"><span data-stu-id="a6afb-180">84</span></span>|<span data-ttu-id="a6afb-181">Chaque garbage collection est terminé.</span><span class="sxs-lookup"><span data-stu-id="a6afb-181">Each garbage collection has ended.</span></span>|

<span data-ttu-id="a6afb-182">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-182">The following table shows the event data:</span></span>

|<span data-ttu-id="a6afb-183">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="a6afb-183">Field name</span></span>|<span data-ttu-id="a6afb-184">Type de données</span><span class="sxs-lookup"><span data-stu-id="a6afb-184">Data type</span></span>|<span data-ttu-id="a6afb-185">Description</span><span class="sxs-lookup"><span data-stu-id="a6afb-185">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a6afb-186">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a6afb-186">AppDomainID</span></span>|<span data-ttu-id="a6afb-187">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-187">win:UInt64</span></span>|<span data-ttu-id="a6afb-188">Identificateur du domaine pour lequel l’utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="a6afb-188">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="a6afb-189">Survived</span><span class="sxs-lookup"><span data-stu-id="a6afb-189">Survived</span></span>|<span data-ttu-id="a6afb-190">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-190">win:UInt64</span></span>|<span data-ttu-id="a6afb-191">Nombre d'octets ayant survécu après la dernière collection et qui sont conservés par ce domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="a6afb-191">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="a6afb-192">Ce nombre est exact et complet après une collection complète, mais peut être incomplet après une collection éphémère.</span><span class="sxs-lookup"><span data-stu-id="a6afb-192">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="a6afb-193">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="a6afb-193">ProcessSurvived</span></span>|<span data-ttu-id="a6afb-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-194">win:UInt64</span></span>|<span data-ttu-id="a6afb-195">Nombre total d'octets qui ont survécu à la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="a6afb-195">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="a6afb-196">Après une collection complète, ce nombre représente le nombre d'octets maintenus actifs dans les tas managés.</span><span class="sxs-lookup"><span data-stu-id="a6afb-196">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="a6afb-197">Après une collection éphémère, ce nombre représente le nombre d'octets maintenus actifs dans les générations éphémères.</span><span class="sxs-lookup"><span data-stu-id="a6afb-197">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="a6afb-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6afb-198">ClrInstanceID</span></span>|<span data-ttu-id="a6afb-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6afb-199">win:UInt16</span></span>|<span data-ttu-id="a6afb-200">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a6afb-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="a6afb-201">Événement ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="a6afb-201">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="a6afb-202">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="a6afb-202">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a6afb-203">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-203">Keyword for raising the event</span></span>|<span data-ttu-id="a6afb-204">Level</span><span class="sxs-lookup"><span data-stu-id="a6afb-204">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a6afb-205">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a6afb-205">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a6afb-206">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-206">Informational(4)</span></span>|
|<span data-ttu-id="a6afb-207">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a6afb-207">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a6afb-208">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-208">Informational(4)</span></span>|

<span data-ttu-id="a6afb-209">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-209">The following table shows the event information:</span></span>

|<span data-ttu-id="a6afb-210">Événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-210">Event</span></span>|<span data-ttu-id="a6afb-211">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-211">Event ID</span></span>|<span data-ttu-id="a6afb-212">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="a6afb-212">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="a6afb-213">87</span><span class="sxs-lookup"><span data-stu-id="a6afb-213">87</span></span>|<span data-ttu-id="a6afb-214">Un thread entre dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="a6afb-214">A thread enters an application domain.</span></span>|

<span data-ttu-id="a6afb-215">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-215">The following table shows the event data:</span></span>

|<span data-ttu-id="a6afb-216">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="a6afb-216">Field name</span></span>|<span data-ttu-id="a6afb-217">Type de données</span><span class="sxs-lookup"><span data-stu-id="a6afb-217">Data type</span></span>|<span data-ttu-id="a6afb-218">Description</span><span class="sxs-lookup"><span data-stu-id="a6afb-218">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a6afb-219">ThreadID</span><span class="sxs-lookup"><span data-stu-id="a6afb-219">ThreadID</span></span>|<span data-ttu-id="a6afb-220">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-220">win:UInt64</span></span>|<span data-ttu-id="a6afb-221">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="a6afb-221">The thread identifier.</span></span>|
|<span data-ttu-id="a6afb-222">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a6afb-222">AppDomainID</span></span>|<span data-ttu-id="a6afb-223">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-223">win:UInt64</span></span>|<span data-ttu-id="a6afb-224">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="a6afb-224">The application domain identifier.</span></span>|
|<span data-ttu-id="a6afb-225">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6afb-225">ClrInstanceID</span></span>|<span data-ttu-id="a6afb-226">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6afb-226">win:UInt16</span></span>|<span data-ttu-id="a6afb-227">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a6afb-227">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="a6afb-228">Événement ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="a6afb-228">ThreadTerminated Event</span></span>

<span data-ttu-id="a6afb-229">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="a6afb-229">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a6afb-230">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-230">Keyword for raising the event</span></span>|<span data-ttu-id="a6afb-231">Level</span><span class="sxs-lookup"><span data-stu-id="a6afb-231">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a6afb-232">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a6afb-232">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a6afb-233">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-233">Informational(4)</span></span>|
|<span data-ttu-id="a6afb-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a6afb-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a6afb-235">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="a6afb-235">Informational(4)</span></span>|

<span data-ttu-id="a6afb-236">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-236">The following table shows the event information:</span></span>

|<span data-ttu-id="a6afb-237">Événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-237">Event</span></span>|<span data-ttu-id="a6afb-238">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="a6afb-238">Event ID</span></span>|<span data-ttu-id="a6afb-239">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="a6afb-239">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="a6afb-240">86</span><span class="sxs-lookup"><span data-stu-id="a6afb-240">86</span></span>|<span data-ttu-id="a6afb-241">Un thread se termine.</span><span class="sxs-lookup"><span data-stu-id="a6afb-241">A thread terminates.</span></span>|

<span data-ttu-id="a6afb-242">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="a6afb-242">The following table shows the event data:</span></span>

|<span data-ttu-id="a6afb-243">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="a6afb-243">Field name</span></span>|<span data-ttu-id="a6afb-244">Type de données</span><span class="sxs-lookup"><span data-stu-id="a6afb-244">Data type</span></span>|<span data-ttu-id="a6afb-245">Description</span><span class="sxs-lookup"><span data-stu-id="a6afb-245">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a6afb-246">ThreadID</span><span class="sxs-lookup"><span data-stu-id="a6afb-246">ThreadID</span></span>|<span data-ttu-id="a6afb-247">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-247">win:UInt64</span></span>|<span data-ttu-id="a6afb-248">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="a6afb-248">The thread identifier.</span></span>|
|<span data-ttu-id="a6afb-249">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a6afb-249">AppDomainID</span></span>|<span data-ttu-id="a6afb-250">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6afb-250">win:UInt64</span></span>|<span data-ttu-id="a6afb-251">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="a6afb-251">The application domain identifier.</span></span>|
|<span data-ttu-id="a6afb-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6afb-252">ClrInstanceID</span></span>|<span data-ttu-id="a6afb-253">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6afb-253">win:UInt16</span></span>|<span data-ttu-id="a6afb-254">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a6afb-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a6afb-255">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6afb-255">See also</span></span>

- [<span data-ttu-id="a6afb-256">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="a6afb-256">CLR ETW Events</span></span>](clr-etw-events.md)
