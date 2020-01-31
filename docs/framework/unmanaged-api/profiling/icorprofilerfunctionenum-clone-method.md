---
title: ICorProfilerFunctionEnum::Clone, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: 2faa7185202b46e77e501d69bb471391a7c6eb68
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864620"
---
# <a name="icorprofilerfunctionenumclone-method"></a>ICorProfilerFunctionEnum::Clone, méthode
Obtient un pointeur d’interface vers une copie de cette interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parameters  
 `ppEnum`  
 à Pointeur vers le pointeur d’interface qui, à son tour, pointe vers la copie de cette interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) . La copie de l’énumérateur conserve son propre état d’énumération séparément de cet énumérateur. Toutefois, la position initiale du curseur de la copie est la même que la position actuelle du curseur de cet énumérateur.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerFunctionEnum, interface](icorprofilerfunctionenum-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
