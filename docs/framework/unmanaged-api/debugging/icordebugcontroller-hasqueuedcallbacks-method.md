---
title: ICorDebugController::HasQueuedCallbacks, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: c33193bd64030852441c7ca60cee4a000b09156c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788915"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="e7cfc-102">ICorDebugController::HasQueuedCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="e7cfc-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="e7cfc-103">Obtient une valeur qui indique si tous les rappels managés sont actuellement mis en file d’attente pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7cfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7cfc-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7cfc-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e7cfc-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="e7cfc-106">dans Pointeur vers un objet « ICorDebugThread » qui représente le thread.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="e7cfc-107">à Pointeur vers une valeur `true` si des rappels managés sont actuellement mis en file d’attente pour le thread spécifié ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="e7cfc-108">Si null est spécifié pour le paramètre `pThread`, `HasQueuedCallbacks` retournera `true` s’il existe actuellement des rappels managés en file d’attente pour n’importe quel thread.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7cfc-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e7cfc-109">Remarks</span></span>  
 <span data-ttu-id="e7cfc-110">Les rappels sont distribués un par un, à chaque fois que [ICorDebugController :: continue](icordebugcontroller-continue-method.md) est appelé.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="e7cfc-111">Le débogueur peut vérifier cet indicateur s’il souhaite signaler plusieurs événements de débogage qui se produisent simultanément.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="e7cfc-112">Lorsque les événements de débogage sont mis en file d’attente, ils se sont déjà produits, de sorte que le débogueur doit vider la file d’attente entière pour garantir l’état de l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="e7cfc-113">(Appelez `ICorDebugController::Continue` pour vider la file d’attente.) Par exemple, si la file d’attente contient deux événements de débogage sur le thread *x*et que le débogueur interrompt le thread *x* après le premier événement de débogage, puis appelle `ICorDebugController::Continue`, le deuxième événement de débogage pour le thread *x* est distribué même si le thread a été suspendu.</span><span class="sxs-lookup"><span data-stu-id="e7cfc-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7cfc-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e7cfc-114">Requirements</span></span>  
 <span data-ttu-id="e7cfc-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7cfc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7cfc-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7cfc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7cfc-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7cfc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7cfc-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7cfc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cfc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7cfc-119">See also</span></span>
