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
ms.openlocfilehash: 0efda458d51677fcd16140cd0f0a835b76c20173
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617176"
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
 dans Nom du fichier de configuration associé à `pExe` .  
  
 `startupFlags`  
 dans Une ou plusieurs des [STARTUP_FLAGS](startup-flags-enumeration.md) valeurs d’énumération.  
  
 `runtimeInfoFlags`  
 dans Une ou plusieurs des [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) valeurs d’énumération.  
  
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
|ERROR_INSUFFICIENT_BUFFER|La mémoire tampon du répertoire n’est pas assez grande pour stocker le chemin d’accès au répertoire.<br /><br /> - ou -<br /><br /> La mémoire tampon de version n’est pas assez grande pour stocker la chaîne de version.|  
  
## <a name="remarks"></a>Notes  
 La `GetRequestedRuntimeInfo` méthode retourne des informations d’exécution sur la version chargée dans le processus, qui n’est pas nécessairement la version la plus récente installée sur l’ordinateur.  
  
 Dans la version 2,0 de .NET Framework, vous pouvez obtenir des informations sur la dernière version installée à l’aide de la `GetRequestedRuntimeInfo` méthode comme suit :  
  
- Spécifiez `pExe` les `pwszVersion` paramètres, et `pConfigurationFile` comme null.  
  
- Spécifiez l’indicateur RUNTIME_INFO_UPGRADE_VERSION dans les `RUNTIME_INFO_FLAGS` énumérations du `runtimeInfoFlags` paramètre.  
  
 La `GetRequestedRuntimeInfo` méthode ne retourne pas la dernière version du CLR dans les circonstances suivantes :  
  
- Un fichier de configuration d’application qui spécifie le chargement d’une version particulière du CLR existe. Notez que le .NET Framework utilisera le fichier de configuration, même si vous spécifiez NULL pour le `pConfigurationFile` paramètre.  
  
- La méthode [CorBindToRuntimeEx](corbindtoruntimeex-function.md) était appelée en spécifiant une version antérieure du CLR.  
  
- Une application qui a été compilée pour une version antérieure du CLR est en cours d’exécution.  
  
 Pour le `runtimeInfoFlags` paramètre, vous ne pouvez spécifier qu’une seule des constantes d’architecture de l' `RUNTIME_INFO_FLAGS` énumération à la fois :  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeVersion, fonction](getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, fonction](getversionfromprocess-function.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
