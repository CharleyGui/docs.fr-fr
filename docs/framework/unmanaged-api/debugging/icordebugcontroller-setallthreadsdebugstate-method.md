---
title: ICorDebugController::SetAllThreadsDebugState, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: be7fce700756d7120e0853446b7b307ec77c2080
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783761"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState, méthode
Définit l’état de débogage de tous les threads managés dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `state`  
 dans Valeur de l’énumération « CorDebugThreadState » qui spécifie l’état du thread pour le débogage.  
  
 `pExceptThisThread`  
 dans Pointeur vers un objet « ICorDebugThread » qui représente un thread à exempter du paramètre d’état de débogage. Si cette valeur est null, aucun thread n’est exempté.  
  
## <a name="remarks"></a>Notes  
 La méthode `SetAllThreadsDebugState` peut affecter les threads qui ne sont pas visibles via la [méthode EnumerateThreads,](icordebugcontroller-enumeratethreads-method.md), de sorte que les threads qui ont été suspendus avec la méthode `SetAllThreadsDebugState` devront être repris avec la méthode `SetAllThreadsDebugState`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
