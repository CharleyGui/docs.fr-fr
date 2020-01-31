---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: ad155c4efb9f11565eeed8bc0a3540311aca4eb7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866271"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode
Notifie le profileur qu’une recherche est terminée pour une fonction qui a été compilée précédemment à l’aide du générateur d’images natives (NGen. exe).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>Parameters

- `functionId`

  \[in] ID de la fonction pour laquelle la recherche a été effectuée.

- `result`

  \[in] valeur de l’énumération [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) qui indique le résultat de la recherche.

## <a name="remarks"></a>Notes  
 Dans la version .NET Framework 2,0, les rappels [ICorProfilerCallback :: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) et `JITCachedFunctionSearchFinished` ne seront pas effectués pour toutes les fonctions dans les images NGen normales. Seules les images NGen optimisées pour un profileur génèrent des rappels pour toutes les fonctions dans l’image. Toutefois, en raison de la surcharge supplémentaire, un profileur doit demander des images NGen optimisées par le profileur uniquement s’il envisage d’utiliser ces rappels pour forcer une fonction à être compilée juste-à-temps (JIT). Dans le cas contraire, le profileur doit utiliser une stratégie paresseuse pour la collecte d’informations sur les fonctions.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
