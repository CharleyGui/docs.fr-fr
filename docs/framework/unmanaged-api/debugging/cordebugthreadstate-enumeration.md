---
title: CorDebugThreadState, énumération
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133691"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState, énumération
Spécifie l'état d'un thread pour le débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`THREAD_RUN`|Le thread s’exécute librement, à moins qu’un événement de débogage se produise.|  
|`THREAD_SUSPEND`|Le thread ne peut pas s’exécuter.|  
  
## <a name="remarks"></a>Notes  
 Le débogueur utilise l’énumération `CorDebugThreadState` pour contrôler l’exécution d’un thread. L’état d’un thread peut être défini à l’aide de la méthode [ICorDebugThread :: SetDebugState,](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) ou [ICorDebugController :: SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) .  
  
 Un rappel fourni à l' [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md) active le pompage de messages, ce qui signifie qu’il n’est pas nécessaire d’interrompre l’État.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
