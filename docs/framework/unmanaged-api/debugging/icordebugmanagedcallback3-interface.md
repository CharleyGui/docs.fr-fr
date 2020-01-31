---
title: ICorDebugManagedCallback3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: b97f29b94ed4fad6892697ca1c7ed4a20c99c03e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793266"
---
# <a name="icordebugmanagedcallback3-interface"></a>ICorDebugManagedCallback3, interface
Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CustomNotification, méthode](icordebugmanagedcallback3-customnotification-method.md)|Indique qu’une notification du débogueur personnalisé activé a été déclenchée.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est une extension logique des interfaces [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) et [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
