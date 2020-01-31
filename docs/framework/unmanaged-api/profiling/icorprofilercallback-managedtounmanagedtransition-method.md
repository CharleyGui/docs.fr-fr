---
title: ICorProfilerCallback::ManagedToUnmanagedTransition, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 0750ac66c654285e11dbbb5941f029bf5f900842
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866193"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="e1b6a-102">ICorProfilerCallback::ManagedToUnmanagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="e1b6a-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="e1b6a-103">Notifie le profileur qu’une transition du code managé au code non managé s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e1b6a-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1b6a-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1b6a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e1b6a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e1b6a-106">dans ID de la fonction appelée.</span><span class="sxs-lookup"><span data-stu-id="e1b6a-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="e1b6a-107">dans Valeur de l’énumération [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) qui indique si la transition s’est produite en raison d’un appel dans du code non managé à partir du code managé, ou à cause d’un retour d’une fonction managée appelée par un qui n’est pas géré.</span><span class="sxs-lookup"><span data-stu-id="e1b6a-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1b6a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e1b6a-108">Remarks</span></span>  
 <span data-ttu-id="e1b6a-109">Si la valeur de `reason` est COR_PRF_TRANSITION_CALL, l’ID de fonction est celui de la fonction non managée, qui n’a jamais été compilée à l’aide du compilateur juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="e1b6a-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="e1b6a-110">Les fonctions non managées sont associées à des informations de base, telles qu’un nom et des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e1b6a-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="e1b6a-111">Si la fonction non managée a été appelée à l’aide d’un appel de code non managé implicite (PInvoke), le runtime ne peut pas déterminer la destination de l’appel et la valeur de `functionId` sera null.</span><span class="sxs-lookup"><span data-stu-id="e1b6a-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="e1b6a-112">Pour plus d’informations sur PInvoke implicite, consultez [utilisation de C++ l’interopérabilité (PInvoke implicite)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="e1b6a-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1b6a-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e1b6a-113">Requirements</span></span>  
 <span data-ttu-id="e1b6a-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1b6a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1b6a-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1b6a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1b6a-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1b6a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1b6a-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1b6a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b6a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1b6a-118">See also</span></span>

- [<span data-ttu-id="e1b6a-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e1b6a-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e1b6a-120">UnmanagedToManagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="e1b6a-120">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="e1b6a-121">Utilisation d’un PInvoke explicite en C++ (attribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="e1b6a-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
