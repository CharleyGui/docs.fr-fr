---
title: GetRequestedRuntimeInfo, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136325"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo, fonction
Obtient les informations de version et de répertoire relatives au common language runtime (CLR) demandé par une application.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pExe`  
 dans Nom de l’application.  
  
 `pwszVersion`  
 dans Chaîne spécifiant le numéro de version du Runtime.  
  
 `pConfigurationFile`  
 dans Nom du fichier de configuration associé à `pExe`.  
  
 `startupFlags`  
 dans Une ou plusieurs des valeurs de l’énumération [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .  
  
 `runtimeInfoFlags`  
 dans Une ou plusieurs des valeurs d’énumération [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) .  
  
 `pDirectory`  
 à Mémoire tampon qui contient le chemin d’accès au répertoire du runtime une fois l’opération terminée.  
  
 `dwDirectory`  
 dans Longueur de la mémoire tampon de répertoire.  
  
 `dwDirectoryLength`  
 à Pointeur vers la longueur de la chaîne du chemin d’accès du répertoire.  
  
 `pVersion`  
 à Mémoire tampon qui contient le numéro de version du runtime en cas de réussite.  
  
 `cchBuffer`  
 dans Longueur de la mémoire tampon de la chaîne de version.  
  
 `dwlength`  
 à Pointeur vers la longueur de la chaîne de version.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|ERROR_INSUFFICIENT_BUFFER|La mémoire tampon du répertoire n’est pas assez grande pour stocker le chemin d’accès au répertoire.<br /><br /> ou<br /><br /> La mémoire tampon de version n’est pas assez grande pour stocker la chaîne de version.|  
  
## <a name="remarks"></a>Notes  
 La méthode `GetRequestedRuntimeInfo` retourne des informations d’exécution sur la version chargée dans le processus, qui n’est pas nécessairement la version la plus récente installée sur l’ordinateur.  
  
 Dans la version 2,0 de .NET Framework, vous pouvez obtenir des informations sur la dernière version installée à l’aide de la méthode `GetRequestedRuntimeInfo` comme suit :  
  
- Spécifiez les paramètres `pExe`, `pwszVersion`et `pConfigurationFile` comme null.  
  
- Spécifiez l’indicateur RUNTIME_INFO_UPGRADE_VERSION dans les énumérations `RUNTIME_INFO_FLAGS` pour le paramètre `runtimeInfoFlags`.  
  
 La méthode `GetRequestedRuntimeInfo` ne retourne pas la dernière version du CLR dans les circonstances suivantes :  
  
- Un fichier de configuration d’application qui spécifie le chargement d’une version particulière du CLR existe. Notez que le .NET Framework utilisera le fichier de configuration, même si vous spécifiez NULL pour le paramètre `pConfigurationFile`.  
  
- La méthode [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) était appelée en spécifiant une version antérieure du CLR.  
  
- Une application qui a été compilée pour une version antérieure du CLR est en cours d’exécution.  
  
 Pour le paramètre `runtimeInfoFlags`, vous ne pouvez spécifier qu’une seule des constantes d’architecture de l’énumération `RUNTIME_INFO_FLAGS` à la fois :  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeVersion, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, fonction](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
