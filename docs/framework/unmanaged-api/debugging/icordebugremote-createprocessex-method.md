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
ms.openlocfilehash: 4b2689f04228c9ecbbbb18531a0aefd3c40e3072
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377978"
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
 dans Pointeur vers une [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md). Utilisé pour déterminer l’ordinateur distant sur lequel le processus sera lancé.  
  
 `lpApplicationName`  
 dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le module à exécuter par le processus lancé. Le module est exécuté dans le contexte de sécurité du processus appelant.  
  
 `lpCommandLine`  
 dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie la ligne de commande devant être exécutée par le processus lancé.  
  
 `lpProcessAttributes`  
 dans Non utilisé pour le débogage distant.  
  
 `lpThreadAttributes`  
 dans Non utilisé pour le débogage distant.  
  
 `bInheritHandles`  
 dans Non utilisé pour le débogage distant.  
  
 `dwCreationFlags`  
 dans Non utilisé pour le débogage distant.  
  
 `lpEnvironment`  
 dans Pointeur vers un bloc d’environnement pour le nouveau processus.  
  
 `lpCurrentDirectory`  
 dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le chemin d’accès complet au répertoire actif du processus. Si ce paramètre a la valeur null, le nouveau processus aura le même lecteur et le même répertoire en cours que le processus appelant.  
  
 `lpStartupInfo`  
 dans Non utilisé pour le débogage distant.  
  
 `lpProcessInformation`  
 dans Non utilisé pour le débogage distant.  
  
 `debuggingFlags`  
 dans Non utilisé pour le débogage distant.  
  
 `ppProcess`  
 à Pointeur vers l’adresse d’un objet « interface ICorDebugProcess » qui représente le processus.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le processus a été lancé sur l’ordinateur distant et a retourné une « interface ICorDebugProcess » pour le débogage.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible de lancer le processus sur l’ordinateur distant et de retourner une « interface ICorDebugProcess » pour le débogage.  
  
## <a name="remarks"></a>Remarks  
 Le débogage en mode mixte n’est pas pris en charge dans Silverlight.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRemote, interface](icordebugremote-interface.md)
- [ICorDebug, interface](icordebug-interface.md)

- [Interfaces de débogage](debugging-interfaces.md)
