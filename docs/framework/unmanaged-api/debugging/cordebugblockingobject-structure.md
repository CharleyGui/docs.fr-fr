---
title: CorDebugBlockingObject, structure
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
ms.openlocfilehash: b16feb1af0d4975411876e78940d21096750d2ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726584"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject, structure

Définit un objet qui bloque un thread et la raison spécifique pour laquelle le thread est bloqué.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pBlockingObject`|Objet sur lequel le thread se bloque. Cet objet est valide uniquement pour la durée de l’état synchronisé actuel. Si deux threads se bloquent sur le même objet dans le même état synchronisé, vous pouvez vous attendre à ce que la méthode [ICorDebugValue :: GetAddress](icordebugvalue-getaddress-method.md) retourne la même valeur. Toutefois, les interfaces peuvent ou ne peuvent pas être équivalentes à un pointeur.|  
|`dwTimeout`|Nombre de millisecondes avant l’expiration du délai d’attente de l’opération de blocage, ou valeur infinie, qui indique qu’il n’expirera pas. La valeur du délai d’attente spécifie la durée totale de l’opération de blocage, et non pas la durée restante.|  
|`blockingReason`|Raison pour laquelle le thread est bloqué sur cet objet.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
