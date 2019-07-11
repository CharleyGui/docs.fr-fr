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
ms.openlocfilehash: 66f60b2342b6ff64f1329cbe57032291d5139384
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770588"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="9933f-102">ICorDebugThread::SetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="9933f-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="9933f-103">Définit les indicateurs qui décrivent l’état de débogage de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9933f-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9933f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9933f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9933f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9933f-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="9933f-106">[in] Une combinaison au niveau du bit CorDebugThreadState des valeurs d’énumération qui spécifient l’état de débogage de ce thread.</span><span class="sxs-lookup"><span data-stu-id="9933f-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9933f-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9933f-107">Remarks</span></span>  
 <span data-ttu-id="9933f-108">`SetDebugState` définit l’état de débogage actuel du thread.</span><span class="sxs-lookup"><span data-stu-id="9933f-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="9933f-109">(Le « état de débogage actuel » représente l’état de débogage si le processus de se poursuivre, pas l’état actuel réel). La valeur normale est THREAD_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="9933f-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="9933f-110">Seul le débogueur peut affecter l’état de débogage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="9933f-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="9933f-111">États de débogage dernier à travers continue, donc si vous souhaitez conserver un thread THREAD_SUSPENDed sur plusieurs continue, vous pouvez configurer en une fois et par la suite pas obligé de vous inquiétez pas.</span><span class="sxs-lookup"><span data-stu-id="9933f-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="9933f-112">Suspension des threads et la reprise du processus peuvent provoquer des blocages, même si elle est généralement peu probable.</span><span class="sxs-lookup"><span data-stu-id="9933f-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="9933f-113">Ceci est une qualité intrinsèque des threads et processus et à la conception.</span><span class="sxs-lookup"><span data-stu-id="9933f-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="9933f-114">Un débogueur peut interrompre et reprendre les threads pour arrêter le blocage de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9933f-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="9933f-115">Si l’état du thread utilisateur inclut USER_UNSAFE_POINT, le thread peut bloquer un garbage collection (GC).</span><span class="sxs-lookup"><span data-stu-id="9933f-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="9933f-116">Cela signifie que le thread suspendu a beaucoup plus de risque de provoquer un interblocage.</span><span class="sxs-lookup"><span data-stu-id="9933f-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="9933f-117">Cela peut affecter pas les événements sont déjà en file d’attente de débogage.</span><span class="sxs-lookup"><span data-stu-id="9933f-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="9933f-118">Par conséquent, un débogueur doit purger la file d’attente de la totalité de l’événement (en appelant [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) avant de suspendre ou reprendre des threads.</span><span class="sxs-lookup"><span data-stu-id="9933f-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="9933f-119">Sinon, il peut obtenir des événements sur un thread qu’il pense qu’il a déjà suspendu.</span><span class="sxs-lookup"><span data-stu-id="9933f-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9933f-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9933f-120">Requirements</span></span>  
 <span data-ttu-id="9933f-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9933f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9933f-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9933f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9933f-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9933f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9933f-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9933f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
