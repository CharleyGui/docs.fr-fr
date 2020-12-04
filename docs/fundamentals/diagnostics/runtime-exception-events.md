---
title: Événements du runtime d’exception
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques aux exceptions et à la gestion des exceptions.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96588659"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="b2bc2-103">Événements d’exception du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="b2bc2-103">.NET runtime exception events</span></span>

<span data-ttu-id="b2bc2-104">Ces événements de Runtime capturent des informations sur les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="b2bc2-105">Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="b2bc2-106">Événement ExceptionThrown_V1</span><span class="sxs-lookup"><span data-stu-id="b2bc2-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="b2bc2-107">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-107">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-108">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-109">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-110">Erreur (1)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-110">Error (1)</span></span>|

 <span data-ttu-id="b2bc2-111">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-111">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-112">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-112">Event</span></span>|<span data-ttu-id="b2bc2-113">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-113">Event ID</span></span>|<span data-ttu-id="b2bc2-114">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="b2bc2-115">80</span><span class="sxs-lookup"><span data-stu-id="b2bc2-115">80</span></span>|<span data-ttu-id="b2bc2-116">Une exception managée est levée.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="b2bc2-117">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="b2bc2-117">Field name</span></span>|<span data-ttu-id="b2bc2-118">Type de données</span><span class="sxs-lookup"><span data-stu-id="b2bc2-118">Data type</span></span>|<span data-ttu-id="b2bc2-119">Description</span><span class="sxs-lookup"><span data-stu-id="b2bc2-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="b2bc2-120">Type de l’exception, par exemple `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="b2bc2-121">Message d’exception réel.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="b2bc2-122">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="b2bc2-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="b2bc2-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="b2bc2-124">`0x01`: HasInnerException.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="b2bc2-125">`0x02`: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="b2bc2-126">`0x04`: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="b2bc2-127">`0x08`: IsCorruptedStateException (indique que l’état du processus est endommagé ; consultez [gestion des exceptions d’état endommagé](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="b2bc2-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="b2bc2-128">`0x10`: IsCLSCompliant (une exception qui dérive de <xref:System.Exception> est conforme CLS ; sinon, elle n’est pas conforme CLS).</span><span class="sxs-lookup"><span data-stu-id="b2bc2-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b2bc2-129">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="b2bc2-130">Événement ExceptionCatchStart</span><span class="sxs-lookup"><span data-stu-id="b2bc2-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="b2bc2-131">Cet événement est émis lorsqu’un gestionnaire catch d’exception managé commence.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="b2bc2-132">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-132">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-133">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-134">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-135">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-135">Informational (4)</span></span>|

 <span data-ttu-id="b2bc2-136">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-136">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-137">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-137">Event</span></span>|<span data-ttu-id="b2bc2-138">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-138">Event ID</span></span>|<span data-ttu-id="b2bc2-139">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="b2bc2-140">250</span><span class="sxs-lookup"><span data-stu-id="b2bc2-140">250</span></span>|<span data-ttu-id="b2bc2-141">Une exception managée est gérée par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="b2bc2-142">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="b2bc2-142">Field name</span></span>|<span data-ttu-id="b2bc2-143">Type de données</span><span class="sxs-lookup"><span data-stu-id="b2bc2-143">Data type</span></span>|<span data-ttu-id="b2bc2-144">Description</span><span class="sxs-lookup"><span data-stu-id="b2bc2-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="b2bc2-145">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="b2bc2-146">Pointeur vers le descripteur de méthode sur la méthode où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="b2bc2-147">Nom de la méthode où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b2bc2-148">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="b2bc2-149">Événement ExceptionCatchStop</span><span class="sxs-lookup"><span data-stu-id="b2bc2-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="b2bc2-150">Cet événement est émis lorsqu’un gestionnaire catch d’exceptions managées se termine.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="b2bc2-151">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-151">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-152">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-153">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-154">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-154">Informational (4)</span></span>|

 <span data-ttu-id="b2bc2-155">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-155">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-156">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-156">Event</span></span>|<span data-ttu-id="b2bc2-157">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-157">Event ID</span></span>|<span data-ttu-id="b2bc2-158">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="b2bc2-159">251</span><span class="sxs-lookup"><span data-stu-id="b2bc2-159">251</span></span>|<span data-ttu-id="b2bc2-160">Un gestionnaire catch d’exceptions managé est terminé.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="b2bc2-161">Événement ExceptionFinallyStart</span><span class="sxs-lookup"><span data-stu-id="b2bc2-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="b2bc2-162">Cet événement est émis lorsqu’une exception managée finally Handler commence.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="b2bc2-163">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-163">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-164">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-165">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-166">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-166">Informational (4)</span></span>|

 <span data-ttu-id="b2bc2-167">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-167">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-168">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-168">Event</span></span>|<span data-ttu-id="b2bc2-169">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-169">Event ID</span></span>|<span data-ttu-id="b2bc2-170">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="b2bc2-171">252</span><span class="sxs-lookup"><span data-stu-id="b2bc2-171">252</span></span>|<span data-ttu-id="b2bc2-172">Une exception managée est gérée par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="b2bc2-173">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="b2bc2-173">Field name</span></span>|<span data-ttu-id="b2bc2-174">Type de données</span><span class="sxs-lookup"><span data-stu-id="b2bc2-174">Data type</span></span>|<span data-ttu-id="b2bc2-175">Description</span><span class="sxs-lookup"><span data-stu-id="b2bc2-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="b2bc2-176">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="b2bc2-177">Pointeur vers le descripteur de méthode sur la méthode où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="b2bc2-178">Nom de la méthode où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b2bc2-179">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="b2bc2-180">Événement ExceptionFinallyStop</span><span class="sxs-lookup"><span data-stu-id="b2bc2-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="b2bc2-181">Cet événement est émis lorsqu’un gestionnaire catch d’exceptions managées se termine.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="b2bc2-182">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-182">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-183">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-184">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-185">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-185">Informational (4)</span></span>|

 <span data-ttu-id="b2bc2-186">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-186">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-187">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-187">Event</span></span>|<span data-ttu-id="b2bc2-188">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-188">Event ID</span></span>|<span data-ttu-id="b2bc2-189">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="b2bc2-190">253</span><span class="sxs-lookup"><span data-stu-id="b2bc2-190">253</span></span>|<span data-ttu-id="b2bc2-191">Une exception managée finally Handler est terminée.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="b2bc2-192">Événement ExceptionFilterStart</span><span class="sxs-lookup"><span data-stu-id="b2bc2-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="b2bc2-193">Cet événement est émis lors du début d’un filtrage d’exceptions managées.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="b2bc2-194">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-194">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-195">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-196">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-197">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-197">Informational (4)</span></span>|

 <span data-ttu-id="b2bc2-198">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-198">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-199">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-199">Event</span></span>|<span data-ttu-id="b2bc2-200">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-200">Event ID</span></span>|<span data-ttu-id="b2bc2-201">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="b2bc2-202">254</span><span class="sxs-lookup"><span data-stu-id="b2bc2-202">254</span></span>|<span data-ttu-id="b2bc2-203">Un filtrage des exceptions managées commence.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="b2bc2-204">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="b2bc2-204">Field name</span></span>|<span data-ttu-id="b2bc2-205">Type de données</span><span class="sxs-lookup"><span data-stu-id="b2bc2-205">Data type</span></span>|<span data-ttu-id="b2bc2-206">Description</span><span class="sxs-lookup"><span data-stu-id="b2bc2-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="b2bc2-207">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="b2bc2-208">Pointeur vers le descripteur de méthode sur la méthode où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="b2bc2-209">Nom de la méthode où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b2bc2-210">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="b2bc2-211">Événement ExceptionFilterStop</span><span class="sxs-lookup"><span data-stu-id="b2bc2-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="b2bc2-212">Cet événement est émis lorsqu’un filtrage d’exceptions managées se termine.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="b2bc2-213">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-213">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-214">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-215">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-216">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-216">Informational (4)</span></span>|

 <span data-ttu-id="b2bc2-217">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-217">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-218">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-218">Event</span></span>|<span data-ttu-id="b2bc2-219">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-219">Event ID</span></span>|<span data-ttu-id="b2bc2-220">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="b2bc2-221">255</span><span class="sxs-lookup"><span data-stu-id="b2bc2-221">255</span></span>|<span data-ttu-id="b2bc2-222">Un filtrage des exceptions managées se termine.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="b2bc2-223">Événement ExceptionThrownStop</span><span class="sxs-lookup"><span data-stu-id="b2bc2-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="b2bc2-224">Cet événement est émis lorsque le runtime a terminé de gérer une exception managée qui a été levée.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="b2bc2-225">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-225">Keyword for raising the event</span></span>|<span data-ttu-id="b2bc2-226">Level</span><span class="sxs-lookup"><span data-stu-id="b2bc2-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b2bc2-227">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b2bc2-228">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="b2bc2-228">Informational (4)</span></span>|
  
 <span data-ttu-id="b2bc2-229">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-229">The following table shows event information.</span></span>

|<span data-ttu-id="b2bc2-230">Événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-230">Event</span></span>|<span data-ttu-id="b2bc2-231">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-231">Event ID</span></span>|<span data-ttu-id="b2bc2-232">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b2bc2-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="b2bc2-233">256</span><span class="sxs-lookup"><span data-stu-id="b2bc2-233">256</span></span>|<span data-ttu-id="b2bc2-234">Un filtrage des exceptions managées se termine.</span><span class="sxs-lookup"><span data-stu-id="b2bc2-234">A managed exception filtering ends.</span></span>|
