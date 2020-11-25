---
title: CorDebugUserState, énumération
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: 968874a46279b7eac651d45c3890429a326651b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726949"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState, énumération

Indique l'état de l'utilisateur d'un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Membres  
  
|Value|Description|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|Un arrêt du thread a été demandé.|  
|`USER_SUSPEND_REQUESTED`|Une suspension du thread a été demandée.|  
|`USER_BACKGROUND`|Le thread s’exécute en arrière-plan.|  
|`USER_UNSTARTED`|Le thread n’a pas commencé à s’exécuter.|  
|`USER_STOPPED`|Le thread a été arrêté.|  
|`USER_WAIT_SLEEP_JOIN`|Le thread attend qu’un autre thread termine une tâche.|  
|`USER_SUSPENDED`|Le thread a été suspendu.|  
|`USER_UNSAFE_POINT`|Le thread se trouve à un point non sécurisé. Autrement dit, le thread est à un point d’exécution où il peut bloquer garbage collection.<br /><br /> Les événements de débogage peuvent être distribués à partir de points non sécurisés, mais l’interruption d’un thread à un point non sécurisé entraîne très probablement un blocage jusqu’à la reprise du thread. Les points sécurisés et non sécurisés sont déterminés par l’implémentation juste-à-temps (JIT, Just-in-Time) et garbage collection.|  
|`USER_THREADPOOL`|Le thread provient du pool de threads.|  
  
## <a name="remarks"></a>Remarques  

 L’état utilisateur d’un thread est l’état que le thread a lorsque le débogueur l’examine. Un thread peut avoir une combinaison d’États utilisateur.  
  
 Utilisez la méthode [ICorDebugThread :: GetUserState,](icordebugthread-getuserstate-method.md) pour récupérer l’état utilisateur d’un thread.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
