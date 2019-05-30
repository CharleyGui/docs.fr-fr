---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52a58f75ca7abd1bd1f871bcf4637bfd7eb7bdcd
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300540"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
[Pris en charge dans le .NET Framework 4.6 et versions ultérieures]  
  
 Active ou désactive certains types de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rappels d’exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Notes  
 Si la valeur de `enableExceptionsOutsideOfJMC` est `false` :  
  
- Une exception DEBUG_EXCEPTION_FIRST_CHANCE pas entraîne un rappel au débogueur.  
  
- Une exception DEBUG_EXCEPTION_CATCH_HANDLER_FOUND pas entraîne un rappel au débogueur si l’exception s’échappe jamais dans le code utilisateur (autrement dit, le chemin d’origine vers un gestionnaire d’exceptions n’a aucune méthode marquée JustMyCode ou JMC).  
  
 La valeur par défaut de `enableExceptionsOutsideOfJMC` est `true`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess8, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
