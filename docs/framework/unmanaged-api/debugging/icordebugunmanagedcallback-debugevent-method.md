---
title: ICorDebugUnmanagedCallback::DebugEvent, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: 24c316ea6bab11fb55e8e0fc1dc9832a312dbc6a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397197"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="7595f-102">ICorDebugUnmanagedCallback::DebugEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="7595f-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="7595f-103">Notifie le débogueur qu’un événement natif a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="7595f-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7595f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7595f-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7595f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7595f-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="7595f-106">dans Pointeur vers l’événement natif.</span><span class="sxs-lookup"><span data-stu-id="7595f-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="7595f-107">[in] `true` , si l’interaction avec l’état de processus managé est impossible après un événement non managé, jusqu’à ce que le débogueur appelle [ICorDebugController :: continue](icordebugcontroller-continue-method.md); sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="7595f-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7595f-108">Notes</span><span class="sxs-lookup"><span data-stu-id="7595f-108">Remarks</span></span>  
 <span data-ttu-id="7595f-109">Si le thread en cours de débogage est un thread Win32, n’utilisez pas les membres de l’interface de débogage Win32.</span><span class="sxs-lookup"><span data-stu-id="7595f-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="7595f-110">Vous pouvez appeler `ICorDebugController::Continue` uniquement sur un thread Win32 et uniquement en cas de dépassement d’un événement hors bande.</span><span class="sxs-lookup"><span data-stu-id="7595f-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="7595f-111">Le `DebugEvent` rappel ne suit pas les règles standard pour les rappels.</span><span class="sxs-lookup"><span data-stu-id="7595f-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="7595f-112">Lorsque vous appelez `DebugEvent` , le processus sera à l’état d’arrêt de débogage du système d’exploitation brut.</span><span class="sxs-lookup"><span data-stu-id="7595f-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="7595f-113">Le processus ne sera pas synchronisé.</span><span class="sxs-lookup"><span data-stu-id="7595f-113">The process will not be synchronized.</span></span> <span data-ttu-id="7595f-114">Elle entrera automatiquement en état synchronisé si nécessaire pour répondre aux demandes d’informations sur le code managé, ce qui peut entraîner d’autres `DebugEvent` rappels imbriqués.</span><span class="sxs-lookup"><span data-stu-id="7595f-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="7595f-115">Appelez [ICorDebugProcess :: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) sur le processus pour ignorer un événement d’exception avant de poursuivre le processus.</span><span class="sxs-lookup"><span data-stu-id="7595f-115">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="7595f-116">L’appel de cette méthode envoie DBG_CONTINUE au lieu de DBG_EXCEPTION_NOT_HANDLED sur la demande de reprise, et efface automatiquement les points d’arrêt hors bande et les exceptions en une seule étape.</span><span class="sxs-lookup"><span data-stu-id="7595f-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="7595f-117">Les événements hors bande peuvent se trouver à tout moment, même lorsque l’application en cours de débogage apparaît comme arrêtée et lorsqu’un événement intrabande en suspens existe déjà.</span><span class="sxs-lookup"><span data-stu-id="7595f-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="7595f-118">Dans la version de .NET Framework 2,0, le débogueur doit immédiatement continuer après un événement de point d’arrêt hors plage.</span><span class="sxs-lookup"><span data-stu-id="7595f-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="7595f-119">Le débogueur doit utiliser les méthodes [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md) et [ICorDebugProcess2 :: ClearUnmanagedBreakpoint,](icordebugprocess2-clearunmanagedbreakpoint-method.md) pour ajouter et supprimer des points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="7595f-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="7595f-120">Ces méthodes ignorent automatiquement les points d’arrêt hors bande.</span><span class="sxs-lookup"><span data-stu-id="7595f-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="7595f-121">Ainsi, les seuls points d’arrêt hors bande qui sont distribués doivent être des points d’arrêt bruts qui se trouvent déjà dans le flux d’instructions, par exemple un appel à la `DebugBreak` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="7595f-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="7595f-122">N’essayez pas d’utiliser `ICorDebugProcess::ClearCurrentException` , [ICorDebugProcess :: GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess :: SetThreadContext](icordebugprocess-setthreadcontext-method.md)ni un autre membre de l' [API de débogage](index.md).</span><span class="sxs-lookup"><span data-stu-id="7595f-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7595f-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7595f-123">Requirements</span></span>  
 <span data-ttu-id="7595f-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7595f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7595f-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7595f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7595f-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7595f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7595f-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7595f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7595f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7595f-128">See also</span></span>

- [<span data-ttu-id="7595f-129">ICorDebugUnmanagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="7595f-129">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
