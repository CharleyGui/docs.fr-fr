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
ms.openlocfilehash: 5e1c1b1984c63bedb3c073f45a7b9a3574afdcec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615681"
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
 dans Nombre d’entrées dans `pwszPropertyNames` et `pwszPropertyValues` .  
  
 `pwszPropertyNames`  
 dans Tableau de noms de propriété, ou null s’il n’y a pas de propriétés. Actuellement, le seul nom de propriété reconnu par cette méthode est « PARTIAL_TRUST_VISIBLE_ASSEMBLIES ».  
  
 `pwszPropertyValues`  
 dans Tableau de valeurs de propriété, ou null s’il n’existe aucune propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames`comprend un nom de propriété qui n’est pas reconnu par cette méthode.|  
  
## <a name="remarks"></a>Notes  
 La valeur de propriété pour « PARTIAL_TRUST_VISIBLE_ASSEMBLIES » est une liste d’assemblys qui ont l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut conditionnel (APTCA) avec l' <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> indicateur, qui doivent être rendus visibles aux appelants d’un niveau de confiance partiel dans le domaine d’application par défaut.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement](index.md)
- [ICLRDomainManager, interface](iclrdomainmanager-interface.md)
