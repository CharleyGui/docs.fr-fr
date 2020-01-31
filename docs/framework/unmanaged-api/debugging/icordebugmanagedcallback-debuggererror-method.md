---
title: ICorDebugManagedCallback::DebuggerError, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: 9b96c0a2eca543b9e01ccf92b271b1aa7003c5c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781949"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError, méthode
Notifie le débogueur qu’une erreur s’est produite lors de la tentative de gestion d’un événement à partir du common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pProcess`  
 dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel l’événement s’est produit.  
  
 `errorHR`  
 dans Valeur HRESULT qui a été retournée par le gestionnaire d’événements.  
  
 `errorCode`  
 dans Entier qui spécifie l’erreur CLR.  
  
## <a name="remarks"></a>Notes  
 Le processus peut être placé en mode de transfert, en fonction de la nature de l’erreur.  
  
 Le rappel de `DebugError` indique que les services de débogage ont été désactivés en raison d’une erreur. les débogueurs doivent donc mettre le message d’erreur à la disposition de l’utilisateur. [ICorDebugProcess :: GetId](icordebugprocess-getid-method.md) peut être appelée sans risque, mais toutes les autres méthodes, y compris [ICorDebug :: Terminate](icordebug-terminate-method.md), ne doivent pas être appelées. Le débogueur doit utiliser des fonctionnalités de système d’exploitation pour terminer les processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
