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
ms.openlocfilehash: d8375948be5820aaf6e879b82bcfde6471cccf3f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679895"
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
  
## <a name="parameters"></a>Paramètres  

 `state`  
 dans Valeur de l’énumération « CorDebugThreadState » qui spécifie l’état du thread pour le débogage.  
  
 `pExceptThisThread`  
 dans Pointeur vers un objet « ICorDebugThread » qui représente un thread à exempter du paramètre d’état de débogage. Si cette valeur est null, aucun thread n’est exempté.  
  
## <a name="remarks"></a>Remarques  

 La `SetAllThreadsDebugState` méthode peut affecter les threads qui ne sont pas visibles via la [méthode EnumerateThreads,](icordebugcontroller-enumeratethreads-method.md), de sorte que les threads qui ont été interrompus avec la `SetAllThreadsDebugState` méthode doivent être repris avec la `SetAllThreadsDebugState` méthode.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
