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
ms.openlocfilehash: 5400350e1c489ec4c2ff3cddf83a4f1a8a0c7947
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726598"
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
|`areGCStructuresValid`|`true` Si les structures garbage collection sont valides et que le tas peut être énuméré ; Sinon, `false` .|  
|`pointerSize`|Taille, en octets, des pointeurs sur l’architecture cible.|  
|`numHeaps`|Nombre de tas de garbage collection logiques dans le processus.|  
|`concurrent`|`TRUE` Si la garbage collection simultanée (arrière-plan) est activée ; Sinon, `FALSE` .|  
|`gcType`|Membre de l’énumération [cordebuggctype,](cordebuggctype-enumeration.md) qui indique si le garbage collector s’exécute sur une station de travail ou sur un serveur.|  
  
## <a name="remarks"></a>Remarques  

 Une instance de la `COR_HEAPINFO` structure est retournée en appelant la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) .  
  
 Avant d’énumérer des objets sur le tas garbage collection, vous devez toujours vérifier le `areGCStructuresValid` champ pour vous assurer que le tas est dans un État énumérable. Pour plus d’informations, consultez la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
