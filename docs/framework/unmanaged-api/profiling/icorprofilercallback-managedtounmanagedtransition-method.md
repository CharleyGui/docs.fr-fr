---
title: ICorProfilerCallback::ManagedToUnmanagedTransition, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 0750ac66c654285e11dbbb5941f029bf5f900842
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866193"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition, méthode
Notifie le profileur qu’une transition du code managé au code non managé s’est produite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parameters  
 `functionId`  
 dans ID de la fonction appelée.  
  
 `reason`  
 dans Valeur de l’énumération [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) qui indique si la transition s’est produite en raison d’un appel dans du code non managé à partir du code managé, ou à cause d’un retour d’une fonction managée appelée par un qui n’est pas géré.  
  
## <a name="remarks"></a>Notes  
 Si la valeur de `reason` est COR_PRF_TRANSITION_CALL, l’ID de fonction est celui de la fonction non managée, qui n’a jamais été compilée à l’aide du compilateur juste-à-temps. Les fonctions non managées sont associées à des informations de base, telles qu’un nom et des métadonnées. Si la fonction non managée a été appelée à l’aide d’un appel de code non managé implicite (PInvoke), le runtime ne peut pas déterminer la destination de l’appel et la valeur de `functionId` sera null. Pour plus d’informations sur PInvoke implicite, consultez [utilisation de C++ l’interopérabilité (PInvoke implicite)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition, méthode](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
