---
title: CorDebugExceptionFlags, énumération
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 352a45a33a109570f100e91a24cd44dc4f6780e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740151"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags, énumération
Fournit des informations supplémentaires sur une exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Il n'existe pas d'exception.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|L'exception peut être interceptée.<br /><br /> Le moment où se produit l'exception peut néanmoins être tel que le débogueur ne peut pas l'intercepter. Par exemple, s'il n'existe pas de code managé en dessous du rappel actif ou si l'événement d'exception provient d'un attachement juste-à-temps, l'exception ne peut pas être interceptée.|  
  
## <a name="remarks"></a>Notes  
 De nouvelles valeurs sont susceptibles d'être ajoutées dans les versions ultérieures : il est donc recommandé de préparer du code qui utilise `CorDebugExceptionFlags` pour les valeurs inattendues.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
