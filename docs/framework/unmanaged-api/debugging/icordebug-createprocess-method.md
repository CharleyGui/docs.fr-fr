---
title: ICorDebug::CreateProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
ms.openlocfilehash: b9ae2b36bff9b4a6c048a8de99fa7d09350b1401
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859709"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess, méthode
Lance un processus et son thread principal sous le contrôle du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `lpApplicationName`  
 dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le module à exécuter par le processus lancé. Le module est exécuté dans le contexte de sécurité du processus appelant.  
  
 `lpCommandLine`  
 dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie la ligne de commande devant être exécutée par le processus lancé. Le nom de l’application (par exemple, « SomeApp. exe ») doit être le premier argument.  
  
 `lpProcessAttributes`  
 dans Pointeur vers une structure `SECURITY_ATTRIBUTES` Win32 qui spécifie le descripteur de sécurité pour le processus. Si `lpProcessAttributes` a la valeur null, le processus obtient un descripteur de sécurité par défaut.  
  
 `lpThreadAttributes`  
 dans Pointeur vers une structure `SECURITY_ATTRIBUTES` Win32 qui spécifie le descripteur de sécurité pour le thread principal du processus. Si `lpThreadAttributes` a la valeur null, le thread obtient un descripteur de sécurité par défaut.  
  
 `bInheritHandles`  
 dans Affectez `true` la valeur pour indiquer que chaque handle pouvant être hérité dans le processus appelant est hérité par le processus `false` lancé, ou pour indiquer que les handles ne sont pas hérités. Les handles hérités ont la même valeur et les mêmes droits d’accès que les handles d’origine.  
  
 `dwCreationFlags`  
 dans Combinaison d’opérations de bits des [indicateurs de création de processus Win32](/windows/win32/procthread/process-creation-flags) qui contrôlent la classe de priorité et le comportement du processus lancé.  
  
 `lpEnvironment`  
 dans Pointeur vers un bloc d’environnement pour le nouveau processus.  
  
 `lpCurrentDirectory`  
 dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le chemin d’accès complet au répertoire actif du processus. Si ce paramètre a la valeur null, le nouveau processus aura le même lecteur et le même répertoire en cours que le processus appelant.  
  
 `lpStartupInfo`  
 dans Pointeur vers une structure `STARTUPINFOW` Win32 qui spécifie la station Windows, le bureau, les handles standard et l’apparence de la fenêtre principale pour le processus lancé.  
  
 `lpProcessInformation`  
 dans Pointeur vers une structure `PROCESS_INFORMATION` Win32 qui spécifie les informations d’identification sur le processus à lancer.  
  
 `debuggingFlags`  
 dans Valeur de l’énumération CorDebugCreateProcessFlags, qui spécifie les options de débogage.  
  
 `ppProcess`  
 à Pointeur vers l’adresse d’un objet ICorDebugProcess qui représente le processus.  
  
## <a name="remarks"></a>Notes   
 Les paramètres de cette méthode sont les mêmes que ceux de la méthode `CreateProcess` Win32.  
  
 Pour activer le débogage en mode mixte non managé, définissez `dwCreationFlags` sur DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Si vous souhaitez utiliser uniquement le débogage managé, ne définissez pas ces indicateurs.  
  
 Si le débogueur et le processus à déboguer (le processus attaché) partagent une console unique, et si le débogage d’interopérabilité est utilisé, il est possible que le processus attaché contienne des verrous de console et s’arrête à un événement de débogage. Le débogueur bloquera alors toute tentative d’utilisation de la console. Pour éviter ce problème, définissez l’indicateur CREATE_NEW_CONSOLE dans le `dwCreationFlags` paramètre.  
  
 Le débogage d’interopérabilité n’est pas pris en charge sur les plateformes Win9x et non-x86, telles que les plateformes basées sur IA-64 et AMD64.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)
