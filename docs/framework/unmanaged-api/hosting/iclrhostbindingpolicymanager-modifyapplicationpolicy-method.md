---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: 8da9c9fea5cf5b3a27eeb9d0222f0845c832b7da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714196"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode

Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pwzSourceAssemblyIdentity`  
 dans Identité de l’assembly à modifier.  
  
 `pwzTargetAssemblyIdentity`  
 dans Nouvelle identité de l’assembly modifié.  
  
 `pbApplicationPolicy`  
 dans Pointeur vers une mémoire tampon qui contient les données de stratégie de liaison de l’assembly à modifier.  
  
 `cbAppPolicySize`  
 dans Taille de la stratégie de liaison à remplacer.  
  
 `dwPolicyModifyFlags`  
 dans Combinaison logique ou de valeurs [EHostBindingPolicyModifyFlags,](ehostbindingpolicymodifyflags-enumeration.md) indiquant le contrôle de la redirection.  
  
 `pbNewApplicationPolicy`  
 à Pointeur vers une mémoire tampon qui contient les nouvelles données de stratégie de liaison.  
  
 `pcbNewAppPolicySize`  
 [in, out] Pointeur vers la taille de la nouvelle mémoire tampon de stratégie de liaison.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La stratégie a été modifiée avec succès.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` ou `pwzTargetAssemblyIdentity` était une référence null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` est trop petite.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 La `ModifyApplicationPolicy` méthode peut être appelée deux fois. Le premier appel doit fournir une valeur null pour le `pbNewApplicationPolicy` paramètre. Cet appel retourne la valeur nécessaire pour `pcbNewAppPolicySize` . Le deuxième appel doit fournir cette valeur pour `pcbNewAppPolicySize` et pointer vers une mémoire tampon de cette taille pour `pbNewApplicationPolicy` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRHostBindingPolicyManager, interface](iclrhostbindingpolicymanager-interface.md)
