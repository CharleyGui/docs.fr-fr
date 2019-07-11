---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd7c835cdc4b53c753d714216d1745eb0b80c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772932"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain, méthode
Définit les propriétés qui seront utilisées pour initialiser le domaine d’application par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `nProperties`  
 [in] Le nombre d’entrées dans `pwszPropertyNames` et `pwszPropertyValues`.  
  
 `pwszPropertyNames`  
 [in] Tableau de noms de propriété, ou null si aucune propriété. Actuellement, le seul nom de propriété qui est reconnu par cette méthode est « PARTIAL_TRUST_VISIBLE_ASSEMBLIES ».  
  
 `pwszPropertyValues`  
 [in] Un tableau de valeurs de propriété, ou null si aucune propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames` inclut un nom de propriété qui n’est pas reconnu par cette méthode.|  
  
## <a name="remarks"></a>Notes  
 La valeur de propriété pour « PARTIAL_TRUST_VISIBLE_ASSEMBLIES » est une liste d’assemblys qui ont l’instruction conditionnelle <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA) avec le <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> indicateur, qui doivent être visibles aux appelants partiellement approuvés dans l’application par défaut domaine.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
