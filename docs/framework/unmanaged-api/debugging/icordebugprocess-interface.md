---
title: ICorDebugProcess, interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: b2429052173a187297b67c756213e5d27a79298b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792594"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess, interface
Représente un processus qui exécute le code managé. Cette interface est une sous-classe de ICorDebugController.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ClearCurrentException, méthode](icordebugprocess-clearcurrentexception-method.md)|Efface l’exception non managée actuelle sur le thread donné.|  
|[EnableLogMessages, méthode](icordebugprocess-enablelogmessages-method.md)|Active et désactive l’envoi des messages du journal au débogueur.|  
|[EnumerateAppDomains, méthode](icordebugprocess-enumerateappdomains-method.md)|Énumère tous les domaines d’application dans le processus.|  
|[EnumerateObjects, méthode](icordebugprocess-enumerateobjects-method.md)|Non implémenté.|  
|[GetHandle, méthode](icordebugprocess-gethandle-method.md)|Obtient un handle pour le processus.|  
|[GetHelperThreadID, méthode](icordebugprocess-gethelperthreadid-method.md)|Obtient l’ID de thread du système d’exploitation pour le thread d’assistance interne du débogueur.|  
|[GetID, méthode](icordebugprocess-getid-method.md)|Obtient l’ID (se) du système d’exploitation du processus.|  
|[GetObject, méthode](icordebugprocess-getobject-method.md)|Non implémenté.|  
|[GetThread, méthode](icordebugprocess-getthread-method.md)|Obtient l’instance de ICorDebugThread qui a l’ID de thread de système d’exploitation spécifié.|  
|[GetThreadContext, méthode](icordebugprocess-getthreadcontext-method.md)|Obtient le contexte pour le thread donné.|  
|[IsOSSuspended, méthode](icordebugprocess-isossuspended-method.md)|Détermine si le thread a été suspendu à la suite de l’arrêt du processus par le débogueur.|  
|[IsTransitionStub, méthode](icordebugprocess-istransitionstub-method.md)|Détermine si une adresse se trouve à l’intérieur d’un stub qui entraîne une transition vers du code managé.|  
|[ModifyLogSwitch, méthode](icordebugprocess-modifylogswitch-method.md)|Définit le niveau de gravité du commutateur de journalisation spécifié.|  
|[ReadMemory, méthode](icordebugprocess-readmemory-method.md)|Lit la mémoire à partir du processus.|  
|[SetThreadContext, méthode](icordebugprocess-setthreadcontext-method.md)|Définit le contexte du thread donné.|  
|[ThreadForFiberCookie, méthode](icordebugprocess-threadforfibercookie-method.md)|Option déconseillée.|  
|[WriteMemory, méthode](icordebugprocess-writememory-method.md)|Écrit des données dans une zone de mémoire dans le processus.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
