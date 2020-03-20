---
title: GetVersionFromProcess, fonction
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178131"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess, fonction
Obtient le numéro de version de l’heure d’exécution de langue commune (CLR) qui est associée à la poignée de processus spécifiée.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hProcess`  
 [dans] Une poignée à un processus.  
  
 `pVersion`  
 [out] Un tampon qui contient la chaîne de numéro de version après avoir terminé la méthode.  
  
 `cchBuffer`  
 [dans] La longueur du tampon de version.  
  
 `pdwLength`  
 [out] Un pointeur sur la longueur de la chaîne de numéro de version.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`pVersion`est nul `cchBuffer` et n’est pas nul, ou vice versa.<br /><br /> -ou-<br /><br /> `hProcess`n’est pas une poignée valide à un processus.<br /><br /> -ou-<br /><br /> Le CLR n’est pas chargé.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`est nul ou inférieur à la longueur de la chaîne de version.|  
|E_NOTIMPL|Cette méthode n’est pas disponible sur le système d’exploitation Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeInfo, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
