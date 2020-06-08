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
ms.openlocfilehash: 0a4cb365ca8f7d52be505368a3d769a9728983bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502962"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread, méthode
Obtient un objet qui peut être interrogé pour l’interface ICorDebugThread. Cette méthode est obsolète dans la version 2,0 de .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppicd`  
 objet [out](/cpp/atl/iunknown) qui peut être interrogé pour l' `ICorDebugThread` interface.  
  
## <a name="remarks"></a>Remarques  
 Les services de débogage common language runtime (CLR) ont pris en charge le débogage in-process limité dans le .NET Framework version 1,0. Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage. Suite aux commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus conforme à l’API de profilage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Version de .NET Framework :** 1,0  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
