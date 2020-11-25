---
title: ICorProfilerFunctionControl::SetCodegenFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: 3593b07759b4d6feee239042e5aabaf0876fdd1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716302"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags, méthode

Définit un ou plusieurs indicateurs à partir de l’énumération [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) pour contrôler la génération de code pour une fonction recompilée juste-à-temps (JIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Paramètres  

 `flags`  
 dans Un ou plusieurs indicateurs de l’énumération [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) .  
  
## <a name="remarks"></a>Remarques  

 Le profileur obtient une instance de cette interface par le biais du rappel [ICorProfilerCallback4 :: getrejitparameters,](icorprofilercallback4-getrejitparameters-method.md) . `SetCodegenFlags` permet au profileur de contrôler la génération de code pour la fonction recompilée. Comme avec tous les autres paramètres de recompilation JIT, les indicateurs de génération de code s’appliquent à toutes les instances de la fonction.  
  
 Le compilateur JIT considère ces indicateurs de compilation, ainsi que d’autres indicateurs spécifiés par d’autres sources, lors de la compilation d’une fonction.  Les autres sources incluent le débogueur, les indicateurs globaux définis par le profileur au démarrage à l’aide de la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) (avec les valeurs `COR_PRF_DISABLE_INLINING` et `COR_PRF_DISABLE_OPTIMIZATIONS` ) et le rappel [ICorProfilerCallback :: JITInlining,](icorprofilercallback-jitinlining-method.md) du profileur.  Le compilateur JIT donne la priorité à une source qui demande le moins d’optimisation.  Par exemple, si le profileur spécifie au `COR_PRF_DISABLE_INLINING` démarrage, mais ne spécifie pas `COR_PRF_CODEGEN_DISABLE_INLINING` dans le rappel [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) , l’incorporation est toujours désactivée.  De même, si le profileur ne spécifie pas `COR_PRF_CODEGEN_DISABLE_INLINING` dans `SetCodegenFlags` , mais désactive l’incorporation à l’aide du rappel [ICorProfilerCallback :: JITInlining,](icorprofilercallback-jitinlining-method.md) , l’incorporation est désactivée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerFunctionControl, interface](icorprofilerfunctioncontrol-interface.md)
