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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d6220270634dd8e2d15787d717020b8f6f86bb9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738328"
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
 [in] Pointeur vers une chaîne se terminant par null qui spécifie le module doit être exécuté par le processus lancé. Le module est exécuté dans le contexte de sécurité du processus appelant.  
  
 `lpCommandLine`  
 [in] Pointeur vers une chaîne se terminant par null qui spécifie la ligne de commande doit être exécuté par le processus lancé. Le nom de l’application (par exemple, « SomeApp.exe ») doit être le premier argument.  
  
 `lpProcessAttributes`  
 [in] Pointeur vers un Win32 `SECURITY_ATTRIBUTES` structure qui spécifie le descripteur de sécurité pour le processus. Si `lpProcessAttributes` est null, le processus obtient un descripteur de sécurité par défaut.  
  
 `lpThreadAttributes`  
 [in] Pointeur vers un Win32 `SECURITY_ATTRIBUTES` structure qui spécifie le descripteur de sécurité pour le thread principal du processus. Si `lpThreadAttributes` est null, le thread obtient un descripteur de sécurité par défaut.  
  
 `bInheritHandles`  
 [in] La valeur `true` pour indiquer que chaque handle pouvant être héritée dans le processus appelant est hérité par le processus lancé, ou `false` pour indiquer que les handles ne sont pas hérités. Les handles hérités ont les mêmes droits d’accès et la valeur en tant que les handles d’origine.  
  
 `dwCreationFlags`  
 [in] Une combinaison au niveau du bit de la [indicateurs de création de processus Win32](https://go.microsoft.com/fwlink/?linkid=69981) qui contrôlent la classe de priorité et le comportement du processus lancé.  
  
 `lpEnvironment`  
 [in] Pointeur vers un bloc d’environnement pour le nouveau processus.  
  
 `lpCurrentDirectory`  
 [in] Pointeur vers une chaîne se terminant par null qui spécifie le chemin complet vers le répertoire actif pour le processus. Si ce paramètre est null, le nouveau processus aura le même lecteur actuel et le répertoire en tant que le processus appelant.  
  
 `lpStartupInfo`  
 [in] Pointeur vers un Win32 `STARTUPINFOW` structure qui spécifie la station Windows, bureau, les handles standards et l’apparence de la fenêtre principale pour le processus lancé.  
  
 `lpProcessInformation`  
 [in] Pointeur vers un Win32 `PROCESS_INFORMATION` structure qui spécifie les informations d’identification sur le processus de lancement.  
  
 `debuggingFlags`  
 [in] Une valeur de l’énumération CorDebugCreateProcessFlags qui spécifie les options de débogage.  
  
 `ppProcess`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugProcess qui représente le processus.  
  
## <a name="remarks"></a>Notes  
 Les paramètres de cette méthode sont les mêmes que celles de Win32 `CreateProcess` (méthode).  
  
 Pour activer le débogage en mode mixte non managé, définissez `dwCreationFlags` à DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Si vous souhaitez utiliser uniquement le débogage managé, ne définissez pas ces indicateurs.  
  
 Si le débogueur et le processus de débogage (le processus attaché) partagent une même console, et si le débogage d’interopérabilité est utilisé, il est possible pour le processus attaché à maintenir les verrous de console et l’arrêter à un événement de débogage. Le débogueur bloquera ensuite toute tentative d’utilisation de la console. Pour éviter ce problème, définissez l’indicateur CREATE_NEW_CONSOLE le `dwCreationFlags` paramètre.  
  
 Débogage d’interopérabilité n’est pas pris en charge sur les plateformes Win9x et non x86 plateformes basés sur IA-64 et AMD64.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
