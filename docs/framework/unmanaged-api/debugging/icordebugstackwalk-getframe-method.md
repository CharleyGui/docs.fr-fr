---
title: ICorDebugStackWalk::GetFrame, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 89576e2b3d5fb4df0cccfdd28c80a5cb67331597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791900"
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame, méthode
Obtient le frame actuel dans l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>Parameters  
 `pFrame`  
 dans Pointeur vers l’adresse de l’objet Frame créé qui représente le frame actuel dans la pile.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le runtime a correctement retourné le frame actuel.|  
|E_FAIL|Le frame actuel n’a pas été retourné.|  
|S_FALSE|Le frame actuel est un frame de pile natif.|  
|E_INVALIDARG|`pFrame` a la valeur null.|  
|CORDBG_E_PAST_END_OF_STACK|Le pointeur de frame est déjà à la fin de la pile ; par conséquent, il n’est pas possible d’accéder à des frames supplémentaires.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 `ICorDebugStackWalk` retourne uniquement les frames de pile réels. Utilisez la méthode [ICorDebugThread3 :: GetActiveInternalFrames,](icordebugthread3-getactiveinternalframes-method.md) pour retourner des frames internes. (Les frames internes sont des structures de données faisant l’objet d’un push dans la pile par le runtime pour stocker des données temporaires.)  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugStackWalk, interface](icordebugstackwalk-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
