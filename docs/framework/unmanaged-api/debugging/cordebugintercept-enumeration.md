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
ms.openlocfilehash: 3d3d4af8e9ee073c0aefec418a3b53c4589adf0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729107"
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
  
## <a name="remarks"></a>Remarques  

 Utilisez la méthode [ICorDebugStepper :: SetInterceptMask,](icordebugstepper-setinterceptmask-method.md) pour établir les types de code qui peuvent être interceptés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
