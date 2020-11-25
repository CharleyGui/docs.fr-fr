---
title: ICorDebugRemote::DebugActiveProcessEx, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: c9847fd6122aa32c95aecd5643a62a6775ae38d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712116"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx, méthode

Lance un processus sur un ordinateur distant sous le débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pRemoteTarget`  
 dans Pointeur vers une [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md). Ce paramètre est utilisé pour déterminer l’ordinateur sur lequel le processus est en cours d’exécution.  
  
 `id`  
 dans ID du processus auquel le débogueur doit être attaché.  
  
 `win32Attach`  
 [in] `true` Si le débogueur doit se comporter comme le débogueur Win32 pour le processus et distribuer les rappels non managés ; Sinon, `false` .  
  
 `ppProcess`  
 à Pointeur vers l’adresse d’un objet « ICorDebugProcess » qui représente le processus auquel le débogueur a été attaché.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK  
 Attachement réussi au processus sur l’ordinateur distant.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible d’attacher au processus sur l’ordinateur distant.  
  
## <a name="remarks"></a>Remarques  

 Le débogage en mode mixte n’est pas pris en charge dans Silverlight.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRemote, interface](icordebugremote-interface.md)
- [ICorDebug, interface](icordebug-interface.md)

- [Interfaces de débogage](debugging-interfaces.md)
