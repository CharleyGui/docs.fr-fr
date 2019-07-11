---
title: ICorProfilerInfo::GetInprocInspectionInterface, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67a680727e824cbe29b9e022e00d661e8694f153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780564"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>ICorProfilerInfo::GetInprocInspectionInterface, méthode
Obtient un objet qui peut être interrogé pour une interface « ICorDebugProcess ». Cette méthode est obsolète dans le .NET Framework version 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppicd`  
 [out](/cpp/atl/iunknown) objet qui peut être interrogé pour une `ICorDebugProcess` interface.  
  
## <a name="remarks"></a>Notes  
 L’API de débogage du common language runtime (CLR) prise en charge limitée dans le processus de débogage dans le .NET Framework version 1.0. Dans le processus de débogage activé un profileur d’utiliser les parties de l’inspection de l’API de débogage. À la suite de commentaires des clients, dans le processus de débogage a été supprimé depuis le .NET Framework version 2.0 et remplacé par un ensemble de fonctionnalités qui sont plus adaptées à l’API de profilage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Version du .NET framework :** 1.0  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
