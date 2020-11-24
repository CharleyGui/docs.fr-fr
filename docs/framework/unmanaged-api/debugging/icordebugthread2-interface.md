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
ms.openlocfilehash: fd4ad536d7d3df2b8f91f206459122cf083c8b9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691134"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2, interface

Sert d’extension logique à l’interface ICorDebugThread.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetActiveFunctions, méthode](icordebugthread2-getactivefunctions-method.md)|Obtient un tableau d’instances de COR_ACTIVE_FUNCTION qui contiennent des données relatives aux fonctions actives dans les frames d’un thread.|  
|[GetConnectionID, méthode](icordebugthread2-getconnectionid-method.md)|Obtient un identificateur de connexion pour ce `ICorDebugThread2` .|  
|[GetTaskID, méthode](icordebugthread2-gettaskid-method.md)|Obtient un identificateur de tâche pour ce `ICorDebugThread2` .|  
|[GetVolatileOSThreadID, méthode](icordebugthread2-getvolatileosthreadid-method.md)|Obtient l’identificateur de thread de système d’exploitation pour ce `ICorDebugThread2` .|  
|[InterceptCurrentException, méthode](icordebugthread2-interceptcurrentexception-method.md)|Permet à un débogueur d’intercepter l’exception actuelle sur un thread.|  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
