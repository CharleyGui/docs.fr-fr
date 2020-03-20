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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178151"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo, fonction
Obtient des informations de version et d’annuaire sur l’heure d’exécution de langue commune (CLR) demandées par une application.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
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
 [dans] Le nom de l’application.  
  
 `pwszVersion`  
 [dans] Une chaîne spécifiant le numéro de version de l’exécution.  
  
 `pConfigurationFile`  
 [dans] Le nom du fichier de `pExe`configuration qui est associé à .  
  
 `startupFlags`  
 [dans] Une ou plusieurs des valeurs d’énumération [STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
  
 `runtimeInfoFlags`  
 [dans] Une ou plusieurs des valeurs d’énumération [RUNTIME_INFO_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)  
  
 `pDirectory`  
 [out] Un tampon qui contient le chemin d’annuaire vers le temps d’exécution une fois terminé.  
  
 `dwDirectory`  
 [dans] La longueur du tampon d’annuaire.  
  
 `dwDirectoryLength`  
 [out] Un pointeur sur la longueur de la chaîne de trajectoire d’annuaire.  
  
 `pVersion`  
 [out] Un tampon qui contient le numéro de version du temps d’exécution une fois terminé.  
  
 `cchBuffer`  
 [dans] La longueur du tampon de chaîne de version.  
  
 `dwlength`  
 [out] Un pointeur sur la longueur de la chaîne de version.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|ERROR_INSUFFICIENT_BUFFER|Le tampon d’annuaire n’est pas assez grand pour stocker le chemin d’annuaire.<br /><br /> - ou -<br /><br /> Le tampon de version n’est pas assez grand pour stocker la chaîne de version.|  
  
## <a name="remarks"></a>Notes   
 La `GetRequestedRuntimeInfo` méthode renvoie les informations en temps d’exécution sur la version chargée dans le processus, qui n’est pas nécessairement la dernière version installée sur l’ordinateur.  
  
 Dans la version cadre .NET 2.0, vous pouvez obtenir `GetRequestedRuntimeInfo` des informations sur la dernière version installée en utilisant la méthode comme suit:  
  
- Spécifier le `pExe`, `pwszVersion`, et `pConfigurationFile` les paramètres comme nuls.  
  
- Spécifier le drapeau `RUNTIME_INFO_FLAGS` RUNTIME_INFO_UPGRADE_VERSION dans les `runtimeInfoFlags` énumérations pour le paramètre.  
  
 La `GetRequestedRuntimeInfo` méthode ne renvoie pas la dernière version CLR dans les circonstances suivantes :  
  
- Il existe un fichier de configuration d’application qui spécifie le chargement d’une version CLR particulière. Notez que le cadre .NET utilisera le fichier `pConfigurationFile` de configuration même si vous spécifiez nul pour le paramètre.  
  
- La méthode [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a été appelée spécifiant une version CLR antérieure.  
  
- Une application qui a été compilée pour une version CLR antérieure est actuellement en cours d’exécution.  
  
 Pour `runtimeInfoFlags` le paramètre, vous ne pouvez spécifier qu’une seule des constantes d’architecture de l’énumération à la `RUNTIME_INFO_FLAGS` fois :  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeVersion, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, fonction](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
