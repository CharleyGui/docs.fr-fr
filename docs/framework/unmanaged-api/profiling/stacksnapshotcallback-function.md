---
title: StackSnapshotCallback (fonction)
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: 49e154ade91ea1a207645f924bd8aea1dbdb635c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868120"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="92277-102">StackSnapshotCallback (fonction)</span><span class="sxs-lookup"><span data-stu-id="92277-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="92277-103">Fournit au profileur des informations sur chaque frame managé et chaque série de frames non managés sur la pile pendant un parcours de pile, qui est initié par la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92277-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92277-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92277-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92277-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="92277-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="92277-106">dans Si cette valeur est égale à zéro, ce rappel est destiné à une exécution de frames non managés. dans le cas contraire, il s’agit de l’identificateur d’une fonction managée et ce rappel est destiné à un frame managé.</span><span class="sxs-lookup"><span data-stu-id="92277-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="92277-107">dans Valeur du pointeur d’instruction de code natif dans le frame.</span><span class="sxs-lookup"><span data-stu-id="92277-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="92277-108">dans Valeur `COR_PRF_FRAME_INFO` qui référence des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="92277-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="92277-109">Cette valeur est valide pour une utilisation uniquement pendant ce rappel.</span><span class="sxs-lookup"><span data-stu-id="92277-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="92277-110">dans Taille de la structure `CONTEXT`, qui est référencée par le paramètre `context`.</span><span class="sxs-lookup"><span data-stu-id="92277-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="92277-111">dans Pointeur vers une structure de `CONTEXT` Win32 qui représente l’état de l’UC pour ce frame.</span><span class="sxs-lookup"><span data-stu-id="92277-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="92277-112">Le paramètre `context` est valide uniquement si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé dans `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="92277-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="92277-113">dans Pointeur vers les données du client, qui est transmis directement à partir de `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="92277-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92277-114">Notes</span><span class="sxs-lookup"><span data-stu-id="92277-114">Remarks</span></span>  
 <span data-ttu-id="92277-115">La fonction `StackSnapshotCallback` est implémentée par le writer du profileur.</span><span class="sxs-lookup"><span data-stu-id="92277-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="92277-116">Vous devez limiter la complexité du travail effectué dans `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="92277-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="92277-117">Par exemple, lorsque vous utilisez `ICorProfilerInfo2::DoStackSnapshot` de manière asynchrone, le thread cible peut contenir des verrous.</span><span class="sxs-lookup"><span data-stu-id="92277-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="92277-118">Si le code dans `StackSnapshotCallback` requiert les mêmes verrous, un interblocage peut se défaire.</span><span class="sxs-lookup"><span data-stu-id="92277-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="92277-119">La méthode `ICorProfilerInfo2::DoStackSnapshot` appelle la fonction `StackSnapshotCallback` une fois par frame managé ou une fois par exécution de frames non managés.</span><span class="sxs-lookup"><span data-stu-id="92277-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="92277-120">Si `StackSnapshotCallback` est appelée pour une série de frames non managés, le profileur peut utiliser le contexte de Registre (référencé par le paramètre `context`) pour effectuer son propre parcours de pile non managé.</span><span class="sxs-lookup"><span data-stu-id="92277-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="92277-121">Dans ce cas, la structure de `CONTEXT` Win32 représente l’état du processeur pour le dernier frame ayant fait l’objet d’un push dans l’exécution de frames non managés.</span><span class="sxs-lookup"><span data-stu-id="92277-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="92277-122">Bien que la structure de `CONTEXT` Win32 comprenne des valeurs pour tous les registres, vous devez vous fier uniquement aux valeurs du registre de pointeur de pile, du registre de pointeur de frame, du registre de pointeur d’instruction et des registres d’entiers non volatiles (autrement dit, conservés).</span><span class="sxs-lookup"><span data-stu-id="92277-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92277-123">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="92277-123">Requirements</span></span>  
 <span data-ttu-id="92277-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92277-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92277-125">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="92277-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="92277-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92277-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92277-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92277-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92277-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92277-128">See also</span></span>

- [<span data-ttu-id="92277-129">DoStackSnapshot, méthode</span><span class="sxs-lookup"><span data-stu-id="92277-129">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="92277-130">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="92277-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
