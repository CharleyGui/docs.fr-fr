---
title: Événements ETW d'analyse de ressource de domaine d'application
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: 0e453b2bafffd9e07a1bdddd97282c5b97f5483d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716216"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="e36b8-102">Événements ETW d'analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="e36b8-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="e36b8-103">Ces événements fournissent des informations de diagnostic détaillées sur l'état d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e36b8-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="e36b8-104">Vous pouvez utiliser ces événements ou la fonctionnalité ARM d'analyse de ressource de domaine d'application pour obtenir les mêmes informations.</span><span class="sxs-lookup"><span data-stu-id="e36b8-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="e36b8-105">Événement ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="e36b8-105">ThreadCreated Event</span></span>

<span data-ttu-id="e36b8-106">Cet événement est également déclenché sous le fournisseur d'arrêt en tant que `ThreadDC` (sous le mot clé `AppDomainResourceManagementRundownKeyword` ).</span><span class="sxs-lookup"><span data-stu-id="e36b8-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="e36b8-107">Il s’agit du seul événement déclenché sous le fournisseur d'arrêt dans cette catégorie.</span><span class="sxs-lookup"><span data-stu-id="e36b8-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="e36b8-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="e36b8-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="e36b8-109">Pour plus d’informations, consultez [niveaux et Mots clés ETW du CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e36b8-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="e36b8-110">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-110">Keyword for raising the event</span></span>|<span data-ttu-id="e36b8-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="e36b8-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e36b8-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e36b8-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e36b8-113">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-113">Informational(4)</span></span>|
|<span data-ttu-id="e36b8-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e36b8-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e36b8-115">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-115">Informational(4)</span></span>|

<span data-ttu-id="e36b8-116">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-116">The following table shows the event information:</span></span>

|<span data-ttu-id="e36b8-117">Event</span><span class="sxs-lookup"><span data-stu-id="e36b8-117">Event</span></span>|<span data-ttu-id="e36b8-118">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-118">Event ID</span></span>|<span data-ttu-id="e36b8-119">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="e36b8-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="e36b8-120">85</span><span class="sxs-lookup"><span data-stu-id="e36b8-120">85</span></span>|<span data-ttu-id="e36b8-121">Un thread a été créé pour le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e36b8-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="e36b8-122">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-122">The following table shows the event data:</span></span>

|<span data-ttu-id="e36b8-123">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="e36b8-123">Field name</span></span>|<span data-ttu-id="e36b8-124">Type de données</span><span class="sxs-lookup"><span data-stu-id="e36b8-124">Data type</span></span>|<span data-ttu-id="e36b8-125">Description</span><span class="sxs-lookup"><span data-stu-id="e36b8-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e36b8-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e36b8-126">ThreadID</span></span>|<span data-ttu-id="e36b8-127">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-127">win:UInt64</span></span>|<span data-ttu-id="e36b8-128">ID du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="e36b8-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="e36b8-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e36b8-129">AppDomainID</span></span>|<span data-ttu-id="e36b8-130">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-130">win:UInt64</span></span>|<span data-ttu-id="e36b8-131">Identificateur du domaine d'application pour lequel l'activité du thread est signalée.</span><span class="sxs-lookup"><span data-stu-id="e36b8-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="e36b8-132">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="e36b8-132">Flags</span></span>|<span data-ttu-id="e36b8-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e36b8-133">win:UInt32</span></span>|<span data-ttu-id="e36b8-134">Indicateurs de création de thread.</span><span class="sxs-lookup"><span data-stu-id="e36b8-134">Thread creation flags.</span></span>|
|<span data-ttu-id="e36b8-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="e36b8-135">ManagedThreadIndex</span></span>|<span data-ttu-id="e36b8-136">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e36b8-136">win:UInt32</span></span>|<span data-ttu-id="e36b8-137">Index managé du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="e36b8-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="e36b8-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="e36b8-138">OSThreadID</span></span>|<span data-ttu-id="e36b8-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e36b8-139">win:UInt32</span></span>|<span data-ttu-id="e36b8-140">ID de système d’exploitation du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="e36b8-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="e36b8-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e36b8-141">ClrInstanceID</span></span>|<span data-ttu-id="e36b8-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e36b8-142">win:UInt16</span></span>|<span data-ttu-id="e36b8-143">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e36b8-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="e36b8-144">Événement AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="e36b8-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="e36b8-145">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="e36b8-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e36b8-146">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-146">Keyword for raising the event</span></span>|<span data-ttu-id="e36b8-147">Niveau</span><span class="sxs-lookup"><span data-stu-id="e36b8-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e36b8-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e36b8-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e36b8-149">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-149">Informational(4)</span></span>|

<span data-ttu-id="e36b8-150">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-150">The following table shows the event information:</span></span>

