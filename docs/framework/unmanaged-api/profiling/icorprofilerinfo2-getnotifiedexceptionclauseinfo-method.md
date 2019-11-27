---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: 52ad124638a1c1ec7d39fa41b9163f3ab50ffe70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433070"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="7394b-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="7394b-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="7394b-103">Obtient les informations d’adresse native et de frame pour la clause d’exception (`catch`/`finally`/`filter`) qui est sur le point d’être exécutée ou qui vient d’être exécutée.</span><span class="sxs-lookup"><span data-stu-id="7394b-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7394b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7394b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7394b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7394b-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="7394b-106">à Pointeur vers une structure [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) qui décrit l’instance de la clause d’exception actuelle et son frame associé.</span><span class="sxs-lookup"><span data-stu-id="7394b-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7394b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="7394b-107">Remarks</span></span>  
 <span data-ttu-id="7394b-108">Lors de la réception d’une notification d’exception, `GetNotifiedExceptionClauseInfo` peut être utilisé pour obtenir les informations d’adresse native et de frame pour la clause d’exception (`catch`/`finally`/`filter`) qui est sur le point d’être exécutée ([ICorProfilerCallback :: ExceptionCatcherEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback :: ExceptionUnwindFinallyEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)ou [ICorProfilerCallback :: ExceptionSearchFilterEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) rappel est reçu par le profileur) ou vient d’être exécutée ([ICorProfilerCallback :: ExceptionCatcherLeave, ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback :: ExceptionUnwindFinallyLeave,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)ou [ICorProfilerCallback :: ExceptionSearchFilterLeave,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) est reçu par le profileur).</span><span class="sxs-lookup"><span data-stu-id="7394b-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="7394b-109">Cet appel peut être effectué à tout moment après l’un des rappels d’entrée ci-dessus jusqu’à ce que le rappel de fin de correspondance soit reçu ou qu’une exception imbriquée soit levée dans la clause actuelle, auquel cas il n’y a aucune notification de sortie pour cette clause.</span><span class="sxs-lookup"><span data-stu-id="7394b-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="7394b-110">Notez qu’il n’est pas possible pour une exception levée d’échapper à une clause d’exception `filter`. il y a donc toujours une notification de sortie dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="7394b-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7394b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7394b-111">Requirements</span></span>  
 <span data-ttu-id="7394b-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7394b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7394b-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7394b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7394b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7394b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7394b-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7394b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7394b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7394b-116">See also</span></span>

- [<span data-ttu-id="7394b-117">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="7394b-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7394b-118">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="7394b-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
