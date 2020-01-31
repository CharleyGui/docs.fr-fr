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
ms.openlocfilehash: bc6543b46200dd611e13bdf55aabfabd8302e70a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793334"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="83e10-102">ICorDebugManagedCallback2::FunctionRemapOpportunity, méthode</span><span class="sxs-lookup"><span data-stu-id="83e10-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="83e10-103">Notifie le débogueur que l’exécution du code a atteint un point de séquence dans une version antérieure d’une fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="83e10-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83e10-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e10-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="83e10-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="83e10-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="83e10-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="83e10-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel le point d’arrêt de remappage a été rencontré.</span><span class="sxs-lookup"><span data-stu-id="83e10-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="83e10-108">dans Pointeur vers un objet ICorDebugFunction qui représente la version de la fonction en cours d’exécution sur le thread.</span><span class="sxs-lookup"><span data-stu-id="83e10-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="83e10-109">dans Pointeur vers un objet ICorDebugFunction qui représente la version la plus récente de la fonction.</span><span class="sxs-lookup"><span data-stu-id="83e10-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="83e10-110">dans Offset MSIL (Microsoft Intermediate Language) du pointeur d’instruction dans l’ancienne version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="83e10-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83e10-111">Notes</span><span class="sxs-lookup"><span data-stu-id="83e10-111">Remarks</span></span>  
 <span data-ttu-id="83e10-112">Ce rappel permet au débogueur d’avoir la possibilité de remapper le pointeur d’instruction à son emplacement approprié dans la nouvelle version de la fonction spécifiée en appelant la méthode [ICorDebugILFrame2 :: RemapFunction,](icordebugilframe2-remapfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83e10-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="83e10-113">Si le débogueur n’appelle pas `RemapFunction` avant d’appeler la méthode [ICorDebugController :: continue](icordebugcontroller-continue-method.md) , le runtime continuera à exécuter l’ancien code et déclenchera un autre rappel `FunctionRemapOpportunity` au point de séquence suivant.</span><span class="sxs-lookup"><span data-stu-id="83e10-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="83e10-114">Ce rappel sera appelé pour chaque frame qui exécute une version antérieure de la fonction donnée jusqu’à ce que le débogueur retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="83e10-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e10-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="83e10-115">Requirements</span></span>  
 <span data-ttu-id="83e10-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e10-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e10-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83e10-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83e10-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83e10-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83e10-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e10-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e10-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83e10-120">See also</span></span>

- [<span data-ttu-id="83e10-121">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="83e10-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="83e10-122">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="83e10-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
