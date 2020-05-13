---
title: ICorDebugManagedCallback::ExitProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 7a49bd6626518179c9b5ef008fca28d304537cc8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205263"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess, méthode
Notifie le débogueur qu’un processus s’est arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pProcess`  
 dans Pointeur vers un objet ICorDebugProcess qui représente le processus.  
  
## <a name="remarks"></a>Remarks  
 Vous ne pouvez pas continuer à partir d’un `ExitProcess` événement. Cet événement peut se déclencher de manière asynchrone vers d’autres événements pendant que le processus semble être arrêté. Cela peut se produire si le processus se termine alors qu’il est arrêté, généralement en raison d’une force externe.  
  
 Si le common language runtime (CLR) est déjà en cours de distribution d’un rappel managé, cet événement est retardé jusqu’à ce que le rappel soit retourné.  
  
 L' `ExitProcess` événement est le seul événement de sortie/déchargement qui est garanti pour être appelé lors de l’arrêt.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
