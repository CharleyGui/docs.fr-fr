---
title: ICorDebugThread::SetDebugState, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e18888e307a14c4396966afc0a623e1acba104
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332809"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="2fd8e-102">ICorDebugThread::SetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="2fd8e-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="2fd8e-103">Définit des indicateurs qui décrivent l’état de débogage de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fd8e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fd8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2fd8e-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="2fd8e-106">dans Combinaison d’opérations de bits de valeurs d’énumération CorDebugThreadState qui spécifient l’état de débogage de ce thread.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fd8e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2fd8e-107">Remarks</span></span>  
 <span data-ttu-id="2fd8e-108">`SetDebugState` définit l’état de débogage actuel du thread.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="2fd8e-109">(L’état de débogage actuel représente l’état de débogage si le processus devait être poursuivi, et non l’état actuel réel.) La valeur normale pour ce est THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="2fd8e-110">Seul le débogueur peut affecter l’état de débogage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="2fd8e-111">Les États de débogage se trouvent en dernier. par conséquent, si vous souhaitez conserver un thread THREAD_SUSPENDed sur plusieurs continues, vous pouvez le définir une fois et ne pas avoir à vous en soucier.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="2fd8e-112">Le fait de suspendre des threads et de reprendre le processus peut provoquer des blocages, bien qu’il soit généralement peu probable.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="2fd8e-113">Il s’agit d’une qualité intrinsèque de threads et de processus et est par conception.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="2fd8e-114">Un débogueur peut interrompre et reprendre de manière asynchrone les threads pour interrompre le blocage.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="2fd8e-115">Si l’état utilisateur du thread comprend USER_UNSAFE_POINT, le thread peut bloquer un garbage collection (GC).</span><span class="sxs-lookup"><span data-stu-id="2fd8e-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="2fd8e-116">Cela signifie que le thread suspendu a une probabilité plus élevée de provoquer un blocage.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="2fd8e-117">Cela peut ne pas affecter les événements de débogage déjà en file d’attente.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="2fd8e-118">Par conséquent, un débogueur doit vider la totalité de la file d’attente des événements (en appelant [ICorDebugController :: HasQueuedCallbacks,](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) avant d’interrompre ou de reprendre des threads.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="2fd8e-119">Sinon, il peut obtenir des événements sur un thread qu’il pense avoir déjà suspendu.</span><span class="sxs-lookup"><span data-stu-id="2fd8e-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd8e-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2fd8e-120">Requirements</span></span>  
 <span data-ttu-id="2fd8e-121">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fd8e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd8e-122">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2fd8e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fd8e-123">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fd8e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd8e-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd8e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
