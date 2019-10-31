---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123374"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
[Pris en charge dans le .NET Framework 4,6 et versions ultérieures]  
  
 Active ou désactive certains types de rappels d’exception [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .  
  
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
  
- Une exception DEBUG_EXCEPTION_FIRST_CHANCE n’entraîne pas de rappel au débogueur.  
  
- Une exception DEBUG_EXCEPTION_CATCH_HANDLER_FOUND n’entraîne pas de rappel au débogueur si l’exception n’échappe jamais dans le code utilisateur (autrement dit, le chemin d’accès d’une exception d’origine à un gestionnaire d’exceptions n’a aucune méthode marquée comme JustMyCode ou uniquement mon code).  
  
 La valeur par défaut de `enableExceptionsOutsideOfJMC` est `true`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess8, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
