---
title: ICorProfilerFunctionEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: 3ccf75523eb9362b8ef5c38d224a419502cb8b92
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724143"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a>ICorProfilerFunctionEnum::GetCount, méthode

Obtient le nombre de fonctions qui ont été chargées par l'application ou chargées de force par le profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a>Paramètres  

 `celt`  
 à Nombre de fonctions qui ont été chargées.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerFunctionEnum, interface](icorprofilerfunctionenum-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
