---
title: ICorDebugRemote::CreateProcessEx, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744776"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx, méthode
Lance un processus sur un ordinateur distant sous le débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pRemoteTarget`  
 [in] Pointeur vers un [icordebugremotetarget, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Utilisé pour déterminer l’ordinateur distant sur lequel le processus sera lancé.  
  
 `lpApplicationName`  
 [in] Pointeur vers une chaîne se terminant par null qui spécifie le module doit être exécuté par le processus lancé. Le module est exécuté dans le contexte de sécurité du processus appelant.  
  
 `lpCommandLine`  
 [in] Pointeur vers une chaîne se terminant par null qui spécifie la ligne de commande doit être exécuté par le processus lancé.  
  
 `lpProcessAttributes`  
 [in] Non utilisé pour le débogage distant.  
  
 `lpThreadAttributes`  
 [in] Non utilisé pour le débogage distant.  
  
 `bInheritHandles`  
 [in] Non utilisé pour le débogage distant.  
  
 `dwCreationFlags`  
 [in] Non utilisé pour le débogage distant.  
  
 `lpEnvironment`  
 [in] Pointeur vers un bloc d’environnement pour le nouveau processus.  
  
 `lpCurrentDirectory`  
 [in] Pointeur vers une chaîne se terminant par null qui spécifie le chemin complet vers le répertoire actif pour le processus. Si ce paramètre est null, le nouveau processus aura le même lecteur actuel et le répertoire en tant que le processus appelant.  
  
 `lpStartupInfo`  
 [in] Non utilisé pour le débogage distant.  
  
 `lpProcessInformation`  
 [in] Non utilisé pour le débogage distant.  
  
 `debuggingFlags`  
 [in] Non utilisé pour le débogage distant.  
  
 `ppProcess`  
 [out] Pointeur vers l’adresse d’un objet « ICorDebugProcess Interface » qui représente le processus.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Lancé avec succès le processus sur l’ordinateur distant et retourné une « Interface ICorDebugProcess » pour le débogage.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible de lancer le processus sur l’ordinateur distant et retourner une « ICorDebugProcess Interface » pour le débogage.  
  
## <a name="remarks"></a>Notes  
 Le débogage en mode mixte n’est pas pris en charge dans Silverlight.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRemote, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
