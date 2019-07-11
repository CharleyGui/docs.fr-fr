---
title: ICLRRuntimeInfo::GetRuntimeDirectory, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2455c896ebdc12f2bb92a30d55745f7bd5bc308a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765519"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>ICLRRuntimeInfo::GetRuntimeDirectory, méthode
Obtient le répertoire d’installation du common language runtime (CLR) associé à cette interface.  
  
 Cette méthode remplace la [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) fournie dans les versions de .NET Framework 2.0, 3.0 et 3.5.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzBuffer`  
 [out] Retourne le répertoire d’installation de CLR. Le chemin d’installation est complet ; par exemple, « c:\windows\microsoft.net\framework\v1.0.3705\\».  
  
 `pchBuffer`  
 [in, out] Spécifie la taille du `pwzBuffer` pour éviter les dépassements de mémoire tampon. Si `pwzBuffer` a la valeur null, `pchBuffer` retourne la taille requise de `pwzBuffer`.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pwzBuffer` ou `pchBuffer` est null.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
