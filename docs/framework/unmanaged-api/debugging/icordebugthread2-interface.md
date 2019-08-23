---
title: ICorDebugThread2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d21c221bba3ac668924003f96580bb660229ad7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963004"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2, interface
Sert d’extension logique à l’interface ICorDebugThread.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetActiveFunctions, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Obtient un tableau d’instances COR_ACTIVE_FUNCTION qui contiennent les données relatives aux fonctions actives dans les frames d’un thread.|  
|[GetConnectionID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Obtient un identificateur de connexion pour ce `ICorDebugThread2`.|  
|[GetTaskID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Obtient un identificateur de tâche pour ce `ICorDebugThread2`.|  
|[GetVolatileOSThreadID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Obtient l’identificateur de thread de système d’exploitation `ICorDebugThread2`pour ce.|  
|[InterceptCurrentException, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Permet à un débogueur d’intercepter l’exception actuelle sur un thread.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
