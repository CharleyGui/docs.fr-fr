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
ms.openlocfilehash: 5f71dfcdffaaa683ca4f2abebaa99115ef90e0ff
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378905"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk, interface
Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetContext, méthode](icordebugstackwalk-getcontext-method.md)|Retourne le contexte du frame actuel dans l' `ICorDebugStackWalk` objet.|  
|[SetContext, méthode](icordebugstackwalk-setcontext-method.md)|Définit le `ICorDebugStackWalk` contexte actuel de l’objet sur un contexte valide pour le thread.|  
|[Next, méthode](icordebugstackwalk-next-method.md)|Déplace l' `ICorDebugStackWalk` objet vers le frame suivant.|  
|[GetFrame, méthode](icordebugstackwalk-getframe-method.md)|Obtient le frame actuel dans l' `ICorDebugStackWalk` objet.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
