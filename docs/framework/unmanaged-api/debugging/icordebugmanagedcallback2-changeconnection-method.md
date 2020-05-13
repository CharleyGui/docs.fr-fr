---
title: ICorDebugManagedCallback2::ChangeConnection, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 2c6ed14f9238d653b15d26dec9d954c05238817c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213450"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection, méthode
Notifie le débogueur que l’ensemble des tâches associées à la connexion spécifiée a changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pProcess`  
 dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus contenant la connexion qui a changé.  
  
 `dwConnectionId`  
 dans ID de la connexion qui a changé.  
  
## <a name="remarks"></a>Remarks  
 Un `ChangeConnection` rappel est déclenché dans l’un des cas suivants :  
  
- Quand un débogueur est attaché à un processus qui contient des connexions. Dans ce cas, le runtime génère et distribue un événement [ICorDebugManagedCallback2 :: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) et un `ChangeConnection` événement pour chaque connexion dans le processus. Un `ChangeConnection` événement est généré pour chaque connexion existante, que l’ensemble de tâches de cette connexion ait été modifié ou non depuis sa création.  
  
- Lorsqu’un hôte appelle [ICLRDebugManager :: SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) dans l' [API d’hébergement](../hosting/index.md).  
  
 Le débogueur doit analyser tous les threads du processus pour récupérer les nouvelles modifications.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
