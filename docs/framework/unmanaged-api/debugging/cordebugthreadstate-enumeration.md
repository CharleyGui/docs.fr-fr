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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce252f5a4b5fbcdbbc7b70c8b1c829490f8f63e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739531"
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
|`THREAD_RUN`|Le thread exécute librement, sauf si un événement de débogage se produit.|  
|`THREAD_SUSPEND`|Le thread ne peut pas s’exécuter.|  
  
## <a name="remarks"></a>Notes  
 Le débogueur utilise la `CorDebugThreadState` énumération pour contrôler l’exécution d’un thread. L’état d’un thread peut être défini à l’aide de la [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) ou [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) (méthode).  
  
 Un rappel fourni à la [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md) permet le pompage de messages, un état interrompu est donc pas nécessaire.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
