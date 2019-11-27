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
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="2ea5b-102">COR_PRF_EX_CLAUSE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="2ea5b-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="2ea5b-103">Stocke des informations sur une instance de clause d'exception spécifique et sa trame associée.</span><span class="sxs-lookup"><span data-stu-id="2ea5b-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ea5b-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2ea5b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2ea5b-105">Members</span></span>  
  
|<span data-ttu-id="2ea5b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2ea5b-106">Member</span></span>|<span data-ttu-id="2ea5b-107">Description</span><span class="sxs-lookup"><span data-stu-id="2ea5b-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="2ea5b-108">Valeur de l’énumération [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) qui spécifie le type de clause d’exception que le code vient d’entrer ou de laisser.</span><span class="sxs-lookup"><span data-stu-id="2ea5b-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="2ea5b-109">Point d’entrée natif du gestionnaire de clauses, par exemple, le contenu du registre de l’élément x86 EIP.</span><span class="sxs-lookup"><span data-stu-id="2ea5b-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="2ea5b-110">Pointeur vers l’image logique du gestionnaire de clause, par exemple, le contenu du Registre x86 EBP.</span><span class="sxs-lookup"><span data-stu-id="2ea5b-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="2ea5b-111">Pointeur vers la pile cachée.</span><span class="sxs-lookup"><span data-stu-id="2ea5b-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="2ea5b-112">Cette valeur est le contenu du Registre BSP et s’applique uniquement à IA64.</span><span class="sxs-lookup"><span data-stu-id="2ea5b-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ea5b-113">Notes</span><span class="sxs-lookup"><span data-stu-id="2ea5b-113">Remarks</span></span>  
 <span data-ttu-id="2ea5b-114">Quand une notification d’exception est reçue, [ICorProfilerInfo2 :: GetNotifiedExceptionClauseInfo,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) peut être utilisé pour obtenir les informations d’adresse native et de frame pour la clause d’exception (`catch`/`finally`/Filter) qui est sur le point d’être exécutée ou qui vient d’être exécutée.</span><span class="sxs-lookup"><span data-stu-id="2ea5b-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="2ea5b-115">L’exécution d’une clause d’exception implique ces rappels du common language runtime (CLR) :</span><span class="sxs-lookup"><span data-stu-id="2ea5b-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="2ea5b-116">ICorProfilerCallback :: ExceptionCatcherEnter,</span><span class="sxs-lookup"><span data-stu-id="2ea5b-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="2ea5b-117">ICorProfilerCallback :: ExceptionUnwindFinallyEnter,</span><span class="sxs-lookup"><span data-stu-id="2ea5b-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="2ea5b-118">ICorProfilerCallback :: ExceptionSearchFilterEnter,</span><span class="sxs-lookup"><span data-stu-id="2ea5b-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="2ea5b-119">ICorProfilerCallback :: ExceptionCatcherLeave,</span><span class="sxs-lookup"><span data-stu-id="2ea5b-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="2ea5b-120">ICorProfilerCallback :: ExceptionUnwindFinallyLeave,</span><span class="sxs-lookup"><span data-stu-id="2ea5b-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="2ea5b-121">ICorProfilerCallback :: ExceptionSearchFilterLeave,</span><span class="sxs-lookup"><span data-stu-id="2ea5b-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="2ea5b-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ea5b-122">Requirements</span></span>  
 <span data-ttu-id="2ea5b-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ea5b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea5b-124">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="2ea5b-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2ea5b-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ea5b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ea5b-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea5b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea5b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea5b-127">See also</span></span>

- [<span data-ttu-id="2ea5b-128">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="2ea5b-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
