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
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501922"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection, méthode
Notifie le débogueur qu’une nouvelle connexion a été créée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pProcess`  
 dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel la connexion a été créée.  
  
 `dwConnectionId`  
 dans ID de la nouvelle connexion.  
  
 `pConnName`  
 dans Pointeur vers le nom de la nouvelle connexion.  
  
## <a name="remarks"></a>Remarques  
 Un `CreateConnection` rappel est déclenché dans l’un des cas suivants :  
  
- Quand un débogueur est attaché à un processus qui contient des connexions. Dans ce cas, le runtime génère et distribue un `CreateConnection` événement et un événement [ICorDebugManagedCallback2 :: ChangeConnection,](icordebugmanagedcallback2-changeconnection-method.md) pour chaque connexion dans le processus.  
  
- Lorsqu’un hôte appelle [ICLRDebugManager :: BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) dans l' [API d’hébergement](../hosting/index.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
