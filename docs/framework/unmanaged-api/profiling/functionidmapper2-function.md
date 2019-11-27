---
title: FunctionIDMapper2, fonction
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: 7f83469920956d73a275f510b0d3c3e94a4caa8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440671"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2, fonction
Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)et [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) pour cette fonction. `FunctionIDMapper2` permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `funcId`  
 [in] Identificateur de fonction à remapper.  
  
 `clientData`  
 [in] Pointeur vers les données utilisées pour distinguer les différents runtimes.  
  
 `pbHookFunction`  
 [out] Pointeur vers une valeur à laquelle le profileur affecte `true` s'il souhaite recevoir des rappels `FunctionEnter3`, `FunctionLeave3` et `FunctionTailcall3` ou `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo` et `FunctionTailcall3WithInfo` ; sinon, il affecte `false` à cette valeur.  
  
## <a name="return-value"></a>Valeur de retour  
 Le profileur retourne une valeur que le moteur d'exécution utilise comme autre identificateur de fonction. La valeur de retour ne peut pas être null, sauf si `false` est retourné dans `pbHookFunction`. Sinon, une valeur de retour null génère des résultats imprévisibles pouvant aller jusqu'à l'arrêt du processus.  
  
## <a name="remarks"></a>Notes  
 Cette méthode étend la fonction [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) avec un paramètre supplémentaire utilisé pour passer les données du client. Les données client sont utilisées pour distinguer les différents runtimes.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo :: SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3 :: Setfunctionidmapper2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
