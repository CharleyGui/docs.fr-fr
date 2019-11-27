---
title: ICorProfilerCallback::UnmanagedToManagedTransition, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 8c4e132b90fa1f51bc6f858d75c159af212ec019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439892"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition, méthode
Notifie le profileur qu’une transition du code non managé au code managé s’est produite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 dans ID de la fonction appelée.  
  
 `reason`  
 dans Valeur de l’énumération [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) qui indique si la transition s’est produite en raison d’un appel dans du code managé à partir de code non managé, ou à cause d’un retour d’une fonction non managée appelée par une fonction managée.  
  
## <a name="remarks"></a>Notes  
 Si la valeur de `reason` est COR_PRF_TRANSITION_RETURN et `functionId` n’est pas null, l’ID de fonction est celui de la fonction non managée et n’aura jamais été compilé à l’aide du compilateur juste-à-temps (JIT). Des informations de base sont associées aux fonctions non managées, telles qu’un nom et des métadonnées.  
  
 Si la valeur de `reason` est COR_PRF_TRANSITION_CALL, il est possible que la fonction appelée (autrement dit, la fonction managée) n’ait pas encore été compilée juste-à-temps.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [Utilisation de l’interopérabilité C++ (PInvoke implicite)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
