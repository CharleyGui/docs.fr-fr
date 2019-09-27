---
title: ICorDebugThread::SetDebugState, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e18888e307a14c4396966afc0a623e1acba104
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332809"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState, méthode
Définit des indicateurs qui décrivent l’état de débogage de ce ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `state`  
 dans Combinaison d’opérations de bits de valeurs d’énumération CorDebugThreadState qui spécifient l’état de débogage de ce thread.  
  
## <a name="remarks"></a>Notes  
 `SetDebugState` définit l’état de débogage actuel du thread. (L’état de débogage actuel représente l’état de débogage si le processus devait être poursuivi, et non l’état actuel réel.) La valeur normale pour ce est THREAD_RUN. Seul le débogueur peut affecter l’état de débogage d’un thread. Les États de débogage se trouvent en dernier. par conséquent, si vous souhaitez conserver un thread THREAD_SUSPENDed sur plusieurs continues, vous pouvez le définir une fois et ne pas avoir à vous en soucier. Le fait de suspendre des threads et de reprendre le processus peut provoquer des blocages, bien qu’il soit généralement peu probable. Il s’agit d’une qualité intrinsèque de threads et de processus et est par conception. Un débogueur peut interrompre et reprendre de manière asynchrone les threads pour interrompre le blocage. Si l’état utilisateur du thread comprend USER_UNSAFE_POINT, le thread peut bloquer un garbage collection (GC). Cela signifie que le thread suspendu a une probabilité plus élevée de provoquer un blocage. Cela peut ne pas affecter les événements de débogage déjà en file d’attente. Par conséquent, un débogueur doit vider la totalité de la file d’attente des événements (en appelant [ICorDebugController :: HasQueuedCallbacks,](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) avant d’interrompre ou de reprendre des threads. Sinon, il peut obtenir des événements sur un thread qu’il pense avoir déjà suspendu.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
