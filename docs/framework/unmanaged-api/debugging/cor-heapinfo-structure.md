---
title: COR_HEAPINFO, structure
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: b6fd3682290c9752125aed7b9663c6704ade25de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132335"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO, structure
Fournit des informations générales sur le tas du récupérateur de mémoire, y compris s’il est ou non énumérable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`areGCStructuresValid`|`true` si les structures garbage collection sont valides et que le tas peut être énuméré ; Sinon, `false`.|  
|`pointerSize`|Taille, en octets, des pointeurs sur l’architecture cible.|  
|`numHeaps`|Nombre de tas de garbage collection logiques dans le processus.|  
|`concurrent`|`TRUE` si la garbage collection simultanée (arrière-plan) est activée ; Sinon, `FALSE`.|  
|`gcType`|Membre de l’énumération [cordebuggctype,](cordebuggctype-enumeration.md) qui indique si le garbage collector s’exécute sur une station de travail ou sur un serveur.|  
  
## <a name="remarks"></a>Notes  
 Une instance de la structure `COR_HEAPINFO` est retournée en appelant la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) .  
  
 Avant d’énumérer des objets sur le tas garbage collection, vous devez toujours vérifier le champ `areGCStructuresValid` pour vous assurer que le tas est dans un État énumérable. Pour plus d’informations, consultez la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) .  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