|<span data-ttu-id="e36b8-151">Event</span><span class="sxs-lookup"><span data-stu-id="e36b8-151">Event</span></span>|<span data-ttu-id="e36b8-152">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-152">Event ID</span></span>|<span data-ttu-id="e36b8-153">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="e36b8-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="e36b8-154">83</span><span class="sxs-lookup"><span data-stu-id="e36b8-154">83</span></span>|<span data-ttu-id="e36b8-155">Chaque bloc de 4 Mo de mémoire (environ) est alloué dans le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e36b8-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="e36b8-156">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-156">The following table shows the event data:</span></span>

|<span data-ttu-id="e36b8-157">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="e36b8-157">Field name</span></span>|<span data-ttu-id="e36b8-158">Type de données</span><span class="sxs-lookup"><span data-stu-id="e36b8-158">Data type</span></span>|<span data-ttu-id="e36b8-159">Description</span><span class="sxs-lookup"><span data-stu-id="e36b8-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e36b8-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e36b8-160">AppDomainID</span></span>|<span data-ttu-id="e36b8-161">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-161">win:UInt64</span></span>|<span data-ttu-id="e36b8-162">Identificateur du domaine d'application pour lequel l'utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="e36b8-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="e36b8-163">Allocated</span><span class="sxs-lookup"><span data-stu-id="e36b8-163">Allocated</span></span>|<span data-ttu-id="e36b8-164">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-164">win:UInt64</span></span>|<span data-ttu-id="e36b8-165">Nombre total d'octets alloués dans ce domaine d'application depuis sa création (la quantité de mémoire libérée n'est pas soustraite).</span><span class="sxs-lookup"><span data-stu-id="e36b8-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="e36b8-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e36b8-166">ClrInstanceID</span></span>|<span data-ttu-id="e36b8-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e36b8-167">win:UInt16</span></span>|<span data-ttu-id="e36b8-168">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e36b8-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="e36b8-169">Événement AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="e36b8-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="e36b8-170">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="e36b8-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e36b8-171">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-171">Keyword for raising the event</span></span>|<span data-ttu-id="e36b8-172">Niveau</span><span class="sxs-lookup"><span data-stu-id="e36b8-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e36b8-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e36b8-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e36b8-174">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-174">Informational(4)</span></span>|

<span data-ttu-id="e36b8-175">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-175">The following table shows the event information:</span></span>

|<span data-ttu-id="e36b8-176">Event</span><span class="sxs-lookup"><span data-stu-id="e36b8-176">Event</span></span>|<span data-ttu-id="e36b8-177">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-177">Event ID</span></span>|<span data-ttu-id="e36b8-178">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="e36b8-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="e36b8-179">84</span><span class="sxs-lookup"><span data-stu-id="e36b8-179">84</span></span>|<span data-ttu-id="e36b8-180">Chaque garbage collection est terminé.</span><span class="sxs-lookup"><span data-stu-id="e36b8-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="e36b8-181">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-181">The following table shows the event data:</span></span>

|<span data-ttu-id="e36b8-182">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="e36b8-182">Field name</span></span>|<span data-ttu-id="e36b8-183">Type de données</span><span class="sxs-lookup"><span data-stu-id="e36b8-183">Data type</span></span>|<span data-ttu-id="e36b8-184">Description</span><span class="sxs-lookup"><span data-stu-id="e36b8-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e36b8-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e36b8-185">AppDomainID</span></span>|<span data-ttu-id="e36b8-186">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-186">win:UInt64</span></span>|<span data-ttu-id="e36b8-187">Identificateur du domaine pour lequel l’utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="e36b8-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="e36b8-188">Survived</span><span class="sxs-lookup"><span data-stu-id="e36b8-188">Survived</span></span>|<span data-ttu-id="e36b8-189">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-189">win:UInt64</span></span>|<span data-ttu-id="e36b8-190">Nombre d'octets ayant survécu après la dernière collection et qui sont conservés par ce domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e36b8-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="e36b8-191">Ce nombre est exact et complet après une collection complète, mais peut être incomplet après une collection éphémère.</span><span class="sxs-lookup"><span data-stu-id="e36b8-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="e36b8-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="e36b8-192">ProcessSurvived</span></span>|<span data-ttu-id="e36b8-193">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-193">win:UInt64</span></span>|<span data-ttu-id="e36b8-194">Nombre total d'octets qui ont survécu à la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="e36b8-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="e36b8-195">Après une collection complète, ce nombre représente le nombre d'octets maintenus actifs dans les tas managés.</span><span class="sxs-lookup"><span data-stu-id="e36b8-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="e36b8-196">Après une collection éphémère, ce nombre représente le nombre d'octets maintenus actifs dans les générations éphémères.</span><span class="sxs-lookup"><span data-stu-id="e36b8-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="e36b8-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e36b8-197">ClrInstanceID</span></span>|<span data-ttu-id="e36b8-198">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e36b8-198">win:UInt16</span></span>|<span data-ttu-id="e36b8-199">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e36b8-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="e36b8-200">Événement ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="e36b8-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="e36b8-201">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="e36b8-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e36b8-202">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-202">Keyword for raising the event</span></span>|<span data-ttu-id="e36b8-203">Niveau</span><span class="sxs-lookup"><span data-stu-id="e36b8-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e36b8-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e36b8-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e36b8-205">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-205">Informational(4)</span></span>|
|<span data-ttu-id="e36b8-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e36b8-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e36b8-207">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-207">Informational(4)</span></span>|

