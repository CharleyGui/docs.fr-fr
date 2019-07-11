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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af933be9edc0d0fe7249f33800fe259ddc779aeb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738316"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach, méthode
Retourne un HRESULT qui indique si le lancement d’un nouveau processus ou l’attachement au processus existant spécifié est possible dans le contexte de la configuration actuelle de l’ordinateur et d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwProcessId`  
 [in] L’ID d’un processus existant.  
  
 `win32DebuggingEnabled`  
 [in] Transmettez `true` si vous envisagez de démarrer avec le débogage Win32 activé ou à joindre avec le débogage Win32 activé ; sinon, passez `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si les services de débogage déterminent que lancer un nouveau processus ou l’attachement au processus donné est possible, étant donné les informations sur la configuration actuelle de l’ordinateur et d’exécution. Les valeurs HRESULT possibles sont :  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Notes  
 Cette méthode est purement informative. L’interface pas vous empêchera de lancement ou l’attachement à un processus, indépendamment de la valeur retournée par `CanLaunchOrAttach`.  
  
 Si vous envisagez de démarrer avec le débogage Win32 activé ou attacher avec activation du débogage Win32, passer `true` pour `win32DebuggingEnabled`. Le HRESULT retourné par `CanLaunchOrAttach` peut être différent si vous utilisez cette option.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
