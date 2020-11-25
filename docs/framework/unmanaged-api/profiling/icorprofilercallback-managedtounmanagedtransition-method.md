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
ms.openlocfilehash: ef65ed908c71bcc2755aaf42070439fd7dab3f6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733137"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition, méthode

Notifie le profileur qu’une transition du code managé au code non managé s’est produite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Paramètres  

 `functionId`  
 dans ID de la fonction appelée.  
  
 `reason`  
 dans Valeur de l’énumération [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) qui indique si la transition s’est produite en raison d’un appel dans du code non managé à partir du code managé, ou à cause d’un retour d’une fonction managée appelée par un qui n’est pas géré.  
  
## <a name="remarks"></a>Remarques  

 Si la valeur de `reason` est COR_PRF_TRANSITION_CALL, l’ID de fonction est celui de la fonction non managée qui n’a jamais été compilée à l’aide du compilateur juste-à-temps. Les fonctions non managées sont associées à des informations de base, telles qu’un nom et des métadonnées. Si la fonction non managée a été appelée à l’aide d’un appel de code non managé implicite (PInvoke), le runtime ne peut pas déterminer la destination de l’appel et la valeur de `functionId` est null. Pour plus d’informations sur PInvoke implicite, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition, méthode](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
