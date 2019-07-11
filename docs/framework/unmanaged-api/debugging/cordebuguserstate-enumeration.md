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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76fbbb3f924f610b604586dca78cab344217b544
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739461"
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|Un arrêt du thread a été demandé.|  
|`USER_SUSPEND_REQUESTED`|Une suspension du thread a été demandée.|  
|`USER_BACKGROUND`|Le thread s’exécute en arrière-plan.|  
|`USER_UNSTARTED`|Le thread n’a pas démarré l’exécution.|  
|`USER_STOPPED`|Le thread a été arrêté.|  
|`USER_WAIT_SLEEP_JOIN`|Le thread est en attente d’un autre thread effectuer une tâche.|  
|`USER_SUSPENDED`|Le thread a été suspendu.|  
|`USER_UNSAFE_POINT`|Le thread est à un point non sécurisé. Autrement dit, le thread est à un point d’exécution où il peut bloquer le garbage collection.<br /><br /> Déboguer des événements peuvent être distribués à partir de points non sécurisés, mais la suspension d’un thread à un point non sécurisé est très susceptible de provoquer un blocage jusqu'à ce que le thread est repris. Les points sécurisés et sont déterminés par le juste-à-temps (JIT) et l’implémentation de garbage collection.|  
|`USER_THREADPOOL`|Le thread est le pool de threads.|  
  
## <a name="remarks"></a>Notes  
 L’état utilisateur d’un thread est l’état que le thread a lorsque le débogueur l’examine. Un thread peut avoir une combinaison des États de l’utilisateur.  
  
 Utilisez le [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) méthode pour récupérer l’état utilisateur d’un thread.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
