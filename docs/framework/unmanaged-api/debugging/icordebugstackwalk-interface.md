---
title: ICorDebugStackWalk, interface
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791875"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk, interface
Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetContext, méthode](icordebugstackwalk-getcontext-method.md)|Retourne le contexte du frame actuel dans l’objet `ICorDebugStackWalk`.|  
|[SetContext, méthode](icordebugstackwalk-setcontext-method.md)|Définit le contexte actuel de l’objet `ICorDebugStackWalk` sur un contexte valide pour le thread.|  
|[Next, méthode](icordebugstackwalk-next-method.md)|Déplace l’objet `ICorDebugStackWalk` vers le frame suivant.|  
|[GetFrame, méthode](icordebugstackwalk-getframe-method.md)|Obtient le frame actuel dans l’objet `ICorDebugStackWalk`.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
