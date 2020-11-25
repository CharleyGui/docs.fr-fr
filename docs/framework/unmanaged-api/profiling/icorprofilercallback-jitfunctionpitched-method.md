---
title: ICorProfilerCallback::JITFunctionPitched, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 51fec26837b3c7f0a0328a7b64ff4a02148283da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725507"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched, méthode

Notifie le profileur qu’une fonction qui a été compilée juste-à-temps (JIT) a été supprimée de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Paramètres  

 `functionId`  
 dans ID de la fonction qui a été supprimée.  
  
## <a name="remarks"></a>Remarques  

 Si la fonction supprimée est appelée, le profileur reçoit de nouveaux événements de compilation JIT lorsque la fonction est recompilée. Actuellement, le compilateur JIT (CLR) common language runtime ne supprime pas les fonctions de la mémoire, ce rappel n’est donc pas utilisé pour le moment et n’est pas reçu par le profileur.  
  
 La valeur de `functionId` n’est pas valide tant que la fonction n’est pas recompilée. Lorsque la fonction est recompilée, la même `functionId` valeur est utilisée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
