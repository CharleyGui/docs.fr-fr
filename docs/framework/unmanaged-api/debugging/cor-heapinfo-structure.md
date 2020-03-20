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
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179309"
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
|`areGCStructuresValid`|`true`si les structures de collecte des ordures sont valides et que le tas peut être énuméré; autrement, `false`.|  
|`pointerSize`|La taille, dans les octets, des pointeurs sur l’architecture cible.|  
|`numHeaps`|Le nombre de tas logiques de collecte des ordures dans le processus.|  
|`concurrent`|`TRUE`si la collecte simultanée des ordures (arrière-plan) est activée; autrement, `FALSE`.|  
|`gcType`|Un membre du [recensement CorDebugGCType](cordebuggctype-enumeration.md) qui indique si le collecteur d’ordures fonctionne sur un poste de travail ou un serveur.|  
  
## <a name="remarks"></a>Notes   
 Un exemple `COR_HEAPINFO` de la structure est retourné en appelant le [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) méthode.  
  
 Avant d’énumérer les objets sur le tas `areGCStructuresValid` de collecte des ordures, vous devez toujours vérifier le champ pour vous assurer que le tas est dans un état enumerable. Pour plus d’informations, voir la méthode [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