<span data-ttu-id="e36b8-208">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-208">The following table shows the event information:</span></span>

|<span data-ttu-id="e36b8-209">Event</span><span class="sxs-lookup"><span data-stu-id="e36b8-209">Event</span></span>|<span data-ttu-id="e36b8-210">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-210">Event ID</span></span>|<span data-ttu-id="e36b8-211">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="e36b8-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="e36b8-212">87</span><span class="sxs-lookup"><span data-stu-id="e36b8-212">87</span></span>|<span data-ttu-id="e36b8-213">Un thread entre dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e36b8-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="e36b8-214">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-214">The following table shows the event data:</span></span>

|<span data-ttu-id="e36b8-215">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="e36b8-215">Field name</span></span>|<span data-ttu-id="e36b8-216">Type de données</span><span class="sxs-lookup"><span data-stu-id="e36b8-216">Data type</span></span>|<span data-ttu-id="e36b8-217">Description</span><span class="sxs-lookup"><span data-stu-id="e36b8-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e36b8-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e36b8-218">ThreadID</span></span>|<span data-ttu-id="e36b8-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-219">win:UInt64</span></span>|<span data-ttu-id="e36b8-220">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="e36b8-220">The thread identifier.</span></span>|
|<span data-ttu-id="e36b8-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e36b8-221">AppDomainID</span></span>|<span data-ttu-id="e36b8-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-222">win:UInt64</span></span>|<span data-ttu-id="e36b8-223">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e36b8-223">The application domain identifier.</span></span>|
|<span data-ttu-id="e36b8-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e36b8-224">ClrInstanceID</span></span>|<span data-ttu-id="e36b8-225">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e36b8-225">win:UInt16</span></span>|<span data-ttu-id="e36b8-226">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e36b8-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="e36b8-227">Événement ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="e36b8-227">ThreadTerminated Event</span></span>

<span data-ttu-id="e36b8-228">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="e36b8-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e36b8-229">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-229">Keyword for raising the event</span></span>|<span data-ttu-id="e36b8-230">Niveau</span><span class="sxs-lookup"><span data-stu-id="e36b8-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e36b8-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e36b8-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e36b8-232">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-232">Informational(4)</span></span>|
|<span data-ttu-id="e36b8-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e36b8-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e36b8-234">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="e36b8-234">Informational(4)</span></span>|

<span data-ttu-id="e36b8-235">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-235">The following table shows the event information:</span></span>

|<span data-ttu-id="e36b8-236">Event</span><span class="sxs-lookup"><span data-stu-id="e36b8-236">Event</span></span>|<span data-ttu-id="e36b8-237">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="e36b8-237">Event ID</span></span>|<span data-ttu-id="e36b8-238">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="e36b8-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="e36b8-239">86</span><span class="sxs-lookup"><span data-stu-id="e36b8-239">86</span></span>|<span data-ttu-id="e36b8-240">Un thread se termine.</span><span class="sxs-lookup"><span data-stu-id="e36b8-240">A thread terminates.</span></span>|

<span data-ttu-id="e36b8-241">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="e36b8-241">The following table shows the event data:</span></span>

|<span data-ttu-id="e36b8-242">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="e36b8-242">Field name</span></span>|<span data-ttu-id="e36b8-243">Type de données</span><span class="sxs-lookup"><span data-stu-id="e36b8-243">Data type</span></span>|<span data-ttu-id="e36b8-244">Description</span><span class="sxs-lookup"><span data-stu-id="e36b8-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e36b8-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e36b8-245">ThreadID</span></span>|<span data-ttu-id="e36b8-246">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-246">win:UInt64</span></span>|<span data-ttu-id="e36b8-247">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="e36b8-247">The thread identifier.</span></span>|
|<span data-ttu-id="e36b8-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e36b8-248">AppDomainID</span></span>|<span data-ttu-id="e36b8-249">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e36b8-249">win:UInt64</span></span>|<span data-ttu-id="e36b8-250">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e36b8-250">The application domain identifier.</span></span>|
|<span data-ttu-id="e36b8-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e36b8-251">ClrInstanceID</span></span>|<span data-ttu-id="e36b8-252">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e36b8-252">win:UInt16</span></span>|<span data-ttu-id="e36b8-253">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e36b8-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e36b8-254">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e36b8-254">See also</span></span>

- [<span data-ttu-id="e36b8-255">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="e36b8-255">CLR ETW Events</span></span>](clr-etw-events.md)
