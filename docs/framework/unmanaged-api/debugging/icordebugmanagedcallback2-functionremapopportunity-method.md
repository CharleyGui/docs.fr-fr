---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24f058ff11a1155aa53a1d1f222ff1230c1c23e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760981"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="925e2-102">ICorDebugManagedCallback2::FunctionRemapOpportunity, méthode</span><span class="sxs-lookup"><span data-stu-id="925e2-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="925e2-103">Notifie le débogueur que l’exécution de code a atteint un point de séquence dans une version antérieure d’une fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="925e2-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="925e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="925e2-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="925e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="925e2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="925e2-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="925e2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="925e2-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel le point d’arrêt de remappage a été rencontrée.</span><span class="sxs-lookup"><span data-stu-id="925e2-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="925e2-108">[in] Pointeur vers un objet ICorDebugFunction qui représente la version de la fonction qui est en cours d’exécution sur le thread.</span><span class="sxs-lookup"><span data-stu-id="925e2-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="925e2-109">[in] Pointeur vers un objet ICorDebugFunction qui représente la dernière version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="925e2-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="925e2-110">[in] L’offset Microsoft intermediate language (MSIL), du pointeur d’instruction dans l’ancienne version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="925e2-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="925e2-111">Notes</span><span class="sxs-lookup"><span data-stu-id="925e2-111">Remarks</span></span>  
 <span data-ttu-id="925e2-112">Ce rappel permet au débogueur de remapper le pointeur d’instruction à son emplacement approprié dans la nouvelle version de la fonction spécifiée en appelant le [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="925e2-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="925e2-113">Si le débogueur n’appelle pas `RemapFunction` avant d’appeler le [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) (méthode), le runtime continue à exécuter l’ancien code et déclenchera un autre `FunctionRemapOpportunity` rappel au point de séquence suivant.</span><span class="sxs-lookup"><span data-stu-id="925e2-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="925e2-114">Ce rappel est appelé pour chaque trame qui exécute une version antérieure de la fonction donnée jusqu'à ce que le débogueur retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="925e2-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="925e2-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="925e2-115">Requirements</span></span>  
 <span data-ttu-id="925e2-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="925e2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="925e2-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="925e2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="925e2-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="925e2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="925e2-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="925e2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="925e2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="925e2-120">See also</span></span>

- [<span data-ttu-id="925e2-121">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="925e2-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="925e2-122">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="925e2-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
