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
ms.openlocfilehash: 11ff430c426c93f1c2a5c0582495e089a33995fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709802"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags, méthode

Définit les indicateurs qui contrôlent la compilation juste-à-temps (JIT) de ce ICorDebugModule2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwFlags`  
 dans Combinaison d’opérations de bits des valeurs d’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Remarques  

 Si la `dwFlags` valeur n’est pas valide, la `SetJITCompilerFlags` méthode échoue.  
  
 La `SetJITCompilerFlags` méthode peut être appelée uniquement à partir du rappel [ICorDebugManagedCallback :: LoadModule](icordebugmanagedcallback-loadmodule-method.md) pour ce module. Toute tentative de l’appeler une fois que le `ICorDebugManagedCallback::LoadModule` rappel a été remis échouera.  
  
 Modifier & Continuer n’est pas pris en charge sur les plateformes 64 bits ou Win9x. Par conséquent, si vous appelez la `SetJITCompilerFlags` méthode sur l’une de ces deux plateformes avec l’indicateur CORDEBUG_JIT_ENABLE_ENC défini dans `dwFlags` , la `SetJITCompilerFlags` méthode et toutes les méthodes spécifiques à modifier & continuer, telles que [ICorDebugModule2 :: ApplyChanges](icordebugmodule2-applychanges-method.md), échouent.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
