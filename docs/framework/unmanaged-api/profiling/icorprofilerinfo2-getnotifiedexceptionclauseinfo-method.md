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
ms.openlocfilehash: a430631948230d16e5d04c869625b4c670faaf02
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868640"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo, méthode
Obtient les informations d’adresse native et de frame pour la clause d’exception (`catch`/`finally`/`filter`) qui est sur le point d’être exécutée ou qui vient d’être exécutée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Parameters  
 `pinfo`  
 à Pointeur vers une structure [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) qui décrit l’instance de la clause d’exception actuelle et son frame associé.  
  
## <a name="remarks"></a>Notes  
 Lors de la réception d’une notification d’exception, `GetNotifiedExceptionClauseInfo` peut être utilisé pour obtenir les informations d’adresse native et de frame pour la clause d’exception (`catch`/`finally`/`filter`) qui est sur le point d’être exécutée ([ICorProfilerCallback :: ExceptionCatcherEnter,](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback :: ExceptionUnwindFinallyEnter,](icorprofilercallback-exceptionunwindfinallyenter-method.md)ou [ICorProfilerCallback :: ExceptionSearchFilterEnter,](icorprofilercallback-exceptionsearchfilterenter-method.md) rappel est reçu par le profileur) ou vient d’être exécutée ([ICorProfilerCallback :: ExceptionCatcherLeave, ](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback :: ExceptionUnwindFinallyLeave,](icorprofilercallback-exceptionunwindfinallyleave-method.md)ou [ICorProfilerCallback :: ExceptionSearchFilterLeave,](icorprofilercallback-exceptionsearchfilterleave-method.md) est reçu par le profileur).  
  
 Cet appel peut être effectué à tout moment après l’un des rappels d’entrée ci-dessus jusqu’à ce que le rappel de fin de correspondance soit reçu ou qu’une exception imbriquée soit levée dans la clause actuelle, auquel cas il n’y a aucune notification de sortie pour cette clause. Notez qu’il n’est pas possible pour une exception levée d’échapper à une clause d’exception `filter`. il y a donc toujours une notification de sortie dans ce cas.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
