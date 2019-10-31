---
title: COR_ACTIVE_FUNCTION, structure
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: cbc272070e9eb6810b34ec1f3fdc9e944c624cd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132381"
---
# <a name="cor_active_function-structure"></a>COR_ACTIVE_FUNCTION, structure
Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread. Cette structure est utilisée par la méthode [ICorDebugThread2 :: GetActiveFunctions,](icordebugthread2-getactivefunctions-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pAppDomain`|Pointeur vers le propriétaire du domaine d’application du champ `ilOffset`.|  
|`pModule`|Pointeur vers le propriétaire du module du champ `ilOffset`.|  
|`pFunction`|Pointeur désignant le propriétaire de la fonction du champ `ilOffset`.|  
|`ilOffset`|Décalage MSIL (Microsoft Intermediate Language) du frame.|  
|`flags`|Réservé pour une future extensibilité.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
