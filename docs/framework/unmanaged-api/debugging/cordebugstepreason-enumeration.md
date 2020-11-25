---
title: CorDebugStepReason, énumération
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 50903b3737c0fc63eda2b1190e4c3d961ce3ae7b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726039"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason, énumération

Indique le résultat d'une étape individuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`STEP_NORMAL`|Exécution pas à pas terminée normalement, au sein de la même fonction.|  
|`STEP_RETURN`|L’exécution pas à pas a continué normalement, après le retour de la fonction.|  
|`STEP_CALL`|L’exécution pas à pas a continué normalement, au début d’une fonction récemment appelée.|  
|`STEP_EXCEPTION_FILTER`|Une exception a été générée et le contrôle a été passé à un filtre d’exception.|  
|`STEP_EXCEPTION_HANDLER`|Une exception a été générée et le contrôle a été passé à un gestionnaire d’exceptions.|  
|`STEP_INTERCEPT`|Le contrôle a été passé à un intercepteur.|  
|`STEP_EXIT`|Le thread s’est arrêté avant la fin de l’étape.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StepComplete, méthode](icordebugmanagedcallback-stepcomplete-method.md)
- [Énumérations de débogage](debugging-enumerations.md)
