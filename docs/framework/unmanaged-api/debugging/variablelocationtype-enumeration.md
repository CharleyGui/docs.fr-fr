---
title: VariableLocationType, énumération
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 1c65efa006a8b2f4fb4db257b4ad2cde99c4e75e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725259"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType, énumération

Indique le type d’emplacement natif d’une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`VLT_REGISTER`|La variable se trouve dans un registre.|  
|`VLT_REGISTER_RELATIVE`|La variable se trouve dans un emplacement de mémoire relatif à un registre.|  
|`VLT_INVALID`|La variable n’est pas stockée dans un registre ou un emplacement de mémoire relatif à un registre.|  
  
## <a name="remarks"></a>Remarques  

 Un membre de l' `VariableLocationType` énumération est retourné par la méthode [ICorDebugVariableHome :: GetLocationType](icordebugvariablehome-getlocationtype-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
