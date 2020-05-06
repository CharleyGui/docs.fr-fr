---
title: CorDebugIlToNativeMappingTypes, énumération
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 808fc70a308eff1b05aa49ea2bb89fe53377c973
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795844"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a>CorDebugIlToNativeMappingTypes, énumération
Indique si une plage particulière d’instructions natives, représentées par une instance de la structure COR_DEBUG_IL_TO_NATIVE_MAP, correspond à une région de code spéciale.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`NO_MAPPING`|La plage d’instructions natives ne correspond à aucune région de code spéciale.|  
|`PROLOG`|La plage d’instructions natives correspond au prologue.|  
|`EPILOG`|La plage d’instructions natives correspond à l’épilogue.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetILToNativeMapping, méthode](icordebugcode-getiltonativemapping-method.md)
- [Énumérations de débogage](debugging-enumerations.md)
