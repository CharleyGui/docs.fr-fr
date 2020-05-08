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
ms.openlocfilehash: c2e8aaa2774e3e2699a73c40804391ca245047b1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976588"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="08565-102">ICorDebugController::SetAllThreadsDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="08565-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="08565-103">Définit l’état de débogage de tous les threads managés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="08565-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08565-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08565-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08565-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08565-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="08565-106">dans Valeur de l’énumération « CorDebugThreadState » qui spécifie l’état du thread pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="08565-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="08565-107">dans Pointeur vers un objet « ICorDebugThread » qui représente un thread à exempter du paramètre d’état de débogage.</span><span class="sxs-lookup"><span data-stu-id="08565-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="08565-108">Si cette valeur est null, aucun thread n’est exempté.</span><span class="sxs-lookup"><span data-stu-id="08565-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08565-109">Notes </span><span class="sxs-lookup"><span data-stu-id="08565-109">Remarks</span></span>  
 <span data-ttu-id="08565-110">La `SetAllThreadsDebugState` méthode peut affecter les threads qui ne sont pas visibles via la [méthode EnumerateThreads,](icordebugcontroller-enumeratethreads-method.md), de sorte que `SetAllThreadsDebugState` les threads qui ont été interrompus avec `SetAllThreadsDebugState` la méthode doivent être repris avec la méthode.</span><span class="sxs-lookup"><span data-stu-id="08565-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08565-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="08565-111">Requirements</span></span>  
 <span data-ttu-id="08565-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08565-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08565-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08565-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08565-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08565-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08565-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08565-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08565-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08565-116">See also</span></span>
