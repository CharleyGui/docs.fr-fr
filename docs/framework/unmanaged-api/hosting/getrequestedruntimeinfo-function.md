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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a6f6d6e73ce42c8c86d4e458322e5bd361f412
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778136"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo, fonction
Obtient des informations de version et au répertoire sur le common language runtime (CLR) demandée par une application.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4.  
  
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
 [in] Le nom de l’application.  
  
 `pwszVersion`  
 [in] Chaîne spécifiant le numéro de version du runtime.  
  
 `pConfigurationFile`  
 [in] Le nom du fichier de configuration qui est associé avec `pExe`.  
  
 `startupFlags`  
 [in] Une ou plusieurs de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) valeurs d’énumération.  
  
 `runtimeInfoFlags`  
 [in] Une ou plusieurs de la [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) valeurs d’énumération.  
  
 `pDirectory`  
 [out] Une mémoire tampon qui contient le chemin d’accès du répertoire à l’exécution en cas de réussite.  
  
 `dwDirectory`  
 [in] La longueur de la mémoire tampon du répertoire.  
  
 `dwDirectoryLength`  
 [out] Pointeur vers la longueur de la chaîne de chemin d’accès de répertoire.  
  
 `pVersion`  
 [out] Une mémoire tampon qui contient le numéro de version du runtime en cas de réussite.  
  
 `cchBuffer`  
 [in] La longueur du tampon de chaîne de version.  
  
 `dwlength`  
 [out] Pointeur vers la longueur de la chaîne de version.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur de composant COM (Object Model) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|ERROR_INSUFFICIENT_BUFFER|Le tampon de répertoire n’est pas suffisamment grand pour stocker le chemin d’accès de répertoire.<br /><br /> ou<br /><br /> Le tampon de version n’est pas suffisamment grand pour stocker la chaîne de version.|  
  
## <a name="remarks"></a>Notes  
 Le `GetRequestedRuntimeInfo` méthode retourne des informations d’exécution sur la version chargée dans le processus, ce qui n’est pas nécessairement la dernière version installée sur l’ordinateur.  
  
 Dans le .NET Framework version 2.0, vous pouvez obtenir des informations sur la dernière version installée à l’aide de la `GetRequestedRuntimeInfo` méthode comme suit :  
  
- Spécifiez le `pExe`, `pwszVersion`, et `pConfigurationFile` paramètres comme null.  
  
- Spécifiez l’indicateur RUNTIME_INFO_UPGRADE_VERSION dans le `RUNTIME_INFO_FLAGS` énumérations pour le `runtimeInfoFlags` paramètre.  
  
 Le `GetRequestedRuntimeInfo` méthode ne retourne pas la dernière version CLR dans les circonstances suivantes :  
  
- Il existe un fichier de configuration qui spécifie le chargement d’une version particulière du CLR. Notez que le .NET Framework utilisera le fichier de configuration même si vous spécifiez null pour le `pConfigurationFile` paramètre.  
  
- Le [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) méthode a été appelée en spécifiant une version antérieure du CLR.  
  
- Une application qui a été compilée pour une version antérieure du CLR est en cours d’exécution.  
  
 Pour le `runtimeInfoFlags` paramètre, vous pouvez spécifier uniquement une des constantes d’architecture de la `RUNTIME_INFO_FLAGS` énumération à la fois :  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeVersion, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, fonction](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
