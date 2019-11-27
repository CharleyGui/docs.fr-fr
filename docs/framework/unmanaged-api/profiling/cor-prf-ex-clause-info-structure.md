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
# <a name="cor_prf_ex_clause_info-structure"></a>COR_PRF_EX_CLAUSE_INFO, structure
Stocke des informations sur une instance de clause d'exception spécifique et sa trame associée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`clauseType`|Valeur de l’énumération [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) qui spécifie le type de clause d’exception que le code vient d’entrer ou de laisser.|  
|`programCounter`|Point d’entrée natif du gestionnaire de clauses, par exemple, le contenu du registre de l’élément x86 EIP.|  
|`framePointer`|Pointeur vers l’image logique du gestionnaire de clause, par exemple, le contenu du Registre x86 EBP.|  
|`shadowStackPointer`|Pointeur vers la pile cachée. Cette valeur est le contenu du Registre BSP et s’applique uniquement à IA64.|  
  
## <a name="remarks"></a>Notes  
 Quand une notification d’exception est reçue, [ICorProfilerInfo2 :: GetNotifiedExceptionClauseInfo,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) peut être utilisé pour obtenir les informations d’adresse native et de frame pour la clause d’exception (`catch`/`finally`/Filter) qui est sur le point d’être exécutée ou qui vient d’être exécutée.  
  
 L’exécution d’une clause d’exception implique ces rappels du common language runtime (CLR) :  
  
- [ICorProfilerCallback :: ExceptionCatcherEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback :: ExceptionUnwindFinallyEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback :: ExceptionSearchFilterEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback :: ExceptionCatcherLeave,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback :: ExceptionUnwindFinallyLeave,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback :: ExceptionSearchFilterLeave,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
