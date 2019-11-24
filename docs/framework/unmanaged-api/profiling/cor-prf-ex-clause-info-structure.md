---
title: COR_PRF_EX_CLAUSE_INFO, structure
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: df4bfe69b22439073342693a03376a0b506f9c70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428372"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="f8981-102">COR_PRF_EX_CLAUSE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="f8981-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="f8981-103">Stocke des informations sur une instance de clause d'exception spécifique et sa trame associée.</span><span class="sxs-lookup"><span data-stu-id="f8981-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8981-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8981-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f8981-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f8981-105">Members</span></span>  
  
|<span data-ttu-id="f8981-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f8981-106">Member</span></span>|<span data-ttu-id="f8981-107">Description</span><span class="sxs-lookup"><span data-stu-id="f8981-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="f8981-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span><span class="sxs-lookup"><span data-stu-id="f8981-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="f8981-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span><span class="sxs-lookup"><span data-stu-id="f8981-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="f8981-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span><span class="sxs-lookup"><span data-stu-id="f8981-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="f8981-111">The pointer to the shadow stack.</span><span class="sxs-lookup"><span data-stu-id="f8981-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="f8981-112">This value is the contents of the BSP register and applies only to IA64.</span><span class="sxs-lookup"><span data-stu-id="f8981-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8981-113">Notes</span><span class="sxs-lookup"><span data-stu-id="f8981-113">Remarks</span></span>  
 <span data-ttu-id="f8981-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span><span class="sxs-lookup"><span data-stu-id="f8981-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="f8981-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="f8981-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="f8981-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="f8981-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="f8981-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="f8981-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="f8981-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="f8981-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="f8981-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="f8981-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="f8981-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="f8981-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="f8981-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="f8981-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="f8981-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="f8981-122">Requirements</span></span>  
 <span data-ttu-id="f8981-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8981-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8981-124">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f8981-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f8981-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8981-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8981-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8981-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8981-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8981-127">See also</span></span>

- [<span data-ttu-id="f8981-128">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="f8981-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
