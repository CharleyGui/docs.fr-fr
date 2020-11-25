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
ms.openlocfilehash: b0d94f5004da85caf0460e8f1d1b2d964944b045
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727066"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="e9ec0-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="e9ec0-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>

<span data-ttu-id="e9ec0-103">Obtient les informations d’adresse native et de frame pour la clause d’exception ( `catch` / `finally` / `filter` ) qui est sur le point d’être exécutée ou qui vient d’être exécutée.</span><span class="sxs-lookup"><span data-stu-id="e9ec0-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ec0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9ec0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9ec0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9ec0-105">Parameters</span></span>  

 `pinfo`  
 <span data-ttu-id="e9ec0-106">à Pointeur vers une structure [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) qui décrit l’instance de la clause d’exception actuelle et son frame associé.</span><span class="sxs-lookup"><span data-stu-id="e9ec0-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9ec0-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="e9ec0-107">Remarks</span></span>  

 <span data-ttu-id="e9ec0-108">Lors de la réception d’une notification d’exception, `GetNotifiedExceptionClauseInfo` peut être utilisé pour obtenir les informations d’adresse native et de frame pour la clause d’exception ( `catch` / `finally` / `filter` ) qui est sur le point d’être exécutée ([ICorProfilerCallback :: ExceptionCatcherEnter,](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback :: ExceptionUnwindFinallyEnter,](icorprofilercallback-exceptionunwindfinallyenter-method.md)ou [ICorProfilerCallback :: ExceptionSearchFilterEnter,](icorprofilercallback-exceptionsearchfilterenter-method.md) le rappel est reçu par le profileur) ou qui vient juste d’être exécutée ([ICorProfilerCallback :: ExceptionCatcherLeave,](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback :: ExceptionUnwindFinallyLeave,](icorprofilercallback-exceptionunwindfinallyleave-method.md)ou [ICorProfilerCallback :: ExceptionSearchFilterLeave,](icorprofilercallback-exceptionsearchfilterleave-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e9ec0-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="e9ec0-109">Cet appel peut être effectué à tout moment après l’un des rappels d’entrée ci-dessus jusqu’à ce que le rappel de fin de correspondance soit reçu ou qu’une exception imbriquée soit levée dans la clause actuelle, auquel cas il n’y a aucune notification de sortie pour cette clause.</span><span class="sxs-lookup"><span data-stu-id="e9ec0-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="e9ec0-110">Notez qu’il n’est pas possible pour une exception levée d’échapper à une `filter` clause d’exception. il y a donc toujours une notification de sortie dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="e9ec0-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9ec0-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e9ec0-111">Requirements</span></span>  

 <span data-ttu-id="e9ec0-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9ec0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9ec0-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9ec0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9ec0-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9ec0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9ec0-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9ec0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ec0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9ec0-116">See also</span></span>

- [<span data-ttu-id="e9ec0-117">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e9ec0-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e9ec0-118">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="e9ec0-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
