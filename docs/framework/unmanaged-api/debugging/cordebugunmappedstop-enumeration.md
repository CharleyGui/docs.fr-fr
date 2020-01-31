---
title: CorDebugUnmappedStop, énumération
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: 23e168b0f322a580917c3fcfcb767a7d4d4628f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793887"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop, énumération
Spécifie le type de code non mappé qui peut déclencher un arrêt dans l'exécution du code par l'exécution pas à pas.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`STOP_NONE`|Ne pas arrêter dans un type de code non mappé.|  
|`STOP_PROLOG`|Arrêtez dans le code de prologue.|  
|`STOP_EPILOG`|Arrêtez dans le code d’épilogue.|  
|`STOP_NO_MAPPING_INFO`|Arrêter dans le code qui n’a pas d’informations de mappage.|  
|`STOP_OTHER_UNMAPPED`|Arrêtez dans du code non mappé qui ne tient pas dans la catégorie prologue, épilogue, no-Mapping-information ou non managé.|  
|`STOP_UNMANAGED`|Arrêtez dans le code non managé. Cette valeur est valide uniquement avec le débogage d’interopérabilité.|  
|`STOP_ALL`|Arrêtez dans tous les types de code non mappé.|  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode [ICorDebugStepper :: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) pour définir les indicateurs qui spécifient le code non mappé dans lequel le pas à pas s’arrêtera.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
