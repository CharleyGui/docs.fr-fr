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
ms.openlocfilehash: 8f3697f8b193319ebb7b155ad79b8ec25a0a2266
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205273"
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
  
## <a name="parameters"></a>Paramètres  
 `pProcess`  
 dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel l’événement s’est produit.  
  
 `errorHR`  
 dans Valeur HRESULT qui a été retournée par le gestionnaire d’événements.  
  
 `errorCode`  
 dans Entier qui spécifie l’erreur CLR.  
  
## <a name="remarks"></a>Remarks  
 Le processus peut être placé en mode de transfert, en fonction de la nature de l’erreur.  
  
 Le `DebugError` rappel indique que les services de débogage ont été désactivés en raison d’une erreur. par conséquent, les débogueurs doivent mettre le message d’erreur à la disposition de l’utilisateur. [ICorDebugProcess :: GetId](icordebugprocess-getid-method.md) peut être appelée sans risque, mais toutes les autres méthodes, y compris [ICorDebug :: Terminate](icordebug-terminate-method.md), ne doivent pas être appelées. Le débogueur doit utiliser des fonctionnalités de système d’exploitation pour terminer les processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
