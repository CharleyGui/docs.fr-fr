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
ms.openlocfilehash: 66f60b2342b6ff64f1329cbe57032291d5139384
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770588"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState, méthode
Définit les indicateurs qui décrivent l’état de débogage de ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `state`  
 [in] Une combinaison au niveau du bit CorDebugThreadState des valeurs d’énumération qui spécifient l’état de débogage de ce thread.  
  
## <a name="remarks"></a>Notes  
 `SetDebugState` définit l’état de débogage actuel du thread. (Le « état de débogage actuel » représente l’état de débogage si le processus de se poursuivre, pas l’état actuel réel). La valeur normale est THREAD_RUNNING. Seul le débogueur peut affecter l’état de débogage d’un thread. États de débogage dernier à travers continue, donc si vous souhaitez conserver un thread THREAD_SUSPENDed sur plusieurs continue, vous pouvez configurer en une fois et par la suite pas obligé de vous inquiétez pas. Suspension des threads et la reprise du processus peuvent provoquer des blocages, même si elle est généralement peu probable. Ceci est une qualité intrinsèque des threads et processus et à la conception. Un débogueur peut interrompre et reprendre les threads pour arrêter le blocage de façon asynchrone. Si l’état du thread utilisateur inclut USER_UNSAFE_POINT, le thread peut bloquer un garbage collection (GC). Cela signifie que le thread suspendu a beaucoup plus de risque de provoquer un interblocage. Cela peut affecter pas les événements sont déjà en file d’attente de débogage. Par conséquent, un débogueur doit purger la file d’attente de la totalité de l’événement (en appelant [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) avant de suspendre ou reprendre des threads. Sinon, il peut obtenir des événements sur un thread qu’il pense qu’il a déjà suspendu.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
