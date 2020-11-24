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
ms.openlocfilehash: e8dd9f21803021975f4651ba3e6e5f4d3da0ea82
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674994"
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
|`clauseType`|Valeur de l’énumération [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) qui spécifie le type de clause d’exception que le code vient d’entrer ou de laisser.|  
|`programCounter`|Point d’entrée natif du gestionnaire de clauses, par exemple, le contenu du registre de l’élément x86 EIP.|  
|`framePointer`|Pointeur vers l’image logique du gestionnaire de clause, par exemple, le contenu du Registre x86 EBP.|  
|`shadowStackPointer`|Pointeur vers la pile cachée. Cette valeur est le contenu du Registre BSP et s’applique uniquement à IA64.|  
  
## <a name="remarks"></a>Remarques  

 Quand une notification d’exception est reçue, [ICorProfilerInfo2 :: GetNotifiedExceptionClauseInfo,](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) peut être utilisé pour obtenir les informations d’adresse native et de frame pour la clause d’exception ( `catch` / `finally` /Filter) qui est sur le point d’être exécutée ou qui vient d’être exécutée.  
  
 L’exécution d’une clause d’exception implique ces rappels du common language runtime (CLR) :  
  
- [ICorProfilerCallback :: ExceptionCatcherEnter,](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback :: ExceptionUnwindFinallyEnter,](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback :: ExceptionSearchFilterEnter,](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback :: ExceptionCatcherLeave,](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback :: ExceptionUnwindFinallyLeave,](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback :: ExceptionSearchFilterLeave,](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de profilage](profiling-structures.md)
