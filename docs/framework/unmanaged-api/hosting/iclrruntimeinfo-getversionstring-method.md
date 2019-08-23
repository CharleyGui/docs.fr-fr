---
title: ICLRRuntimeInfo::GetVersionString, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a886106e5da49e7124dac5c8ea7416859aa441da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929845"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString, méthode
Obtient les informations de version de common language runtime (CLR) associées à une interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) donnée.  
  
 Cette méthode remplace les fonctions suivantes:  
  
- [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzBuffer`  
 à Version de compilation .NET Framework au format «v*A*. *B* [. *X*]». *A*, *B*et *X* sont des nombres décimaux qui correspondent à la version principale, à la version mineure et au numéro de Build. *X* est facultatif. Si *X* n’est pas présent, il n’y a aucun point final.  
  
> [!NOTE]
> Ce paramètre doit correspondre au nom de répertoire de la version .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.  
  
 Les exemples de valeurs sont «v 1.0.3705», «v 1.1.4322», «v 2.0.50727» et «v 4.0». *x*», où *x* dépend du numéro de Build installé. Notez que le préfixe «v» est obligatoire.  
  
 `pchBuffer`  
 [in, out] Spécifie la taille `pwzBuffer` de pour éviter les dépassements de mémoire tampon. Si `pwzBuffer` `pchBuffer` `pwzBuffer` a `null`la valeur, retourne la taille requise de pour autoriser la préallocation.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pwzBuffer` ou `pchBuffer` est null.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
