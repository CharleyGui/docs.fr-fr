---
title: ICorDebugStackWalk::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: b89e968e9b12943c8192af3b280f8bd321a02110
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378790"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next, méthode
Déplace l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) vers le frame suivant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le runtime a été correctement déroulé au frame suivant (consultez la section Notes).|  
|E_FAIL|L' `ICorDebugStackWalk` objet n’a pas pu être avancé.|  
|CORDBG_S_AT_END_OF_STACK|La fin de la pile a été atteinte à la suite de ce déroulement.|  
|CORDBG_E_PAST_END_OF_STACK|Le pointeur de frame est déjà à la fin de la pile ; par conséquent, il n’est pas possible d’accéder à des frames supplémentaires.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarks  
 La `Next` méthode avance l' `ICorDebugStackWalk` objet jusqu’au frame appelant uniquement si le runtime peut dérouler le frame actuel. Dans le cas contraire, l’objet passe au frame suivant que le runtime est en mesure de dérouler.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugStackWalk, interface](icordebugstackwalk-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
