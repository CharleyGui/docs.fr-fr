---
title: ICorDebug::CanLaunchOrAttach, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 195c7e1e7c61fd6ac8a21226b52e3782d2f7e421
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723491"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach, méthode

Retourne un HRESULT qui indique si le lancement d’un nouveau processus ou l’attachement au processus existant spécifié est possible dans le contexte de la configuration d’ordinateur et d’exécution actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwProcessId`  
 dans ID d’un processus existant.  
  
 `win32DebuggingEnabled`  
 dans Transmettez `true` si vous envisagez de lancer avec le débogage Win32 activé ou pour attacher le débogage Win32 activé ; sinon, Pass `false` .  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si les services de débogage déterminent que le lancement d’un nouveau processus ou l’attachement au processus donné est possible, en fonction des informations relatives à la configuration actuelle de l’ordinateur et de l’exécution. Les valeurs HRESULT possibles sont les suivantes :  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Remarques  

 Cette méthode est purement informatif. L’interface ne vous empêche pas de lancer ou de s’attacher à un processus, quelle que soit la valeur retournée par `CanLaunchOrAttach` .  
  
 Si vous envisagez de lancer avec le débogage Win32 activé ou d’attacher avec le débogage Win32 activé, transmettez `true` pour `win32DebuggingEnabled` . Le HRESULT retourné par `CanLaunchOrAttach` peut différer si vous utilisez cette option.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)
