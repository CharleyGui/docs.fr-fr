---
title: ICorProfilerCallback::UnmanagedToManagedTransition, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 8c4e132b90fa1f51bc6f858d75c159af212ec019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439892"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="bcd3d-102">ICorProfilerCallback::UnmanagedToManagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="bcd3d-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="bcd3d-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span><span class="sxs-lookup"><span data-stu-id="bcd3d-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcd3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcd3d-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcd3d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bcd3d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="bcd3d-106">[in] The ID of the function that is being called.</span><span class="sxs-lookup"><span data-stu-id="bcd3d-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="bcd3d-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span><span class="sxs-lookup"><span data-stu-id="bcd3d-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcd3d-108">Notes</span><span class="sxs-lookup"><span data-stu-id="bcd3d-108">Remarks</span></span>  
 <span data-ttu-id="bcd3d-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span><span class="sxs-lookup"><span data-stu-id="bcd3d-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="bcd3d-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span><span class="sxs-lookup"><span data-stu-id="bcd3d-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="bcd3d-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span><span class="sxs-lookup"><span data-stu-id="bcd3d-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcd3d-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="bcd3d-112">Requirements</span></span>  
 <span data-ttu-id="bcd3d-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcd3d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcd3d-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bcd3d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcd3d-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcd3d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcd3d-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcd3d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd3d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcd3d-117">See also</span></span>

- [<span data-ttu-id="bcd3d-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="bcd3d-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bcd3d-119">ManagedToUnmanagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="bcd3d-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="bcd3d-120">Utilisation d’un PInvoke explicite en C++ (attribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="bcd3d-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="bcd3d-121">Utilisation de l’interopérabilité C++ (PInvoke implicite)</span><span class="sxs-lookup"><span data-stu-id="bcd3d-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
