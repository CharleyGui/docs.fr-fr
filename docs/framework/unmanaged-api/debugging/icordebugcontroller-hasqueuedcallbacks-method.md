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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d17f51867b64780fca9b21c5f48c88db36343af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748786"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="3c534-102">ICorDebugController::HasQueuedCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="3c534-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="3c534-103">Obtient une valeur qui indique si des rappels managés sont actuellement en file d’attente pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="3c534-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c534-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c534-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c534-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3c534-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="3c534-106">[in] Pointeur vers un objet « ICorDebugThread » qui représente le thread.</span><span class="sxs-lookup"><span data-stu-id="3c534-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="3c534-107">[out] Un pointeur vers une valeur qui est `true` si des rappels managés sont actuellement en file d’attente pour le thread spécifié ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="3c534-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="3c534-108">Si null est spécifié pour le `pThread` paramètre, `HasQueuedCallbacks` retournera `true` s’il existe actuellement géré les rappels en attente de n’importe quel thread.</span><span class="sxs-lookup"><span data-stu-id="3c534-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c534-109">Notes</span><span class="sxs-lookup"><span data-stu-id="3c534-109">Remarks</span></span>  
 <span data-ttu-id="3c534-110">Les rappels sont distribués un par un, chaque fois [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) est appelée.</span><span class="sxs-lookup"><span data-stu-id="3c534-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="3c534-111">Le débogueur peut contrôler cet indicateur si elle souhaite créer un rapport se produisent simultanément plusieurs événements de débogage.</span><span class="sxs-lookup"><span data-stu-id="3c534-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="3c534-112">Lorsque les événements de débogage sont en attente, ils ont déjà eu lieu, afin du débogueur doit vider la file d’attente entière pour être sûr que de l’état de l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="3c534-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="3c534-113">(Appelez `ICorDebugController::Continue` pour vider la file d’attente.) Par exemple, si la file d’attente contient deux événements de débogage sur le thread *X*, et le débogueur suspend le thread *X* après le premier événement de débogage, puis appelle `ICorDebugController::Continue`, le deuxième événement de débogage pour thread *X* seront distribués bien que le thread a été suspendu.</span><span class="sxs-lookup"><span data-stu-id="3c534-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c534-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3c534-114">Requirements</span></span>  
 <span data-ttu-id="3c534-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c534-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c534-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c534-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c534-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c534-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c534-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c534-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c534-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c534-119">See also</span></span>
