---
title: ICorProfilerInfo3::SetFunctionIDMapper2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 723cb277a7df592e0494505018f7422e4e40f5f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496150"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2, méthode
Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur. Cette méthode étend la méthode [ICorProfilerInfo :: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) avec un paramètre de données supplémentaire, que les profileurs peuvent utiliser pour lever l’ambiguïté entre les runtimes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pFunc`  
 dans Pointeur vers une implémentation de [FunctionIDMapper2,](functionidmapper2-function.md) qui sera appelée pour mapper les `FunctionID` valeurs à leurs autres valeurs.  
  
 `clientData`  
 dans Pointeur qui est passé à chaque appel de fonction [FunctionIDMapper2,](functionidmapper2-function.md) effectué par le runtime actuel. Le profileur peut utiliser ces informations pour lever l’ambiguïté entre les runtimes.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
## <a name="remarks"></a>Remarques  
 Les alternatives pour les valeurs FunctionID seront passées aux raccordements d’entrée/sortie de fonction du profileur ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md); ou [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) qui sont spécifiés par la méthode [SetEnterLeaveFunctionHooks3,](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) ou [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .  
  
 La `FunctionIDMapper2` méthode ne peut être définie qu’une seule fois ; nous vous recommandons de la définir dans le rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
