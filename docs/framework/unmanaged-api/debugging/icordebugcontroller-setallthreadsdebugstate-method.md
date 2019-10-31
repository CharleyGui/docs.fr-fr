---
title: ICorDebugController::SetAllThreadsDebugState, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: 1190f83e2671216cf1627eeb710ba576e4b2ec93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125361"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="962b1-102">ICorDebugController::SetAllThreadsDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="962b1-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="962b1-103">Définit l’état de débogage de tous les threads managés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="962b1-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="962b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="962b1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="962b1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="962b1-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="962b1-106">dans Valeur de l’énumération « CorDebugThreadState » qui spécifie l’état du thread pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="962b1-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="962b1-107">dans Pointeur vers un objet « ICorDebugThread » qui représente un thread à exempter du paramètre d’état de débogage.</span><span class="sxs-lookup"><span data-stu-id="962b1-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="962b1-108">Si cette valeur est null, aucun thread n’est exempté.</span><span class="sxs-lookup"><span data-stu-id="962b1-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="962b1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="962b1-109">Remarks</span></span>  
 <span data-ttu-id="962b1-110">La méthode `SetAllThreadsDebugState` peut affecter les threads qui ne sont pas visibles via la [méthode EnumerateThreads,](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), de sorte que les threads qui ont été suspendus avec la méthode `SetAllThreadsDebugState` devront être repris avec la méthode `SetAllThreadsDebugState`.</span><span class="sxs-lookup"><span data-stu-id="962b1-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="962b1-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="962b1-111">Requirements</span></span>  
 <span data-ttu-id="962b1-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="962b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="962b1-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="962b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="962b1-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="962b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="962b1-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="962b1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962b1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="962b1-116">See also</span></span>
