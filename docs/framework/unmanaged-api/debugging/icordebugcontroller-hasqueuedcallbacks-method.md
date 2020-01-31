---
title: ICorDebugController::HasQueuedCallbacks, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: c33193bd64030852441c7ca60cee4a000b09156c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788915"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks, méthode
Obtient une valeur qui indique si tous les rappels managés sont actuellement mis en file d’attente pour le thread spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pThread`  
 dans Pointeur vers un objet « ICorDebugThread » qui représente le thread.  
  
 `pbQueued`  
 à Pointeur vers une valeur `true` si des rappels managés sont actuellement mis en file d’attente pour le thread spécifié ; Sinon, `false`.  
  
 Si null est spécifié pour le paramètre `pThread`, `HasQueuedCallbacks` retournera `true` s’il existe actuellement des rappels managés en file d’attente pour n’importe quel thread.  
  
## <a name="remarks"></a>Notes  
 Les rappels sont distribués un par un, à chaque fois que [ICorDebugController :: continue](icordebugcontroller-continue-method.md) est appelé. Le débogueur peut vérifier cet indicateur s’il souhaite signaler plusieurs événements de débogage qui se produisent simultanément.  
  
 Lorsque les événements de débogage sont mis en file d’attente, ils se sont déjà produits, de sorte que le débogueur doit vider la file d’attente entière pour garantir l’état de l’élément débogué. (Appelez `ICorDebugController::Continue` pour vider la file d’attente.) Par exemple, si la file d’attente contient deux événements de débogage sur le thread *x*et que le débogueur interrompt le thread *x* après le premier événement de débogage, puis appelle `ICorDebugController::Continue`, le deuxième événement de débogage pour le thread *x* est distribué même si le thread a été suspendu.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
