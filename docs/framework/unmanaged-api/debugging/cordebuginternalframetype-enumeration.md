---
title: CorDebugInternalFrameType, énumération
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: 2be827e12db765485ee889d6a4a19a982dad5d54
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778370"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType, énumération
Identifie le type de frame de pile. Cette énumération est utilisée par la méthode [ICorDebugInternalFrame :: GetFrameType,](icordebuginternalframe-getframetype-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`STUBFRAME_NONE`|Valeur null. La méthode `ICorDebugInternalFrame::GetFrameType` ne retourne jamais cette valeur.|  
|`STUBFRAME_M2U`|Frame stub managé vers non managé.|  
|`STUBFRAME_U2M`|Frame stub non managé vers managé.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Transition entre des domaines d’application.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Appel de méthode allégé.|  
|`STUBFRAME_FUNC_EVAL`|Début de l’évaluation de la fonction.|  
|`STUBFRAME_INTERNALCALL`|Appel interne dans le common language runtime.|  
|`STUBFRAME_CLASS_INIT`|Début d’une initialisation de classe.|  
|`STUBFRAME_EXCEPTION`|Exception levée.|  
|`STUBFRAME_SECURITY`|Frame utilisé pour la sécurité d’accès du code.|  
|`STUBFRAME_JIT_COMPILATION`|Le runtime fait la compilation juste-à-temps d’une méthode.|  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
