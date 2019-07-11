---
title: COR_DEBUG_IL_TO_NATIVE_MAP, structure
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 238e59978bd084379fe6c0576107d674812bce8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740785"
---
# <a name="cordebugiltonativemap-structure"></a>COR_DEBUG_IL_TO_NATIVE_MAP, structure
Contient les décalages qui sont utilisés pour mapper du code MSIL (Microsoft Intermediate Language) à du code natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`ilOffset`|Le décalage du code MSIL.|  
|`nativeStartOffset`|Le décalage du début du code natif.|  
|`nativeEndOffset`|Le décalage de la fin du code natif.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorDebug.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetILToNativeMapping, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [GetILToNativeMapping, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
