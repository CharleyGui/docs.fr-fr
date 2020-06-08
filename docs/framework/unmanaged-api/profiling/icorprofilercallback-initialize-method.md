---
title: ICorProfilerCallback::Initialize, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500102"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize, méthode
Appelé pour initialiser le profileur de code chaque fois qu’une nouvelle application common language runtime (CLR) est démarrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Paramètres

- `pICorProfilerInfoUnk`

  \[in] pointeur vers une interface [IUnknown](/cpp/atl/iunknown) que le profileur doit interroger pour obtenir un pointeur d’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) .  

## <a name="remarks"></a>Remarques  
 L' `Initialize` appel est la seule possibilité d’activer (ou de désactiver) les rappels qui sont immuables. Une fois qu’un rappel est activé par l' `Initialize` appel, il ne peut pas être désactivé ultérieurement à l’aide de [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md). La valeur COR_PRF_MONITOR_IMMUTABLE de l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) indique quels événements sont immuables.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [Shutdown Method](icorprofilercallback-shutdown-method.md)
