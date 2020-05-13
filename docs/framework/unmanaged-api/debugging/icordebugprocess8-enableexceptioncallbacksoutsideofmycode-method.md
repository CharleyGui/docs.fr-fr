---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: e54dd051f0dbd9c1964d381c2e05189c375fa66d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210135"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
[Pris en charge dans le .NET Framework 4,6 et versions ultérieures]  
  
 Active ou désactive certains types de rappels d’exception [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Remarks  
 Si la valeur de `enableExceptionsOutsideOfJMC` est `false` :  
  
- Une exception DEBUG_EXCEPTION_FIRST_CHANCE n'entraîne pas un rappel au débogueur.  
  
- Une exception DEBUG_EXCEPTION_CATCH_HANDLER_FOUND n'entraîne pas un rappel au débogueur si l'exception ne s'échappe jamais dans le code utilisateur (autrement dit, le chemin de l'origine d'une exception vers un gestionnaire d'exceptions n'a aucune méthode marquée JustMyCode ou JMC).  
  
 La valeur par défaut de `enableExceptionsOutsideOfJMC` est `true`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess8 (interface)](icordebugprocess8-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
