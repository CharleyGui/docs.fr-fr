---
title: ICorDebugManagedCallback2::CreateConnection, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d69ffa05cff534609f8f6b3addc657664b09decb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624489"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection, méthode
Notifie le débogueur qu’une nouvelle connexion a été créée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pProcess`  
 [in] Un pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel la connexion a été créée  
  
 `dwConnectionId`  
 [in] ID de la nouvelle connexion.  
  
 `pConnName`  
 [in] Un pointeur vers le nom de la nouvelle connexion.  
  
## <a name="remarks"></a>Notes  
 Un `CreateConnection` rappel est déclenché dans les cas suivants :  
  
- Quand un débogueur est attaché à un processus qui contient les connexions. Dans ce cas, le runtime générer et distribuer un `CreateConnection` événement et un [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) événement pour chaque connexion dans le processus.  
  
- Lorsqu’un hôte appelle [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) dans le [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
