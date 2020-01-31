---
title: ICorProfilerInfo::GetInprocInspectionIThisThread, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 0ab383f0968061667b3580a2058687eecda99dde
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870040"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread, méthode
Obtient un objet qui peut être interrogé pour l’interface ICorDebugThread. Cette méthode est obsolète dans la version 2,0 de .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Parameters  
 `ppicd`  
 objet [out](/cpp/atl/iunknown) qui peut être interrogé pour l’interface `ICorDebugThread`.  
  
## <a name="remarks"></a>Notes  
 Les services de débogage common language runtime (CLR) ont pris en charge le débogage in-process limité dans le .NET Framework version 1,0. Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage. Suite aux commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus conforme à l’API de profilage.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Version de .NET Framework :** 1,0  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
