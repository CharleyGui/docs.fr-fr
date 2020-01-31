---
title: ICorDebugModule2::SetJITCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: b28e457ea0b51d320581c0fbe36574698081ea36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792961"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags, méthode
Définit les indicateurs qui contrôlent la compilation juste-à-temps (JIT) de ce ICorDebugModule2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `dwFlags`  
 dans Combinaison d’opérations de bits des valeurs d’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Notes  
 Si la valeur `dwFlags` n’est pas valide, la méthode `SetJITCompilerFlags` échoue.  
  
 La méthode `SetJITCompilerFlags` peut être appelée uniquement à partir du rappel [ICorDebugManagedCallback :: LoadModule](icordebugmanagedcallback-loadmodule-method.md) pour ce module. Toute tentative d’appel de cette opération après la remise du rappel `ICorDebugManagedCallback::LoadModule` échoue.  
  
 Modifier & Continuer n’est pas pris en charge sur les plateformes 64 bits ou Win9x. Par conséquent, si vous appelez la méthode `SetJITCompilerFlags` sur l’une de ces deux plateformes avec l’indicateur CORDEBUG_JIT_ENABLE_ENC défini dans `dwFlags`, la méthode `SetJITCompilerFlags` et toutes les méthodes spécifiques à modifier & continuer, telles que [ICorDebugModule2 :: ApplyChanges](icordebugmodule2-applychanges-method.md), échouent.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
