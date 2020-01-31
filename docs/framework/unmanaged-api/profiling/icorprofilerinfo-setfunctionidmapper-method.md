---
title: ICorProfilerInfo::SetFunctionIDMapper, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 52ab9a089b5def4f3db2f99abc5a718d66cca739
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863450"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a>ICorProfilerInfo::SetFunctionIDMapper, méthode
Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a>Parameters  
 `pFunc`  
 dans Pointeur vers l’implémentation de [FunctionIDMapper](functionidmapper-function.md) qui sera appelée pour mapper les valeurs de `FunctionID` à leurs autres valeurs.  
  
## <a name="remarks"></a>Notes  
 Les alternatives pour les valeurs de `FunctionID` seront passées aux raccordements d’entrée/sortie de fonction du profileur ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)et [FunctionTailcall2](functiontailcall2-function.md)) qui sont spécifiés par la méthode [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .  
  
 La `FunctionIDMapper` ne peut être définie qu’une seule fois et il est recommandé de la définir dans le rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
