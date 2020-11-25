---
title: Énumérations de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: bdd4b60d068677ae2a0874b589294ba220f0d854
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722997"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="89179-102">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="89179-102">Debugging Enumerations</span></span>

<span data-ttu-id="89179-103">Cette section décrit les énumérations non managées utilisées par l'API de débogage.</span><span class="sxs-lookup"><span data-stu-id="89179-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89179-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="89179-104">In This Section</span></span>  

 [<span data-ttu-id="89179-105">CLR_DEBUGGING_PROCESS_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="89179-106">Fournit des valeurs utilisées par la méthode [ICLRDebugging :: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89179-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="89179-107">CLRDataEnumMemoryFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="89179-108">Indique les régions de mémoire qu’un appel à la méthode [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) doit inclure.</span><span class="sxs-lookup"><span data-stu-id="89179-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="89179-109">COR_PUB_ENUMPROCESS, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="89179-110">Identifie le type de processus à énumérer.</span><span class="sxs-lookup"><span data-stu-id="89179-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="89179-111">CorDebugBlockingReason, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="89179-112">Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.</span><span class="sxs-lookup"><span data-stu-id="89179-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="89179-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="89179-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="89179-114">Indique la ou les raisons de la mise en route d'une chaîne d'appels.</span><span class="sxs-lookup"><span data-stu-id="89179-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="89179-115">CorDebugCodeInvokeKind, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="89179-116">Indique de quelle manière une fonction exportée appelle du code managé.</span><span class="sxs-lookup"><span data-stu-id="89179-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="89179-117">CorDebugCodeInvokePurpose, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="89179-118">Indique pourquoi une fonction exportée appelle du code managé.</span><span class="sxs-lookup"><span data-stu-id="89179-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="89179-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="89179-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="89179-120">Fournit des options de débogage supplémentaires qui peuvent être utilisées dans un appel à la méthode [ICorDebug :: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89179-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="89179-121">CorDebugDebugEventKind, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="89179-122">Indique le type d’événement dont les informations sont décodées par la méthode [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89179-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="89179-123">CorDebugDecodeEventFlagsWindows, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="89179-124">Fournit des informations supplémentaires sur les événements de débogage propres à la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="89179-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="89179-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="89179-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="89179-126">Indique le type de rappel effectué à partir d’un événement [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89179-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="89179-127">CorDebugExceptionFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="89179-128">Fournit des informations supplémentaires sur une exception.</span><span class="sxs-lookup"><span data-stu-id="89179-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="89179-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="89179-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="89179-130">Indique l'événement qui est signalé par le rappel lors de la phase de déroulement.</span><span class="sxs-lookup"><span data-stu-id="89179-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="89179-131">CorDebugGCType, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="89179-132">Indique si le récupérateur de mémoire s'exécute sur une station de travail ou sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="89179-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="89179-133">CorDebugGenerationTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="89179-134">Spécifie la génération d’une région de la mémoire sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="89179-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="89179-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="89179-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="89179-136">Indique le type de handle.</span><span class="sxs-lookup"><span data-stu-id="89179-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="89179-137">CorDebugIlToNativeMappingTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="89179-138">Indique si une plage particulière d'instructions natives correspond à une région spéciale du code.</span><span class="sxs-lookup"><span data-stu-id="89179-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="89179-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="89179-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="89179-140">Indique les types de code qui peuvent l'objet d'une exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="89179-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="89179-141">CorDebugInterfaceVersion, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="89179-142">Spécifie une version de .NET Framework ou la version de .NET Framework où une interface a été introduite.</span><span class="sxs-lookup"><span data-stu-id="89179-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="89179-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="89179-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="89179-144">Identifie le type de frame de pile.</span><span class="sxs-lookup"><span data-stu-id="89179-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="89179-145">CorDebugJITCompilerFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="89179-146">Contient des valeurs qui influencent le comportement du compilateur juste-à-temps managé.</span><span class="sxs-lookup"><span data-stu-id="89179-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="89179-147">CorDebugJITCompilerFlagsDeprecated, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="89179-148">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="89179-148">Obsolete.</span></span> <span data-ttu-id="89179-149">Utilisez à la `CORDEBUG_JIT_DEFAULT` place le membre de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="89179-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="89179-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="89179-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="89179-151">Fournit les détails sur la façon dont la valeur du pointeur d'instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="89179-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="89179-152">CorDebugMDAFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="89179-153">Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.</span><span class="sxs-lookup"><span data-stu-id="89179-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="89179-154">CorDebugNGenPolicy, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="89179-155">Fournit une valeur qui détermine si un débogueur charge les images natives (NGen) depuis le cache d'images natives.</span><span class="sxs-lookup"><span data-stu-id="89179-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="89179-156">CorDebugPlatform, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="89179-157">Fournit les valeurs de plateforme cible utilisées par la méthode [ICorDebugDataTarget :: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89179-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="89179-158">CorDebugRecordFormat, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="89179-159">Décrit le format des données dans un tableau d'octets qui contient des informations sur un événement de débogage d'exception native.</span><span class="sxs-lookup"><span data-stu-id="89179-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="89179-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="89179-160">CorDebugRegister</span></span>  
 <span data-ttu-id="89179-161">Spécifie les registres associés à une architecture de processeur donnée.</span><span class="sxs-lookup"><span data-stu-id="89179-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="89179-162">CorDebugSetContextFlag, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="89179-163">Indique si le contexte provient du frame (ou feuille) actif ou s'il a été calculé par déroulement à partir d'un autre frame.</span><span class="sxs-lookup"><span data-stu-id="89179-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="89179-164">CorDebugStateChange, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="89179-165">Représente la quantité de données mises en cache à ignorer sur la base des modifications apportées au processus.</span><span class="sxs-lookup"><span data-stu-id="89179-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="89179-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="89179-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="89179-167">Indique le résultat d'une étape individuelle.</span><span class="sxs-lookup"><span data-stu-id="89179-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="89179-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="89179-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="89179-169">Spécifie l'état d'un thread pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="89179-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="89179-170">\>CorDebugUnmappedStop,</span><span class="sxs-lookup"><span data-stu-id="89179-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="89179-171">Spécifie le type de code non mappé qui peut déclencher un arrêt dans l'exécution du code par l'exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="89179-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="89179-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="89179-172">CorDebugUserState</span></span>  
 <span data-ttu-id="89179-173">Indique l'état de l'utilisateur d'un thread.</span><span class="sxs-lookup"><span data-stu-id="89179-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="89179-174">CorGCReferenceType, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="89179-175">Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.</span><span class="sxs-lookup"><span data-stu-id="89179-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="89179-176">ILCodeKind, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="89179-177">Fournit des valeurs qui spécifient si le débogueur peut accéder aux variables locales ou au code ajoutés dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="89179-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="89179-178">LoggingLevelEnum, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="89179-179">Indique le niveau de gravité d'un message de description qui est écrit dans le journal des événements quand un thread managé consigne un événement.</span><span class="sxs-lookup"><span data-stu-id="89179-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="89179-180">LogSwitchCallReason, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="89179-181">Indique l'opération qui a été effectuée sur un commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="89179-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="89179-182">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="89179-183">Indique le type d’emplacement natif d’une variable.</span><span class="sxs-lookup"><span data-stu-id="89179-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="89179-184">WriteableMetadataUpdateMode, énumération</span><span class="sxs-lookup"><span data-stu-id="89179-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="89179-185">Fournit des valeurs qui spécifient si les mises à jour en mémoire apportées aux métadonnées sont visibles par un débogueur.</span><span class="sxs-lookup"><span data-stu-id="89179-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="89179-186">[Énumération ClrDataSourceType](clrdatasourcetype-enumeration.md) Fournit des valeurs utilisées par la structure CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="89179-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="89179-187">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="89179-187">Related Sections</span></span>  

 [<span data-ttu-id="89179-188">Débogage des coclasses</span><span class="sxs-lookup"><span data-stu-id="89179-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="89179-189">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="89179-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="89179-190">Fonctions statiques globales du débogage</span><span class="sxs-lookup"><span data-stu-id="89179-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="89179-191">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="89179-191">Debugging Structures</span></span>](debugging-structures.md)
