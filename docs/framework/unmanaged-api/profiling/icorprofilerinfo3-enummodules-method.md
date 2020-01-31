---
title: ICorProfilerInfo3::EnumModules, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 626ecddae8ba91d1830d98210208f9fbee36f073
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868584"
---
# <a name="icorprofilerinfo3enummodules-method"></a>ICorProfilerInfo3::EnumModules, méthode
Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein d’une collection de modules managés chargés dans l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parameters  
 `ppEnum`  
 à Pointeur vers une interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerFunctionEnum, interface](icorprofilerfunctionenum-interface.md)
- [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
