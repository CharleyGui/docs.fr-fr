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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a659e139040174a66043283ed4633d9c9d223ce8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774035"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo, méthode
Obtient les informations d’adresse et le frame natives pour la clause d’exception (`catch`/`finally`/`filter`) qui doit être exécutée ou vient d’être exécutée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pinfo`  
 [out] Un pointeur vers un [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure qui décrit l’instance de clause d’exception actuelle et sa trame associée.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une notification d’exception est reçue, `GetNotifiedExceptionClauseInfo` peut être utilisé pour obtenir les informations d’adresse et d’image natives pour la clause d’exception (`catch`/`finally`/`filter`) qui doit être exécutée ([ ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), ou [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)rappel est reçu par le profileur) ou récemment exécuté ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), ou [ ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) rappel est reçu par le profileur).  
  
 Cet appel peut être effectué à tout moment après l’un des rappels Enter ci-dessus jusqu'à ce que le rappel Leave correspondant est reçu ou une exception imbriquée est levée dans la clause actuelle, auquel cas il n’est aucune notification de congé de cette clause. Notez qu’il n’est pas possible pour une exception levée échapper un `filter` clause d’exception, il est donc toujours une notification de congé dans ce cas.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
