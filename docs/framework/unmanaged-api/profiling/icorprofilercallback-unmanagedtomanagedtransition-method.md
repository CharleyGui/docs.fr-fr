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
ms.openlocfilehash: 8734fa9c9418b818cbe14ebe87ce2af6fa59c078
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499842"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="88f51-102">ICorProfilerCallback::UnmanagedToManagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="88f51-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="88f51-103">Notifie le profileur qu’une transition du code non managé au code managé s’est produite.</span><span class="sxs-lookup"><span data-stu-id="88f51-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88f51-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88f51-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="88f51-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="88f51-106">dans ID de la fonction appelée.</span><span class="sxs-lookup"><span data-stu-id="88f51-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="88f51-107">dans Valeur de l’énumération [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) qui indique si la transition s’est produite en raison d’un appel dans du code managé à partir de code non managé, ou à cause d’un retour d’une fonction non managée appelée par une fonction managée.</span><span class="sxs-lookup"><span data-stu-id="88f51-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88f51-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="88f51-108">Remarks</span></span>  
 <span data-ttu-id="88f51-109">Si la valeur de `reason` est COR_PRF_TRANSITION_RETURN et `functionId` n’est pas null, l’ID de fonction est celui de la fonction non managée et n’aura jamais été compilé à l’aide du compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="88f51-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="88f51-110">Des informations de base sont associées aux fonctions non managées, telles qu’un nom et des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="88f51-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="88f51-111">Si la valeur de `reason` est COR_PRF_TRANSITION_CALL, il est possible que la fonction appelée (autrement dit, la fonction managée) n’ait pas encore été compilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="88f51-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88f51-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="88f51-112">Requirements</span></span>  
 <span data-ttu-id="88f51-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88f51-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88f51-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88f51-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88f51-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88f51-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88f51-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88f51-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f51-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88f51-117">See also</span></span>

- [<span data-ttu-id="88f51-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="88f51-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="88f51-119">ManagedToUnmanagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="88f51-119">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="88f51-120">Utilisation d’un PInvoke explicite en C++ (attribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="88f51-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="88f51-121">Utilisation de l’interopérabilité C++ (PInvoke implicite)</span><span class="sxs-lookup"><span data-stu-id="88f51-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
