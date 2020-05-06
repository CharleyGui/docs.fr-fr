---
title: CorDebugIntercept, énumération
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 18a5e337b6026a20a95b1c29f3d7bda5187efc66
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795857"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept, énumération
Indique les types de code qui peuvent être interceptés (c'est-à-dire pouvant faire l'objet d'un pas à pas détaillé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`INTERCEPT_NONE`|Aucun code ne peut être intercepté.|  
|`INTERCEPT_CLASS_INIT`|Un constructeur peut être intercepté.|  
|`INTERCEPT_EXCEPTION_FILTER`|Un filtre d'exception peut être intercepté.|  
|`INTERCEPT_SECURITY`|Le code qui applique la sécurité peut être intercepté.|  
|`INTERCEPT_CONTEXT_POLICY`|Une stratégie de contexte peut être interceptée.|  
|`INTERCEPT_INTERCEPTION`|Non utilisé.|  
|`INTERCEPT_ALL`|Aucun code ne peut être intercepté.|  
  
## <a name="remarks"></a>Notes   
 Utilisez la méthode [ICorDebugStepper :: SetInterceptMask,](icordebugstepper-setinterceptmask-method.md) pour établir les types de code qui peuvent être interceptés.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
