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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1c75e1844fca4e592faa924a55432dd42fa7355
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772623"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="3fd4f-102">ICorDebugUnmanagedCallback::DebugEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="3fd4f-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="3fd4f-103">Notifie le débogueur qu’un événement natif a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fd4f-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fd4f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fd4f-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="3fd4f-106">[in] Pointeur vers l’événement natif.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="3fd4f-107">[in] `true`, si l’interaction avec l’état de processus managé est impossible après un événement non managé, jusqu'à ce que le débogueur appelle [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fd4f-108">Notes</span><span class="sxs-lookup"><span data-stu-id="3fd4f-108">Remarks</span></span>  
 <span data-ttu-id="3fd4f-109">Si le thread en cours de débogage est un thread Win32, n’utilisez pas tous les membres de Win32 interface de débogage.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="3fd4f-110">Vous pouvez appeler `ICorDebugController::Continue` uniquement sur un thread Win32 et uniquement lorsque vous continuez après un événement hors-bande.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="3fd4f-111">Le `DebugEvent` rappel ne suit pas les règles standard pour les rappels.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="3fd4f-112">Lorsque vous appelez `DebugEvent`, le processus est dans le texte brut, état arrêté du débogage de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="3fd4f-113">Le processus ne seront pas synchronisé.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-113">The process will not be synchronized.</span></span> <span data-ttu-id="3fd4f-114">Il insère automatiquement l’état synchronisé lorsque cela est nécessaire pour répondre aux demandes d’informations sur le code managé, ce qui peut aboutir dans d’autres imbriqués `DebugEvent` rappels.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="3fd4f-115">Appelez [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) sur le processus pour ignorer un événement d’exception avant de poursuivre le processus.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="3fd4f-116">Appelez cette méthode envoie DBG_CONTINUE au lieu de DBG_EXCEPTION_NOT_HANDLED sur la demande de continuer et efface automatiquement les points d’arrêt hors-bande et les exceptions de la seule étape.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="3fd4f-117">Out-of-band événements peuvent provenir à tout moment, même lorsque l’application en cours de débogage s’affiche arrêtée et lorsqu’un événement dans la bande en attente existe déjà.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="3fd4f-118">Dans le .NET Framework version 2.0, le débogueur doit continuer immédiatement après un événement de point d’arrêt hors-bande.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="3fd4f-119">Le débogueur doit être à l’aide de la [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) et [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) méthodes pour ajouter et supprimer des points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="3fd4f-120">Ces méthodes ignoreront automatiquement les points d’arrêt hors-bande.</span><span class="sxs-lookup"><span data-stu-id="3fd4f-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="3fd4f-121">Par conséquent, les points d’arrêt uniquement out-of-band distribuer doivent être des points d’arrêt bruts qui sont déjà dans le flux d’instructions, tel qu’un appel à la constante Win32 `DebugBreak` (fonction).</span><span class="sxs-lookup"><span data-stu-id="3fd4f-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="3fd4f-122">N’essayez pas d’utiliser `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), ou tout autre membre de la [API de débogage](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="3fd4f-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd4f-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3fd4f-123">Requirements</span></span>  
 <span data-ttu-id="3fd4f-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd4f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd4f-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fd4f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fd4f-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fd4f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fd4f-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd4f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd4f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fd4f-128">See also</span></span>

- [<span data-ttu-id="3fd4f-129">ICorDebugUnmanagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3fd4f-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
